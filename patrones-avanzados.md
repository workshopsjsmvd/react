# ✈️ Patrones avanzados

## Presentation y Container components

Es un patrón simple y muy útil en el desarrollo de aplicaciones react. A medida que ganamos experiencia en react surge casi de forma intuitiva utilizar este patrón. 

Te darás cuenta que el uso de componentes con react son mucho más fáciles de reutilizar y entender si los dividimos en dos grandes grupos: [Presentation y Container components](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0).

### Presentation components

Este tipo de componentes tiene la responsabilidad de renderizar la UI, son una especie de template. 

Deberán:

* Preocuparse por cómo se ven nuestra UI
* Contienen markdown HTML
* No manejan estado
* Recibe datos y funciones solamente por props
* Se escriben con funtions, rara vez se utiliza class component

### Container components

Este tipo de componentes tiene la responsabilidad de manejar el estado y la logica de la UI.

Deberán:

* Preocuparse por cómo funcionan las cosas
* Proporcionar los datos a los componentes de presentación
* Proporcionar funciones de comportamiento a los componentes de presentación
* Hacen peticiones HTTP o se comunican con los services que lo hacen

### Beneficios y un ejemplo

Listemos algunos beneficios de utilizar este patrón:

* Mejor separación de preocupaciones. Por un lado tenemos los template y por otro la lógica.
* Reutilización. Podemos usar el mismo componente de presentación con fuentes de estado completamente diferentes.
* Podemos darle los componentes de presentación a un diseñador, es casi HTML. Podrá trabajar en ellos.

### Ejemplo

Apliquemos el patrón al el ejemplo que escribimos en la sección anterior.

Originalmente teníamos esto.

```javascript
class FetchGithub extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: '',
      location: ''
    };
  }
​
  componentDidMount() {
    fetch('https://api.github.com/users/workshopsjsmvd')
      .then(res => {
        return res.json();
      })
      .then(res => {
        this.setState({
          name: res.name,
          location: res.location
        })
      });
  }
​
  render() {
    return [
      <h1 key="name">{`Nombre: ${this.state.name}`}</h1>,
      <h2 key="location">{`País: ${this.state.location}`}</h2>
    ];
  }
}
​
ReactDOM.render(
  <FetchGithub />,
  document.getElementById('root')
);
```

Luego de aplicar el patrón tendríamos esto.

```javascript
const FetchGithubTemplate = (props) => [
    <h1 key="name">{`Nombre: ${props.name}`}</h1>,
    <h2 key="location">{`País: ${props.location}`}</h2>
];

class FetchGithubContainer extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: '',
      location: ''
    };
  }
​
  componentDidMount() {
    fetch('https://api.github.com/users/workshopsjsmvd')
      .then(res => {
        return res.json();
      })
      .then(res => {
        this.setState({
          name: res.name,
          location: res.location
        })
      });
  }
​
  render() {
    return (
      <FetchGithubTemplate 
        name={this.state.name}
        location={this.state.location} 
      />
    );
  }
}
​
ReactDOM.render(
  <FetchGithubContainer />,
  document.getElementById('root')
);
```

Cómo verás nuestro componente FetchGithubTemplate nos quedo super abstracto, no depende de la API que utilicemos ni de cómo manejemos el state.

Para aprender más sobre este patrón ingresa aquí:

{% embed data="{\"url\":\"https://medium.com/@dan\_abramov/smart-and-dumb-components-7ca2f9a7c7d0\",\"type\":\"link\",\"title\":\"Presentational and Container Components\",\"description\":\"There’s a simple pattern I find immensely useful when writing React applications. If you’ve been doing React for a while, you have probably already discovered it. This article explains it well, but I…\",\"icon\":{\"type\":\"icon\",\"url\":\"https://cdn-images-1.medium.com/fit/c/304/304/1\*8I-HPL0bfoIzGied-dzOvA.png\",\"width\":152,\"height\":152,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://cdn-images-1.medium.com/max/1200/1\*TatfeANQMBmjrk\_nhKbZoA.jpeg\",\"width\":1200,\"height\":900,\"aspectRatio\":0.75}}" %}

## High Order Components

Los HoC son componentes que buscan abstraer funcionalidad que se repite en varios componentes, y agregarla como add ons a otros componentes que podemos ir creando. Más concretamente, un High Order Component es una función que toma como parámetro un componente, y devuelve otro componente.

Esto lo podemos ver con un ejemplo más concreto. Supongamos que tenemos un Form en donde se puse un nombre de usuario y un password, y al hacer click en el botón de Iniciar sesión, queremos que se muestre un componente de Loading, para darle un poco de feedback al usuario de que estamos trabajando.

```jsx
const React = require('react');
const PropTypes = require('prop-types');
const Loading = require('../Loading');

class Form extends React.Component {
    constructor(props) {
        super(props);
        this.onClick = this.onClick.bind(this);
        this.state = {
            showLoading: false
        }
    }
    onClick(e) {
        this.setState({
            showLoading: true
        })
    }

    render() {
        return (
            <div>
                <input type="text" name="user" />
                <input type="password" name="password" />
                <button onClick={this.onClick}>Login</button>
                { this.state.showLoading && <Loading />}
            </div>
        );
    }
}

module.exports = Form;

```

Con este código podemos lograr esto,  ¿pero qué sucede si tenemos otro componente que al hacer alguna otra acción?, ¿necesitamos hacer el mismo comportamiento? Aquí es donde entra el High Order Component. 

Veamos como queda:

```jsx
const React = require('react');
const LoadingComponent = require('..Loading');

const LoadingPlugin = (WrappedComponent) => class Loading extends React.Component {
    constructor(props) {
        super(props);
        this.showLoading = this.showLoading.bind(this);
        this.state = {
            isLoading: false
        };
    }
    showLoading() {
        this.setState({ isLoading: !this.state.isLoading });
    }

    render() {
        const props = Object.assign({}, this.props, this.state, { showLoading: this.showLoading });
        return [
            <WrappedComponent {...props} />,
            { this.state.isLoading && <LoadingComponent /> }
        ];
    }
};

module.exports = LoadingPlugin;
```

Por otro lado, actualizamos nuestro componente original:

```jsx
const React = require('react');
const PropTypes = require('prop-types');
const Loading = require('../LoadingPlugin');

class Form extends React.Component {
    onClick(e) {
        this.props.showLoading()
    }

    render() {
        return (
            <div>
                <input type="text" name="user" />
                <input type="password" name="password" />
                <button onClick={this.onClick}>Login</button>
            </div>
        );
    }
}

module.exports = Loading(Form);

```

Para aprender más sobre los HoC ingresa aquí:

{% embed data="{\"url\":\"https://reactjs.org/docs/higher-order-components.html\",\"type\":\"link\",\"title\":\"Higher-Order Components - React\",\"description\":\"A JavaScript library for building user interfaces\",\"icon\":{\"type\":\"icon\",\"url\":\"https://reactjs.org/favicon.ico\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://reactjs.org/logo-og.png\",\"width\":1200,\"height\":630,\"aspectRatio\":0.525}}" %}




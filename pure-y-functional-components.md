---
description: >-
  En esta sección aprenderás sobre cómo funciona un patrón muy utilizado en las
  aplicaciones construidas con react.
---

# ✈️ Patrones avanzados

## Introducción

Es un patrón simple y muy útil en el desarrollo de aplicaciones react. A medida que ganamos experiencia en react surge casi de forma intuitiva utilizar este patrón. 

Te darás cuenta que el uso de componentes con react son mucho mas faciles de reutilizar y entender si los dividimos en dos grandes grupos: [Presentation y Container components](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0).

## Presentation components

Este tipo de componentes tiene la responsabilidad de renderizar la UI, son una especie de template. 

Deberán:

* Preocuparse por cómo se ven nuestra UI
* Contienen markdown HTML
* No manejan estado
* Recibe datos y funciones solamente por props
* Se escriben con funtions, rara vez se utiliza class component

## Container components

Este tipo de componentes tiene la responsabilidad de manejar el estado y la logica de la UI.

Deberán:

* Preocuparse por cómo funcionan las cosas
* Proporcionar los datos a los componentes de presentación
* Proporcionar funciones de comportamiento a los componentes de presentación
* Hacen peticiones HTTP o se comunican con los services que lo hacen

## Beneficios y un ejemplo

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

Para aprender más sobre este patrón [ingresa aquí.](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0)


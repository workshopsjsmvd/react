---
description: >-
  En esta sección aprenderás a hacer llamados AJAX para traer data a la
  aplicación.
---

# 🦍 Haciendo un HTTP request con react

## Introducción

La primera pregunta que surge es ¿dónde y cómo hago los llamados AJAX? Respondamos esa pregunta.

Primero que nada aclarar que react no tiene una forma especial de hacer llamadas AJAX.

## Entonces, ¿cómo juega React en las llamadas AJAX?

React ni siquiera se enterará que vamos a hacer un llamado AJAX, no es una de sus responsabilidades. Simplemente renderiza elementos a partir de data, que se dividen en props y state.

Teniendo en cuenta esto, si necesitamos que nuestra aplicación utilice datos obtenidos desde una API, necesitamos obtener esos datos y pasarlos a los componentes vía state o props.

### Seleccionando una librería para hacer llamados HTTP

Ya que react no se encarga de hacer llamados HTTP necesitaremos una librería para hacerlos. Existen muchas opciones, veamos algunas de las más populares:

* [Axios](https://github.com/axios/axios) 
* [Superagent](https://github.com/visionmedia/superagent)
* [Fetch](https://github.com/github/fetch) \(es el standard y no es necesario instalar nada, es soportada por los navegadores\)

// es realmente la opcion favorita? XD creo que esto puede confundir un poco, en realidad fetch no lo debería usar nadie, es muy básico y no tiene mucha funcionalidad. capaz que pondria que para este ejemplo está bueno usar eso
Nuestra opción favorita es usar fetch y por eso la utilizaremos en el ejemplo, pero sientete libre de utilizar la que más te guste.

###  Obteniendo la data

Ahora que entendimos hasta dónde va la responsabilidad de react para los llamados AJAX, hagamos un ejemplo en donde traigamos data desde una API y la rendericemos en un componente.

En el ejemplo utilizaremos la [API de github ](https://developer.github.com/v3/search/)para obtener el nombre y el país de nuestro usuario.

```javascript
class FetchGithub extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: '',
      location: ''
    };
  }

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

  render() {
    return [
      <h1 key="name">{`Nombre: ${this.state.name}`}</h1>,
      <h2 key="location">{`País: ${this.state.location}`}</h2>
    ];
  }
}

ReactDOM.render(
  <FetchGithub />,
  document.getElementById('root')
);
```

Analicemos el código. Primero que nada podemos ver que en el **constructor** inicializamos el state, dónde guardaremos los datos que obtendremos desde la API.

En el **componentDidMount** es donde ocurre todo. Cómo vimos en secciones anteriores este método se ejecuta cuando se termine de montar el componente por primera vez\(sólo se ejecuta una vez\), es por eso que es un buen momento para hacer nuestros llamados AJAX. Allí usamos la [API nativa fetch ](https://developer.mozilla.org/es/docs/Web/API/Fetch_API)para obtener los datos de nuestro usuario de github.

Por último, luego de obtener los datos hacemos un setState para actualizar la interfaz.

## Práctico

Llevemos esto a la práctica, vamos a bla bla bla bla bla






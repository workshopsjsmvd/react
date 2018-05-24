# 🦁 Manipulando el dom con refs

## Introducción

Refs nos permite acceder a los elementos del DOM o a los elementos react creados en el método render.

En los casos típicos de componentes react las props son el medio de comunicación entre componentes padres e hijos. Para modificar un hijo, simplemente hacemos un re-render pasándole nuevas props. Pero en algunos casos necesitamos modificar un hijo al que no le podemos pasar una nueva prop. Para esos casos react provee refs.

### Dónde usar refs

Hay algunos casos comunes de uso de refs, nombremos algunos:

* Para manejar focus, selección de texto o controles multimedia
* Para lanzar animaciones
* Para interactuar con librerías de terceros

Siempre que puedas evita utilizar refs, esta pensado para utilizar en casos que no podamos solucionar con props, state y funciones.

## Creando un refs

Los refs se crean utilizando React.createRef\(\) y se relacionan al  elemento con la propiedad ref.

Veamos un ejemplo.

```javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.myRef = React.createRef();
  }
  render() {
    return <div ref={this.myRef} />;
  }
}
```

### Accediendo al ref

Cuando se pasa una prop ref a un elemento en el método render, se accede al nodo en el atributo current de la referencia.

```javascript
const node = this.myRef.current;
```

Para aprender mas sobre cómo utilizar refs puedes ingresar aquí:

{% embed data="{\"url\":\"https://reactjs.org/docs/refs-and-the-dom.html\",\"type\":\"link\",\"title\":\"Refs and the DOM - React\",\"description\":\"A JavaScript library for building user interfaces\",\"icon\":{\"type\":\"icon\",\"url\":\"https://reactjs.org/favicon.ico\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://reactjs.org/logo-og.png\",\"width\":1200,\"height\":630,\"aspectRatio\":0.525}}" %}




# 💾 13\) Haciendo uso del State

## Introducción

Hasta ahora veníamos viendo cómo podíamos cargar contenido dinámico en nuestros componentes a partir de las props. Ahora vamos a ver cómo podemos utilizar el state y cuáles son las diferencias con las props.

Al igual que con las props, con el state podemos hacer que nuestro componente cambie la forma en que se comporta o renderiza. 

## ¿Qué es el state?

State es un objeto JS interno a cada componente, que intenta representar el estado actual del componente. Dicho estado puede cambiar dependiendo de la funcionalidad de la aplicación, puede cambiar por una interacción externa por ejemplo de un usuario, una llamada Ajax, etc.

El state es privado a cada componente y es controlador internamente por el componente. Las props de los componentes pueden afectar como se inicializa este estado, pero luego de que se inicializa el componente, el estado es completamente manejado internamente.

## Props vs State

Las props son definidas en el momento que se crea el componente, ya sea por JSX o por JavaScript. Son simplemente un parámetro que recibe la función que crea nuestro componente. El state, solo vive dentro de nuestro componente, es un dato privado de los class component. Esa es la principal diferencia entre props y state.

Cuando pensamos en props, pensamos en datos de iniciación de un componente. Cuando pensamos en state, pensamos en datos internos del componente que pueden cambiar y modificar su comportamiento. Un componente no puede modificar el valor de sus props, pero si el de su state.

## Un ejemplo

Veamos un ejemplo clásico en donde necesitamos utilizar el state. Imagina que necesitas crear un componente Clock que debe ser reutilizable y encapsulado. Debe tener la capacidad de configurar su temporizador y actualizarse cada un segundo.

Primero intentemos hacerlo sin el uso del state:

```javascript
const Clock = (props) => (
  <div>
    <h1>Hello, world!</h1>
    <h2>It is {props.date.toLocaleTimeString()}.</h2>
  </div>
);
 
const tick = () => {
  ReactDOM.render(
    <Clock date={new Date()} />,
    document.getElementById('root')
  );
}

setInterval(tick, 1000);
```

Cómo veras nuestro reloj funciona. PERO no cumplimos con un requerimiento clave para las aplicaciones orientadas a componentes: **Clock debe ser un componente encapsulado y reutilizable**, debe saber configurarse el mismo y actualizarse cada un segundo. En el ejemplo Clock no sabe actualizarse, simplemente renderiza lo que le llega por props.

Para lograrlo, necesitamos utilizar el state, veamos cómo hacerlo.

### Functional component a class component

Para utilizar el state, lo primero que debemos hacer es convertir nuestro functional component Clock en un class component.

Los pasos para convertirlo son 5:

1. Crear un ES6 class, con el mismo nombre, que extienda de React.Component.
2. Agregar un método render\(\).
3. Mover el cuerpo de la function dentro del método render\(\).
4. Remplazar la variable props por this.props dentro de render\(\).
5. Eliminar la function.

```javascript
class Clock extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.props.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
```

Clock ahora está definido cómo una clase en lugar de cómo una function, esto nos permite utilizar las funciones adicionales que trae React.Component entre ellas el state.

### Agregándole state

Ahora pasaremos el valor que nos llega en this.props.date al state. Para ellos seguiremos 3 pasos.

1. Remplazar this.props.date por this.state.date en el método render

```javascript
class Clock extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
```

2. Agregamos un constructor de class que inicie el state

```javascript
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
```

**Nota el detalle del llamado a super\(props\).**

3. Eliminar la prop date del elemento Clock

```javascript
ReactDOM.render(
  <Clock />,
  document.getElementById('root')
);
```

El resultado de todos estos cambios es algo así:

```javascript
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}

ReactDOM.render(
  <Clock />,
  document.getElementById('root')
);
```

Ahora haremos que el temporizador se configure y actualice cada un segundo.

### setState

Necesitamos actualizar el valor de this.state.date cada 1 segundo, con el método setState que nos provee React.Component podemos mutar el state cada 1 segundo para actualizar.

React cada vez que se mute el state, hará un render del componente y con eso lograremos actualizar la UI cada 1 segundo.

Veamos cómo quedaría la implementación completa de nuestro Clock.

```javascript
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
    
    setInterval(
      () => this.setState({ date: new Date() }),
      1000
    );
  }
  
  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}

ReactDOM.render(
  <Clock />,
  document.getElementById('root')
);
```

Listo, ya tenemos nuestro componente reutilizable y encapsulado.

#### Nota

No es recomendable agregar lógica dentro del constructor, en la siguiente sección veremos cómo mejorar el código de nuestro Clock utilizando los lifecycle  methods de react.

Para aprender más sobre state ingresa aquí:

{% embed data="{\"url\":\"https://reactjs.org/docs/state-and-lifecycle.html\",\"type\":\"link\",\"title\":\"State and Lifecycle - React\",\"description\":\"A JavaScript library for building user interfaces\",\"icon\":{\"type\":\"icon\",\"url\":\"https://reactjs.org/favicon.ico\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://reactjs.org/logo-og.png\",\"width\":1200,\"height\":630,\"aspectRatio\":0.525}}" %}

## Práctico

Llevemos esto a la práctica:

{% embed data="{\"url\":\"https://github.com/workshopsjsmvd/react/tree/master/practico/steps/handling-events.html\",\"type\":\"link\",\"title\":\"workshopsjsmvd/react\",\"description\":\"react - Workshop sobre React\",\"icon\":{\"type\":\"icon\",\"url\":\"https://github.com/fluidicon.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://avatars1.githubusercontent.com/u/38766393?s=400&v=4\",\"width\":240,\"height\":240,\"aspectRatio\":1}}" %}




# ♻️ Ciclo de vida de los componentes

## Introducción

Al igual que las cosas en el mundo real, los componentes pasan por ciertas etapas: creación, crecimiento o modificación y destrucción. Veamos que pasa cada vez que un componente se renderiza. 

Todos los componentes al renderizarse pasan por 4 grandes fases:

1. Iniciación
2. Montado
3. Actualización
4. Desmontado

En cada una de estas fases se ejecutan diferentes métodos que veremos a continuación.

### Iniciación

Es lo primero que ocurre. El primer método que se llama en esta fase es el **constructor**\(cómo vimos en la sección anterior del workshop\). En este método es donde iniciamos nuestro componente, por ejemplo: su state, sus props default, se bindean métodos, etc.

Un error común\(que cometimos en la sección anterior\) es agregar lógica dentro de este método, se recomienda no hacerlo, para ello hay otros métodos que veremos a continuación.

### Montado

La fase de iniciación es seguida por la fase de montado. El primer método que se ejecuta es el **componentWillMount** y es usado para lo mismo que el constructor. Cómo verás no tiene mucho sentido y por eso el equipo de react anunció que será deprecado en React v17.

Lo que le sigue al componentWillMount es el método **render** que ya hemos utilizado anteriormente. Este método monta el componente en el DOM.

Luego de que el componente es montado en el DOM se ejecuta **componentDidMount,** este método es muy utilizado. Una particularidad es que se ejecuta una sola vez en todo el ciclo de un componente, es por eso que se utiliza por ejemplo para hacer llamados AJAX.

En resumen la fase de montado es el siguiente:

1. **componentWillMount \(será deprecado en react v17\)**
2. **render**
3. **componentDidMount**

### Actualización

Una vez que el componente esta montado entra en la fase de actualización. Estos métodos se ejecutan cuando el componente sufre algún tipo de modificación.

El primero que se ejecuta es el **componentWillReceiveProps\(newProps\)**. Este método se llama cada vez que cambia alguna prop de las que recibe el componente, recibe cómo parámetro las nuevas props. Este método también será deprecado en la v17 de react.

El siguiente método que se ejecuta es el **shouldComponentUpdate\(nextProps, nextState, nextContext\).** Por defecto el componente se actualizará cada vez que reciba nuevas props, cambie el state o el [context](https://reactjs.org/docs/context.html). Si nosotros creemos que es innecesario actualizar el componente podemos hacer que este método retorne **false**, eso evita que se ejecute el método render.

Luego se ejecuta el método **componentWillUpdate\(nextProps, nextState\)** que también será deprecado en la v17 de react.

Luego, al igual que en la fase de montaje tenemos se ejecuta el método **render**.

Si el método render se ejecuta correctamente se llamará al método **componentDidUpdate.** Aquí se suelen ejecutar llamadas AJAX o algún tipo de lógica post update.

Desde react 16 tenemos un método nuevo llamado **componentDidCatch\(errorString, errorInfo\).** Este método funciona de forma muy similar al clásico try/catch, en caso de que ocurra un error al actualizar el componente se ejecutará. Podemos utilizarlo por ejemplo en un componente padre que sepa hacer el manejo de errores de nuestra aplicación. Recibe dos parámetros:

* errorString: contiene el mensaje del error
* errorInfo: es un objecto que contiene el componentStack para detectar donde ocurrió el error

#### Aclaración sobre componentDidCatch

Escuchara solamente los errores de sus componentes hijos.

En resumen la fase de actualización es el siguiente:

1. **componentWillReceiveProps \(será deprecado en react v17\)**
2. **shouldComponentUpdate**
3. **componentWillUpdate \(será deprecado en react v17\)**
4. **render**
5. **componentDidUpdate**
6. **componentDidCatch \(solo si ocurre un error en un hijo\)**

### Desmontado

Por último tenemos la fase de desmontado. Se ejecuta cada vez que un componente será quitado del DOM.

Esta fase se compone de un solo método y es el **componentWillUnmount**.

Es común utilizar este método por ejemplo para eliminar los temporizadores o quitar eventos sobre el DOM, como escuchar un scroll o resize.

## Un ejemplo

Ahora que conocemos todas las fases por las que pasa un componente react, actualicemos el ejemplo que hicimos en la sección anterior.

Hasta ahora tenemos un componente Clock que inicializa el temporizador en el método constructor, cómo ya dijimos eso es un error. Veamos que es lo que teníamos:

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
​
ReactDOM.render(
  <Clock />,
  document.getElementById('root')
);
```

Para corregir el error deberíamos pasar el setInterval al método **componentDidMount** y limpiarlo en el **componentWillUnmount.** Veamos cómo quedaría.

```javascript
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }
  
  componentDidMount() {
    var intervalId = setInterval(
      () => this.setState({ date: new Date() }),
      1000
    );
    this.setState({ intervalId });
  }
  
  componentWillUnmount() {
    clearInterval(this.state.intervalId);
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
​
ReactDOM.render(
  <Clock />,
  document.getElementById('root')
);
```

Listo, ya tenemos nuestro Clock finalizado.

## Práctico

Llevemos esto a la práctica:

{% embed data="{\"url\":\"https://github.com/workshopsjsmvd/react/tree/master/practico/steps/life-cycle\",\"type\":\"link\",\"title\":\"workshopsjsmvd/react\",\"description\":\"react - Workshop sobre React\",\"icon\":{\"type\":\"icon\",\"url\":\"https://github.com/fluidicon.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://avatars1.githubusercontent.com/u/38766393?s=400&v=4\",\"width\":240,\"height\":240,\"aspectRatio\":1}}" %}




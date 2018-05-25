# 🤡 8\) Condicionando un render

## ¿Cómo lo hacemos?

Es muy común que en nuestra aplicaciones queramos condicionar secciones de la UI dependiendo de algunas condiciones.

El [conditional render](https://reactjs.org/docs/conditional-rendering.html) en react funciona de la misma manera que las condicionales en JavaScript. Podemos utilizar un if o el [conditional operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator) para condicionar el render de un componente. 

Veamos un ejemplo. Imagina que tenemos un componente para dar un saludo a un usuario que ingresa a nuestra aplicación, en caso de que el ya este autenticado vamos a mostrarle un mensaje, en el caso de que no este autenticado le mostraremos otro mensaje.

```javascript
const UserGreeting = (props) => {
  return <h1>Welcome back!</h1>;
}

const GuestGreeting = (props) => {
  return <h1>Please sign up.</h1>;
}
```

Estos son los dos mensajes que mostraremos. Ahora crearemos un componente que utiliza los dos mensajes, y dependiendo de si esta autenticado o no muestra el que corresponde.

```javascript
const Greeting = (props) => {
  const isLoggedIn = props.isLoggedIn;
  if (isLoggedIn) {
    return <UserGreeting />;
  }
  return <GuestGreeting />;
}

ReactDOM.render(
  <Greeting isLoggedIn={false} />,
  document.getElementById('root')
);
```

Como verás, usamos el clásico if para condicionar un componente, sin trucos. Podríamos haberlo hecho utilizando el conditional operator de esta manera.

```javascript
const Greeting = (props) => {
  const isLoggedIn = props.isLoggedIn;
  return isLoggedIn ? <UserGreeting /> : <GuestGreeting />;
}
​
ReactDOM.render(
  <Greeting isLoggedIn={false} />,
  document.getElementById('root')
);
```

#### ¿Qué sucede si nuestro condicional lo queremos realizar dentro del componente?

React permite poner condicionales dentro del JSX:

```jsx
const Greeting = (props) => {
  const isLoggedIn = props.isLoggedIn;
  return { isLoggedIn ? <UserGreeting /> : <GuestGreeting /> };
}
​
ReactDOM.render(
  <Greeting isLoggedIn={false} />,
  document.getElementById('root')
);
```

También podemos hacer lo siguiente:

```jsx
const Greeting = (props) => {
  const isLoggedIn = props.isLoggedIn;
  return (
    <div>
      { isLoggedIn ? <UserGreeting /> : <GuestGreeting /> }
      { isLoggedIn && <span>Welcome!</span> }
    </div>;
}
​
ReactDOM.render(
  <Greeting isLoggedIn={false} />,
  document.getElementById('root')
);
```

Para ver aprender más sobre cómo condicionar un render puedes ingresar aquí:

{% embed data="{\"url\":\"https://reactjs.org/docs/conditional-rendering.html\",\"type\":\"link\",\"title\":\"Conditional Rendering - React\",\"description\":\"A JavaScript library for building user interfaces\",\"icon\":{\"type\":\"icon\",\"url\":\"https://reactjs.org/favicon.ico\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://reactjs.org/logo-og.png\",\"width\":1200,\"height\":630,\"aspectRatio\":0.525}}" %}


---
description: En esta sección aprenderás a condicionar el render de un componente (la UI).
---

# 🤡 Condicionando un render

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

Para ver aprender más sobre cómo condicionar un render puedes [ingresar aquí.](https://reactjs.org/docs/conditional-rendering.html)

// Acá agregaría una condicion dentro del componente, onda { isLoggedIn && bla bla} para mostrar como se puede usar el condicional dentro de ahi si
// en realidad lo que queres hacer es evitar el render de una sección del componente

## Práctico

Llevemos esto a la práctica, vamos a bla bla bla bla bla


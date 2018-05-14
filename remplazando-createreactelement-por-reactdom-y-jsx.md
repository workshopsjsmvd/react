---
description: >-
  En esta sección aprenderás que es JSX y porque es tan importante en el
  desarrollo de aplicaciones con React.
---

# 💣 Remplazando createElement por JSX

## Introducción

JSX es el standard para escribir aplicaciones con React. Analicemos esta declaración de variable:

```javascript
const element = <h1>Hello world!</h1>;
```

El contenido de la variable no es ni HTML ni es un String. Parece HTML pero realmente es una mezcla de JavaScript y HTML. 

Se llama JSX y es una extensión de JavaScript. Los creadores de React recomiendan usarlo para describir como debería ser la UI de un componente. Es parecido a un lenguaje de template, con la ventaja de que puedes agregarle todo el JavaScript que quieras, sin limitaciones.

Todo lo que escribimos en JSX se transforma en un "element" cómo vimos en el capítulo anterior. Esta transformación la hará con [Babel](https://babeljs.io/).

## ¿Por qué JSX?

No se requiere realmente usar JSX mientras se trabaja con aplicaciones React. Puedes desarrollar tus aplicaciones con createElement cómo vimos en el capitulo anterior. Pero usar JSX tiene ventajas.

Quizás se hizo popular por su sintaxis familiar, es casi como escribir HTML. La lógica de nuestra UI sea muy descriptiva y fácil de entender.

Analicemos este componente:

{% code-tabs %}
{% code-tabs-item title="with-jsx.js" %}
```javascript
<div>
  <img src={url} className='item-image' />
  <span className='item-description'>{title + description}</span>
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="without-jsx.js" %}
```javascript
React.createElement(
  'div',
  null,
  React.createElement('img', { src: url, className: 'item-image' }),
  React.createElement(
    'span',
    { className: 'item-description' },
    title + description
  )
);
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**Sin JSX** no queda del todo claro que es lo que está sucediendo. **Con JSX** visualizamos rápidamente como será la UI y además entendemos rápido desde donde se cargará la data. Es fácil entender lo que pasará con ese componente.

Cómo mencionamos, es una mezcla de JavaScript y HTML y por eso podemos incrustar variables o incluso código directamente en el template.

#### Agregando JavaScript

En el siguiente ejemplo verás como podemos condicionar la UI vía JavaScript dentro del JSX.

Si el usuario esta autenticado mostramos un botón de editar su perfil, sino un botón para contactarnos con el usuario del perfil que estamos visitando.

```javascript
<div className='profile'>
  <img src={url} />
  {isAuth ? <EditButton /> : <ContactButton />}
</div>
```

### Remplazando createElement por JSX

A continuación remplazaremos el código que hicimos en el capitulo anterior por JSX.

```javascript
<html>
    <body>
        <div id="app"></div>
        <script src="https://unpkg.com/react@16/umd/react.development.js"></script>
        <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
        <script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
        <script type="text/babel">
        const rootElement = document.getElementById('app');
        // const element = React.createElement(
        //    'div',
        //    {className: 'container'},
        //    'Hello word'
        // );
        const element = <div>Hello word</div>;
        ReactDOM.render(element, rootElement);
        </script>
    </body>
</html>
```

Cómo verás el código es mucho mas lindo. 

Además de incluir los scripts de React y React-Dom ahora agregamos [Babel](https://babeljs.io/). Babel transformará el código JSX en el código equivalente React.

En nuestro ejemplo Babel transforma el código JSX a lo siguiente:

```javascript
React.createElement(
    'div',
    null,
    'Hello word'
);
```

#### Contenido dinámico

Gracias a JSX y a su posibilidad de incrustar código JavaScript dentro de los template, podemos generar contenidos dinámicos en base a datos, condiciones, etc. A continuación se muestran algunos ejemplos, más adelante en el workshop profundizaremos.

* Haciendo que el contenido del componente sea dinámico

```javascript
const content = "Hello word";
const element = <div>{content}</div>;
```

* Clases dinámicas

```javascript
const content = "Hello word";
const style = "container";
const element = <div className={style}>{content}</div>;
```

* Pasándole propiedades

```javascript
const content = "Hello word";
const style = "container";
const props = {
    className: style,
    children: content,
};
const element = <div {...props}>;
```

![boom](.gitbook/assets/image.png)

Calma, más adelante veremos que es eso de las props y cómo darle estilos a nuestros componentes. 

Lo importante es que hayas entendido que es JSX y cómo funciona, para saber más [ingresa aquí.](https://reactjs.org/docs/introducing-jsx.html)




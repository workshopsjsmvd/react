---
description: >-
  En esta sección aprenderás como react maneja los componentes por debajo.
  Quizás nunca vuelvas a utilizar React.createElement pero es importante que
  entiendas cómo funciona.
---

# 🤓 Creando elementos HTML con React.createElement API

## Creando un elemento HTML sin React

Antes de empezar con react repasemos como haríamos el clásico Hello Word sin react, con vanilla JavaScript.

```markup
<html>
    <body>
        <div id="app"></div>
        <script>
        const rootElement = document.getElementById('app');
        const element = document.createElement('div');
        element.textContent = 'Hello word';
        element.className = 'container';
        rootElement.appendChild(element)
        </script>
    </body>
</html>
```

## Creando un elemento HTML con React

Los elementos con react se escriben de forma similar. El cambio principal esta en el document.createElement y en las propiedades de este elemento.

Lo primero que necesitamos es importar los scripts de [React y React-Dom](https://reactjs.org/docs/cdn-links.html), con ellos tenemos acceso a la API de react.

```markup
<html>
    <body>
        <div id="app"></div>
        <script src="https://unpkg.com/react@16/umd/react.development.js"></script>
        <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
        <script>
        const rootElement = document.getElementById('app');
        // const element = document.createElement('div');
        // element.textContent = 'Hello word';
        // element.className = 'container';
        // rootElement.appendChild(element)
        const element = React.createElement(
            'div',
            {className: 'container'},
            'Hello word'
        );
        ReactDOM.render(element, rootElement);
        </script>
    </body>
</html>
```

React.createElement recibe 3 parámetros básicos:

1. El tipo de elemento html
2. Las propiedades del elemento
3. El contenido del elemento

Un elemento creado con react es un object con propiedades, que luego ReactDOM sabe renderizar en el DOM. Para el ejemplo, este sería el object que se crea:

```javascript
{
  type: 'div',
  props: {
    className: 'container',
    children: 'Hello world'
  }
};
```

Para saber más sobre como funciona React por debajo puedes [ingresar aquí.](https://reactjs.org/docs/react-without-jsx.html)


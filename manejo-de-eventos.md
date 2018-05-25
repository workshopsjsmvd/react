# 💫12\) Manejo de eventos

## Handling Events

Manejar eventos con react es muy parecido a manejar eventos del DOM. Hay algunas pequeñas diferencias de sintaxis:

* React nombra a los eventos utilizando [camel case](https://en.wikipedia.org/wiki/Camel_case).
* Cuando utilizamos JSX pasamos una function al event handler, en el caso de HTML pasamos un string.

Veamos un ejemplo.

{% code-tabs %}
{% code-tabs-item title="with-html.html" %}
```javascript
<button onclick="execute()">
  Label
</button>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

En el código de arriba, estamos utilizando el DOM directamente, ahora veamos cómo sería utilizando JSX y un element de react.

{% code-tabs %}
{% code-tabs-item title="with-react.js" %}
```javascript
const execute = () => console.log('click');

<button onClick={execute}>
  Label
</button>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Cómo verás tiene algunos pequeños cambios. El primero es que cambiamos el nombre del evento onclick por onClick. El segundo es cómo pasamos la function que queremos ejecutar, en el caso de HTML se pasa un string, con react se pasa directamente la function.

[Estos](https://reactjs.org/docs/events.html) son todos los eventos que soporta react.

### Prevent default

Otra diferencia es que no podemos retornar false para evitar el comportamiento por defecto de un  elemento HTML. Esto es algo común cuando queremos ejecutar una function dentro de un &lt;a&gt; ya que por defecto el elemento &lt;a&gt; intenta navegar.

Imaginemos que tenemos un botón que es un elemento &lt;a&gt; de HTML. Queremos ejecutar una function cuando un usuario haga click en él y además queremos evitar que navegue. Veamos cómo lo haríamos con HTML y cómo con react.

Con HTML:

```markup
<a href="#" onclick="console.log('The button was clicked.'); return false">
  Click me
</a>
```

Con react:

```javascript
const handleClick = (event)=> {
    event.preventDefault();
    console.log('The button was clicked.');
};

const button = () => (
    <a href="#" onClick={handleClick}>
      Click me
    </a>
);
```

Como verás nuestra function handleClick recibe un parámetro event automáticamente. Event es un objeto que contiene toda la info del evento ocurrido, además nos brinda diferentes métodos cómo preventDefault\(\) para que utilicemos en nuestro event handler.

Si quieres aprender mas sobre cómo manejar los eventos en react ingresa aquí:

{% embed data="{\"url\":\"https://reactjs.org/docs/handling-events.html\",\"type\":\"link\",\"title\":\"Handling Events - React\",\"description\":\"A JavaScript library for building user interfaces\",\"icon\":{\"type\":\"icon\",\"url\":\"https://reactjs.org/favicon.ico\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://reactjs.org/logo-og.png\",\"width\":1200,\"height\":630,\"aspectRatio\":0.525}}" %}




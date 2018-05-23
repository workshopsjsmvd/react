# 💅 Dando estilo a nuestro  componente

## Estilos con react

Una de las cosas que hacemos cómo desarrolladores es dar estilos a nuestras aplicaciones. Con react tenemos dos formas de agregarle estilos a nuestros componentes, a continuación explicaremos cada uno de ellos.

### className prop

Todos los componentes react pueden recibir la propiedad [className](https://reactjs.org/docs/faq-styling.html) la cual funciona igual que el atributo class de los elementos HTML. 

Veamos un ejemplo.

```javascript
const component = () => <p className='text'>Hello word</p>
```

Como puedes ver, pasamos a nuestro componente la propiedad className que cómo dijimos anteriormente funciona exactamente igual que el atributo class de los elementos HTML. Esto quiere decir que en algún lado de nuestra aplicación tendremos un archivo CSS que contendrá una class text. 

Podría ser algo así.

{% code-tabs %}
{% code-tabs-item title="style.css" %}
```css
.text {
    color: red;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="component.js" %}
```javascript
const component = () => <p className='text'>Hello word</p>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

En este caso, el resultado es un texto de color rojo con la frase _Hello word_.

### style prop

Todos los componentes react pueden recibir la propiedad [style](https://reactjs.org/docs/dom-elements.html#style) la cual recibe un object con los estilos que deseamos agregar. React los agregará [inline en el HTML](https://www.w3schools.com/html/html_styles.asp) resultante.

Veamos un ejemplo.

```javascript
const style = {
    color: 'red',
    fontSize: 22,
};
const component = () => <p style={style}>Hello word</p>
```

El resultado será un elemento &lt;p&gt; con el estilo inline. El &lt;p&gt; contendrá un texto de color rojo y fuente tamaño 22px, con la frase _Hello word_.

Cómo habrás notado, las keys del object que le pasamos a la prop style deben estar escritos en [camel case](https://en.wikipedia.org/wiki/Camel_case). Otra particularidad es que los pixeles los estamos pasando como un number sin el 'px'.

Para aprender más puedes [ingresar aquí.](https://reactjs.org/docs/dom-elements.html#style)

#### Nota

En general, no se recomienda utilizar la prop style como medio principal para dar estilos a nuestra aplicación. Al igual que pasa en HTML los estilos inline no escalan.

Existen algunas librerías muy interesantes para apoyar a react en temas de estilos, estas son algunas de ellas: [styled-components](https://www.styled-components.com/), [css-modules](https://github.com/css-modules/css-modules), [JSS](http://cssinjs.org/), [Radium](https://github.com/FormidableLabs/radium).

## Práctico

Llevemos esto a la práctica!

{% embed data="{\"url\":\"https://github.com/workshopsjsmvd/react/tree/master/practico/steps/conditional-render\",\"type\":\"link\",\"title\":\"workshopsjsmvd/react\",\"description\":\"react - Workshop sobre React\",\"icon\":{\"type\":\"icon\",\"url\":\"https://github.com/fluidicon.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://avatars1.githubusercontent.com/u/38766393?s=400&v=4\",\"width\":240,\"height\":240,\"aspectRatio\":1}}" %}




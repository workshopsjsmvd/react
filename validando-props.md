# 👮 6\) Validando props

## PropTypes

A medida que nuestra aplicación crece, podemos detectar y prevenir muchos errores con la verificación de tipos. Algunas aplicaciones, utilizan extensiones de JavaScript como [Flow](https://flow.org/) o [TypeScript](https://www.typescriptlang.org/) para tipear toda la aplicación. Pero en el caso que no usemos estas extensiones, react tiene incorporado un validador de tipos para las props. 

Veamos un ejemplo:

```javascript
import PropTypes from 'prop-types';

const HelloWorld = (props) => <div>{props.content}</div>

HelloWorld.propTypes = {
  content: PropTypes.string.isRequired
};
```

PropTypes [exporta una gama de validadores](https://reactjs.org/docs/typechecking-with-proptypes.html) que pueden utilizarse para garantizar que los datos que reciba el componente sean válidos. 

En este ejemplo, estamos usando PropTypes.string. Cuando el componente reciba un valor no válido para sus propiedades se mostrará un error en la consola de JavaScript. 

_Por motivos de rendimiento, propTypes solo se comprueba en modo de desarrollo._

Por otro lado, también se pueden definir defaultProps para props que no son requeridas:

```jsx
import PropTypes from 'prop-types';

const HelloWorld = (props) => <div className={props.className}>{props.content}</div>

HelloWorld.propTypes = {
  content: PropTypes.string.isRequired,
  className: PropTypes.string
};

HelloWorld.defaultProps = {
  className: 'hello-world'
};
```

## Práctico

Llevemos esto a la práctica:

{% embed data="{\"url\":\"https://github.com/workshopsjsmvd/react/tree/master/practico/steps/prop-types\",\"type\":\"link\",\"title\":\"workshopsjsmvd/react\",\"description\":\"react - Workshop sobre React\",\"icon\":{\"type\":\"icon\",\"url\":\"https://github.com/fluidicon.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://avatars1.githubusercontent.com/u/38766393?s=400&v=4\",\"width\":240,\"height\":240,\"aspectRatio\":1}}" %}




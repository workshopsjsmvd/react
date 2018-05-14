---
description: En esta sección aprenderás a validar las propiedades que recibe un componente.
---

# 👮 Validando props

## PropTypes

A medida que nuestras aplicación crece, podemos detectar y prevenir muchos errores con la verificación de tipos. Algunas aplicaciones, utilizan extensiones de JavaScript como [Flow](https://flow.org/) o [TypeScript](https://www.typescriptlang.org/) para tipear toda la aplicación. Pero en el caso que no usemos estas extensiones, react tiene incorporado un validador de tipos. 

Veamos un ejemplo:

```javascript
import PropTypes from 'prop-types';

const HelloWord = (props) => <div>{props.content}</div>

HelloWord.propTypes = {
  content: PropTypes.string
};
```

PropTypes [exporta una gama de validadores](https://reactjs.org/docs/typechecking-with-proptypes.html) que pueden utilizarse para garantizar que los datos que reciba el componente sean válidos. 

En este ejemplo, estamos usando PropTypes.string. Cuando el componente reciba un valor no válido para sus propiedades se mostrará un error en la consola de JavaScript. 

_Por motivos de rendimiento, propTypes solo se comprueba en modo de desarrollo._

## Práctico

Llevemos esto a la práctica, vamos a bla bla bla bla bla


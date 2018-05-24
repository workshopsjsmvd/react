# 📝 Listas

## En JavaScript

Primero, repasemos cómo transformar las listas en JavaScript.

En el código de aquí debajo, tomamos una lista de números y utilizamos [map\(\)](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array/map) para duplicar los valores. Asignaremos el resultado devuelto por map\(\) a una nueva variable.

```javascript
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map((number) => number * 2);
console.log(doubled);
```

Este código imprimer \[2, 4, 6, 8, 10\] en consola.

En react transformar listas de valores en listas de elements es casi igual.

## Renderizando multiples componentes con React

Podemos crear una colección de elementos e incrustarlos en nuestro JSX con las llaves {}.

Siguiendo el ejemplo de los números, hagamos un componente que tome la lista de números y los convierta en react elements utilizando map\(\) y JSX.

```javascript
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>
  <li>{number}</li>
);
```

Ahora rendericemos la lista completa dentro de un elemento &lt;ul&gt;.

```javascript
ReactDOM.render(
  <ul>{listItems}</ul>,
  document.getElementById('root')
);
```

Este código muestra una lista entre 1 y 5.

### Componente de lista básico

Muchas veces necesitaremos renderizar listas dentro de nuestros componentes. Cambiemos un poco el ejemplo de los números y hagamos un componente que reciba una prop con una lista de números y renderice una lista ordenada.

```javascript
const NumberList = (props) => {
  const numbers = props.numbers;
  const listItems = numbers.map((number) =>
    <li>{number}</li>
  );
  return (
    <ul>{listItems}</ul>
  );
}

const numbers = [1, 2, 3, 4, 5];
ReactDOM.render(
  <NumberList numbers={numbers} />,
  document.getElementById('root')
);
```

Listo, funciona. Pero si mirás la consola veras un error que menciona que debes agregar una key a cada elemento de la lista. Solucionemos eso.

```javascript
const NumberList = (props) => {
  const numbers = props.numbers;
  const listItems = numbers.map((number) =>
    <li key={number.toString()}>{number}</li>
  );
  return (
    <ul>{listItems}</ul>
  );
}
​
const numbers = [1, 2, 3, 4, 5];
ReactDOM.render(
  <NumberList numbers={numbers} />,
  document.getElementById('root')
);
```

Las keys ayudan a react a identificar qué elementos han cambiado, se han agregado o se han eliminado de la lista.




# Migrando a Class Components!

## ¿Qué estaremos haciendo?
La idea es migrar el componente de Item que tenemos, asi como tambien nuestro componente principal a class components.

Cuando finalicemos este práctico nos debería quedar algo asi:

```jsx
const root = document.getElementById('root');

class Item extends React.Component {
    ...
}

class App extends React.Component {
    ...
} 

ReactDOM.render(<App />, root);
```
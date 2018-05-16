---
description: En esta sección aprenderás crear un formulario con react.
---

# 📝 Creando formularios

## Introducción

Los elementos form de HTML funcionan un poco diferente en react, eso se debe a que los form manejan casi que un estado propio en HTML. 

Imaginemos que tenemos un form para ingresar el un nombre.

```markup
<form>
  <label>
    Name:
    <input type="text" name="name" />
  </label>
  <input type="submit" value="Submit" />
</form>
```

Este formulario tiene el comportamiento por defecto de HTML. Cuando el usuario confirme el formulario intentará navegar a una nueva página, si quieres hacer eso en react este código simplemente funcionará. Pero en la mayoría de los casos no es lo que necesitamos, sino que queremos tener una function JavaScript que se ejecute cuando el usuario confirme el formulario pudiendo acceder a los datos que se ingresaron. En react esto se llama [controlled components.](https://reactjs.org/docs/forms.html)

### Controlled components

En HTML los elementos &lt;input&gt;, &lt;textarea&gt; y &lt;select&gt; mantienen su propio estado a partir de lo que el usuario ingresa. En react el estado de estos elementos se suele guardar dentro del state del componente y solo se modificará con el método setState\(\).

Todo input element cuyo valor es controlado por react es denominado un “controlled component”. 

Pasemos el ejemplo de arriba a un controlled component.

```javascript
class NameForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {value: ''};

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('A name was submitted: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Name:
          <input type="text" value={this.state.value} onChange={this.handleChange} />
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```

Presta atención a como el atributo **value** de nuestro input se obtiene desde el state del componente, esto nos da la ventaja de que el state de react es la única fuente de la verdad. El input recibe una prop **onChange** la cual es una funtion\(**handleChange**\)  que se ejecutara cada vez que el usuario escriba en el input, esta funtion recibe como parámetro event que dentro tiene el valor del input correspondiente.

En los controlled components cada mutación de estado en un input element tendrá una function handler asociada. Esto nos da control total sobre lo que sucede en nuestra aplicación.

Por último, presta atención a la funtion handleSubmit que se ejecutará cuando el usuario confirme el formulario. Esto sucede ****gracias a que enviamos **handleSubmit** dentro de la propiedad **onSubmit**.

Si quieres aprender más sobre cómo manejar formularios puedes [ingresar aquí](https://reactjs.org/docs/forms.html).

#### Uncontrolled component

Para manejar formularios existe otra técnica llamada uncontrolled component, esta no la veremos en el workshop pero puedes [aprender más aquí.](https://reactjs.org/docs/uncontrolled-components.html)

## Práctico

Llevemos esto a la práctica, vamos a bla bla bla bla bla


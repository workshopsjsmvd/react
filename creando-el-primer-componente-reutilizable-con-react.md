---
description: >-
  En esta sección aprenderás a crear un componente reutilizable. Veremos que son
  las props de un componente, esto es clave para poder reutilizar y construir
  aplicaciones con react.
---

# 🎉 Creando el primer componente reutilizable con React

## Arquitectura orientada a componentes

Las aplicaciones construidas con react tienen una [arquitectura orientada a componentes.](https://en.wikipedia.org/wiki/Component-based_software_engineering) Esto provee un nivel de abstracción mayor que colabora a que podamos tener muchos componentes reutilizables a lo largo de la aplicación, facilitando el desarrollo y el mantenimiento.

## Primer componente reutilizable

Vamos a crear nuestro primer componente reutilizable, en este ejemplo haremos una card utilizada en la home de Mercado Libre.

![promotion](.gitbook/assets/captura-de-pantalla-2018-05-14-a-las-15.36.54.png)

#### Componentes del componente

A simple vista podemos ver que este componente contiene varios sub componentes: **Imagen, categoría, título y botón.**

Si pensamos cómo podríamos estructurar este componente podríamos tener algo así:

```javascript
const HomeCard = (
    <Card>
        <Image src="https://cdn.mercadolibre.com/mercado-pago.png" />
        <Information>
            <Category description="POINT" />
            <Title description="ACEPTA TARJETAS" />
        </Information>
        <Button label="Ver más" />
    </Card>
);
```

Estos tags no son tags de HTML, sino que cada uno de ellos son un componente de nuestra propia aplicación. 

![components](.gitbook/assets/image%20%282%29.png)

Ya empezamos a entender cómo se estructuran las aplicaciones en react. Ahora necesitamos que nuestro componente pueda cargar la información dinámicamente, hasta ahora los datos están fijos por lo tanto no es un componente reutilizable.

### Pasando props a nuestro componente

Conceptualmente todo componente react es una function que recibe propiedades y retorna react elements.

```javascript
function HelloWord(props) {
    return <div>{props.text}</div>;
}
```

Babel transformará este código a:

```javascript
function HelloWord(props) {
    return React.createElement(
        "div",
        null,
        props.text
    );
}
```

#### Nuestro ejemplo

Sigamos con nuestro componente de ejemplo,  pensemos que props podríamos pasarle para hacer que el componente sea reutilizable.

```javascript
const HomeCard = (props) => (
    <Card>
        <Image src={props.image} />
        <Information>
            <Category description={props.category} />
            <Title description={props.description} />
        </Information>
        <Button label={props.buttonLabel} />
    </Card>
);
```

El componente ahora carga la información de manera dinámica, por lo tanto podemos utilizarlo desde varios lugares dentro de nuestra aplicación.

Para repasar sobre la importancia del uso de JSX veamos cómo sería escribir **nuestro componente sin JSX.**

```javascript
var HomeCard = function HomeCard(props) {
    return React.createElement(
        Card,
        null,
        React.createElement(Image, { src: props.image }),
        React.createElement(
            Information,
            null,
            React.createElement(Category, { description: props.category }),
            React.createElement(Title, { description: props.description })
        ),
        React.createElement(Button, { label: props.buttonLabel })
    );
};
```

### Utilizando nuestro componente

Ahora que hicimos reutilizable nuestro componente, hagamos un ejemplo sobre cómo utilizarlo.

```javascript
import HomeCard from './components/HomeCard';

<div>
    <HomeCard
        image="https://cdn.mercadolibre.com/mercado-pago.png"
        category="POINT"
        description="ACEPTA TARJETAS"
        buttonLabel="Ver más"
    />
    <HomeCard
        image="https://cdn.mercadolibre.com/diseno-deco.png"
        category="DISEÑO Y DECO"
        description="ESPACIOS DE DISEÑO"
        buttonLabel="Ver más"
    />
</div>
```

Hermoso, nuestro componente ya es completamente reutilizable. Esto lo logramos gracias a las props de react. 

Es importante tratar de dividir nuestra aplicación en componentes lo mas pequeños posibles, esto ayuda a que escribamos menos código, tengamos aplicaciones robustas, con menos bugs, testeables y fáciles de mantener.

## Práctico

Llevemos esto a la práctica, vamos a bla bla bla bla bla


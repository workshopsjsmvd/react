---
description: Bienvenidos nuevamente al workshop de ReactJs.
---

# 🤷 ¿Por qué aprender React?

## ¿Qué es React?

> A JavaScript library for building user interfaces

Es una librería de JavaScript que nos va a ayudar a construir interfaces de usuario. La interfaz de usuario es todo lo que "toca y ve" un usuario en una aplicación\(header, body, footer, botones, listas, imágenes, etc\).

### ¿Por qué JavaScript y React se adueñan del desarrollo de estas interfaces?

Desde hace un tiempo, las necesidades de las interfaces de usuarios han ido aumentando. Las aplicaciones son cada día mas complejas y ya no nos alcanza con tener páginas simples con HTML algo de JavaScript y CSS.

Hoy en día las aplicaciones son dinámicas, manejan datos, disparan muchos eventos, contienen animaciones complejas, se comunican con otros sistemas y muchas cosas más. ¿Todo esto se podría hacer con JavaScript vanilla? Si, se podría. ¿Vale la pena? No, esa opción tiene muchos problemas, por ejemplo: no escala, código ilegible, problemas de performance, etc.

### Evolución del front end

Antes de convencerte sobre porque utilizar React y porque es una buena opción dentro del desarrollo front end hablemos un poquito de cómo evolucionó JavaScript y como tomó todas estas responsabilidades.

#### 2005

Nos remontamos al año 2005, dónde quizás comenzó todo este cambio de la mano de el viejo y querido [jQuery](https://jquery.com/).

jQuery es una librería de JavaScript que como dice su slogan "escribe menos hace más" busca facilitar el desarrollo con JavaScript brindando una API más amigable que la API nativa del navegador. Soluciona problemas de compatibilidad entre navegadores, manejo de eventos, etc. 

Si hoy en día tenemos problemas entre diferentes navegadores, eventos, etc imagina en el año 2005. Esta librería era un super poder para el año 2005. Pero las interfaces se empezar a tener más complejidad y se fue quedando chica.

#### 2010

Para cubrir las necesidades que tenía jQuery llega [BackboneJS](http://backbonejs.org/). Se utilizaba como apoyo para jQuery, nos ayudaba a interactuar con datos, por ejemplo a trabajar con listas. jQuery se encargaba de la interfaz visual y Backbone se encargaba del trabajo con los datos de la aplicación.

#### 2012 llegan los frameworks

Si bien se lanzaron muchos, [Angular 1](https://angularjs.org/), [Ember](https://www.emberjs.com/) y [Meteor](https://www.meteor.com/) fueron los más importantes. Se crean para ayudarnos a lograr lo que hacíamos mezclando jQuery y Backbone pero de una manera más amigable. Cada uno de ellos es casi un lenguaje de programación en si mismo\(se que me van a criticar este comentario\),  cada uno tiene su manera de interactuar con los datos, manejar los eventos y dibujar los elementos HTML.

Es un enfoque muy interesante, pero recordemos que cada día las aplicaciones se ponen más complejas, los navegadores se optimizan y los requerimientos de los usuarios aumentan. Ese es un punto débil de los frameworks, al ser casi un lenguaje nuevo de programación, nuestras aplicaciones quedan atadas al avance del framework en si mismo y algunas veces no llevan el ritmo que quisiéramos.

#### Hoy 2018

Luego del largo camino recorrido, los desarrolladores llegamos a la conclusión de que debíamos poder escribir nuestras aplicaciones enfocadas a componentes. Toda la vida lo hicimos en el CSS, pero ahora también lo aplicamos a la lógica de las aplicaciones. Teniendo esto en mente los grandes protagonistas son [Angular 2](https://angularjs.org/), [VueJS](https://vuejs.org/) y [React](https://reactjs.org/).

Es un enfoque muy interesante para construir aplicaciones que escalen y puedan mantenerse en el tiempo.

### React

En este Workshop vas a aprender React y estas son algunas de las particularidades que hacen que sea una excelente opción.

#### Declarativo

Es declarativo. A continuación vemos un ejemplo de cómo podría estructurarse una aplicación.

{% code-tabs %}
{% code-tabs-item title="declarative.js" %}
```javascript
<MyApp>
    <Header>
        <Menu />
    </Header>
    <Main>
        <Products />
    </Main>
    <Footer />
</MyApp>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Cómo ves, es muy sencillo de leer y se entiende rápidamente lo que hace nuestra aplicación.

#### Basado en componentes

Crear aplicaciones con React es algo así como construir con Legos.

![aplicaci&#xF3;n con React](.gitbook/assets/xukfdats25fkziyhrnq677pife.jpg)

Imagina que cada ficha de Lego es un componente\(el header, el menu, el footer\). Para construir la aplicación basta con ir conectándolos unos con otro en el orden que corresponda. Cada componente puede ser tan grande o tan pequeño como tu quieras, cuando más pequeño sea, podrás mantenerlo mejor.

> Crear aplicaciones en React es como jugar con Legos. Me pagan por jugar con Legos - Martín

Cada componente debe funcionar por si mismo pero a la vez debe poder ser conectado fácilmente con los demás.

#### Independiente y dónde quieras

Algo muy interesado de React es que una vez que decides utilizarlo en una aplicación existente, no debes migrar toda tu aplicación a React. Migrarla puede ser un trabajo de días, meses o años.

Los creadores de React pensaron en que se pudiera utilizar de forma independiente. Imagina que tienes una aplicación desarrollada con Angular y deseas pasarte a React. Lo que puedes ir haciendo es escribir los componentes nuevos en React, ellos se integraran de forma transparente con el resto de tu aplicación, sin necesidad de tirar el código que ya tienes en Angular.

### Otros motivos

* **Creada y utilizada por Facebook**. Es una empresa con grandes ingenieros con una aplicación gigante. El hecho de que crearon React para ellos mismos otorga credibilidad a la librería.
* **Se utiliza muchísimo**. Si quieres conseguir un buen trabajo, debes aprender los lenguajes que se están utilizando el la industria. 
* **Se adapta a la nueva moda de programación funcional y reactiva.** Es un tema que esta muy de moda en la industria y ayuda a crecer como profesional.
* **Se puede utilizar en diferentes tipos de aplicaciones**. Con React no solo puede crear aplicaciones web, sino que también móviles con [React Native](https://facebook.github.io/react-native/) y realidad virtual con [React 360](https://facebook.github.io/react-360/).
* **Grandes empresas la utilizan.** Utilizado por Instagram, Netflix, Paypal, Apple, Airbnb, Mercado Libre, etc.

### Ecosistema

React tiene un gran ecosistema. Como dijimos hace un rato, React se encarga de la interfaz de usuario, pero en el desarrollo front end necesitamos resolver más cosas además de la UI, para ello existen algunas librerías que complementan a React:

* [Redux:](https://redux.js.org/introduction) Ayuda a manejar el estado de la aplicación.
* [React Native:](https://facebook.github.io/react-native/) Para construir aplicaciones móviles nativas.
* [React router:](https://github.com/ReactTraining/react-router)  Para manejar las rutas de la aplicación.
* [NextJs:](https://github.com/zeit/next.js/) Para hacer server side rendering.
* [Más](https://github.com/enaqx/awesome-react)


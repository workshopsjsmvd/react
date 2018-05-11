---
description: Bienvenidos nuevamente al workshop de ReactJs.
---

# 🤷 ¿Por qué aprender React?

## ¿Qué es React?

> A JavaScript library for building user interfaces

Es una librería de JavaScript que nos va a ayudar a construir interfaces de usuario. La interfaz de usuario es todo lo que "toca y ve" un usuario en una aplicación\(header, body, footer, botones, listas, imágenes, etc\).

### ¿Por qué JavaScript y React se adueñan del desarrollo de estas interfaces?

Desde hace un tiempo, las necesidades de las interfaces de usuarios han ido aumentando. Las aplicaciones son cada día mas complejas y ya no nos alcanza con tener páginas simples con HTML algo de JavaScript y CSS.

Hoy en día las aplicaciones son dinámicas, manejan datos, disparan muchos eventos, contienen animaciones complejas, se comunican con otros sistemas y muchas más cosas. ¿Todo esto se podría hacer con JavaScript vanilla? Si, se podría. ¿Vale la pena? No, esa opción tiene muchos problemas, por ejemplo: no escala, código ilegible, problemas de performance, etc.

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

Es un enfoque muy interesante, pero recordemos que cada día las aplicaciones se ponen más complejas, los navegadores se optimizan y los requerimientos de los usuarios aumentan. Ese es un punto débil de los frameworks, al ser casi que un lenguaje nuevo de programación, nuestras aplicaciones quedan atadas al avance del framework en si mismo y algunas veces no llevan el ritmo que quisiéramos.

#### Hoy 2018

Luego del largo camino recorrido, los desarrolladores llegamos a la conclusión de que debíamos poder escribir nuestras aplicaciones enfocadas a componentes. Teniendo esto en mente los grandes protagonistas son [Angular 2](https://angularjs.org/), [VueJS](https://vuejs.org/) y [React](https://reactjs.org/).

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

Cómo ves, es muy sencillo de leer y entender rápidamente que hace nuestra aplicación.

#### Basado en componentes




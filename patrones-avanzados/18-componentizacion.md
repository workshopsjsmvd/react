# 🎉 18\) Componentización

Un aspecto muy importante de React, incluso tal vez el más importante, es la premisa en la cual está basado, que es la Componentización.

El uso y reuso de componentes hace que esta librería pueda escalar de una manera sencilla, fácil de utilizar, y fomenta la reutilización, la encapsulación asi como también el testing y el mantenimiento.

Veamos un ejemplo práctico. Tenemos el siguiente componente que renderiza una lista de imágenes:

![](https://lh3.googleusercontent.com/eIF0r0qJtrj7r-iZX6CV6ATADu09_2k-uVTcuciez4EPV70brtzMzAx0cVff6wewRYmH8P6Fln_gWPYf5GYGScIQm34S7_vA08gKDpDxKG8tU73N-L9AhuBuxTUjuE8K5Lmw4e48JSI)

Parece sencillo no? Qué sucede si queremos cambiar la clase de cada imágen cuando image tiene una property booleana que se llama isDisabled? Y si queremos mostrar una imágen en mobile y otra en desktop?

![](https://lh3.googleusercontent.com/5j2CTZ4tiViBUuPPTh1Jj27H3U_qkoW6uTQNEBdBzzstK5Zk6wacym2qzB-4Rfx8WgBXx8coXDk1sGBdowM_KJeEHCPrXsqhtXqhPSyZPVorRj-eQ2GyKj29PuVM9zUaO9ji4TcDXAo)

Ya fue necesario modificar la función map y agregamos dos líneas para manejar las clases que queremos usar para cada imagen, asi como también la sección del src

Qué sucede ahora si queremos trackear cuantas veces el usuario hace click en estas imágenes?

![](https://lh4.googleusercontent.com/AsvVyXlxOw4OdBrRUwmAC1jeaHr8QF4pcYMzX3wV7bU5elmhHVgg_s7Rw7d91kYjK-wjRxXdL66OLTVhwik5wGVxn4L2SnnTJldgkFfuMwLx-TK1iQx0s8plnKeSOwJR0dFUPaSjFEg)

Fue necesario agregar un onClick a este Componente, lo cual ya lo hizo crecer en tamaño debido a que fue necesario agregar un constructor también. También, si vemos como quedó el código, la función onClick quedó a nivel del componente Images. Si alguien lee nuestro código, puede pensar que este evento es al hacer click en el Componente Images, y no en cada imágen.

Y si quisieramos no solo reportar que se hizo click, sino que además en que imágen se hizo click?



![](https://lh5.googleusercontent.com/sBYoHEDAjkwd_5xuPYJyeL9fJq_rGo-RRDNNgXfox53aytEMED5ekMHdCXwfZ2bQ0SEw0Wf7YdZhX_0JMj52I7gGDvz_iu8uBy5GEixNHQBa6hKlxW3fyQK7P4wm_sMbueFx6sk-kKo)

Para hacer esto, tuvimos que definir una función anónima a nivel de la imagen para que devuelva la imagen seleccionada. Queda raro no? Además, por ahora solo estamos imprimiendo la imagen, pero imaginense si también fuese necesario que al hacer click en la imagen, necesitamos marcarla como visitada. Esto implicaría recorrer esa lista de imágenes, buscar la imágen que fue clickeada y actualizar la información. Y si además quisieramos mostrar estas imágenes en un slider?

![](https://lh6.googleusercontent.com/DBN-i7kBfDi0g8oGIhM6Lmc40bvwo1IJLUkZdzAU8S4PrO0Ynph0KUOZmvSbYGBirrAkL-AgpBmoE6dHaGYuJIVoL07nx8IBnFyWiIwrEEM-gfhQmTtj68EJLsKXH4gnNffeOcMatQI)

 De todo esto, podemos concluir que:

* **El código del componente padre se comienza a mezclar con el del hijo, y comienza a generar un poco de confusión**
* **Existen 2 razones por las cuales podríamos tocar este componente, lo cual lo hace más difícil de mantener**
* **El padre comienza a manejar responsabilidades del hijo**
* **El testing pertinente a este componente comienza a hacerse más complejo**

Como quedaría este componente entonces?

![](https://lh5.googleusercontent.com/qgNHy_3SMARnm2jgFXEpIzzkTmeW05uBPJwnUrwRxMzlvZs8k04JQirs_ZWlZagyInj8eatbR-tPwa-1aLu5c5pcqKB-S9L2s28SA835U_wR0_oOvxoh5h0J17lAv4zGx9SMtgw2yn8)



![](https://lh6.googleusercontent.com/ta0RzVudzG_ghquuBmdbVKsnJfyvADyx4TnHVnnFMaMC41PjKSkOXFSSSWnKA-wpVhmJZRjqlqK0bk4BFSK09ErMgeszeRUSahH4DTXI51_YdaArkqTEY1W6J4vEfgQwrIf0QblL90M)


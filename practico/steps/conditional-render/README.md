# Listas, renders condicionales y estilos!

## ¿Qué estaremos haciendo?
Para aplicar lo que hemos aprendido hasta ahora, deberás realizar:
- A partir de una lista de items que se encuentra global (ver más abajo), hacer un render iterando por cada item, utilizando el componente que ya teníamos
- Para hacer el render, validar que el listado no sea vacío
- Agregar la imagen del item, la cantidad de items disponibles y el precio al componente. Siempre validar de que estos valores existan para renderizarlos!
- Usando estilos inline, agregar algún indicativo visual en verde en caso de que el item sea nuevo (item.condition === 'new')
- En caso de que esté agotado el item, mostrar algún indicativo del status
- Recuerda que por cada prop que agregues, deberás agregar una validación de prop types

Lista de items:
- Dentro del scope de la aplicación, se encuentra una variable que se llama `api`, que es un entrypoint a nuestros datos. Tiene los siguientes métodos:
    - get(): devuelve una lista de items
    - filter(text): filtra los resultados dependiendo de un texto, comparando contra el atributo `title` del item
- Cada item tiene los siguientes atributos:
    - id
    - title: string con el nombre del item
    - price: number, precio en UYU
    - available_quantity: cuantos items disponibles hay
    - condition: new || used
    - thumbnail: url de la imagen
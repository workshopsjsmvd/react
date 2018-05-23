# Life cycle!

## ¿Qué estaremos haciendo?
Para la siguiente iteración, lo que buscamos hacer es:
- Cuando la aplicación comience, queremos mostrar una publicación al comienzo del listado, y marcarla como "Publicación destacada". Para obtener ese producto, podemos usar el método api.getRandom
- Luego, cada 2 segundos, queremos que se actualice esa publicación con otra publicación aleatoria.
- Por último, queremos que, en caso de que la nueva publicación aleatoria sea igual a la anterior, que no se haga un render. Recuerda también tener en cuenta los otros elementos que estamos manejando en el state
- Para la publicación destacada, crear un componente separado.

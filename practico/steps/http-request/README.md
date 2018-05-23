# Requests!

## ¿Qué estaremos haciendo?
Lo que estaremos haciendo ahora es, cuando el usuario escribe un texto, se haga una request a la api de items de mercadolibre para obtener items y utilizar esa respuesta para mostrar los resultados. Para hacer esto debemos:
- En el método onChange se debe hacer una request a la api de mercadolibre (https://api.mercadolibre.com/sites/MLU/search) con los siguientes parámetros:
    - q=iphone => este parámetro determina el texto a buscar. Lo inicializamos en un valor para poder obtener el mismo resultado que estabamos mostrando previamente
    - limit=15 => cantidad de resultados que queremos que se devuelvan
- Dicho resultado lo guardamos nuestro helper api, ejecutando el método api.set(resultado de api), asi mantenemos el código que teníamos previamente y todo sigue funcionando
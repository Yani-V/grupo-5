A partir de un set de datos en formato de array de objetos, vamos a crear una API Rest para hacer consultas a un json de peliculas, respecto a la diferente información que contiene, como ser:
- codigo
- titulo
- categoría
- reparto
- genero
- sinopsis
- trailer (URL con el link al video en Youtube)

Vamos a utilizar distintos métodos:
- Get para obtener todas las peliculas
- Get especifico para obtener por titulo, categoria, reparto y trailer

Tambien vamos a utilizar funciones de orden superior

Con toda esta información, vamos a crear diferentes Endpoints que permiten consultar los datos.

En primera instancia creamos la estructura básica de un servidor web utilizando Express JS, incluyendo el archivo .ENV donde se almacena la variable de entorno con la ruta parcial + nombre del archivo de datos JSON, además del puerto de ejecución del servidor web.

El archivo JSON se guardo en una subcarpeta del proyecto llamada /database/

El número de puerto del servidor utilizado es 3008

Se carga el contenido del archivo JSON en una constante llamada TRAILERFLIX en formato Array de objetos (usando fileSystem API + JSON.parse para obtener y transformar los datos)

Se crea el contenido en formato texto de bienvenida para la ruta raíz del proyecto “/”.

Con la estructura base del proyecto ya desarrollada, creamos los endpoints necesarios para listar el catálogo de películas y series por diferentes posibles búsquedas.

* Creamos un endpoint llamado /catalogo que lista todo el contenido de trailerflix JSON. Se retorna todo el contenido del archivo.

* Creamos un endpoint llamado /titulo/:title que lista el catálogo de películas y/o series que se aproxima al título enviado, es decir, una busqueda parcial del nombre de la pelicula. Para este endopint se utilizaron rutas dinámicas, recibiendo como parámetro el título o parte de este. Para ello se aplica la función .filter(), el método includes() y toLowerCase() para normalizar la búsqueda. En caso de no encontrar ninguna coincidencia total o parcial se devuleve un json con el error y su descripcion

* Creamos un endpoint llamado /categoria/:cat que lista todo el contenido del archivo JSON de acuerdo a la categoría enviada como parámetro (serie o película).Para este endpoint utilizamos .filter() y retorna todos los resultados encontrados. (Aquí son dos posibles valores solamente)

* Crea un endpoint llamado /reparto/:act que liste el catálogo que incluya a la actriz o actor indicado por el nombre. (la búsqueda del nombre debe ser parcial) Para este endpoint aplicamos la misma lógica que la utilizada en el endpoint de title. Como resultado, retorna solo un array con la propiedad reparto y la propiedad título y sus respectivos datos (no todo el contenido)

* Creamos un endpoint llamado /trailer/:id que retorna la URL del trailer de la película o serie. Si ésta no posee video asociado, retorna un mensaje en formato JSON notificando la no disponibilidad del mismo. En caso de encotrarlo retorna las propiedades “id”, “titulo”, “trailer”. Como no todas las peliculas/series poseen la propiedad tráiler, se aplica el operador de acceso condicional {objeto?.trailer}


Vamos a usar
- Express
- Jsons
- FileSystems API
- Libreria dotenv
- Librería body-parser
- Método next()

# Instalacion
- npm i dotenv body-parser
- npm i express

# Estructura
- Carpeta src  
        - Carpeta database (contiene el archivo json)
        - Archivo con funciones que consume el archivo json (controladores)
-Archivo index.js
-Archivo package.json
-Archivo package-lock.json

# Pasos

- Creo package json
- Modifico el start 
- Creo env
- Creo archivo index.js
- Genero carpeta src
- Genero carpeta database
- Dentro de data base pego el json con todas las peliculas de trailerflix
- Genero archivo controlador: trailerflix.controller.js, con funciones para leer las peliculas
- Creamos archivo .gitignore



- Llamo a libreria dotenv
- Llamo a libreria body-parser
- Express que es nuestro framework (para trabajar el servidor)
- Genero la instancia del servidor
- Variable de entorno con puerto, si no lee la variable le da vlor 3008
- Genero variable DB para tener la base de datos, ya que trabajamos con un json


- Dentro del controlador: llamo a la libreria para leer las peliculas y defino funcion para leer las peliculas, transforma los datos para usar
 
- Se levanta MIDDLEWARE, dentro de el se coloca la funcion que lea y extraiga el contenido y que continue trabajando

- Defino const leerpeliculas en index.js

Se comienza a trabajar con las funciones:

- Se inicia servidor
- Funcion para manejar rutas inexistentes
- Metodo get generico para traer toda la informacion 
- Método get especifico para titulo



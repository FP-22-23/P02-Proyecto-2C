# Proyecto del Segundo Cuatrimestre Fundamentos de Programación (Curso 2022/23)
Autor/a: Jose Fornes Jimenez. uvus: kbw4222


## Estructura de las carpetas del proyecto

* **/src**: Contiene los diferentes archivos que forman parte del proyecto. Debe estar estructurado en los siguentes paquetes
  * **fp.videojuegos**: Paquete que contiene los tipos del proyecto y tests.
  * **fp.common**: Paquete que contiene los tipos auxiliares del proyecto
  * **fp.utiles**:  Paquete que contiene las clases de utilidad. 
* **/data**: Contiene el dataset o datasets del proyecto
    * **videojuegos.csv**: Datos de los videojuegos.
    
## Estructura del *dataset*

El dataset está compuesto por 8 columnas, con la siguiente descripción:

* **Nombre del juego**: de tipo String, representa el título del juego.
* **Fecha de lanzamiento**: de tipo LocalDate, representa la fecha de lanzamiento del videojuego.
* **Precio de salida**: de tipo Double, representa el precio de salida del videojuego.
* **Precio actual**: del tipo Double, representa el precio del videojuego actualmente.
* **Puntuacion**: de tipo Double, representa la puntuacion del videojuego.
* **Multijugador**: Boolean representa si el juego es multijugador o no.
* **Consola**: de tipo enumerate consola representa a la consola que pertenece el juego.
* **Compañia desarrolladora**: de tipo String representa la compañia que desarrollo el juego.
* **Juegos similares**: de tipo List<String> representa un listado de juegos similares

## Tipos implementados

# Tipo Base - Videojuego
Representa un Videojuego.

**Propiedades**:

- *titulo*: nombre del juego, de tipo String, consultable y editable.
- *autor*: autor de la foto, de tipo String, consultable y editable.
- *fechadelanzamiento*: fecha en la que se lanzo el juego, de tipo LocalDate, consultable y editable.
- *antiguedad*: antiguedad del videojuego de tipo int y propiedad derivada de fecha de lanzamiento, consultable y editable
- *descargas*: número de descargas de la foto, de tipo Integer, consultable y modificable.
- *Precios*: de tipo Precio representa los valores del videojuego cuando salio y en la actualidad, consultable y editable
- *puntuacion*: puntuacion del videojuego, de tipo Double, consultable y editable.
- *multijugador*: indica si el videojuego es o no multijugador, de tipo Bolean, consultable y editable.

**Constructores**: 

- C1: Constructor con un parámetro por cada propiedad básica del tipo.
- C2: Constructor con parámetros para título, fechadelanzamiento, precio.

**Restricciones**:
 
- R1: La fecha de lanzamiento tiene que ser posterior a la de hoy.
- R2: La puntuacion debe de ser superior o igual a 0.

**Criterio de igualdad**: dos fotos son iguales si tienen el mismo título, autor
y fecha de toma

**Criterio de ordenación**: las fotos se ordenan por su nombre, a igualdad de este
por su empresa, y a igualdad de este por su fecha de lanzamiento.

**Otras operaciones**:
- no hay.

# Tipos auxiliares

- **Consola**, enumerado. Puede tomar todos los tipos de consolas.
- **Precio**, tipo auxiliar. Tiene dos propiedades de tipo Double,
  *precio_de_salida* y *precio_actual*, consultables, y una operación *diferencia*
  que calcula la diferencia de precio entre dos videojuegos.

### Factoría
Representa una factoría para construir objetos de tipo Coleccion.

**Operaciones**:

- *public static List<Foto> leerVideojuegos(String fichero)*: lee el fichero y
devuelve una lista de videojuegos.
- *private static Videojuego parsearVideojuego(String cadena)*: parsea una cadena y construye un videojuego a partir de ella.
- *private static List<String> parsearSimilares(String similares)*: parsea una cadena y construye una lista de juegos similares a partir de ella.

### Tipo Contenedor

Representa una coleccion donde se almacenan los videojuegos

**Propiedades**:

- *nombre*: nombre del creador de la coleccion, de tipo String, consultable. 
- *nick*: nick del propietario de la coleccion, de tipo String, consultable. 
- *fecha*: fecha de creación de la coleccion, de tipo LocalDate, consultable. 
- *recomendado*: indica si el juego es recomendado a no por el usuario. 
- *videojuegos*: lista de videojuegos almacenadas en la coleccion, de tipo List<Videojuego>, consultable.

**Constructores**: 

- C1: Constructor con un parámetro por cada propiedad básica.
- C2: Constructor con un parámetro por cada propiedad básica excepto la fecha, que se inicializa con la fecha del día actual,
      y la lista de videojuegos, que se inicializa con una lista vacía.

**Restricciones**:
 
- R1: el nombre del usuario no puede estar vacío.

**Criterio de igualdad**: dos coleccion son iguales si tienen el mismo nombre del creador y pertenecen al mismo nick del usuario.

**Criterio de ordenación**: no hay.

**Otras operaciones**:

- *Integer getNumeroVideojuegos()*: obtiene el número de videojuegos que hay en la coleccion.
- *void añadeVideojuego(Videojuego j)*: añade un videojuego a la coleccion si aún no está en ella; si ya está, no hace nada.
- *void añadeVideojeugos(Collection<Videojuego> c)*: Añade una colección de videojuegos a la coleccion, sin añadir las que ya están en ella.
- *void eliminaVideojuego(Videojuego j)*: elimina un videojuego de la coleccion si está en ella; si no está, no hace nada.
- *Boolean contieneVideojuego(Videojuego j)*: indica si una coleccion contiene o no un videojuego dado, devolviendo true si lo contiene
   y false si no lo contiene.
   
- *Boolean existeVideojuegoconPreciosYFechadelanzamiento(LocalDate fecha, Precios precio, Double diferencia)*: devuelve true
   si existe al menos un videouego que fue lanzado en la fecha dada y tiene una diferencia de precio igual a la dada, y false en caso contrario.
- *Double getMediaPuntuacionConsola(Consola consola, Integer año)*: obtiene la media de puntuacion de los videojuegos de la consola dada.
- *List<String> getVideojuegosenAño(LocalDate fecha)*: obtiene un listado de los videojuegos que fueron lanzados en la fecha dada
- *Map<Consola, List<Videojuego>> getVideoJuegosPorConsola()*: obtiene un Map que relaciona cada consola con los videojuegos que hay en ella.
- *Double getPuntuacionMaxima*: obtiene la puntuacion maxima de la coleccion de videojuegos.

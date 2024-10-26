# Mi aprendizaje
En la presente práctica aprendí sobre el uso de volúmenes en Docker, que permiten almacenar, incluso cuando los contenedores se detienen o eliminan. 
Aprendí que existen distintos tipos de volumenes como: 
* Volúmenes en el host: que se vinculan a un directorio específico en el sistema de archivos del host, lo cual permite almacenar y acceder a los datos fuera del contenedor.
* Volúmenes nombrados: que son gestionados automáticamente por Docker, y permiten la persistencia de datos sin necesidad de especificar una ruta exacta en el sistema de archivos del host.
* Volúmenes anónimos: que Docker crea temporalmente y elimina cuando el contenedor deja de estar en uso.
  
Asi como su gestión por linea de comando.

Además, aprendí a crear una red personalizada en Docker para permitir la comunicación entre múltiples contenedores, como la que utilicé para levantar un servidor Drupal y conectarlo con un servidor de base de datos PostgreSQL. Esto implica vincular los volúmenes correctos para que Drupal pueda almacenar archivos y configuraciones de manera persistente, facilitando así la administración de contenido y datos en un entorno aislado.
.

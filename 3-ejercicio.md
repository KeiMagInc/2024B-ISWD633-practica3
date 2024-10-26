## Esquema para el ejercicio
![Imagen](img/esquema-ejercicio3.PNG)

### Crear red net-wp
```
docker network create net-wp
```

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
En el esquema del ejercicio, la carpeta del contenedor (a) es /var/lib/mysql.
Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
La carpeta db del host contendrá los archivos de la base de datos de MySQL, que incluyen las tablas y datos almacenados, permitiendo la persistencia de datos.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
```
docker run -d --name mysql-container --network net-wp -e MYSQL_ROOT_PASSWORD=root_password -e MYSQL_DATABASE=wordpress_db -e MYSQL_USER=wp_user -e MYSQL_PASSWORD=wp_password -v C:/Users/SoloParaKerlly/Desktop/ejercicio3/db:/var/lib/mysql mysql:8
```
![image](https://github.com/user-attachments/assets/716c6f6c-ec27-45b2-81a8-fbcf5790edec)

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
En la carpeta db ahora se encuentran archivos y carpetas creados por MySQL para almacenar las bases de datos, tablas y configuraciones, lo que garantiza la persistencia de datos.
![image](https://github.com/user-attachments/assets/1cad28d8-1608-415a-84a5-c52051737680)


### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio, la carpeta del contenedor (b) es /var/www/html.

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
```
docker run -d --name wordpress-container --network net-wp -e WORDPRESS_DB_HOST=mysql-container -e WORDPRESS_DB_USER=wp_user -e WORDPRESS_DB_PASSWORD=wp_password -e WORDPRESS_DB_NAME=wordpress_db -p 9500:80 -v C:/Users/SoloParaKerlly/Desktop/ejercicio3/www:/var/www/html wordpress
```
![image](https://github.com/user-attachments/assets/582e9b33-fb33-4867-85f3-ee328de62b19)

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?
Al eliminar y volver a crear el contenedor de WordPress, la personalización y las entradas se conservan, ya que la información de la base de datos persiste en la carpeta db del host, y los archivos de configuración y contenido de WordPress se mantienen en la carpeta www.



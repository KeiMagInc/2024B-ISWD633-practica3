# VOLUMEN TIPO HOST
Un volumen host (o bind mount) es un tipo de volumen donde se monta un directorio o archivo específico del sistema de archivos del host en un contenedor.
 
```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
```
C:\Users\SoloParaKerlly\Desktop\nginx
```
![Volúmenes](img/directorio.PNG)

### Crear un volumen tipo host con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](img/volumen-host.PNG)
```
docker run -d -p 80:80 -v C:/Users/SoloParaKerlly/Desktop/nginx:/usr/share/nginx/html nginx:alpine
```
![image](https://github.com/user-attachments/assets/855ab17b-d65c-41bd-9d26-d691ffb1375d)


### ¿Qué sucede al ingresar al servidor de nginx?
Al ingresar al servidor de Nginx en http://localhost, se muestran los archivos HTML o recursos estáticos (como imágenes, CSS, JavaScript) que estén en la carpeta local C:\Users\SoloParaKerlly\Desktop\nginx. Si existe un archivo index.html, Nginx lo servirá automáticamente como la página principal. 

### ¿Qué pasa con el archivo index.html del contenedor?
Cuando se crea un volumen host y se enlaza la carpeta local C:\Users\SoloParaKerlly\Desktop\nginx a la ruta /usr/share/nginx/html dentro del contenedor, el contenido original de esta carpeta en el contenedor queda oculto o reemplazado por el contenido de la carpeta local. Esto significa que solo se mostrarán los archivos de la carpeta local, y el archivo index.html del contenedor no será accesible mientras el volumen esté montado. 

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
Al ingresar al servidor de Nginx en http://localhost, Nginx mostrará el template descargado de HTML5 UP como una página web, utilizando el archivo index.html y los recursos estáticos del template en la carpeta C:\Users\SoloParaKerlly\Desktop\nginx.
![image](https://github.com/user-attachments/assets/c9704f22-2608-47f7-957f-65fb69e70ecc)

### Eliminar el contenedor
```
docker rm -f 213dc778547b
```
![image](https://github.com/user-attachments/assets/5c2a346c-95f2-49d9-bc32-c2f7e75c6b75)


### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?
Al crear nuevamente el mismo contenedor Nginx con el volumen de tipo host enlazado a la carpeta del contenedor, Nginx servirá automáticamente los archivos de la carpeta local especificada. Esto significa que, si se descargó un template HTML en esa carpeta, Nginx mostrará el contenido de ese template al ingresar a http://localhost. Los archivos del contenedor se sobreescribirán temporalmente por el contenido del volumen, por lo que cualquier modificación en la carpeta local se reflejará de inmediato en el servidor sin necesidad de reiniciar el contenedor.

### ¿Qué hace el comando pwd?
El comando pwd en la terminal muestra la ruta completa del directorio actual en el que se encuentra. Es importante para saber en qué ubicación del sistema de archivos está trabajando en un momento dado.

Si quieres incluir el comando pwd dentro de un comando de Docker, lo puedes hacer de diferentes maneras dependiendo del shell que estés utilizando.


### Volumen tipo host usando PWD y PowerShell
```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v ${PWD}/<ruta relativa>:<ruta absoluta> <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (Git Bash)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd -W)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (en Linux)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```


# BIND MOUNT
En un bind mount mapeamos (montar) un directorio o archivo específico del sistema de archivos del host con una parte del sistema de ficheros del contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
ó
```
docker run -d --name <nombre contenedor> --mount type=bind,source=<ruta carpeta host>,target=<ruta carpeta contenedor> <imagen>
```
- destination, dst, target: La ruta donde se monta el archivo o directorio en el contenedor.
- source, src: El origen del montaje.
  
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](directorio.PNG)

### Crear un contenedor con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](volumen-host.PNG)
# COMPLETAR CON EL COMANDO
```
docker run -d --name nginx-practica -P -v "C:\Users\samia\OneDrive - Escuela Politécnica Nacional\Universidad\2025B_Sexto Semestre\Construcción y Evolución de Software\Primer Bimestre\Prácticas\Practica 3\nginx\html" nginx:alpine
```
### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Al ingresar al servidor de Nginx desde el navegador (por ejemplo, http://localhost), verás una página en blanco o error 403 si no hay ningún archivo index.html en la carpeta html del host.

### ¿Qué pasa con el archivo index.html del contenedor?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
El archivo index.html original del contenedor se sobrescribe (queda oculto) por el bind mount. El contenedor ya no usa su archivo interno, sino el contenido de la carpeta html del host.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Después de descomprimir el template en la carpeta html, al ingresar al servidor Nginx se ve el sitio web del template cargado correctamente. 

### Eliminar el contenedor
# COMPLETAR CON EL COMANDO
```
docker rm -f nginx-practica
```
### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
El nuevo contenedor seguirá mostrando el mismo contenido del template, ya que los archivos están en el host. El bind mount asegura que el contenido persiste aunque el contenedor se elimine y se cree uno nuevo.


## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
# COMPLETAR CON EL COMANDO COMANDO
```
docker network create net-wp
```
### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es */var/lib/mysql*.


Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
No contiene nada ahora.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
# COMPLETAR CON EL COMANDO
```
docker run -d --name mysql-wp --network net-wp -e MYSQL_ROOT_PASSWORD=admin123 -e MYSQL_DATABASE=wordpressdb -e MYSQL_USER=wpuser -e MYSQL_PASSWORD=wppass -v "C:\Users\samia\OneDrive - Escuela Politécnica Nacional\Universidad\2025B_Sexto Semestre\Construcción y Evolución de Software\Primer Bimestre\Prácticas\Practica 3\ejercicio3\db:/var/lib/mysql" mysql:8
```
### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Se han generado múltiples archivos y carpetas internas de MySQL que representan la base de datos wordpressdb, el usuario wpuser y otros datos del sistema. Esto indica que el volumen está funcionando correctamente.
<img width="1610" height="1413" alt="image" src="https://github.com/user-attachments/assets/22777582-5563-41c5-8e9c-67ce48b98752" />

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es */var/www/html*.

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# COMPLETAR CON EL COMANDO
```
docker run -d --name wordpress-wp --network net-wp -e WORDPRESS_DB_HOST=mysql-wp:3306 -e WORDPRESS_DB_USER=wpuser -e WORDPRESS_DB_PASSWORD=wppass -e WORDPRESS_DB_NAME=wordpressdb -v "C:\Users\samia\OneDrive - Escuela Politécnica Nacional\Universidad\2025B_Sexto Semestre\Construcción y Evolución de Software\Primer Bimestre\Prácticas\Practica 3\ejercicio3\www:/var/www/html"  -p 8080:80 wordpress
```
### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA 
La apariencia personalizada y la entrada agregada en WordPress siguen presentes, porque los datos se guardaron en el volumen del host. Esto demuestra que la información persiste incluso si el contenedor se elimina y se vuelve a crear.

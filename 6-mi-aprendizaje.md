Aprendí con claridad cómo funcionaban los volúmenes ni la diferencia entre bind mounts, volúmenes nombrados y volúmenes anónimos. Ahora entiendo la importancia que el volumen tiene en la persistencia de datos.
Después de completar la práctica, logré entender:
- Cómo montar carpetas del host en contenedores usando bind mounts, y cómo esto afecta los archivos internos del contenedor.
- La utilidad de los volúmenes nombrados para mantener datos persistentes sin depender de rutas específicas del host.
- El comportamiento de los volúmenes anónimos y cómo se eliminan automáticamente si no se gestionan correctamente.
- Cómo crear redes personalizadas para que los contenedores se comuniquen entre sí sin exponer puertos innecesarios.
- La importancia de revisar la documentación oficial de cada imagen para conocer las rutas de almacenamiento y variables de entorno necesarias.

## Problemas solucionados
Durante la práctica, tuve un problema al intentar acceder a los archivos montados en el contenedor nginx. El servidor mostraba error 403 porque la carpeta html del host no contenía un archivo index.html. Lo solucioné descargando un template desde html5up.net y colocándolo en la carpeta correspondiente.
También utilicé los siguientes comandos adicionales:
- docker volume inspect <nombre> para verificar el punto de montaje de los volúmenes nombrados.
- docker network ls para confirmar que las redes personalizadas se habían creado correctamente.
- docker exec -it <nombre contenedor> bash para ingresar al contenedor y verificar rutas internas

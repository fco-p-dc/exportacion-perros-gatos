# Implementacion de clasificador de perros y gatos

## Creacion de modelo

Para la creacion del modelo se utilizo el archivo de colab: https://colab.research.google.com/drive/1tV8N1ylobpbERyNSpUVHy_4CuTMhqiYw 

Se cambio la implementacion para el aumento de datos y se borraron las celdas con el signo ! para correrlas directamente en terminal con un script y asegurarnos que la version de tensorflow es la 2.14. Una vez el script se corre tendremos los archivos de tensorflow.js comprimidos en perros-gatos.zip

## Implementacion de aplicacion web

Para correr el modelo clonaremos el repositorio:
https://github.com/ringa-tech/exportacion-perros-gatos

Eliminaremos los archivos: "model.json", "group1-shard1of4.bin", "group1-shard2of4.bin", "group1-shard3of4.bin", "group1-shard4of4.bin".

### Cargar archivos

Usando un servicio ftp, moveremos el archivo perros-gatos.zip de la choya a nuestra carpeta exportacion-perros-gatos. Una vez el archivo este en la nueva carpeta, lo descompriremos y moveremos su contenido a la carpeta junto al index.html, quedandonos de nuevo los archivos "model.json", "group1-shard1of4.bin", "group1-shard2of4.bin", "group1-shard3of4.bin", "group1-shard4of4.bin" pero ahora de nuestro modelo. 

### Servicios de alojamiento

Ya que tengamos nuestro modelo cargado en el directorio, lo que haremos para correrlo sera abrir el directorio en la terminal y correr el siguiente comando:

    python -m http.server 8000

Una vez nuestra app este corriendo, podemos checar que el modelo sirva en la direccion http://localhost:8000 

Para poder probarlo en el celular tenemos que utilizar un programa que nos permita alojarlo en una pagina web https. En este caso usaremos Ngrok, lo descargaremos de su pagina oficial y crearemos una cuenta. Despues de iniciar sesion, tenemos que obtener nuestro token, el cual copiaremos y pegaremos en otra terminal:

    ngrok authtoken <YOUR_AUTH_TOKEN_HERE>

y podremos correr nuestro tunel ngrok con el siguiente comando:

    ngrok http 8000

recuerda que el numero de puerto debe ser el mismo al de tu servidor local.

### Probar el clasificador

Para probar el clasificador usaremos la pagina que nos genere grok, por ejemplo:

    https://<random-id>.ngrok-free.app

Una vez metamos la url en el celular u otro dispositivo, aceptaremos visitar el sitio ngrok, nos redirigira y ahi le daremos acceso a nuestra camara. Listo puedes probar tu clasificador de perros y gatos!

## Repositorio

El modelo y pagina web creados para la clase de Redes Neuronales se encuentra en el repositorio:
https://github.com/fco-p-dc/exportacion-perros-gatos
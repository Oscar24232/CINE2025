<h1>TRABAJO CONFIGURAR APLICACIÓN CON DOCKER</h1>
<h2>1️⃣ Preparación</h2>
<br>

<p>Para empezar debemos de instalar el docker y tener un repositorio local del trabajo de cine en tu pc.
<p>Para ello sino tienes como es mi caso, hare un forked a mi repositorio. Como veremos a continuación</p>
<br>

<img width="1293" height="536" alt="1" src="https://github.com/user-attachments/assets/b340a42d-4ed1-49ce-a180-3697a0d0748f" />
<br>
<br>
Además, necesitamos una imagen base en Docker para poder desplegar nuestro proyecto. 
En mi caso, la imagen creada aparece como en la siguiente captura:

<img width="1577" height="883" alt="7 0 creacion de imagen" src="https://github.com/user-attachments/assets/eb930730-4a86-4dac-a79a-40a4ea9c709b" />
<br>
<br>
<h2>2️⃣ Preparar el Nginx</h2>
Debo de explicar que en la pagina html habia un archivo que tenia otro nombre, investigando supe que necesita un index.html y decidi a la pagina principal 
cambiarle el nombre a index para que así el programa lo busque de manera mas rápida y enseguida acceda a ese html, Nginx busca por defecto index.html como página de inicio.

<p>A continuación vamos a ir creando los archivos que nos hace falta para nuestro trabajo.
Para ello se tiene que crear en el mismo rango que en CINE2025CURSOGIT-main a la misma altura que index.html como vemos en la 
siguiente ilustración</p>
<br>
<img width="1527" height="240" alt="2" src="https://github.com/user-attachments/assets/da7b1c8a-da3b-4878-8182-349a93369657" />
<br><br>
<p>Dentro de esta carpeta añadiremos otra con el nombre de nginx como tambien veremos en la siguiente ilustración</p>
<img width="1619" height="185" alt="3" src="https://github.com/user-attachments/assets/e9b95c7b-9fd8-4e7b-958f-9aeec26386a0" />
<br>
<p>Finalmente, dentro de nginx, se añade el archivo default.conf. 
  Este archivo puede crearse con un editor sencillo como el Bloc de Notas y contiene la configuración que indica a Nginx 
  que sirva nuestra carpeta /usr/share/nginx/html y use index.html como página principal.
</p>
<br>
<img width="1707" height="393" alt="4y5" src="https://github.com/user-attachments/assets/0a97e989-00de-4782-bca7-c905c4773b94" />
<br>
<p>En el siguiente paso crearemos un archivo yml donde se mostrará como se monta todo:
  la imagen, los volúmenes y los puertos expuestos.
Además muestra donde se tiene que dejar el archivo, a la altura de docker y html.
</p>
<br>
<img width="1392" height="377" alt="6" src="https://github.com/user-attachments/assets/a512bb16-451b-46f6-9f72-3cb65950b41b" />
<br>
Aquí en esta ilustración anterior son los datos de los que tienes que almacenar, debido a que se debe de cargar, 
Un aspecto clave es que no podemos utilizar un puerto que ya esté ocupado por otro programa. 
En mi caso, el puerto 8081 estaba en uso, por lo que tuve que cambiarlo a 8082 para que la aplicación funcionara sin errores.

A continuación se muestra en el container la imagen desde el docker como vemos a continuación
<br>
<img width="1587" height="886" alt="7 container con la imagen desde el docker" src="https://github.com/user-attachments/assets/56167247-0512-4080-a37c-347bc08a356e" />
<br>
 <h2>3️⃣Preparar el proyecto para Nginx</h2>
Una vez configurado todo, procedí a levantar el contenedor desde la terminal (cmd) situada en la carpeta raíz del proyecto, el comando: docker compose up -d
<br>
<img width="1266" height="690" alt="8 levantar contenedor" src="https://github.com/user-attachments/assets/17361886-89be-4468-a41a-e54bb53dd53e" />
<br>
En una primera ejecución tuve un fallo debido a las rutas. Para solucionarlo, modifiqué las rutas en los volúmenes y reinicié el contenedor con los siguientes comandos.
A continuación muestro como reincio y vuelvo a ejecutar el contenedor
<br>
<img width="2316" height="191" alt="8 reiniciar por fallo" src="https://github.com/user-attachments/assets/70457bcb-7783-4967-8fb3-4f27f7796b25" />
<br>
Este comando me permitió verificar que el contenedor estaba en ejecución. con el comando: docker compose ps.
<br>
<img width="2319" height="93" alt="9 comprobar que esta corriendo" src="https://github.com/user-attachments/assets/fd957296-863a-41b9-bca3-6436f63e0889" />
<br>
Al revisar Docker Desktop, pude comprobar que el contenedor del proyecto cine2025 estaba generado y funcionando
<br>
<img width="1591" height="890" alt="8 1 desde docker" src="https://github.com/user-attachments/assets/10814e95-70fd-4152-b72e-1b3320bdf153" />
<br>
<h2>4️⃣ Verificar que funciona</h2>
Y por ultimo vemos si todo ha ido bien y ha sido un exito!!!!
<br>
<img width="1771" height="967" alt="final!!" src="https://github.com/user-attachments/assets/ecdfeacc-5dc3-4f72-ad5e-a87feff31d59" />
<br>
Finalmente, accediendo a http://localhost:8082
 en el navegador, confirmé que mi página index.html se mostraba correctamente.
 Con este proceso he conseguido desplegar correctamente mi aplicación con Nginx dentro de un contenedor Docker. Ahora la aplicación es accesible desde el navegador mediante 
 el localhost:8082

![](https://img.shields.io/badge/server-nginx-green)
![](https://img.shields.io/badge/download-47-green)
![](https://img.shields.io/github/issues/JuanseMastrangelo/Streaming-con-Android-RTMP)
![](https://img.shields.io/github/stars/JuanseMastrangelo/Streaming-con-Android-RTMP)

# S T R E A M I N G -> ANDROID + RTMP

Servidor (nginx) y cliente (Android) en español

<br>
<p align="center">
  <img width="300" src="https://gifimage.net/wp-content/uploads/2018/06/streaming-gif-7.gif">
</p>
<br>


## Descripción
Streaming con Android Studio projecto (Kotlin) + nginx(RTMP/HLS).

## Documentación
Ngxinx permite crear servidores; dentro de la carpeta <b>"nginx/conf"</b> veremos un archivo llamado nginx.conf el cual almacena los servidores
que necesitamos crear al ejecutar el servicio. Veremos que dentro hay un servidor HTTP (puerto: 81) y un RTMP (puerto: 1935).
<br>
El streaming se realiza mediante el protocolo RTMP (Real Time Messaging Protocol - Protocolo de mensajería en tiempo real) el
cual transfiere 
pequeños videos de x segundos al servidor de ngxinx guardando estos pequeños fragmentos de videos (*.ts*) en la carpeta <b>"nginx/hls"</b>.
Junto a estos archivos
existe el principal con extensión .m3u8 el cual crea un lista de reproduccion interna para ordenar los fragmentos (*.ts*).
<br>
*El nombre de estos archivos de la carpeta <b>"nginx/hls"</b> se da a partir de la llamada a la url que vemos mas adelante.*
<br><br>
Luego tenemos el servidor HTTP el cual se encargará de extraer mediante el index.html (dentro de la carpeta <b>"nginx/html"</b>)
el archivo con extensión .m3u8 (dentro de la carpeta <b>"nginx/hls"</b>) utilizando los servicios de <a href="https://videojs.com/">video.js</a>.
<br><br>

Como podemos imaginar, el cliente desarrollado con Android Studio utilizando la libreria <a href="https://github.com/TakuSemba/RtmpPublisher">RtmpPublisher</a>
enviará los videos (.ts) al servidor utilizando la variable <b>url</b> en MainActivity.kt donde reemplazaremos *###.###.###* por nuestra IPV4 (usar dentro de la console el cmd: *ipconfig* para revelar nuestra
ipv4). Como vimos anteriormente el ejemplo de url posee en su ultima parte el nombre stream, este es el nombre por el cual se llamarán
los archivos en el servidor (si se quiere cambiar tambien tienes que cambiar el index.html -> src de la etiqueta video).

Instalación:
Para instalar necesitamos tirar la carpeta nginx dentro del disco local C: y abrir con android Studio la carpeta dentro del .rar. Una vez abierto el projecto en Android necesitamos reemplazar de MainActivity.kt la variable url, donde está ###.###.### reemplazaremos por nuestra IPV4 (usar dentro de la console el comando: ipconfig para revelar nuestra ipv4). Una vez cambiada nuestro cliente Android ya esta listo para usarse.
Para dar comienzo al servidor necesitaremos abrir una consola o terminal dirigirnos a donde tenemos el nginx, en este caso en usaremos el comando "cd C:/nginx". Luego colocaremos el comando nginx.exe para ejecutar el exe (esto lo hacemos para saber si hay errores) si no aparece nada en consola quiere decir que ya esta abierto el servidor exitosamente.

Para ver nuestro stream necesitaremos comenzar a grabar con nuestro dispositivo Android y podemos mirarlo en la url: http://localhost:81.

Si queremos enviar desde nuestra pc como hariamos en caso de un directo en Youtube o Facebook necesitaremos OBS (https://obsproject.com/es)

Para cerrar el servidor ejecutar el archivo stop.bat dentro de "C:/nginx".


<br><br>
El servidor posee un delay de aprox. 20 segundos. :/

<br />
<b>Demo:</b>
<br><br>
<p align="center">
  <img width="300" src="https://github.com/TakuSemba/RtmpPublisher/raw/master/arts/sample.gif">
</p>


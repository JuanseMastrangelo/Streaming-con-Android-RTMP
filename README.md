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

<br><br>
El servidor posee un delay de aprox. 20 segundos. :/

<br />
<b>Demo:</b>
<br><br>
<p align="center">
  <img width="300" src="https://github.com/TakuSemba/RtmpPublisher/raw/master/arts/sample.gif">
</p>


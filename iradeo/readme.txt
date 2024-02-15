iRadeo, tu radio en línea... gratis
5–6 minutos

Cuando tuve la posibilidad de conseguir conexión permanente a Internet -hace varios años-, uno de los desafíos que más me llamaba la atención, era el de montar una radio en línea.

Lamentablemente las cosas no eran tan fáciles en ese entonces, tanto por el tema del ancho de banda como por la configuración del servidor... algo que hoy parece no ser problema, y menos si usamos iRadeo. iRadeo es un reproductor de Streaming que funciona con archivos WAV y MP3, y que solo requiere de un servidor con soporte para PHP.

Esta aplicación es -medianamente- fácil de configurar, y es Open Source, por lo que podrán modificarla a su gusto si quieren mejorarla, o bien adaptarla para algún sitio web (con el extra de que la podrán descargar libremente).

La única limitación es que funciona con streaming directo, por lo que si poseen un servidor con ancho de banda muy reducido, seguramente sufrirán las consecuencias rápidamente.
Default image alt

Crédito: Thinkstock

Lo estuve probando un rato, y la verdad es que me pareció muy sencillo, fácil e interesante, sin duda.

¿Te animás a armar tu propia radio?

Primero que nada, el servidor

Podríamos asumir que ya tenés un servidor web instalado en tu máquina, pero como esto no es algo tan común (a menos si no sos desarrollador web), te recomendamos que leas este viejo artículo de Horacio, e instales XAMPP para comenzar.

Comencemos...

Desde la página oficial, descargamos la última versión, y la descomprimimos dentro de una carpeta del servidor.

Los archivos que nos interesan son:

    config.php
    index.php

Modificando el config.php

Primero que nada, configuremos el archivo config.php:

    Cambiamos el título de la página que se mostrará, desde la variable $title
    En el Array de $labels, cambiamos Song por Canción; Artist por Autor; y dejamos Album como está
    En la variable $mp3_dir apuntamos a la carpeta en donde estén los archivos, agregando un /mp3s/ al final. Ejemplo, si tienen la carpeta en /htdocs/www/, quedaría como "/htdocs/www/mp3s/". Si están en Windows, la dirección sería "X:\...\mp3s\" siendo X la unidad y los puntos suspensivos la direccción hacia la carpeta de archivos del servidor web.
    En la variable $http_path apuntamos a la dirección web del sitio, más la ubicación de la carpeta de archivos MP3s o WAVs. Ejemplo, si la carpeta es iradeo, y estamos usando en localhost, lo más probable es que sea "http://localhost/iradeo/mp3s/"
    La variable $shuffle la modificamos acorde a si queremos que la selección sea aleatoria (true) o no (false)
    La variable $skip_limit nos permitirá limitar a los usuarios en cuanto al cambio de temas. Si está en -1, entonces los usuarios pueden cambiar de temas cuantas veces quieran, en 0 no pueden cambiar de tema, en X (1 a infinito), los usuarios podrán cambiar de tema siempre en X intentos, pero luego pasarán a escuchar el tema completo sin poder cambiar hasta que termine (ideal para evitar abusos, poner un valor de 1 a 5).
    El array $playable nos permitirá decidir que extensiones de archivo se reproducirán, aunque no recomiendo modificar los valores ya que solo soporta el formato MP3 y WAV
    Y finalmente, $auto_play en "true" hará que el reproductor comience automáticamente cuando cargan la página, mientras que en "false" el usuario deberá apretar en el botón de Play.

Parece difícil, pero no lo es... yo monté la radio en solo 5 minutos (contado el tiempo de descarga de archivo!).

Retoquemos el diseño en index.php

El otro archivo (index.php), les permitirá modificar la apariencia del reproductor, de cara a los visitantes. Por mi parte no le he modificado nada, ya que me pareció simple y agradable.

Si a alguno le surge alguna brillante idea relacionado con la interfaz, entonces reportenla a sus desarrolladores... quien sabe, al ser Open Source, quizás la tomen en cuenta para futuras versiones.

Listo, a pasar música en línea...

Una vez que terminaron, desde el navegador ingresan a la dirección en donde esté ubicada la carpeta de iRadeo y listo... ya está funcionando.

Si quieren pasar música a otras personas en Internet, deberán configurar la variable $http_path con su IP pública, dado que con localhost solo podrán acceder ustedes mismos.

No voy a entrar en detalles respecto a la (in)seguridad de tener un servidor casero abierto a Internet, por lo que ese detalle véanlo por separado... y solo pasen la dirección IP a aquellas personas en quienes confíen (aún así, no garantiza nada... pero al menos, minimiza las posibilidades).

Conclusión

Como habrán notado, es un script bastante sencillo de utilizar, y que nos permitirá sacar andando una radio en cuestión de minutos.

Lo bueno de todo es que funciona por medio de un reproductor Flash, tecnología que está instalada en la mayoría de los navegadores (y hasta teléfonos móviles), lo que nos permitirá llegar a una mayor audiencia que con aplicaciones similares que utilizan Silverlight o JAVA (en este último caso, suele ser bastante pesado para el lado del cliente).

Si lo han probado, o tienen dudas, dejen sus comentarios más abajo...

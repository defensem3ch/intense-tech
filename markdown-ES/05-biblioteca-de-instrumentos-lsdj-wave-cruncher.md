**Intense Tech con Defense Mech -- Biblioteca de instrumentos LSDj Wave Cruncher**
- Posted March 28th, 2019 by [Pixel
Guy](https://apixelguy.com "Posts by Pixel Guy")
*Artículo Original de [DEFENSE
MECHANISM](../en/05-lsdj-wave-cruncher-instrument-library.md.html). Traducción al
Español por [Pixel Guy](https://apixelguy.com).*

¡Hola y bienvenidos una vez más a una edición extremadamente emocionante
de *Intense Tech*! Estoy entusiasmado de compartir con ustedes los
resultados logrados durante los últimos meses, porque creo que ahora un
mundo nuevo de sonidos está a su disposición. Acompáñenme a medida que
regresamos a la Consola de Comandos utilizando la herramienta creada por
4ntler: lsdj-wavetable-import, incluida en libLSDJ.

------------------------------------------------------------------------

Tal vez quieras hacer un ejercicio de memoria sobre [el artículo
pasado](04-organiza-tus-archivos-de-guardado-con-liblsdj.md.html), en el cual
hablamos de la Consola de Comandos y de libLSDj; además de los dos
primeros artículos, en los cuales hicimos un análisis profundo del
sintetizador del canal Wave del LSDj. En esta ocasión combinaremos esas
herramientas para hacer un parche que te permita añadir formas de onda
personalizadas en un archivo .lsdng o en un archivo .sav. Durante estas
semanas comencé a armar una biblioteca de instrumentos para lograr que
una gran variedad sonidos estén disponibles para el uso de cualquiera.
Antes de continuar, permítanme explicar cómo funciona esto.

Hace unos años encontré una herramienta creada por [DOTCNT](https://soundcloud.com/dotcnt) llamada
«[lsdj-wave-cruncher](https://github.com/iLambda/lsdj-wave-cruncher)». La idea era tomar una muestra de sonido de un
instrumento, como un tambor metálico de Trinidad y Tobago, y reducirlo a
una serie de formas de onda de 4 bits compatibles con el sintetizador
del canal Wave del Gameboy. Ahora ya es posible el tomar muestras de
sonido de instrumentos utilizando LSDPatcher para crear un parche con
muestras personalizables directamente en la ROM del LSDj; pero con las
limitantes inherentes al kit de *samples* del LSDj. Tocar notas a
diferentes alturas requiere ajustar una muestra por nota. Algunos de
esos ajustes pueden ser realizados, aunque no siempre son adecuados para
instrumentos tonales monofónicos.

La [revelación](https://www.penzeys.com) que viene con el *wave
cruncher* es que, ¡convierte al sintetizador del canal Wave en una
herramienta rudimentaria para el muestreo! En lugar de generar formas de
onda usando el sintetizador integrado, las *wavetables* pueden ser
creadas a partir de la muestra de un instrumento, permitiéndole llenar
los dieciséis espacios para *waveforms* de la pantalla Instrument del
canal Wave. Veamos el siguiente ejemplo de un piano eléctrico:

![Muestra de un piano eléctrico FM](../media/epiano.mp3)

Cuando el *sample* es puesto en el *wave cruncher*; los ciclos de la
onda serán reducidos para hacer que cada ciclo encaje dentro de uno de
los dieciséis espacios del sintetizador del canal Wave. A partir de aquí
ajusta Play a Once en la pantalla Instrument del canal Wave, además de
manipular los parámetros de Length y Speed a tu gusto. Aquí hay un
pequeño *riff* con las siguientes configuraciones; Length: 3, Speed: 3.

![Piano eléctrico reducido a un instrumento de ondas de 4 bits en LSDj](../media/epiano2.mp3)

Las malas noticias son que, al ajustar la muestra, las configuraciones
del *wave cruncher* y del sintetizador del canal Wave pueden tomar mucho
trabajo antes de conseguir un resultado satisfactorio. ¡Las buenas
noticias son que ya he hecho un poco de ese trabajo por ti! Creé un
depósito en Github llamado
«[lsdsynths](https://github.com/psgcabal/lsdjsynths)», el cual contiene
las *wavetables* como archivos .snt. La herramienta
lsdj-wavetable-import de libLSDj te permitirá utilizar dichos sonidos en
tus proyectos. De manera diferente a los kits de *samples*, los cuales
son añadidos a la ROM, los instrumentos de las *wavetables* del
sintetizador son añadidos al archivo de guardado, lo cual es sumamente
útil cuando se trabaja en colaboraciones o se comparten archivos de
guardado con otros usuarios de LSDj.

Ahora tomémonos un minuto para aprender a utilizar la herramienta
lsdj-wavetable-import. Si aún no lo has hecho, puedes descargar
[libLSDJ](https://github.com/stijnfrishert/liblsdj/releases) para tu
sistema operativo.

Coloca lsdj-wavetable-import y el sintetizador (archivo .snt) que
quieras parchar junto con tu archivo de guardado de LSDj, o tu archivo
.lsdsng, dentro de una misma carpeta. Abre la Consola de Comando o
Ventana Terminal en esa ubicación. Para parchar el archivo .snt los
comandos son los siguientes:

`lsdj-wavetable-import savefile.sav synth.snt 0`

Esto parchará «synth.snt» a Synth 0 del archivo «savefile.sav». Cuando
se parcha un archivo de guardado, solo la canción en la memoria de
trabajo es parchada; así que asegúrate de que la canción que quieras
parchar se encuentre cargada en el archivo de guardado. Puedes sustituir
«savefile.sav» por cualquier archivo .lsdsng. ¡Bastante simple!

¡Espero que encuentres estos sonidos útiles e interesantes! Siéntete
libre de compartir los resultados que obtengas al intentarlo por ti
mismo.

------------------------------------------


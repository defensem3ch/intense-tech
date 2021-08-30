**Intense tech con Defense Mech – ¡Nueva configuración para *Noise* y noticias de la versión 
9.1.0!**
  -Publicado 16 enero, 2021 por [DEFENSE MECHANISM](../en/19-new-noise-and-910-news.md.html). 
  *Traducción por [Pixel Guy](https://apixelguy.com/)*

¡Hola y bienvenidos a otra edición de Intense tech! ¡En este artículo hablaremos de de los cambios 
en la recién lanzada versión 9.1.0 del LSDj! Esta versión es emocionante, aunque incluye algunos 
cambios que podrían arruinar potencialmente los instrumentos del tipo Noise que haya en tus 
canciones. ¡Demos un vistazo más de cerca para que estés listo para estos cambios!

---------------
Cambios en los canales
---------------

Si alguna vez pensaste que el canal Noise del LSDj era confuso, ¡no estás solo! Incluso cuando hace 
poco escribí [un artículo explicando su funcionamiento 
interno](https://defensemech.com/intense-tech/es/17-las-alegrias-del-ruido.md.html) no fue 
suficiente para desmitificar su extraño comportamiento. Era obvio que la usabilidad podía ser 
mejorada y esto impulsó una reorganización completa de todo el canal Noise para la versión 9.1.0. 
Esta nueva organización ordena las notas de ese canal de acuerdo a su frecuencia: primero están los 
sonidos de bucle largo acomodados desde la frecuencia más baja hasta la más alta utilizando las 
notas que van de `00` a `3B`. Justo encima de eso están los sonidos de bucle corto colocados de la 
frecuencia más baja a la más alta y desde la octava -9 (nueve negativa) a la 8 utilizando nombres de 
notas musicales para representar la frecuencia que esté más cercana (do, re, fa y sol#). Todas las 
octavas desde la -9 hasta la 4 contienen las cuatro notas anteriores; las octavas de la 5 hasta la 8 
solo contienen la nota do (excepto por un fa extra en la octava 5).

![El canal Noise vuelve a utilizar nombres de notas, ¡pero esta vez son notas musicales de 
verdad!](../media/noisenotes-1610903754.mp4)

Si cargas una canción ya existente o un archivo de guardado en la versión 9.1.0, las notas del canal 
Noise serán convertidas automáticamente; sin embargo, los valores de transposición o los comandos S 
no lo serán. Como resultado, he desarrollado este útil conversor para las notas del canal Noise en 
caso de que estés interesado en cambiar manualmente los valores en las phrases o tables del canal 
Noise. (También puedes encontrar [esta herramienta sin el artículo 
aquí.](https://defensem3ch.github.io/noise-convert).)

Una nueva tierra para los comandos
----------------------------

Uno de los cambios más útiles y emocionantes es que ahora es posible utilizar el comando P para 
hacer una transición suave entre notas sin utilizar una *table* personalizada. El comando P también ha 
cambiado un poco su funcionamiento debido a que se añadió un control de velocidad: en lugar de que 
el comando `P01` apique `S01` en cada *tick*, este lo aplica cada cuatro y `P04` aplica `S01` cada 
*tick* permitiendo así un control más detallado sobre el sonido final del *sweep*. Tener ese control 
extra quiere decir que ahora es posible hacer *kicks*, *hi hats* y *crashes* realmente geniales en el 
canal Noise sin necesidad de dedicar *tables* extra para esos sonidos.

![Aquí hay un ejemplo de una phrase que muestra un *kick*, un *hi hat* y un *crash* utilizando el 
mismo instrumento.](../media/noise-1610903555.mp4)

Otro cambio en los comandos en el canal Noise es que el comando C ahora funciona básicamente de la 
misma manera en la que lo hace en los canales Pulse y Wave, en los cuales hace el arpegio partiendo 
de la nota raíz siguiendo con el segundo y tercer dígito. La diferencia más básica radica en que los 
valores están limitados a las notas disponibles en el canal Noise. De esta manera, para crear un 
arpegio para la triada de fa menor tienes que colocar `F 5` y aplicar un comando C con un valor de 
`C12`.  Esto intercalará entre las notas fa, sol# (o lab) y do. Intervalos más grandes se extenderán 
a varias octavas.

![Un ejemplo de arpegios con el comando C.](../media/noisearps-1610903924.mp4)

Por último, ¡se ha añadido un nuevo comando! El comando V agrega *vibrato* al ruido (dicho vibrato 
siempre está basado en los *ticks*).

![¡Rango del vibrato yendo desde un efecto suave hasta uno extremo en los valores más 
altos!](../media/noisevib-1610904078.mp4)

¿Qué más hay de nuevo?
-----------------

Además del arreglo de unos cuantos errores y transformaciones estéticas, se han hecho algunos 
cambios notables desde la última entrega de *Intense tech*. ¡Cubrámoslos rápidamente!

<big>**Indicadores de reproducción más rápidos**</big>

La actualización a la versión 9.1.0 incluye nuevos indicadores de reproducción en las pantallas 
Song, Phrase y Table basados en el *sprite*. Estos ahora se actualizan a 60 Hz, ¡lo que hace que sean 
más visibles!

![¡Vista épica de la pantalla Table!](../media/table-1610904442.mp4)

<big>**Cambios en el *vibrato* basado TICKS**</big>

También se cambiaron las velocidades del *vibrato* basado en *ticks* para que sea más rítmico en el 
*groove* por defecto. Esto se explica en la bitácora de la siguiente manera:

```none
La velocidad del vibrato V e el modo PITCH=TICK ahora son iguales a las celdas de la phrase:

    V0x = 16 celdas
    V1x = 12 celdas
    V2x = 32/3 celdas
    V3x = 8 celdas
    V4x = 6 celdas
    V5x = 16/3 celdas
    ...
    VFx = 1/2 celdas
```

<big>**Presición aumentada en el FINETUNE de los instrumentos**</big>

Los valores de FINETUNE han sido expandidos a dos dígitos. El valor anterior de `01` ahora equivale 
a `10`.

<big>**Cambios en los marcadores**</big>

Marcar *chains* individuales en la pantalla Song ha sido cambiado a fin de poder marcar líneas 
enteras.  Presionar B+Arriba/Abajo hará que se salte entre la selección anterior y la siguiente.

![Saltando entre marcadores.](../media/bookmarks-1610904841.mp4)

<big>**Sobrepasando los LIMITes en el sintetizador del canal Wave**</big>

El valor de LIMIT se ha incrementado a dos dígitos y ahora puede sobrepasar `0F`. AL hacer esto es 
posible crear una especie de distorsión. Esto también permite recortar valores mientras se utiliza 
una distorsión CLIP al mismo tiempo que añade nuevos armónicos. ¡Pruébalo y ve qué clase sonidos 
resultan!

![Aumentando LIMIT por encima de `0F`](../media/limit-1610904715.mp4)

<big>**El comando F anula el Silky Wave**</big>

La aplicación de comandos F en las *phrases* del canal Wave anteriormente presentaba un retraso debido 
al Silky Wave, pero ahora los comandos se aplican instantáneamente, justo como lo hacían antes de 
que se implementara esta función en la versión 7. Mientras que esto puede reintroducir un ligero 
clic, permite hacer cambios inmediatos en los cuadros de la forma de onda para aumentar la precisión 
rítmica como lo hacía en versiones anteriores.

<big>**Los instrumentos del tipo Noise ya no necesitan la función FREE/STABLE**</big>

La función FREE/STABLE del canal Noise se eliminó y los silencios aleatorios en dicho canal han sido 
reducidos. Sin embargo, muchos modelos de Gameboy siguen viéndose afectados por un error en el 
hardware que puede causar que el canal Noise se silencie de manera aleatoria, mientras que los 
emuladores como el BGB o el Sameboy, al igual que muchos modelos de Gameboy Advance, no han sido 
afectados. 


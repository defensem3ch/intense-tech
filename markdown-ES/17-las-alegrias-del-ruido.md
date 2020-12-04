**Intense tech con Defense Mech – Las alegrías del ruido**
-Publicado November 5, 2020 por [DEFENSE MECHANISM](../en/17-the-joys-of-noise.md.html). Traducción por [Pixel 
Guy](https://apixelguy.com/)

¡Hola y bienvenidos a otra edición de Intense tech! En esta ocasión nos adentraremos en la 
complejidad del canal Noise y descubriremos lo que es posible, ¡tratando de expandir nuestro arsenal 
de posibilidades sónicas al máximo! Explicaremos cómo dicho canal genera sonidos y aprovecha unos 
cuantos principios para obtener texturas inesperadas. ¡Vamos a ello

--------------------------------------------------------------------
Poniendo la esencia en lo esencial
--------------------------------------------------------------------
Como muy probablemente lo esperabas viniendo de este blog, es momento de otro análisis a detalle. 
Siéntete libre de saltar esta parte si no estás interesado en el funcionamiento del canal Noise, de 
otra manera, ¡continúa leyendo! También vale la pena mencionar
[este excelente videotutorial hecho por Boy Meets 
Robot](https://www.youtube.com/watch?v=wD7omqjHXmI), en el cual se explica este canal de una manera 
similar. Siempre puedes volver a esta sección a manera de referencia si lo consideras necesario. 

El canal Noise funciona en base a un concepto conocido como «registro de desplazamiento con 
retroalimentación lineal (LFSR por sus siglas en inglés)». Para nuestros fines, solo es necesario 
saber que es una manera rápida y fácil de conseguir ruido pseudoaleatorio; este genera una serie de 
ondas de pulso de un bit, cada una con una amplitud aleatoria. El ruido se crea de acuerdo al reloj 
del procesador, el cual es dividido de acuerdo a un divisor —excepto por el número más alto, el 
cual, de hecho, dobla la frecuencia.  El resultado es dividido entre una potencia de dos, lo que 
básicamente controla la octava en la que se produce el ruido. Esto se traslada al LSDj para 
permitirnos controlar la octava con el primer dígito de Shape, mientras que el segundo controla la 
frecuencia divisoria. 

<center><big>**Cuadro explicativo de los valores de Shape en el canal Noise**</big></center>
Primer dígito | Octava | Segundo dígito | Valor de la frecuencia divisoria
------------|--------|--------------|--------------
**F** | Octava más alta | **F** | Multiplicada por dos
**E** | Una octava por debajo | **E** | Sin cambios (multiplicada por uno)
**D** | Dos octava por debajo | **D** | Dividida entre dos
**C** | Tres octava por debajo | **C** | Dividida entre tres
**B** | Cuatro octava por debajo | **B** | Dividida entre cuatro
**A** | Cinco octava por debajo | **A** | Dividida entre cinco
**9** | Seis octava por debajo | **9** | Dividida entre seis
**8** | Siete octava por debajo | **8** | Dividida entre siete
**7** | Ocho octava por debajo | **7** | Multiplicada por ocho
**6** | Nueve octava por debajo | **6** | Sin cambios (multiplicada por uno)
**5** | Una octava por debajo | **5** | Dividida entre dos
**4** | Una octava por debajo | **4** | Dividida entre tres
**3** | Una octava por debajo | **3** | Dividida entre cuatro
**2** | Una octava por debajo | **2** | Dividida entre cinco
**1** | <span style="color:gray;">*No utilizado - Sin sonido*</span> | **1** | Dividida entre seis
**0** | <span style="color:gray;">*No utilizado - Sin sonido*</span> | **0** |  Dividida entre siete
<div class="fig">*Nota: en versiones anteriores a la 8.6.0, la octava 5 en el apartado de phrase 
corresponde al primer dígito de Shape en los instrumentos del canal Noise (octava 6 en versiones 
anteriores a la 5.1.6). Cambiar la octava hacia arriba o hacia abajo cambia el primer dígito de 
Shape hacia arriba o hacia abajo (una vez alcanzado el punto más alto o más bajo, cambiar la octava 
no tiene ningún efecto). El tono de la nota no afecta la forma del ruido, solo el valor de la 
octava.*</div>

Probablemente ya te diste cuenta de que el valor divisor del segundo dígito es el mismo para `F` y  `7`, 
los mismo pasa con `E` y `6`, etc.; esto se debe a los valores de `0` a `7` ajustan el modo **short-loop**, 
mientras que los dígitos de `8` a `F` ajustan el modo **long-loop**. El modo *short-loop* quiere decir que 
la forma de onda del ruido tiene la mitad de su longitud y, como resultado, produce sonidos más 
tonales, metálicos y resonantes. El modo *long-loop* ajusta la onda a su duración completa, lo que 
resulta en un sonido menos afinado y más parecido al ruido blanco. Podemos comprobarlo descendiendo 
el segundo dígito al ir de `CF` a `C0`:

![](../media/noise-sweep.mp4)

A diferencia del sintetizador del canal Wave donde los sonidos son creados a partir de multiplicar 
la frecuencia base por números completos para generar la serie armónica, las notas del canal Noise 
generan la serie armónica negativa, lo que es resultado de dividir la frecuencia entre números 
enteros. Dado que la nota base es cercana en frecuencia a do, podemos ver qué notas resultan cuando 
se divide la frecuencia entre cada número:

![*Los tonos disponibles en el modo* short-loop *no son exactos, pero suenan muy parecidos a do, fa, 
la♭, y re.**](../media/negative-harmonic-series.png)

Un ejemplo excelente del uso del modo *short-loop* para generar notas es este demo, de
[they/them](https://theythemmusic.bandcamp.com/), en el cual solo se usa el canal Noise.
<iframe width="100%" height="166" scrolling="no" frameborder="no" allow="autoplay" 
src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/265499387&color=%2322c8ff&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true" 
style="height: 166px;"></iframe>

Encontrando la <span class="defense">S</span>ilueta
---------------------------------------------------
La forma del ruido puede controlarse con el comando S, el cual es útil para tener un control más 
meticuloso sobre la misma. Mientras que en la versión 8.6.0 (y posteriores) del LSDj puedes 
programar la forma directamente en la pantalla Phrase utilizando la columna de las notas, es 
importante conocer cómo funciona el comando S.

El comando S añade su valor a la forma del ruido siendo cada dígito independiente. De manera 
diferente a otros comandos, donde podría esperarse que al ajustar S a `01` teniendo Shape en `49` 
esta resultaría en `50`, esto no sucede gracias a que cada dígito actúa de manera separada. Así, al 
aplicar `S01` a Shape `4F`, esta resulta en Shape `40`. Lo mismo ocurre al aplicar `SFF` a Shape 
`4F`, que resulta en Shape `3E`.

Esto funciona diferente al aplicar una transposición en ambos, phrase y table, donde se afecta a 
AMBOS dígitos. Aquí, al aplicar un valor de `01` en la columna TSP teniendo Shape `4F` SÍ resulta en 
Shape `50`, lo mismo pasa aplicando un valor de TSP de `FF`, que resulta en `4E`.

Otra diferencia clara en las tables entre los comandos S y la columna TSP es que los primeros son 
aditivos, lo que quiere decir que al poner comandos S de manera consecutiva se añade el valor de los 
comandos previos al valor de Shape. La columna TSP aplica la transposición solo cuando la table 
corre la línea que la contiene y el valor de Shape vuelve su ajuste anterior cuando no hay una 
transposición activa.

<span class="defense">P</span>oniendo más <span class="mechanism">C</span>omandos en práctica
---------------------------------------------------------------------------------------------
Ahora que ya cubrimos el cómo funciona el comando S, podemos extrapolar su funcionalidad a otros dos 
comandos: P y C. Cada uno de estos añade su respectivo valor a Shape en el canal Noise. La 
diferencia es que el comando C alterna entre el valor base de Shape y el valor añadido de Shape en 
cada tick, mientras que el comando P añade su valor de manera continua. De manera que si el valor 
base de Shape es FF, añadir C01 alternará entre FF y F0 en cada tick, mientras que poner P01 hará un 
ciclo yendo de FF a F0, después continuará F1, F2 y así sucesivamente. Si cambiar el valor de Shape 
en cada tick resultara muy rápido, ajustar el valor de CMD/RATE para el instrumento Noise a un valor 
más alto hará que la frecuencia de los comandos sea más lenta.

Dado que estos comandos no toman en cuenta las frecuencias que se generan y cambian libremente entre 
los modos *short-loop* y *long-loop*, en ocasiones aún es necesario el crear tables especiales con 
comandos S cuando quieras hacer un paso más suave entre formas de ruido. Aquí hay un par de ejemplos 
de cómo hacer eso usando tables para hacer una transición suave al descender y al ascender:

![](../media/custom-sweep.mp4)

Trabajando con los raros
------------------------
Una de las peculiaridades del canal Noise del Game Boy es que, en ocasiones, este se silencia sin 
razón aparente. En efecto, hay una probabilidad de 1 en 256 —o 0.4 %— de que el canal Noise no 
produzca ningún ruido al cambiar entre el modo *long-loop* y el modo *short-loop*. En otras palabras, si 
el segundo dígito del valor de Shape va de 8 a F y lo cambias a uno que vaya de 0 a 7, el canal 
Noise puede dejar de sonar. Para evitar que esto pase, puedes cambiar la configuración de S Mode (o 
S CMD en versiones anteriores) de tus instrumentos Noise de FREE a STABLE. Esto permitirá cambiar al 
valor divisor del instrumento sin alterar el modo en el que hace bucle, lo que quiere decir que 
dicho modo solo será determinado por el valor base de Shape que se le proporcione

Getting Into A Crash
--------------------
Un tuco bastante genial que aprendí del [videotutorial *EXPLORING 
CHIPTUNES*](https://youtu.be/4jPUOpUUYd0?t=948) fue el uso del comando Z en la forma del ruido para 
crear platillos crash aleatorios y así añadir un poco de variedad al presentar canciones en vivo. Un 
pequeño recordatorio de [No te duermas sobre la 
Z](https://defensemech.com/intense-tech/no-te-duermas-sobre-la-z-presentado-a-hypnogram.html); el 
comando Z utiliza valores aleatorios para cada dígito por separado, lo que nos permite controlar las 
variaciones dentro de un determinado modo de bucle dentro de ciertas octavas. ¡Pero no tengas miedo 
de salir de ahí!

![](../media/noise-crash.mp4)

<div class="fig">En este ejemplo, Z puede añadir 1 al primer dígito cuatro veces, lo que quiere 
decir que el mayor dígito posible es F. Si este excediera F, entonces volvería a empezar desde 0 
—que es silencio—. Para evadir esta posibilidad, ajusté algunos comandos Z para que tengan como 
primer dígito 0. Sin embargo, dado que el divisor será un número completamente aleatorio en cada 
ocasión, ajusté los segundos dígitos a F. De esta manera es posible que el divisor sea cualquier 
valor de 0 a F en cada línea. </div>

Pateando con estilo
-------------------
Uno de los aspectos más útiles del canal Noise es su capacidad para generar frecuencias graves, 
incluso cuando estas sean difíciles de controlar. Esto es útil por obvias razones, a veces necesitas 
enfatizar un poco la parte grave, pero no lo puedes conseguir usando kicks en el canal Pulse o tal 
vez los otros tres canales están ocupados, ¡pero aún necesitas un kick! Después de pensar cómo 
funciona el canal Noise, comencé a reconsiderar la manera en la que hago dichos instrumentos en el 
canal Noise. Como siempre, este solo un ejemplo de cómo puede verse un kick en este canal. Después 
de que explique mis métodos, ¡espero que puedas utilizarlos a tu manera!

![](../media/noise-kick.mp4)

<div class="fig">Este ejemplo comienza ralentizando la table de manera que puedas ver y escuchar 
cómo suena el kick a medida que se mueve la table por todas las líneas. Comienzo con un valor base 
para Shape de `95`, pero la primera línea de la table tiene un valor de transposición de `10`, de 
manera que el sonido que escuchas en el primer tick es en realidad el de un valor de Shape de `A5`. 
Esta manera de ajustar el tono en el primer tick quiere decir que puedo mover el valor de TSP hacia 
arriba o hacia abajo para cambiar el ataque sin cambiar el sonido del resto del kick. Después se 
desliza hacia abajo, a `93`, luego a `91` y `90`. No quiero que el segundo dígito vuelva a comenzar 
en F, por lo que voy aún más abajo del primer dígito hasta `80`, luego a `70` y `60`. Vale el 
mencionar que el instrumento está ajustado en el modo STABLE, por lo que este permanece en modo 
*short-loop*, asegurando que el canal no se silenciará accidentalmente. Por último pero no menos 
importante, ¡los kicks en el canal Noise suenan fantásticos cuando son RUIDOSOS!</div>

Alargando las posibilidades
---------------------------
Lo creas o no, solo hemos tocado la superficie de los sonidos que se pueden conseguir utilizando el 
canal Noise. Si se enciende y apaga rápidamente el canal Noise se puede generar una onda de pulso. 
La manera más sencilla de hacerlo es con el comando R. (Nota rápida sobre el comando R: dependiendo 
de la versión del LSDj, `R00` puede reiniciar la nota una vez o puede reiniciarla en cada tick. En la 
versión 8.9.3, `R01` la reinicia en cada tick.) Para controlar el volumen del sonido podemos utilizar 
un valor más bajo para LENGTH o un ADSR (o envolvente) más corto. El tono de la onda de pulso 
resultante es determinado por la frecuencia del comando R, el tempo de la canción (el cual controla 
la duración de cada tick) y la forma del ruido. También puedes usar los valores que van de `R80` a 
`R8F` —la reactivación rápida—, los cuales no son afectados por el tempo de la canción o el valor de 
LENGTH. Aquí hay un video que ilustra algunos ejemplos:

![](../media/noise-retrig.mp4)

Tiempo de resultados
--------------------
Una de las canciones más épicas que he escuchado viene nada más ni nada menos que de 
[.exe](https://dotexe.space) esta se llama NOIZE JAMS y en ella usa solo el canal Noise de manera 
magistral.

<iframe width="100%" height="166" style="height: 166px;" scrolling="no" frameborder="no" 
allow="autoplay" 
src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/753000481&color=%2322c8ff&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true"></iframe>

Afortunadamente, ¡.exe accedió a dejarme compartir el archivo de guardado por este medio! Funciona 
con el LSDj v8.5.1 stable.

<center><span style="font-size: 200%;"> --> [**NOIZE JAMS 
SAV**](https://defensemech.com/intense-tech/dotexe-NOIZE_JAMS.sav) <-- </span></center>

Por favor, ¡apoyen a .exe [comprando su álbum en 
Bandcamp!](https://dotexechiptune.bandcamp.com/album/jams-exe)

<center>
<iframe style="border: 0; width: 350px; height: 470px;" 
src="https://bandcamp.com/EmbeddedPlayer/album=3256814611/size=large/bgcol=ffffff/linkcol=0687f5/tracklist=false/transparent=true/" 
seamless><a href="https://dotexechiptune.bandcamp.com/album/jams-exe">JAMS.exe by .exe</a></iframe>
</center>

------------------------------------------


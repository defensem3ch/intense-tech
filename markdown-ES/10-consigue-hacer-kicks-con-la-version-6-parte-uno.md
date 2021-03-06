**Intense tech con Defense Mech -- Consigue hacer kicks con la versión 6: parte uno**
- Posted October 29th, 2019 by [Pixel Guy](https://apixelguy.com)
*Artículo original de [DEFENSE MECHANISM](10-get-your-kicks-with-version-6-part-1.md.html). Traducción al
español por [Pixel Guy](https://apixelguy.com).*

¡Hola y bienvenidos a otra edición de *Intense tech*! En esta ocasión
veremos algunas técnicas para los *kicks*, las cuales ya he cubierto
previamente en un
[videotutorial](https://www.youtube.com/watch?v=8ihMjHn90zY). Aunque en
este artículo hablaré sobre ellas más a detalle. Después de leer esta
lección deberías de tener un buen manejo de la configuración DRUM o FAST
incluida en el parámetro P/L/V de la pantalla Instrument en la versión
seis, lo que te permitirá crear un *kick* que se adapte a tus
necesidades. También incluiré el archivo de guardado al final de esta
lección, de manera que podrás explorarlo por tu cuenta en la versión
6.9.0. ¡Manos a la obra!

------------------------------------------------------------------------

*Kicks* en el canal Wave: lo básico
-----------------------------------

Comencemos en el canal Wave, una elección popular para hacer *kicks* y
por una buena razón: puede alcanzar tonos más graves que el resto de los
canales; lo que lo hace ideal para explotar la parte más grave de la
parte baja de la onda. Como hemos visto anteriormente, [al generar una
onda senoidal en el canal
Wave](01-analisis-del-sintetizador-del-canal-wave-en-lsdj-parte-uno.md.html)
se puede producir un tono puro cercano a los 65 Hz en do1 ---la nota más
grave posible---.

Por supuesto, la manera más rápida de obtener un buen *kick* es
simplemente utilizar uno proveniente de un kit. De otra manera, ajusta
el parámetro Waveform de la pantalla Synth de tu instrumento del canal
Wave a una onda sinusoide ---o a una que parezca cuadrada--- y usa un
comando `PC0` para deslizar el tono hacia abajo. Experimenta colocando la
nota en algún lugar entre do5 y do6; también puede ser de do7 hacia
arriba, todo depende de que tan agudo y energético quieras que sea el
ataque. Aunque hacer un cambio de una octava puede hacer la diferencia,
¡incluso en el *kick* más sencillo! Continúa leyendo para saber cómo.

Cambiar el parámetro Pitch con P/L/V
------------------------------------

Cuando el LSDj cambió de la versión 4 a la 5.1.0, la escritura del
*pitch* también cambió. Hasta la versión 6 no había manera de recrear la
configuración logarítmica del *pitch*. Para nuestra fortuna, ahora
tenemos un parámetro en la pantalla Instrument llamado P/L/V, del cual
no es completamente obvio el qué es lo que hace, pero aclararé eso en
seguida. La configuración de P/L/V afecta cómo trabajan los comandos P,
L y/o V. La configuración por defecto, «FAST», reproduce los *slides* y
el *vibrato* a la velocidad más rápida posible (esto era anteriormente
conocido como «HF»). Al presionar el botón A + la flecha de dirección
hacia abajo, esta configuración cambia a «TICK», la cual reproduce
dichos efectos a una velocidad mucho más baja y que también es afectada
por el *tempo* de la canción. Al repetir el proceso presionando los
mismos botones, la configuración cambia de nuevo, esta vez a «STEP».
Dicha configuración hace que los comandos P sean solo para compensación
del *pitch*, lo que no es muy útil para hacer *kicks*, ¡aunque hace que
los comandos P en los *snares* de los kits del canal Wave sean más
interesantes! La parte que de verdad queremos cambiar se encuentra al
presionar el botón A + la flecha de dirección hacia arriba estando en
FAST; es así como encontramos una nueva opción: ¡DRUM!

![Presionar el botón A + la flecha de dirección hacia arriba cuando P/L/V: FAST esta seleccionado cambiará la configuración del pitch a DRUM](../media/image2.png)

El secreto para utilizar P/L/V: DRUM es que los comandos L y P ahora son
reproducidos usando un modo especial para el *pitch*, el cual emula los
*slides* en el *pitch* logarítmico de las versiones anteriores. Sin
embargo, esto viene con una advertencia: puede ser que al utilizar la
columna Transpose en las *phrases* o *tables* no se obtengan los
resultados deseados. De igual manera, también se elimina la posibilidad
de crear *kicks* que se deslicen directamente hacia las notas del bajo.
Esto se debe a que la tabla de referencia[^table] especial no funciona de la
misma manera en la que lo hace en la configuración por defecto: FAST.
También es importante apuntar que la configuración TRANSPOSE de la
pantalla Instrument puede ser desactivada a fin de evitar este problema
al transponer las *phrases*.

Ahora que hemos descubierto la configuración DRUM para el *pitch*,
escuchemos la diferencia entre un *kick* que utiliza FAST y uno que
utiliza DRUM.

[Kicks utilizando la configuración del pitch FAST vs kicks utilizando la configuración del pitch DRUM.](../media/fast-drum.mp4)

Configurando a detalle los *kicks* del canal Wave
-------------------------------------------------

Ahora que conocemos lo básico de los *kicks* del canal Wave, veamos
algunas maneras de ajustar las diferentes características del *kick*,
comenzando con la primera parte del mismo: el ataque. Este atributo es
muy a menudo pasado por alto, pero un ataque energético en el *kick*
puede ayudar a que este se distinga en la mezcla.

Hay diferentes maneras de ajustar el ataque de un *kick*, las opciones
más flexibles pueden ser utilizadas al aplicar una *table* en la
pantalla Instrument del canal Wave. De esta forma tendremos control de
lo que pasa en cada *tick*. Al momento de crear una *table* para un
*kick*, normalmente coloco un comando P muy rápido como primer comando,
lo que controla qué tan rápido ha de deslizarse hacia abajo el tono de
la nota que se está reproduciendo. Justo debajo y como segundo comando,
pongo un comando L con un valor de TSP de `80`. Utilizar el ajuste de esa
manera garantiza que, no importa que nota se esté tocando en la
*phrase*, el tono se deslizará hasta la nota más grave posible  y
---dado que el comando L lo detendrá al alcanzar dicho valor--- no se
reiniciará desde la nota más aguda. Esto es útil si más adelante decides
cambiar el *tempo* de la pista a uno más lento, ya que los comandos P y
L en la configuración DRUM no son afectados por el *tempo*. De manera
adicional, esto también quiere decir que soy libre de cambiar la nota
del *kick* en la *phrase* y ajustar la velocidad del comando P a mi
gusto. Experimentemos con diferentes notas partiendo de do5.

![Cambiar la octava del kick te permite ajustar el valor del trasient y del comando P.](../media/kickpitch.mp4)

Otra opción es cambiar la forma de onda en el *kick* en el primer
*tick*. Esto es una variación de lo que en ocasiones es conocido como
«Kyoto Kick». Una técnica popularizada por Toriena y algunos otros. [Una
forma de onda que contiene un poco de ruido y
«polvo»](analisis-del-sintetizador-del-canal-wave-en-lsdj-parte-dos.html)
puede ser utilizada como primera configuración para después ser cambiada
por una forma de onda regular para un kick. En este ejemplo, Wave 00 es
una forma de onda para un *kick* modificada para que contenga más ruido,
mientras que la configuración de Wave `01` a `0F` es la normal para un
*kick*. He colocado un comando `F01` en la segunda línea de la *table* del
*kick* para cambiar de Wave00 a Wave01. Sin embargo, podemos eliminar la
necesidad de usar dicho comando si ajustamos los parámetros del
instrumento a Play: Loop, Length: `1`, Repeat: `0` y Speed: `01`. Esto hará
que se reproduzca Wave `00` por un *tick* para después ser cambiado a Wave
`0F`.

![Cambiar la primera forma de onda también puede añadir impacto al trasient del kick](../media/frametransient.mp4)

Es importante notar que la configuración DRUM puede ser muy efectiva al
ser utilizada para crear otro tipo de percusiones, como *toms* o
*snares*. ¡Y también funciona en los instrumentos del canal Pulse!

Moverse del *kick* al bajo
-------------------------------------------------

¿Qué pasa si queremos un *kick* que pueda hacer una transición perfecta
a una nota de bajo al más puro estilo del *kick* de un 808? Para hacer
esto necesitaremos cambiar de nuevo a la configuración FAST y
asegurarnos de que la opción Transpose de nuestro instrumento esté
encendida. En el siguiente ejemplo he colocado la nota raíz una octava
por encima de donde la nota del bajo se reproducirá. La primera línea de
la *table* tiene una transposición de una octava hacia arriba y un
comando P que se desliza hacia abajo por dos *ticks*. La tercera línea
de la *table* tiene una transposición de una octava hacia abajo y un
comando L. Esto resulta en un sonido más suave en lo general, aunque
podrías experimentar combinándolo con la técnica de cambio de forma de
onda mencionada más arriba.

![Es necesario cambiar la configuración de P/L/V a FAST para transponer](../media/808kick.mp4)

Un dato importante del cual hacer mención es que, en muchos casos, es
bastante simple el reducir el tiempo de transición entre el *kick* y el
bajo al hacer un [ajuste en
el](un-groove-grooveante-y-trucos-para-los-ticks-parte-uno/)
*[groove](06-un-groove-grooveante-y-trucos-para-los-ticks-parte-uno.md.html)*.
¡Así no hay necesidad de usar la transposición en el *kick*! Para el
siguiente ejemplo el primer número de ticks en Groove `10` es la cantidad
de los mismos que durará el *kick*, el segundo número de *ticks* es qué
tan largo será el sonido del bajo.

![Ajustar el groove puede reducir el tiempo de transición entre en kick y la nota del bajo](../media/kickgroove.mp4)

Como lo había prometido, [aquí está el enlace al archivo de
guardado](https://defensemech.com/songs/kicktech.sav) que contiene los
ejemplos aquí expuestos. Eso es todo en esta entrega de *Intense tech*.
Estén pendientes, ya que la próxima vez profundizaremos en cómo hacer
*kicks* en otros canales.

[^table]: Una tabla de referencia, tabla de datos o lookup table es la tabla
donde el LSDj almacena las frecuencias para cada nota, de tal forma que
al seleccionar una ---digamos la5---, el programa reproduce una
frecuencia ---en este caso 440 Hz---. La configuración DRUM utiliza una
tabla de referencia diferente al reproducir los slides a fin de que
estos suenen como lo harían con la configuración logarítmica del pitch.

------------------------------------------

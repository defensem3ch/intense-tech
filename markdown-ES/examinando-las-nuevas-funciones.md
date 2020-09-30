Intense tech con Defense Mech -- ¡Examinando las nuevas funciones! {#examinando-las-nuevas-funciones}
==================================================================

\- Posted January 15th, 2020 by [Pixel
Guy](https://apixelguy.com "Posts by Pixel Guy")\
*Artículo original de* [*DEFENSE
MECHANISM*](scoping-out-new-features.html)*. Traducción al español por*
[*Pixel Guy*](https://apixelguy.com)*.*

¡Hola y bienvenidos de vuelta a *Intense tech con Defense Mech*! En esta
ocasión daremos un vistazo a las nuevas funciones de la versión 7 del
LSDj. Les garantizo que encontrarán algo que despertará su interés en la
versión más reciente, así que, ¡veamos de qué se trata!

***Aviso: Al momento de escribir este artículo, la versión 7 aún
presenta*** **bugs *y, ¡puede que incluso deje de funcionar! Siéntanse
libres de experimentar con las nuevas funciones, pero ¡por favor
respalden su trabajo! Es recomendable permanecer en la última versión
estable: la 6.9.0.***

------------------------------------------------------------------------

A lo largo de las últimas semanas, el benevolente desarrollador, Johan
Kotlinski, ha estado trabajando duro haciendo mejoras a nuestro amado
secuenciador para Game Boy: el LSDj. La vez pasada nos quedamos en la
versión 7.0.6; en esa ocasión hablamos de la recién adicionada función
de DRUM Pitch. Esta vez hablaremos de la versión 7.7.4, ¡y probaremos
algunas de las características más emocionantes de la misma!
¡Comencemos!

Configuración FX/SPEED
----------------------

Una de las nuevas funciones es FX/SPEED. Como su nombre lo indica, esta
ajusta la velocidad para algunos de los comandos de efectos: llámense C,
P, R y V (los comandos P y V en los canales Pulse y Wave solo son
afectados si PITCH está ajustado en TICK). Al incrementar el valor,
incrementa el número de *ticks* que dura cada efecto, disminuyendo así
la velocidad del mismo. El siguiente video muestra como se afecta cada
uno de los comandos siguiendo el orden dado.

\
*Ajustando FX/SPEED para ralentizar los efectos*.

Comando B (mayBe)
-----------------

Un nuevo comando ha nacido en la versión 7. Este comando es parecido al
comando Z ---[el cual ya cubrimos
anteriormente](no-te-duermas-sobre-la-z-presentando-a-hypnogram.html)---
en algunos aspectos. Al igual que Z, el comando B puede ser utilizado
para aplicar ciertas probabilidades en las notas o en las *tables*. El
utilizar B en las tables también permite la probabilidad de que sea
aplicada. El comando B funciona como el comando H, de forma que
«saltará» a una línea en específico, pero el hecho de que lo haga o no
lo haga es dejado a la probabilidad. Ajustar un comando B a B05 hará que
nunca salte a la línea 05; ajustarlo a B85 hará que salte a la línea 05
cerca de un 50 % de las veces; ajustarlo a BF5 hará que salte a la línea
05, aproximadamente, quince de dieciséis veces.

Utilizar el comando B con instrumentos del tipo Pulse, Wave o Noise
permite ajustar las probabilidades de 0 a F (15). Ajustar el comando a
B00 hará que nunca se active la nota, mientras que ajustarlo a B0F hará
que siempre se active. Los valores intermedios aplican otras
probabilidades; B04 significa que la nota tiene un 25 % de
probabilidades de ser reproducida. B08 indica que la nota tiene un 50 %
de probabilidades de activarse y así sucesivamente. Para los kits de
instrumentos cada dígito afecta a la muestra del lado derecho o
izquierdo por separado. Un comando B48 quiere decir que la muestra de la
izquierda tiene un 25 % de probabilidad de ser reproducida, mientras que
la del lado derecho tiene un 50 %. Veamos cómo se luce esto, pero
primero, hablemos de algo que tal vez ya notaron. Echemos un vistazo a
otra nueva característica, ¡al mismo tiempo!

¡Osciloscopio en el canal Wave!
-------------------------------

Tal vez, en este caso, la característica más impresionante es bastante
fácil de identificar; pero ¡ahora el canal Wave cuenta con un
osciloscopio!

\
*Tal vez no sea mi mejor trabajo, ¡pero la vista es muy agradable!*

Silky Wave
----------

Otra función igualmente sorprendente es la del llamado Silky Wave.
Muchos músicos veteranos del Game Boy tal vez estén familiarizados con
el célebre «clic» en el canal Wave; único del hardware. Mientras que
anteriormente esto requería de la dura aceptación del hecho, ahora,
gracias a los brillantes esfuerzos de Johan Kotlinski, ¡se ha alcanzado
una solución! Los detalles pueden tener un tinte un tanto esotérico,
pero ---hasta donde entiendo---, se ha añadido un temporizador que
permite cambiar la forma de la onda con una mejor sincronía evadiendo el
tan molesto «clic». Esto quiere decir que un espacio de sintetizador que
utilice la velocidad máxima (Speed: 01) es ahora prominentemente más
audible a la frecuencia en la que se supone debería estar. El siguiente
video compara el sonido antes y después del Silky Wave.

\
*¡El «clic» extra ha sido eliminado gracias a Silky Wave!*

R8x: Reactivación súper rápida
------------------------------

Una de las funciones más solicitadas fue la del retorno del viejo *pitch
wrap* del canal Wave. De forma interesante, ese sonido característico
era producido cuando el generador de sonido se reiniciaba una velocidad
bastante alta. Utilizarlo en el canal Wave permite que la afinación del
sonido se apegue a la voluntad del usuario en lugar de simplemente
depender de un comando P. Utilizarlo en un instrumento del tipo Pulse,
como un *kick*, permite que el sonido alcance cerca de tres tonos por
debajo del límite de lo que el canal Pulse genera normalmente. ¡Aquí un
video que lo demuestra!

*Finetune* en los instrumentos del tipo Wave
--------------------------------------------

Como el nombre lo indica, ahora es posible el aplicar *finetune* en un
rango de -F (-15) a +F (+15) en los instrumentos del tipo Wave.

Incremento en el *tempo* máximo
-------------------------------

Una vez más, como el nombre lo indica, ¡ahora el *tempo* máximo es de
295 BPM! Los *tempi* de 256 a 295 BPM pueden ser aplicados al utilizar
los valores de 00 a 27 del comando T.

Incremento en la velocidad de carga de canciones y guardado
-----------------------------------------------------------

El tiempo de carga para guardar y cargar canciones ha sido reducido
drásticamente. Tal vez veas lo que parecen ser algunos *glitches* en los
gráficos, ¡pero es a propósito!

¿Me olvide de alguno? Si tienes alguna pregunta acerca de estas
funciones o algún otro cambio en la versión 7, ¡siéntete libre de
contactarme a defensem3ch\@gmail.com! ¡Hasta la próxima! Espero que se
diviertan jugando con esta nueva versión. Se despide, DEFENSE MECHANISM.

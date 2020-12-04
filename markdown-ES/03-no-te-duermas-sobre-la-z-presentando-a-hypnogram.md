**Intense Tech con Defense Mech -- No te duermas sobre la Z (Presentando a Hypnogram)**
- Posted December 18th, 2018 by [Pixel
Guy](https://apixelguy.com)
*Artículo Original de [DEFENSE
MECHANISM](../en/03-dont-sleep-on-z-feat-hypnogram.md.html). Traducción al Español
por [Pixel Guy](https://apixelguy.com).*

¡Hola, soy DEFENSE MECHANISM! Bienvenidos una vez más a *Intense Tech*,
donde hacemos un análisis profundo sobre algunas de las características
del LSDj, esto con el fin de ayudar a aumentar tu nivel de entendimiento
del programa y tus habilidades como artista.

En la lección del mes pasado vimos el sintetizador del canal Wave. Ahora
nos desviaremos de la síntesis de ondas durante algunas lecciones, pero
¡regresaremos a ella después de preparar el terreno para una emocionante
lección sobre ese tema! Este mes hablaremos del comando Z en LSDj y
exploraremos cómo es que puede [darle sabor a tu
vida](https://www.penzeys.com/).

**Nota:** Puedes encontrar una versión previa de este artículo escrita
por [Hypnogram](https://soundcloud.com/hypnogram) aquí:
<https://hypnogrammusic.blogspot.com/2016/03/dontsleep-on-z-by-h-ypnogram.html>
(El contenido que aquí aparece fue utilizado con su autorización.
¡Gracias, Noah!)

------------------------------------------------------------------------

De la misma manera que el sintetizador del canal Wave del LSDj ---al
cual se le dedicaron [los
dos](01-analisis-del-sintetizador-del-canal-wave-en-lsdj-parte-uno.md.html)
[tutoriales
pasados](02-analisis-del-sintetizador-del-canal-wave-en-lsdj-parte-dos.md.html)--- el
asombroso comando Z es a menudo incomprendido. Aclaremos lo que puede
hacer con algunos divertidos ejemplos de usos creativos para el mismo.
¡Al finalizar esta lección tendrás los recursos necesarios para añadir
un poco de caos controlado a tus composiciones!

Para comenzar, demos un vistazo al [manual del
LSDj](https://www.littlesounddj.com/lsd/latest/documentation/) (versión
6), de esta forma podremos saber qué es exactamente el comando Z.

> **Z, *RandomiZe***:
>
> El comando Z repite el último comando que no sea el Z; añadiendo un
> número al azar al valor original del comando. Los valores del comando Z
> controlan el valor máximo de cada dígito que se añadirá.

Ahora, vamos directo al aprendizaje utilizando un ejemplo:

**Vibrato aleatorio**
---------------------

![ ](../media/z01.mp4)

Para el primer ejemplo explicaré las cosas celda por celda. En la celda
0 tenemos una nota con un comando `V00`. Una vez hecho esto, tenemos la
misma nota con el comando `Z03` en cada una de las que le siguen. Dado que
el último comando que no es Z es V, cada valor `Z03` actuará como otro
comando V; aplicando un valor que se encuentre dentro de los posibles:
ya sea `V00` (otra vez), `V01`, `V02` o `V03`. Sin embargo, esto no afectará o
dañará de alguna manera en particular al comando Z anterior, de forma
que puedes personalizar cada comando Z.

***Duty cicle* aleatorio**
---------------------

![ ](../media/z02.mp4)

A primera vista podría no tener sentido cómo un comando Z se puede
aplicar a un caso como el del *duty cicle* de una onda de pulso; ya que
el comando W utiliza valores gráficos en lugar de números, aún así
pueden tener la seguridad de que funciona bastante bien.

*Width* de la onda a 12.5 % = `00`

*Width* de la onda a 25 % = `01`

*Width* de la onda a 50 % = `02`

*Width* de la onda a 75 % = `03`

En este ejemplo, cada comando `Z03` tiene la posibilidad de aplicar
cualquier *duty cicle* disponible. Sin embargo, ya que 25 % y 75 %
suenan igual, este nos dará una variación un tanto más aleatoria en el
sonido si el rango del comando Z es reducido cambiándolo a Z02; lo que
nos podría dar ya sea 12.5 %, 25 % o 50 % con una probabilidad igual
para cada uno.

***Panning* aleatorio**
---------------------

![ ](../media/z03.mp4)

El comando O es otro caso donde no es tan obvio el cómo funcionaría el
comando Z. O controla la salida hacia izquierda o derecha y, también,
puede ser utilizado para silenciar la salida de ambos canales por
completo. Es muy importante que cuando vayas a aplicar un comando Z
escojas el valor de O con mucho cuidado.

`OLR` (ambos canales encendidos) = `00`

`O__` (ambos canales apagados) = `01`

`OL_` (solo canal izquierdo) = `02`

`O_R` (solo canal derecho) = `03`

En este ejemplo estamos alternando el *panning* entre solo izquierda y
solo derecha. Sin embargo, si buscásemos elegir al azar entre ambos
canales encendidos, solo el izquierdo y solo el derecho; entonces
podríamos poner nuestro valor inicial para el comando O en `OL_`, de esta
forma solo añadiríamos comandos `Z02` de forma sucesiva.

En la versión 6, el comando Z también funciona en las *tables*, donde
actuará poniendo valores aleatorios sobre los valores del último efecto
utilizado en las mismas. Es posible alternar aleatoriamente entre `OLR` y
`O__` en la *table* de un instrumento utilizando Automate=ON para, de
esta forma, conseguir un efecto de *gate* aleatorio, como se muestra a
continuación:

En este caso ---y en el del cambio en el *duty cicle* de una onda pulso
mostrado más arriba--- si el rango del comando Z sobrepasa esos cuatro
valores; el valor será el remanente que quede después de que el valor
inicial de Z se divida entre cuatro. Por ejemplo; si `Z11` aplica de forma
aleatoria el valor `11` (`11` en hexadecimal igual a 17 en decimal)
a nuestro comando P u O, entonces 17 se divide
entre cuatro veces cuatro (16), dejando un remanente de 1, por lo que
este comando Z aplicará el mismo efecto como lo haría si estuvieses
utilizando un valor de `01`.

**Melodía aleatoria**
---------------------

Veamos de nuevo la segunda parte de la descripción del comando Z que nos
ofrece el manual del LSDj; donde se establece que: «Los valores del
comando Z controlan el valor máximo de cada dígito que se añadirá». Esto
quiere decir que cada dígito del comando Z funciona independientemente.

> **Ejemplo**:
> 
> `Z02` añade `0`, `1` o `2` al valor original.
> 
> `Z20` añade `0`, `10` o `20` al valor original.
> 
> `Z22` añade `0`, `1`, `2`, `10`, `11`, `12`, `20`, `21`, o `22` al valor original.
> 
> **Nota**: Por ahora los valores aleatorios no funcionan con comandos
> *Hop*, *Groove* o *Delay*.

Nota sobre la nota: los valores aleatorios SÍ funcionan con los comandos *Hop*, *Groove* y *Delay* a partir de la versión 8.1.9.

Esto puede ser útil en casos donde busques utilizar un *pitch* de manera
aleatoria. Por ejemplo; al utilizar el comando F. `Fxy` controla el
Finetune del canal Pulse con el segundo dígito (`y`), mientras que con el
primero (`x`), controla la afinación del canal Pulse2. `x` representa
cuántos semitonos deben ser añadidos a la nota en la que se esté
trabajando. De esta forma al aplicar `ZF0`, podemos hacer una melodía de
forma aleatoria, pero solo en el canal Pulse2. Cada comando Z añadirá
cualquier nota que se encuentre entre el rango de una octava y una
tercera mayor por encima, incluyendo la nota sobre la que se esté
trabajando.

**Acordes aleatorios**
---------------------

En la versión 4 del LSDj, los dígitos utilizados en los comandos Z no
eran independientes los unos de los otros, lo que hacía que utilizar el
comando Z junto on el comando C (*chord*) fuera un tanto menos útil,
aunque eso no quiere decir que no pudieses conseguir algunos sonidos
interesantes al intentarlo. Al introducirse la independencia entre
dígitos en la versión 6; se hizo posible el ganar más control, de forma
que ahora los acordes, por ejemplo, pueden alternar aleatoriamente entre
mayores y menores. Un acode menor es creado usando `C37`; un acorde mayor
es creado utilizando `C47`. A partir de esto, si utilizas un comando `C37` y
aplicas `Z10`, el comando Z podrá aplicar ya sea `C37` o `C47`.

***Sweep* aleatorio**
---------------------

Nuestro ejemplo final es [la firma del sonido de
Hypnogram](https://soundcloud.com/hypnogram/phantasm-dragon) (escuchen a
partir de la marca en el minuto 1:30 para que lo puedan oír en
contexto). Es muy fácil y divertido. Tengan en mente que este sonido
para un *lead* solo funcionará en el canal Pulse1, ya que es el único
canal que cuenta con *Sweep* de hardware.

<iframe width="100%" height="166" style="height: 166px;"  scrolling="no" frameborder="no" 
allow="autoplay" 
src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/319678401&color=%2322c8ff&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true"></iframe>

Esos son solo algunos ejemplos de lo que puedes hacer con el comando Z.
¡No tengas miedo de experimentar y crear los tuyos!

-----------------------------------------

Por favor, ¡apoyen a [Hypnogram](https://hypnogram.bandcamp.com) comprando sus álbumes en Bandcamp!

<center>
<iframe style="border: 0; width: 350px; height: 470px;" 
src="https://bandcamp.com/EmbeddedPlayer/album=696052333/size=large/bgcol=ffffff/linkcol=0687f5/tracklist=false/transparent=true/" 
seamless><a href="https://hypnogram.bandcamp.com/album/xiii">XIII by Hypnogram</a></iframe>
</center>

------------------------------------------


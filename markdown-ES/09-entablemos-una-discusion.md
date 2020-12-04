**Intense tech con Defense Mech -- ¡EnTABLEmos una discusión!**
- Posted July 23rd, 2019 by [Pixel
Guy](https://apixelguy.com)
*Artículo Original de [DEFENSE
MECHANISM](../en/09-lets-table-this-discussion.md.html). Traducción al Español por
[Pixel Guy](https://apixelguy.com).*

¡Bienvenidos de vuelta a *Intense tech*! En esta
ocasión me gustaría discutir algunas de las diferentes formas de
utilizar las *tables* en LSDj. Espero que después de leer esta lección
te inspires para usar este recurso de formas nuevas y creativas.
¡[Pongamos la mesa](http://penzeys.com/) para comenzar!

------------------------------------------------------------------------

Las *tables* en LSDj son, sin duda, la herramienta más útil para dar
forma a tus sonidos. Pueden ser utilizadas en casi cualquier
instrumento: desde una onda de pulso, hasta arpegios y *leads* o bajos y
percusiones; ¡y pareciera que nunca se tienen suficientes! En esta
lección cubriré algunas técnicas para las *tables* y así dar combustible
a tu creatividad.

Primero veamos lo básico. Hay cuatro columnas en una *table*: Volume,
Transpose y dos columnas para comandos de efectos. La columna Volume
puede utilizarse para hacer envolventes de volumen personalizados ---o
*volume envelopes*--- para los instrumentos. El primer dígito especifica
el volumen (en un rango `0-F` para los canales Pulse y Noise y de `0-3` para
el canal Wave), el segundo indica el número de *ticks* que se mantendrá
ese volumen. De forma que un valor de `36` en la columna Volume ajustará
el instrumento a un volumen de 3 durante seis *ticks*. Después de seis
*ticks*, la siguiente línea de volumen es aplicada hasta el último
comando de volumen. El instrumento se mantendrá en el nivel de volumen
especificado en la última línea hasta que la nota sea silenciada. A
menos que las dieciséis líneas de la columna estén llenas, en ese caso
los valores se repetirán en bucle, iniciando desde el principio una vez
que se alcance la última línea. En el siguiente ejemplo he ajustado una
*table* para automatizar el volumen de un bajo en el canal Wave, de
forma que utiliza Volume `1` durante tres *ticks* y Volume `2` por tres
*ticks* para después cambiar a Volume `3` en el siguiente *tick* y
mantenerse en ese volumen.

![ ](../media/table1.mp4)

La columna Transpose, comúnmente utilizada para arpegios personalizados,
aplica el valor de transposición (Transpose) a la nota actual en
semitonos, con «`01-7F`» transponiendo hacia arriba y «`80-FF`» haciéndolo
hacia abajo. Las columnas para comandos de efectos son muy similares a
las columnas de efectos en las *phrases*, con la excepción de que
algunos comandos no son funcionales en las *tables* ---como los comandos
D--- y los comandos L funcionan de acuerdo a la columna Transpose (solo
en la primera columna. También hay que notar que si se aplica «`L00`», el
*pitch* del instrumento se reiniciará).

Las tables corren a un *tick* por línea de manera predeterminada, a no
ser que la velocidad sea especificada utilizando un comando Groove. Sin
embargo, una *table* también puede ser ajustada en Automate, para, de
esta forma, hacer que la misma aplique una línea por nota.

Usar comandos A en las *tables*
-------------------------------

Al inicio puede resultar confuso, pero es completamente factible el
aplicar una *table* desde dentro de una *table*. Esto puede ser de
utilidad cuando una table está ajustada en Automate y se requiere
utilizar efectos adicionales en la misma nota. En este ejemplo el
instrumento corre Table `01` con Automate activado. Un comando es usado en
la *phrase*, otro en Table `01` y «`A02`» aplica Table 02 en la segunda
columna de Table `01`. De esta forma dos comandos adicionales son
utilizados en Table `02`, ¡haciendo un total de cuatro comandos al mismo
tiempo!

![ ](../media/table3a.mp4)

Utilizado dentro de una *table* sin Automate, un comando A extenderá la
*table* actual dentro de la *table* especificada. Por último, al usar un
valor de `20` o superior, se detendrá a la *table*, ya que no existen
*tables* más allá de `1F`. Esta es una gran forma de terminar una *table*
sin silenciar la nota con un comando K.

![ ](../media/table3b.mp4)

Automatización simultánea
-------------------------

He descubierto un truco genial que sucede cuando dos canales ---como los
dos canales Pulse--- utilizan el mismo instrumento con una *table*
ajustada en «Automate=On» y tocan notas al mismo tiempo: las notas en el
canal uno son afectadas por las líneas marcadas con números pares y las
notas en el canal dos lo son por las que tienen números impares. Esto
permite un efecto de *paning* (o similar) más sencillo al usar solo una
*table*, un instrumento y, ¡solo una *phrase*!

![ ](../media/table2.mp4)

Reforzar el ataque de un instrumento
------------------------------------

Las *tables* son extremadamente útiles para dar a nuestros instrumentos
un brillo extra. Una manera de hacer esto es utilizando un comando de
volumen. Esto también se puede hacer en la columna Volume, pero, en
ocasiones, puede ser más conveniente utilizar un comando. En este
ejemplo de un *snare* de ruido blanco, el volumen del instrumento ajusta
el volumen del ataque inicial, para después ser atenuado de forma
drástica por un comando E. El volumen del instrumento es ajustado a un
nivel relativamente alto para darle al *snare* ese «pop» inicial y así
ayudarlo a pasar por sobre otros instrumentos; aunque después baja para
no ser completamente dominante con un volumen más alto.

Puede resultarte familiar la forma en que se acentúa; es como colocar `0C`
en el primer *tick* de la columna Transpose o cambiar la forma de onda
de las ondas de pulso en los *ticks* uno y dos. Estas pueden ser formas
efectivas de acentuar tus instrumentos. Otro truco para aumentar el
ataque de un instrumento ---como una onda de pulso o un *lead* del canal
Wave--- es ajustar un comando V de alta frecuencia (modo High-Frecuency)
en el primer *tick* para después apagarlo en el segundo con un comando
`V00` o utilizar valores menores para lograr un *vibrato* más sutil. Estas
técnicas pueden ser combinadas para lograr un mejor efecto.

![ ](../media/table3c.mp4)

Hay muchas más maneras de utilizar las *tables*, por lo que este
artículo podría fácilmente continuar por muchas páginas más, ¡incluyendo
ejemplos! Espero que esto te dé algunas ideas al momento de diseñar tus
instrumentos. 

------------------------------------------

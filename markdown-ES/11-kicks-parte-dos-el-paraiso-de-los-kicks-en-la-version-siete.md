**Intense tech con Defense Mech -- kicks parte dos: ¡El paraíso de los kicks en la versión siete!** 
- Posted November 8th, 2019 by [Pixel Guy](https://apixelguy.com) 
*Artículo original de* [*DEFENSE MECHANISM*](../en/kicks-part-2-kick-heaven-in-version-7.md.html)*. Traducción al
español por* [*Pixel Guy*](https://apixelguy.com)

¡Bienvenidos de vuelta a *Intense Tech*! Esta semana
continuaremos con la parte dos del tutorial sobre cómo hacer *kicks*
utilizando LSDj, ¡incluyendo una importante actualización! Al finalizar
esta lección tendrás un amplio arsenal de técnicas para hacer *kicks*
del cual podrás elegir. ¡Continúa leyendo para saber más!

------------------------------------------------------------------------

¡Se aproximan grandes cambios!
-------------------------------------------------

La semana pasada el desarrollador del LSDj, Johan Kotlinski, actualizó
el programa, ¡de modo que ahora se encuentra en la versión siete! (Al
momento de escribir este artículo, la última versión es la 7.0.6.) Una
mejora emocionante en esta versión es que la función TRANSPOSE ahora
funciona con la configuración DRUM del parámetro para el *pitch*; dicho
parámetro ---P/L/V--- también ha sido renombrado a PITCH para evadir
confusiones.

![PITCH antes se llamaba P/L/V](../media/image.png)

Analicemos esta función con un *kick* que haga una transición a la nota
del bajo. Comenzaré con el *kick* dos octavas por encima de la nota en
la que quiero que esté el bajo. La *table* que utilizará el *kick* usa
un comando P rápido seguido de un comando L y un valor de transposición
de E8 para que la nota se deslice dos octavas hacia abajo.

Otros usos de la configuración DRUM
-------------------------------------------------

Como mencioné la semana pasada, la configuración DRUM del *pitch* es
efectiva al momento de crear *snares* o *toms*. Al hacer un *snare*,
usualmente sigo la misma estructura general de la *table* que al diseñar
un *kick*; utilizo un comando P rápido seguido de un comando L para
transponer la nota a donde ya he afinado el *snare*. Esto le da al
*snare* una sensación de tonalidad que puede ser reforzada con un
*snare* de ruido blanco a fin de conseguir un sonido con «cuerpo». En el
siguiente ejemplo también bajo el volumen con comandos E para proveer de
forma al *decay*.

![ ](../media/wavsnare.mp4)

La configuración DRUM en los canales Pulse
-------------------------------------------------

La configuración DRUM también funciona en los canales Pulse. En el
siguiente ejemplo he creado un *kick* de onda de pulso, así como un
*snare* y *toms*. Utilicé un *duty cycle* de 50 %, también conocido como
onda cuadrada, para conseguir un mayor impacto. Aunque los canales Pulse
no pueden alcanzar la octava grave de la que es capaz el canal Wave,
¡pueden generar *kicks* efectivos! La *table* para el *snare* en estos
canales es similar a la del canal Wave, excepto que removí los comandos
E y, en su lugar, utilicé lo envolventes (*envelopes*) de la pantalla
Instrument para controlar el *decay*. El *tom* tiene una duración
inferior, por lo que agregué los comandos P directamente en la *phrase*
para ajustar el *slide*; así no hay que utilizar una *table*.

![ ](../media/pulsedrum.mp4)

Percusiones utilizando el *sweep* del *pitch* de hardware en el canal Pulse 1
-------------------------------------------------

El canal Pulse 1 tiene *sweep* para el pitch de hardware, el cual es
útil para hacer sonidos atonales, y aquellos *blips* y *blops* parecidos
a los de los videojuegos de antaño (sí, comprendo que el chip de sonido
del Gameboy es muy bueno para esto). Aunque esta función también se
puede utilizar para hacer *kicks*, *snares* o *toms*. En el ejemplo de
abajo utilizo un valor de F4 para el comando S para el *kick* y un valor
de `E3` para el *snare*. Valores similares a este (E) en el comando S
pueden ser utilizados para hacer *toms*.

![ ](../media/sweepdrum.mp4)

*Kicks* en el canal Noise
-------------------------------------------------

Por último pero no menos importante, y a pesar de que no produce los
sonidos más «elegantes», el canal Noise puede ser usado para generar
tonos graves que funcionan bien como *kicks*. En [este turorial del
canal Noise hecho por Boy Meets
Robot](https://www.youtube.com/watch?v=wD7omqjHXmI) se explica el mismo
a profundidad. A manera de un resumen rápido se podría decir que
cualquier forma (*shape*) de un instrumento en dicho canal que termine
en un valor de `0` a `7` producirá un sonido más tonal, lo cual puede ser
explotado para crear un sonido más suave para un *kick*. Transponer
hacia abajo en intervalos de diez bajará la octava en la que se
encuentre este sonido parecido a la estática y generará una bajada en el
tono para, así, crear un *kick* en canal Noise.

![ ](../media/noisekick.mp4)

Combinando canales
-------------------------------------------------

Cuando utilizamos dos canales para un *kick*, ¡podemos combinar sus
fuerzas! En el siguiente ejemplo creé un *kick* muy corto utilizando la
octava más baja posible en el canal Noise y la combiné con un *kick* en
un canal Pulse. Dado que el canal Noise produce la frecuencias más bajas
y el canal Pulse añade una inclinación descendiente en el tono ---además
de tener material tonal que añadir al *kick*---; el resultado es un
sonido más «lleno» que al utilizar solo un canal para hacerlo. Este
ejemplo es de [mi remix de *Dox the fash*, Cyanide
Dansen](https://cyanidedansen.bandcamp.com/track/dox-the-fash-remix-by-defense-mechanism)
(puedes encontrar el archivo de guardado
[aquí](https://defensemech.com/songs)):

![ ](../media/doxfash.mp4)

¡Eso es todo en este artículo de dos partes! Regresen el próximo año (me
tomaré libre el mes próximo) para prender aún más técnicas que utilizar
el LSDj.

------------------------------------------

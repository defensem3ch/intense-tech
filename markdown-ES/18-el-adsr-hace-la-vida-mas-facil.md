**Intense tech con Defense Mech - ¡El ADSR hace la vida más fácil!**
-Publicado November 29, 2020 por [DEFENSE MECHANISM](../en/18-adsr-makes-life-easier.md.html). Traducción por [Pixel 
Guy](https://apixelguy.com/)

¡Hola y bienvenidos a otra entrega de *Intense tech*! En esta ocasión
daremos un vistazo a una función relativamente nueva que fue introducida
en la versión 8.1.0: ¡ADSR para los instrumentos del tipo Pulse y Noise!
Esta es una mejora muy grande comparada con los viejos envolventes; así
que veremos qué es nuevo y diferente. También cubriremos un cambio
importante respecto a versiones anteriores: la sustitución del volumen
de hardware por volumen de software en la versión 8.8.0. ¡Vamos a ello!

Atacando la curva de aprendizaje del volumen
--------------------------------------------

*********************************************************
*        .                                              *
*       / \                                             *
*      /   \                                            *
*     /     '-----------------------------------.       *
*    /                                           \      *
*   /                                             \     *
*  /                                               \    *
* Attack  Decay           Sustain              Release  *
*(ataque)(decaimiento) (sostenimiento) (desvanecimiento)*
*********************************************************

El ADSR, que viene del acrónimo inglés para Attack (ataque) - Decay
(decaimiento) -Sustain (sostenimiento) -- Release (desvanecimiento),
hace referencia a las cuatro etapas del volumen que son consideradas
normalmente al momento de moldear un sonido. Puede representarse
gráficamente de la siguiente manera:

Un sonido con un ataque largo comienza a un volumen bajo que se
incrementa lentamente, mientras que un sonido con un ataque corto
aumenta su volumen casi de manera instantánea. De igual manera, un
sonido con un *decay* (decaimiento) corto se desvanecerá rápidamente
hacia el silencio, pero un *decay* largo permite al sonido el
desaparecer lentamente. El *sustain* nos da la opción de ajustar un
volumen constante en caso de que la nota se mantenga. Por último,
configurar un *release*\* de una duración corta o larga permitirá que la
nota se desvanezca hacia el silencio de forma rápida o lenta,
respectivamente, una vez que el volumen establecido por el *sustain* es
liberado. Como sucede con *sustain*, esto es opcional y puede no tener
efecto si este no está activo.

Una vez que hemos explicado todo esto, podemos comenzar a discutir cómo
funciona el ADSR en el LSDj. Puede que ya estés familiarizado con los
envolventes para instrumentos de versiones anteriores en los que el
primer dígito representa el volumen inicial con un valor de `0` a `F` y el
segundo dígito representa el *decay*. En este último los valores de `1` a
`7` disminuyen el volumen, siendo `1` el más rápido y `7` el más lento, y los
valores de `9` a `F` lo incrementan, siendo `9` el más lento y `F` el más
rápido. Los valores `0` y `8` en el segundo dígito mantienen el volumen del
primero indefinidamente.

El ADSR funciona en una manera similar a la que lo hacen los comandos E.
En lugar de ajustar una configuración de volumen para cada etapa del
envolvente ADSR, cada una de esas etapas actúa como un comando E. El
primer dígito especifica el volumen y el segundo indica la longitud del
tiempo por la que se ha de mantener dicho volumen. Ya sea que el volumen
aumente o disminuya dentro de dicho lapso de tiempo, esto es
especificado por la siguiente etapa del ADSR hasta que se alcanza la
tercera, en la que el volumen se desvanece a cero.

**Ejemplo**: `54/00/--`

Un sonido con este ADSR comenzará con un volumen de `5`, después se le
aplicará un *decay* con velocidad de `4` hasta que se silencie.

**Ejemplo**: `03/A2/71`

Un sonido con este ADSR comenzará con un volumen de `0` que se
incrementará rápidamente con una velocidad de `3` hasta un valor de `A`, que
disminuirá de manera acelerada a una velocidad de `2` hasta un volumen de
`7` y se desvanecerá apresuradamente hacia el silencio a una velocidad
de `1`.

**Ejemplo**: `74/07/43`

Un sonido con este ADSR comenzará con un volumen de `7`, se le aplicará un
*decay* con velocidad de `4` hasta que alcance un volumen `0`, entonces
aumentará lentamente a una velocidad de `7` hasta un volumen de `4` hasta
que se desaparezca en el silencio a una velocidad de `3`.

Actualizando las configuraciones de volumen en las nuevas versiones
--------------------------------------------

En todas las versiones de LSDj anteriores a la 8.8.0, el volumen para
los canales Pulse y Noise es controlado por el hardware del Game Boy. Un
desafortunado efecto secundario de esto es que cuando el envolvente del
hardware es alterado, el sonido de los canales Pulse o Noise se
reinicia, lo que resulta en un clic que es apreciable. En el canal Noise
también causa un ligero cambio en el tono del ruido por un instante
después de que el sonido se reinicia. Gracias a esto no era posible que
hubiera transiciones suaves entre las diferentes etapas del ADSR.

Sin embargo, a partir de la versión 8.8.0, ¡el software se encarga del
volumen! Los cambios en dicha característica ahora suceden sin que se
reinicie el sonido, lo que resulta en transiciones de volumen suaves e
ininterrumpidas para los canales Pulse y Noise. Usar la columna Volume
en las *tables* ahora tampoco genera clics, lo que nos ofrece otro
método de control sin clics.

Los comandos E funcionan como lo hacían antes para mantener la
compatibilidad con canciones viejas, pero el ADSR del software añade un
poco a las configuraciones: una velocidad de 1 es extremadamente corta,
mientras que una de F es un poco más larga que la anterior para 7. Aquí
hay una pequeña tabla que muestra la equivalencia más conveniente
respecto a los viejos envolventes con el nuevo ADSR del software.

<style>
th { display: none;}
</style>
 | 
 --|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--
**Software** | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | A | B | C | D | E | F
**Hardware** | 0 | - | - | - | - | - | 1 | - | 2 | 3 | 4 | 5 | 6, 7 | - | - | -

Como puedes observar, tenemos cinco valores que son más rápidos que los
más rápidos del hardware, ¡y tres que son más largos que los más largos
de los anteriores! Usar las velocidades más rápidas que nos ofrece el
software te dará un control más detallado sobre el ataque y el *decay*,
lo que es extremadamente útil cuando se diseñan instrumentos de
percusión, sobre todo a *tempi* bajos. Ajustar la duración a 0 siempre
sostendrá indefinidamente el volumen especificado.

*Decay* instantáneo
-------------------

Para crear un sonido que tena un *decay* instantáneo ajusta el segundo
dígito o la tercera etapa del ADSR a una duración de 1. El siguiente
ejemplo muestra un ADSR de dos etapas con *decay* instantáneo.

![*Decay* instantáneo](../media/adsrinst.mp4)

*Transient* para percusiones del tipo Noise
--------------------------------------------

Aquí hay un par de ejemplos de percusiones del tipo Noise con
*transients*.

El siguiente video muestra cuatro *hi-hats* con un *transient* de
volumen de 6 que desciende rápidamente a un volumen de 4 para
desvanecerse hacia el silencio; después se muestran cuatro *hi-hats* que
empiezan con un volumen de 4 y se desvanecen hacia el silencio.

![Hi-hat *ADSR*](../media/adsrchh.mp4)

¿Puedes notar el impacto extra que tienen los primeros cuatro *hi-hats*?
Aunque es sutil, incluso este pequeño ajuste puede ayudar a los
*hi-hats* a resaltar en la mezcla. Puedes jugar con las configuraciones
de volumen y duración de ambas etapas del ADSR e incluso usar ambos
instrumentos; tal vez solo quieras que haya *transients* en los tiempos
débiles.

El primer ejemplo de los de abajo es un *snare* que utiliza comandos E
en una *table* con volumen de hardware en la versión 8.5.0. EL segundo
ejemplo es un *snare* utilizando *transients* de ADSR en la versión
8.9.6.

![Snare *con* transients *en la versión 8.5.0*](../media/esnare.mp4)

![Snare *con* transients *de ADSR en la versión 8.9.6*](../media/adsrsnare.mp4)

Como se puede observar, ahora es posible conseguir estos sonidos sin
recurrir a colocar comandos E en la *table* del instrumento. A *tempi*
lentos, estos *transients* pueden durar menos que un *tick*, lo que es
imposible de alcanzar controlando el volumen desde una *table*. También
puedes notar que el comando K ya no causa un clic al final de las notas.

**Nota importante: el BGB no tiene soporte para los envolventes de
software si está corriendo en *modo Gameboy*. Si usas BGB, asegúrate de
ajustar el emulador para Gameboy Color o de otra manera el volumen no
funcionará correctamente.**

Reconsiderando el trémolo
-------------------------

Un genial efecto secundario del ADSR es lo que pasa cuando se usan
comando R. Dado que el comando R puede cambiar el volumen cada vez que
se reactiva, ahora es posible conseguir un efecto parecido al trémolo.
Aquí hay un ejemplo.

![Trémolo con ADSR y comandos R](../media/tremolo.mp4)

------------------------------------------

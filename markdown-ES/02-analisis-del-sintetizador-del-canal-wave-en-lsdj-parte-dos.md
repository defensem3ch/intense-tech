**Intense Tech con Defense Mech -- Análisis del sintetizador del canal Wave en LSDj. Parte dos**
- Posted November 9th, 2018 by [Pixel
Guy](https://apixelguy.com)
*Artículo Original de [DEFENSE
MECHANISM](../en/02-lsdj-wave-synth-deep-dive-part-2.md.html). Traducción al Español por
[Pixel Guy](https://apixelguy.com).*

Hola, soy DEFENSE MECHANISM, ¡bienvenidos de nueva cuenta a *Intense
Tech*! Únanse a mí a medida que exploramos a profundidad las funciones
del LSDj con el fin de ayudarte a ti, lector, a aumentar tu
entendimiento del programa.

¡En este tutorial continuaremos cubriendo lo que se necesita para
entender el sintetizador del canal Wave! [La vez
pasada](01-analisis-del-sintetizador-del-canal-wave-en-lsdj-parte-uno.md.html)
vimos los parámetros Signal, Volume, Filter, Cutoff y Q. En esta ocasión
veremos específicamente los parámetros de Dist, Phase, Vshift y Limit.
¡Te mostraré cómo añadir un poco de esa cualidad crujiente
característica del Noise a tus sonidos del canal Wave! Al terminar
deberías de tener una idea vasta de cómo conseguir cualquier tipo de
sonido en el canal Wave, desde un *lead* suave y sedoso, hasta un bajo
enigmático y crujiente.

------------------------------------------------------------------------

En la [primera
parte](01-analisis-del-sintetizador-del-canal-wave-en-lsdj-parte-uno.md.html)
hablé sobre cómo usar diferentes configuraciones en el filtro afecta a
los armónicos que se producen en el canal Wave. Cómo ya hemos visto,
entre más ciclos tenga una forma de onda en el cuadro de onda (pantalla
WAVE), más agudo será el armónico que se produzca. De hecho, el número
de ciclos corresponde al número de armónicos que se reproducirán.

Si has dado un vistazo a las configuraciones por tu cuenta o has leído
el manual del LSDj; muy probablemente te has encontrado con otra forma
de cambiar el número de ciclos: cambiar el valor de Phase.

El parámetro Phase en LSDj comprime la forma de la onda horizontalmente.
Cuando el parámetro está ajustado en Normal, incrementar el valor por
encima de 0 comprimirá la onda por completo, añadiendo *samples* con
volumen de 0 al final. De esta forma se podría decir que es igual a
cambiar el *width* de una onda de pulso, alias [*duty
cycle*](https://es.wikipedia.org/wiki/Ciclo_de_trabajo). De hecho, una
técnica común para conseguir *leads* de onda de pulso modulados
(usualmente asociados con el SID de la C64 por ejemplo) es ajustar
Signal a Square, mantener la configuración de Phase en Normal, poner el
valor inicial de Phrase a 00 y el de final a 1F (o 1E en la versión 4).

![Lead SID con el parámetro de Phase en Normal.](../media/normal-phase.gif)

![ ](../media/normal-phase.mp3)

Para conseguir un *lead* que se asemeje a una voz, intenta esto con
Signal ajustado a Triangle en lugar de Square.

Si cambiamos el parámetro de Phase a Resync, solo nos estaremos dando
otra forma de añadir armónicos, una similar a cambiar el Cutoff de la
onda. Lo que hace Resync es que, en lugar de comprimir la forma de onda
una vez y añadir *samples* con valor de 0 al final, repite la forma de
onda hasta que los 32 espacios para *samples* están llenos.

![Nota: en la versión 4 de LSDj, Phase 1F es usualmente silencio, por lo
que este espacio tendría que ser llenado manualmente.](../media/resync-phase.gif)

![ ](../media/resync-phase.mp3)

También puedes experimentar con Resync2 que, como Resync, repite la
forma de onda para llenar el cuadro de onda, pero no la comprime. Esto
normalmente tiene el efecto de bajar el volumen, como cuando solo
repites en bucle una parte de la forma de onda. Por lo general nunca
llega tan alto o tan bajo como bien podría hacerlo. Sin embargo, la
pérdida de volumen complementa armónicos adicionales compresos en la
forma de onda.

![](../media/resync2-phase.gif)

![ ](../media/resync2-phase.mp3)

Hasta ahora, los cambios en las formas de onda han resultado en un
sonido bastante limpio. Los armónicos tienen un sonido suave y claro,
pero ¿y si realmente quisiéramos añadir un poco de suciedad? Tendríamos
que bajar y ensuciarnos un poco para transformar a nuestra onda senoidal
en algo como esto:

![](../media/nois1-1541522752.gif)

![ ](../media/nois1-1541522752.mp3)

Ese último cuadro del sintetizador mostrado arriba es como se ve el
Noise puro en el canal Wave. Entre más difusa se ve la forma de onda,
más armónicos son combinados de manera diferente para añadir más
suciedad. Aquí hay un ejemplo de cómo suenan 16 cuadros de Noise puro.

![](../media/nois2-1541523664.gif)

![ ](../media/nois2-1541523664.mp3)

Entonces, ¿cómo añadir todo esto a nuestras formas de onda? Una manera
de hacerlo es, en esencia, añadir algunos «puntos» extra. Estos se
pueden agregar de forma manual, como al poner un poco de polvo en una
onda senoidal normal.

![](../media/sine-grit.gif)

![ ](../media/sine-grit2.mp3)

El parámetro de Dist (Distorsión) también afecta el contenido de
suciedad en la onda. El término distorsión en LSDj se refiere a lo que
pasa cuando la forma de onda sobrepasa el rango dinámico disponible; en
otras palabras, es lo que pasa cuando se incrementa el valor de Volume o
de Q de una forma de onda y se lleva por encima del volumen máximo. Como
recordarás, el volumen es representado por los valores de 0-F. Si el
pico de volumen de la señal es superior a F o inferior a 0, el parámetro
Dist de la forma de onda determinará cómo reaccionará el LSDj.

El parámetro por defecto de Dist, Clip, elige solo «recortar» los
valores en 0 y F. Es como si solo cortáramos la punta y el fondo. Entre
más incrementemos el volumen de nuestra onda senoidal, más comenzará a
sonar como una onda cuadrada.

![](../media/clip.gif)

![ ](../media/clip.mp3)

Recuerda que una onda cuadrada añade algunos armónicos un tanto extraños
al sonido de una onda senoidal, por lo que esta es una posibilidad.

La siguiente opción, Fold (la cual fue introducida en la versión 6),
«refleja» lo que esos parámetros de volumen podrían ser en la punta y en
el fondo.

![](../media/fold.gif)

![ ](../media/fold.mp3)

Ahora, en lugar de cortar esos componentes de nuestra onda senoidal que
llegan a los límites superior e inferior, los excedentes de volumen son
reincorporados a la forma de onda principal. Comparado con el corte
profundo parecido a una onda cuadrada de la opción Clip, este es mucho
más agudo y resonante, con armónicos más altos. También tiene un volumen
más bajo, ya que hay menos *samples* al fondo del rango dinámico. Sin
embargo, puedes incrementar el valor de Volume o de Q y dejar que los
*samples* se reincorporen varias veces para un mayor efecto.

La última opción, Wrap, se encargará de cualquier sonido agudo que pase
la punta y lo añadirá al siguiente *sample* yendo de arriba hacia abajo
y viceversa. Comparado con Clip y Fold, este es caracterizado por la
dureza y ruido reflejados en el sonido final. Tiende a tener un volumen
más alto que Fold, debido a que distribuye más samples de manera
uniforme a través de todo el rango dinámico, aunque su volumen no es tan
alto como el de Clip.

![](../media/wrap.gif)

![ ](../media/wrap.mp3)

Cuando se ajusta Dist en Wrap y se incrementa el volumen, muchos de los
volúmenes de *samples* son puestos de forma repetida, ya que se exceden
los valores de 0-F muchas veces. Esto crea varios escenarios donde los
*samples* saltan a través de porciones grandes en el rango dinámico.
Cuando incrementas el valor de Volume o de Q puedes causar que la forma
de onda se mueva de forma impredecible; algo con lo que puede ser un
tanto complicado trabajar al momento de lidiar con un sonido preciso.
Solo tienes que experimentar y escuchar cómo diferentes armónicos le dan
color al sonido, pero en general solo sonará duro, rico, ruidoso y
crujiente.

Para recapitular, lo que hemos aprendido hasta el momento es:

-   Si tu forma de onda se ve como una onda senoidal, triangular o
    cuadrada con un ciclo completo contenido enteramente en el cuadro de
    onda, su sonido será claro y suave. En octavas bajas tendrá bajos
    abundantes.
-   Entre más repeticiones de ciclos de onda se tengan en el cuadro de
    onda, las frecuencias producidas en los sonidos resultantes serán
    más altas. El número de repeticiones corresponde al armónico de la
    nota en la serie armónica que será reproducido.
-   Entre más ruido se produzca dentro de cuadro de onda, menos claro
    será el sonido y el mismo será dotado de más color en los armónicos
    superiores, dándole así un tono ruidoso y resonante. En octavas
    bajas tendrá bajos menos enfatizados y un sonido más duro, crudo y
    crujiente.
-   Las formas de añadir frecuencias más altas incluyen: poner «puntos»
    de manera manual en la forma de onda; aumentar el valor de Cutoff e
    incrementar el valor de Q para dar énfasis; cambiar el parámetro de
    Phase e incrementar los valores; añadir diferentes parámetros para
    Dist al mismo tiempo que se aumentan los valores de Volume o de Q.

Muy bien, así que, ¡tenemos una forma de onda muy ruidosa! ¿Ahora qué?
Bueno, ¡tal vez es DEMASIADO ruidosa! ¿Qué hay si nos gusta su sonido,
pero queremos suavizarla un poco manteniendo su carácter casi intacto?

¡Me alegra que preguntes! Otra nueva función agregada en la versión 6 es
el poder limitar (Limit) el volumen DESPUÉS de que los  valores
iniciales de Volume, Cutoff, Q y Phase son aplicados. El valor aplicado
a Limit restringe los *samples* a un rango de volumen, por ejemplo:
poner Limit a "F" permite los volúmenes de 0 a F, pero si lo ponemos a
5, solo permitirá los volúmenes de 5 a A (diez en hexadecimal), por lo
que los valores que se pudieran alcanzar por debajo de 5 o por encima de
A serían limitados a quedar dentro de ese rango de acuerdo al parámetro
de Dist que se esté manejando en ese momento.

Esto es una función realmente útil, porque, como ya hemos visto, es
fácil alcanzar el nivel máximo disponible en el rango dinámico de la
pantalla WAVE, inclusive si nuestros valores de volumen son bastante
bajos. Adicionalmente, el Gameboy no nos ayuda mucho al solo permitir
cuatro volúmenes para el hardware en el canal Wave: 100 %, 50 %, 25 % y
0 % (*off*). Cuando aplicamos Clip o Wrap a nuestras formas de onda y
alcanzamos constantemente todo el rango de volumen; yendo de 0 a F, el
canal Wave desafortunadamente tiende a, en ocasiones, ser demasiado
ruidoso con un volumen de 100 % y demasiado silencioso a 25 % o 50 %.
Afortunadamente, ahora podemos elegir distorsionar nuestra forma de onda
para conseguir un poco de riqueza en el sonido con algunos armónicos
añadidos, teniendo al mismo tiempo un completo control del rango de
volumen. Para ayudarnos aún más, ahora podemos elegir un rango de
volumen como punto de partida y otro como punto final. Esto nos
permitirá hacer transiciones más suaves entre volúmenes altos y bajos y
viceversa; como se muestra a continuación, con Limit iniciando en F y
terminando en 4.

![](../media/limit.gif)

![ ](../media/limit.mp3)

Para terminar tenemos la función de Vshift, o *Vertical shift*. Este
parámetro nos permitirá poner los *samples* de la forma de onda  de
manera ascendente. En versiones anteriores de LSDj, Vshift funcionaba de
manera similar a la distorsión Wrap; ya que la forma de onda se mueve de
manera vertical y al alcanzar F se reincorpora de nuevo comenzando en 0.
Esto hace posible el poder elegir usar Dist con configuración Clip,
aumentar el volumen y aún así añadir un cambio de Vshift para introducir
algunos sonidos más duros. De la misma manera que Wrap, el incrementar
Vshift, a menudo, resulta en cambios impredecibles, aunque puede ser
divertido experimentar con esto.

El al versión 6 de LSDj, Vshift sigue la configuración de Dist que se
encuentre activa en ese momento. Con Clip, Vshift aplastará la forma de
onda contra el tope a medida que su valor se incremente. Esto, al igual
que Fold y Resync2, tiene el efecto de hacer que la forma de onda tenga
un volumen más bajo.

![](../media/vshift1.gif)

![ ](../media/vshift1.mp3)

Al mover la configuración a Fold, comenzará a reflejarse de nueva cuenta
a través del límite. Con Vshift ajustado a FF, la onda original será
invertida.

![](../media/vshift2.gif)

![ ](../media/vshift2.mp3)

Ajustado a Wrap, se reincorporará desde el fondo.

![](../media/vshift3.gif)

![ ](../media/vshift3.mp3)

¡Con suerte ahora tienes una mejor idea de cómo funciona el sintetizador
del canal Wave en LSDj! Espero que esto te haya ayudado a explorar sin
miedo todos los tipos de opciones que hay y te dé un concepto de qué
tipo de parámetros necesitas ajustar cuando busques conseguir un sonido
determinado. ¡Aunque también espero que esta clase experimentación te
ayude a encontrar un sonido que no hayas escuchado antes!

------------------------------------------

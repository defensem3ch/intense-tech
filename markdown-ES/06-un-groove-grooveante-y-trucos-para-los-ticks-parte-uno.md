**Intense Tech con Defense Mech -- Un groove grooveante y trucos para los ticks: Parte uno**
- Posted April 11th, 2019 by [Pixel
Guy](https://apixelguy.com)
*Artículo Original de [DEFENSE
MECHANISM](../en/06-groovy-groove-and-tick-tricks-part-1.md.html). Traducción al
Español por [Pixel Guy](https://apixelguy.com).*

¡Hola y bienvenidos una vez más a *Intense Tech*!  Este
mes compartiré algunos ejemplos de cómo utilizar diferentes *grooves* en
LSDj. Una vez que hayas leído esta lección, deberías de sentirte cómodo
al utilizar técnicas avanzadas para manipular el tiempo en tus
creaciones en LSDj.

------------------------------------------------------------------------

Me gustaría comenzar con lo [básico](http://penzeys.com), así que sean
pacientes hasta que lleguemos a territorio conocido. Primeramente, ¿qué
es un ***tick***? Un *tick* es la unidad de medida más pequeña en LSDj.
Es como un pixel de tiempo; no puedes dividirlo en partes más pequeñas
(¡lo que básicamente lo hace la unidad de Planck del LSDj!) Qué tan
corto o largo sea depende de la configuración de *tempo*; por ejemplo,
un tick a 80 BPM es el doble de largo que uno a 160 BPM. (En ocasiones,
los valores individuales de cada *tick* pueden variar ligeramente en pos
de mantener el *tempo* lo más consistente posible.)

Los valores para comandos como <b>K</b>ill, <b>D</b>elay y <b>R</b>etrigger son
especificados en un número de *ticks*. Por ejemplo; K01 silenciará una
nota después de un *tick*. La configuración de Speed en los instrumentos
del canal Wave también es especificada en *ticks*. De forma adicional,
las *tables* corren los comandos a razón de un *tick* por línea de
manera predeterminada.

El añadir un ***groove*** nos permite especificar cuantos *ticks* debe
durar cada línea de una *phrase* o *table*. El *groove* por defecto es
`6/6`, lo que quiere decir que la primera línea de la *phrase* dura seis
*ticks* (de hecho, el segundo «6» en el *groove* es redundante y puede
ser removido sin que se afecte la forma en que se reproduce la canción).
Para aplicar el *groove* a la *phrase* o a la *table*, solo coloca un
comando **G**. La línea en la que sea colocado dicho comando G durará el
número *ticks* especificados en el primer dígito de ese *groove* y cada
línea después de esa durará lo especificado en los dígitos siguientes.
Por ejemplo, un *groove* en `7/5` colocado en la línea 3 de una *phrase* o
*table* querrá decir que la línea 3 durará siete *ticks*, la línea 4
durará cinco y así sucesivamente.

Para organizar los *grooves* dentro de una canción; yo utilizo una
técnica que aprendí de [Hypnogram](http://hypnogram.angelfire.com/).
Esta consiste en introducir el número de *ticks* en los *grooves* de
acuerdo al número del *groove* mismo. Por ejemplo;  Groove `00` es el que
viene predeterminado, pero no se puede introducir cero *ticks*, por lo
que quedaría `6/6` (o `6`, o lo que yo quiera que sea la configuración por
defecto). En los *grooves* siguientes, Groove `01`, será ajustado a 1;
Groove `02` a 2 y así sucesivamente. Generalmente acostumbro hacer esto
hasta llegar a `0C` ---o 12---, que es el doble de la configuración
predeterminada: 6 (aunque, si así lo deseas, puedes continuar hasta
Groove `0F`). De esta forma si utilizo un comando G en una *phrase* o
*table*, es inmediatamente notorio el cuánto dura cada línea del mismo.
Es entonces cuando introduzco algunos *grooves* personalizados para
Groove `10-1F`; de esta forma si doy un vistazo al comando G y veo `G12` o
`G17`, sabré que cada línea durará un número diferente de *ticks*. Por
ejemplo, puede que quiera hacer de `G10` un *groove* que se columpia a
`7/5`.

Una técnica divertida es el explotar la habilidad única del LSDj de
poder utilizar un *groove* diferente en cada canal. En
[mi](https://www.youtube.com/watch?v=a1rFQiJ6NvA)
*[cover](https://www.youtube.com/watch?v=a1rFQiJ6NvA)* [de la canción
*Into you*, de Ariana
Grande](https://www.youtube.com/watch?v=a1rFQiJ6NvA), ajusté el *groove*
del canal Wave a `7/5` para darle un efecto de *swing* al bajo y al
*kick*; manteniendo el resto de los canales en una configuración en `6/6`
. Esto le da un efecto de tensión algo agradable, al mismo tiempo que da
la impresión de sonar como si se estuviera balanceando a la vez que
mantiene una sensación rítmica pareja.

En un *groove* como `7/5`, la primera línea dura siete *ticks* y la
segunda dura cinco. Dado que solo hay dos valores especificados en este
*groove*, cada línea que le siga alternará entre durar cinco o siete
*ticks*. Esta sensación rítmica de duraciones cortas y largas
alternándose añade *swing* a las semicorcheas. Incrementar la diferencia
entre los números del *groove,* como en `8/2` o `9/3`, aumentará el *swing*
de forma dramática.

También podrías experimentar utilizando un canal con un *swing* a `8/4` y
otro a `7/5` para obtener una sensación rítmica más fluida. En mi canción
[*Illumin8*](https://defensemechanism.bandcamp.com/track/illumin8),
utilicé diferentes ajustes en los *groove* para el *lead* de forma que
pudiera enfatizar diferentes partes en la melodía. Algunos *grooves*,
como `8/5` o `7/4`, combinan ambas sensaciones rítmicas comprendiendo
veinticuatro *ticks* en cuatro líneas, lo mismo que un *groove* de seis
*ticks* o uno a `7/5`. Esto además incrementa la forma en que se genera el
«estira y afloja» de la melodía, contribuyendo a crear una sensación más
suelta, menos rígida y más humana en el *lead*. Lo que le da un sutil
contraste comparado con el *groove* simple de `7/5` que tienen el resto de
los canales.

![Los Grooves `10`, `11`, `13` y `15` tienen todos diferentes valores en el groove](../media/illumin8.mp4)

Podría hacer de `G11` un *groove* a `3/9` para hacer algunos *bendings*
(usualmente hago algo así en estos casos: `3/9/6/6`. Solo en caso de que
necesite espacio para añadir algunos comandos hasta que pueda ingresar 
un comando G para regresar a un *groove* de seis *ticks*). Este *groove*
también es útil si quieres que tu *kick* del canal Wave dure solo tres
*ticks* antes de que la nota del bajo entre. Aquí hay un ejemplo donde
utilicé este *groove* de ambas formas, *BEAT JuiCE*:

![Añadiré una nota aquí. En la versión 6 de LSDj, se permite el
reactivar el mismo *groove* utilizando comandos G sucesivos para
reiniciar el mismo *groove* desde la línea uno. Las versiones anteriores
de LSDj, sin embargo, no reiniciarán el *groove* si el mismo comando es
utilizado de forma consecutiva.](../media/beatjuice.mp4)

Aunque es muy común trabajar con la forma predeterminada de seis
*ticks*, puede haber casos en los que seis *ticks* por línea sea muy
lento. Escoger un *groove* de tres *ticks* por línea nos da una mayor
resolución para las notas rápidas y también al momento de activar los
comandos. Básicamente; tocar *phrases* con un *groove* de seis *ticks*
nos permite reproducir dieciséis notas y comandos, cada uno con una
duración de seis *ticks*, lo que nos da un total de 96 *ticks* por
*phrase*. Si tocas una *phrase* con un *groove* de tres *ticks*, podrás
reproducir notas y comandos al doble de velocidad; pero cada *phrase*
durará solo 48 *ticks*, por lo que necesitarás dos *phrases* de tres
*ticks* para cubrir la misma cantidad de tiempo que una *phrase* de seis
*ticks*. De la misma forma, al incrementar la resolución, necesitarás de
tres *phrases* de dos *ticks* ---o seis de *phrases* de un *tick*---
para cubrir la misma cantidad de tiempo.

Una forma de tomar ventaja de las *phrases* con una resolución mayor es
usar un comando <b>H</b>op dentro de la *phrase* para añadir *ticks* a su
duración. Con los comandos Hop adecuados, una *phrase* que normalmente
dura 48 *ticks* puede ser convertida para durar 96. Algunas veces esto
hace que sea complicado el reproducir en bucle, ¡pero puede ser
gratificante el averiguar cómo hacerlo!

En este ejemplo utilizando mi canción [*Near
Miss*](https://defensemechanism.bandcamp.com/track/near-miss), ajusté un
canal con un *groove* de tres *ticks* y repetí las notas que quería
hacer en arpegio. Es común utilizar las *tables* para crear arpegios,
pero este método utiliza *phrases* para hacer lo mismo. En las
*phrases*, el primer dígito del comando H especifica el número de
espacios a saltar (utilizar 0 hace que se salte a la siguiente
*phrase*). El segundo dígito especifica a qué línea se saltará. Por
ejemplo; H71 salta a la línea 1 siete veces, luego continúa
reproduciendo la *phrase* hasta H5A, donde salta a la línea A cinco
veces antes de terminar la *phrase*.

![Las phrases pueden ser alargadas utilizando comando H](../media/nearmiss.mp4)

¡Espero que esta lección te haya dado algunas nuevas ideas para utilizar
los *grooves* en tus canciones! La próxima vez daremos un vistazo a
algunos ejemplos más sobre cómo utilizar diferentes *grooves* en las
*phrases* y *tables*.

------------------------------------------

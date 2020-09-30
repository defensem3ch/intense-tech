Intense Tech con Defense Mech -- ¡Apreciemos la versión 8! {#apreciemos-la-versión-8}
==========================================================

\- Posted March 26th, 2020 by [Pixel
Guy](https://apixelguy.com "Posts by Pixel Guy")\
*Artículo original de* [*DEFENSE
MECHANISM*](lets-appreciate-version-8/)*. Traducción al español por*
[*Pixel Guy*](https://apixelguy.com)*.*

Hola de nuevo y ¡bienvenidos a otra edición de *Intense Tech*! Este mes
me gustaría hacer énfasis en algunos de los cambios que se han
implementado desde mi artículo sobre la [versión
7](examinando-las-nuevas-funciones/). ¡Profundicemos en el asunto!

------------------------------------------------------------------------

### ¡El manual ha sido actualizado para la versión 8!

Para nosotros, a quienes nos gusta leer el maldito manual, es agradable
el saber que la versión oficial del mismo ha sido actualizada con todos
los cambios de la versión 8. Si tienes preguntas específicas sobre
algunas de las características del programa o la funcionalidad del
mismo; las respuestas pueden ---con frecuencia--- ser encontradas en el
instructivo. El cual puede ser encontrado en [el sitio del LSDj en la
seción de
documentos](https://www.littlesounddj.com/lsd/latest/documentation/).

### Nuevo diseño de las pantallas

El diseño de las pantallas ha sido actualizado para reducir la cantidad
de veces que se tenía que navegar entre las mismas. En lugar del viejo
diseño a tres hileras horizontales, ahora solo hay dos. La hilera
principal, que incluye las pantallas Song, Chain, Phrase, Instrument y
Table, permanece sin cambios. La hilera de arriba ahora incluye, en
orden de izquierda a derecha, las pantallas Project, Groove, Synth y
Wave. Asimismo, al moverte hacia arriba desde la hilera principal, ahora
el LSDJ recuerda en qué pantalla estabas. Esto permite un cambio más
fácil, por poner un ejemplo, entre las pantallas Phrase y Synth. También
existen algunos atajos para más comodidad. Por ejemplo, al moverte hacia
arriba desde Song, siempre llegarás a Project; moverse hacia arriba
desde un comando G siempre te llevará a la pantalla Groove. Aquí hay un
mapa del nuevo diseño de las pantallas extraído del manual del LSDj:

![](image4.png)

### Controles ADSR para instrumentos del tipo Pulse y Noise

Como se mencionó en [la entrevista con Johan
Kotlinski](entrevista-con-el-desarrollador-del-lsdj-johan-kotlinski/),
las configuraciones para la forma de onda en los instrumentos del tipo
Pulse y Noise han sido reemplazadas con controles ADSR para tener un
control más preciso. Estos tienen tres fases, para cada una de las
cuales se asignan dos dígitos: el primero, configurable de de 0 a F,
controla el volumen; el segundo, configurable de 0 a 7, controla la
duración (aplicar 0 hace que se mantenga el volumen establecido por
tiempo indefinido). Un ADSR de 5100 es equivalente a una configuración
de 51 en el viejo sistema. El volumen empieza en 5 y rápidamente baja a
0. Un valor de 246731 comenzará con un volumen de 2, mismo que aumentará
un tanto aceleradamente a 6 para bajar un poco más lento a 3 y
desvanecerse rápidamente hasta llegar a 0. Utilizar los ADSR en
conjunción con comandos como RFx (un *retrigger* con un volumen más
bajo) puede tener un efecto similar al de un comando de tremolo. Los
comandos E y las columnas de volumen en las *tables* permanecen igual y
funcionan de la misma manera en la que lo hacían antes, es decir, pueden
desactivar el volumen de los ADSR cuando  estos son utilizados en
*tables* o *phrases*.

### Mejoras en los comandos Z

En el artículo *[No te duermas sobre la Z (Presentando a
Hyonogram)](no-te-duermas-sobre-la-z-presentando-a-hypnogram/),* hago
notar que Z no funcionaba con los comandos D, G y H. ¡Lo cual ya no es
cierto! Z ahora funciona con todos los comandos salvo H (y, por
supuesto, el mismo comando Z). Esto puede traer algunas consecuencias
rítmicas bastante interesantes dado que ahora tenemos la posibilidad de
asignar valores aleatorios para intercalar ---por ejemplo--- entre un
groove «parejo» y uno con *swing*. ¡Estoy ansioso por probar esto y ver
qué pasa!

### Cambios menores varios

Para terminar este apartado, hay algunos cambios menores que merecen ser
mencionados para evitar confusión. Aquí va una «ronda rápida» de los
mismos:

• Las *tables* ahora pueden alternar entre Play y Step. Play corre a un
*tick* por línea y Step es lo que antes se conocía como Automate.

• La configuración antes conocida como FX/SPEED ahora se llama CMD RATE.

• La pantalla Instrument para los instrumentos WAV ahora muestra el
parámetro Loop Pos en lugar de Repeat y, en lugar de indicar cuántos
cuadros se repetirán, ajusta la posición del punto de bucle. Ajustar el
mismo a 0 repetirá cada cuadro especificado por el valor de Length del
instrumento.

• Utilizar comandos R en el Canal Wave ahora reactivará el sintetizador
desde el primer cuadro de la forma de onda.

• Los instrumentos Wave ahora tienen la configuración Manual por
defecto.

• Los espacios de Synth ahora pueden ser clonados desde la pantalla
Instrument (presiona Select + AB sobre el número de Synth que quieras
clonar).

• Al crear un nuevo instrumento, este se ajusta para ser utilizado en el
canal en el que se creó.

• Ajustar a xF en la columna de volumen de las *tables* saltará a la
celda x.

• Ahora es posible utilizar la preescucha con un teclado PS/2 y
configurar el tiempo de sincronización de entrada (*key delay*) en la
pantalla Project.

• «Clean Song Data» y «Clean Instrument Data» ahora remueven las
*chains*, *instruments* y *tables* clonadas.

### Optimizaciones y retoques para la usabilidad

Esto es lo último, ¡pero NO POR ESO es menos importante! Se han hecho
muchos cambios para mejorar la reproducción de las canciones y la forma
en que reacciona la interfaz. Desde hace tiempo se tiene conocimiento de
que el utilizar comandos V en tres canales al mismo tiempo podría hacer
que el Game Boy se trabe, se congele, deje de responder y/o se pueda
causar un «crasheo». ¡Esto ha cambiado! El viejo ladrillo DMG ahora
puede soportar esto y más a *tempi* tan o más altos que 250 sin que este
se ponga lento o deje de funcionar. Algunos de los comandos al presionar
botones (como presionar dos veces A para crear una nueva *chain*) han
sido optimizados para ser más sensibles; también se hizo más fácil la
navegación entre pantallas.

Una vez más, muchísimas gracias a Johan Kotlinski por su maravilloso
trabajo durante estos meses para hacer de la versión 8 una pieza de
software verdaderamente increíble, ¡y lograr mejoras que parecían casi
imposibles!

Díganme si tienen alguna pregunta sobre la nueva versión o ideas de lo
que les gustaría ver en futuras entregas de *Intense Tech*. ¡Pueden
enviarlas a
[defensemech\@chiptuneswin.com](mailto:defensem3ch@gmail.com)! ¡Hasta la
próxima! Se despide, DEFENSE MECHANISM.

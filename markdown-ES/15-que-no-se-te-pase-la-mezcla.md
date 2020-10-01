Intense tech con Defense Mech -- ¡Que no se te pase la mezcla! {#que-no-se-te-pase-la-mezcla}
==============================================================

\- Posted April 30th, 2020 by [Pixel
Guy](https://apixelguy.com "Posts by Pixel Guy")\
*Artículo original de [DEFENSE MECHANISM](lets-mix-it-up-and-down.html).
Traducción al español por* [*Pixel Guy*](https://apixelguy.com)*.*

Hola de nuevo, ¡y bienvenido a otra edición de *Intense tech*! Este mes
daremos un vistazo a algunos de los diferentes métodos que se pueden
tomar en consideración para mezclar tus canciones en LSDj. Una vez que
hayas leído este artículo tendrás, espero, nuevas maneras de proceder al
trabajar con los volúmenes, la separación estéreo y los rangos de
frecuencia de tus instrumentos para hacerlos brillar en tus canciones.
¡Vamos a ello!

------------------------------------------------------------------------

Desde que comencé a utilizar el LSDj, siempre he tenido problemas para
hacer que las partes encajen de tal manera que se resalten unas a otras;
aunque me he encontrado con algunas formas de ayudar a balancear los
instrumentos y los canales para que cada uno tenga un lugar y
complemente a los demás.

Mientras que podría valer la pena el pensar en la mezcla en términos de
los volúmenes de los instrumentos y los canales; hay diversas formas de
ajustar el sonido que no involucran simplemente subir y bajar el
volumen. También podemos considerar la colocación estéreo del sonido y
el rango de su frecuencia. Si mantenemos en mente esas tres opciones
podemos tener todavía más posibilidades al momento de equilibrar los
componentes en la mezcla, ¡incluso en el Game Boy!

Controla el espacio utilizando paneos
-------------------------------------

Una de las grandes fortalezas del chip de sonido del Game Boy es que
tiene controles para el sonido estéreo. Aún cuando solo puedes controlar
si tiene salida a la derecha, a la izquierda o por ambos canales, este
recurso puede ser utilizado para obtener resultados impresionantes.
Incluso si solo añades un paneo simple en notas de los canales Pulse o
en *hi-hats* en el canal Noise, esto puede crear una sensación de
espacio y atmósfera. En este ejemplo se muestra un arreglo con un *lead*
en el primer canal Pulse, un poco de armonía de apoyoen el segundo, un
*kick* y un bajo en el canal Wave y *hi-hats* y un *snare* en el canal
Noise. Escuchen la diferencia entre la primera parte sin paneo y la
segunda parte con paneo:

Controla la frecuencia utilizando octavas
-----------------------------------------

Esto podría parecer obvio, pero no subestimes las posibilidades que se
obtienen al hacer algo tan simple como transponer una octava. Utilizando
el ejemplo anterior, veamos qué pasa cuando transponemos una octava la
melodía:

Esto puede refrescar un *lead* que parecía anticuado al tiempo que añade
el beneficio de no tener a dos instrumentos peleando en el mismo rango
de frecuencia. Imagina que estás tocando el piano a dos manos; es mucho
más simple colocar tu mano izquierda en la parte de los graves y tu mano
derecha sobre la de los agudos. Si ambas manos se encontraran tratando
de tocar notas en la misma octava, podría llegar a parecer que compiten
por tocar. En lugar de subir el volumen, trata de cambiar la frecuencia
de tal forma que cada canal se encuentre cómodo dentro de su propio
rango. Aunque esto no funcionará siempre, verás cómo ayuda a conseguir
algo de espacio en la mezcla. Sin mencionar que, cuando solo tienes
cuatro bits de rango dinámico, ¡cada bit cuenta!

Controla el volumen utilizando *transients*
-------------------------------------------

Un *[transient](https://en.wikipedia.org/wiki/Transient_(acoustics))* (o
transitorio) es un sonido que contiene una parte corta y brusca con un
sonido alto y explosivo al inicio. Aprendí el siguiente truco de [Pain
Perdu](https://soundcloud.com/pain-perdu): puedes utilizar esa explosión
de ruido para hacer que un *snare* resalte en la mezcla sin reducir la
intensidad de los otros canales. Aquí hay un pequeño ejemplo de un
*snare* que es suave, luego fuerte y después utiliza el *transient*:

Ajustar el volumen del instrumento a un valor relativamente medio o alto
---como 90--- quiere decir que el mismo inicia con el volumen alto,
mismo que es reducido cuando actúa el comando E de la *table*. Esto
también quiere decir que puedes utilizar comandos E en la *phrase*
siguiente al *snare* si quieres aumentar o bajar el volumen del
*transient*. Como puedes oír, esto puede ayudar al *snare* a abrirse
camino a través de la mezcla y crear un mayor impacto sin sobreponerse a
ninguno de los otros elementos, ofreciendo así un sentido a tus
percusiones. Esto también puede ser utilizado con efectividad en otros
instrumentos del tipo Noise o incluso del tipo Pulse.

Controla el volumen del canal Wave utilizando la función Limit
--------------------------------------------------------------

El canal Wav puede proveer mucho del impacto y poder de una canción,
pero, a veces, el control de volumen en el mismo puede resultar un poco
difícil. Usar comandos E ofrece ayuda limitada cuando E3 a un 100 % del
volumen es demasiado fuerte, pero E2 a 50 % del volumen es demasiado
bajo. Utilizar la función Limit en el sintetizador del instrumento del
canal Wave te permite mantener el volumen de dicho sintetizador al
máximo mientras controla el volumen de las formas de onda. Como
recordarás, Limit restringirá el rango dinámico de la forma de onda a un
espacio determinado de volumen, sin importar qué tan alto esté el
volumen del mismo sintetizador o del instrumento. Ajustar Limit a 8
reducirá el volumen del instrumento Wav al 50 %, aún cuando este esté
ajustado a 3; de forma que cualquier valor para Limit entre 9 (cerca del
56 % del volumen) y E (alrededor del 94 % del volumen) te dará acceso a
más variación en el volumen. Ve el ejemplo en el video de abajo:

Adicionalmente, si ajustas los valores de inicio y fin de Limit a
diferentes valores, puedes usar comandos W para controlar la velocidad y
la duración. Esto te permitirá un control aún mayor sobre el volumen,
como se muestra en el siguiente ejemplo.

Controla el volumen del canal Pulse utilizando ADSR
---------------------------------------------------

Por último, hay una característica maravillosa en las versiones más
recientes del LSDJ: los controles
[ADSR](https://es.wikipedia.org/wiki/Envolvente_acústico). Al inicio
puede parecer confuso, pero puedes verlo como encadenar comandos E. Para
cada fase del ADSR el primer dígito especifica el volumen y el segundo
la longitud. Una vez que introduces el segundo dígito, la siguiente fase
se «desbloquea». Esto se puede utilizar de manera similar a un
*transient* para comenzar con un volumen fuerte que se desvanezca hacia
un sonido más bajo. O al revés, un sonido bajo que aumente gradualmente.
La gran ventaja de hacer este tipo de modulaciones de volumen con los
ADSR es que, de manera contraria a los comandos E que aparecen
gradualmente, al aumentar el volumen este solo llega hasta un máximo de
F (o hasta el comando E más próximo); de manera que la siguiente fase de
los ADSR puede ajustarse a un volumen máximo más bajo. Aquí hay un
ejemplo de cómo funcionan los ADSR:

Tanto en las versiones previas de LSDj como en la actual, puede imitarse
el efecto de la función ADSR utilizando la columna de volumen de una
*table*. Aunque esto significaría el uso de una *table* adicional, puede
ser útil cuando los comandos E no te ayudan a conseguir ese nivel extra
de detalle que puedes necesitar al tratar de que una parte se acomode
perfectamente en la mezcla.

¡Eso es todo por esta edición de *Intense tech*! ¿De qué otros temas te
gustaría que hablara? Siéntete libre de enviarme tus comentarios a
<defensem3ch@gmail.com>. Hasta la próxima, se despide, DEFENSE
MECHANISM.

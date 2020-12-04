**Intense tech con Defense Mech -- ¿Así que quieres hablar de cartuchos?**
- Posted May 21st, 2020 by [Pixel
Guy](https://apixelguy.com)
*Artículo original de [DEFENSE
MECHANISM](../en/16-so-you-want-a-cartridge-family.md.html). Traducción al español
por* [*Pixel Guy*](https://apixelguy.com)*.*

¡Bienvenidos de vuelta a *Intense tech*! Aunque
normalmente escribo sobre técnicas utilizables en el LSDj, he recibido
muchas preguntas sobre qué tipo de cartuchos recomiendo. El mercado de
los cartuchos flash para Gameboy tiende a cambiar cada cierta cantidad
de años, así que espero contribuir con información, ya que se ha vuelto
relevante. Hoy cubriré tres tipos de cartuchos flash y cómo puedes
utilizarlos si quieres escribir música utilizando el LSDJ y hardware (mi
método favorito de trabajo). ¡Profundicemos en ello!

------------------------------------------------------------------------

Cartuchos flash que utilizan una memoria SD
-------------------------------------------

En los cartuchos flash que utilizan una memoria SD, los archivos de
guardado son almacenados en una tarjeta microSD, misma que los carga
directamente en el cartucho. Algunos ejemplos de este tipo de cartuchos
que han ganado popularidad en los últimos años son: el Krikzz Everdrive
GB (X3/X5/X7), el BennVenn El Cheapo SD y el EZ Flash Junior.

Mientras que el [Everdrive GB
X5](https://krikzz.com/store/home/47-everdrive-gb.html) es una elección
perfectamente razonable y funcional para un cartucho ya que soporta los
128 Kbps de RAM necesaria para que el LSDj funcione; a menudo son
costosos. Su precio ronda los noventa dólares o incluso más.  Una
alternativa mucho más barata es el EZ Flash Junior, el cual puede ser
adquirido por cerca de [cuarenta dólares en
Amazon](https://www.amazon.com/EZ-Flash-EZ-FlashJr-Original-Everdrive/dp/B08379XZWY)
o en tiendas especializadas en la modificación de consolas Game Boy.

Si planeas utilizar el EZ Flash Junior, necesitarás descargar el
firmware del sitio [ezflash.cn](https://ezflash.cn) y cargar el archivo
llamado «[ezgb.dat](https://penzeys.com)» en la carpeta raíz de la
tarjeta microSD; también puedes copiar el *rom* del LSDj en esa carpeta.
Cuando inicies el cartucho por primera vez, aparecerá un menú que te
dará la opción de seleccionar el *rom* del LSDj. Una vez que cargues el
archivo de guardado en la memoria, el LSDJ se ejecutará (los archivos de
guardado van en la carpeta «SAVER» de la tarjeta microSD).

Cuando hayas terminado de trabajar con el LSDj y apagues el Game Boy, la
batería mantendrá el archivo de guardado en la memoria. De manera que,
la próxima vez que enciendas con ese cartucho, el menú te pedirá que
respaldes tu archivo de guardado en la tarjeta microSD. Si eliges no
hacerlo, todo tu trabajo se perderá. Puedes cargar tantos *rom* y
archivos de guardado como quepan en tu tarjeta microSD. Mientras tus
archivos compartan el mismo nombre con su respectivo *rom* del LSDj,
estos se cargarán con el *rom* de tu elección. Si no se encuentra ningún
archivo de guardado, se creará uno nuevo.

El EZ Flash Jr. también tiene un botón para hacer un reinicio suave ---o
*soft reset*--- que puedes utilizar para regresar al menú; eliminando la
necesidad de encender y apagar el Game Boy. Dicho botón está un poco
escondido dentro del cartucho, presionar la parte media del mismo hacia
adentro lo activará. Esto es una advertencia para los que usan Game Boy
Color o SP: apoyar la consola en una mesa y presionarla podría activar
el botón de reinicio. Dejando eso de lado, este cartucho es una
excelente opción por el precio.

Cartuchos flash USB
-------------------

*¡Actualización importante!* La adorable gente de insideGadgets ha
desarrollado un nuevo cartucho flash USB: el
[LinkLoad32](https://shop.insidegadgets.com/product/gameboy-linknload32-flash-cart-4mb-128kb-fram-with-usb/)!.
Utilizando el [mismo software que para el GBxCart
Flasher](https://gbxcart.com) serás capaz de actualizar y respaldar el
contenido de este cartucho con facilidad. Aunque o lo he utilizado,
puedo confirmar la calidad de los cartuchos de insideGadgets en general
y lo recomendaría si estás interesado en un cartucho exclusivo para
LSDj.

Probablemente los formatos más populares de cartuchos son aquellos con
su propio puerto mini, o micro, USB. El EMS 64M Smart Card y el
Drag'n'Derp son indiscutiblemente los dos cartuchos de este tipo más
conocidos. Lamentablemente, los Drag'n'Derp no se han producido desde
hace tiempo y aún más triste es que la producción de los cartuchos EMS
64M se ha detenido recientemente. Mientras aún haya en existencia,
podrías tener suerte y conseguir uno en
[retromodding.com](http://retromodding.com) o en
[store.kitsch-bent.com](http://store.kitsch-bent.com) (aunque es
probable que los precios se eleven a medida que baje el inventario).

He incluido los cartuchos EMS 64M en este artículo pese a su escasez
porque son bastante famosos y además porque un software bastante útil
llamado [ems-qart](https://github.com/rbino/ems-qart) hace a este
cartucho mucho más fácil de utilizar en los sistemas operativos modernos
(el programa está escrito en Java y acepta Windows, Mac y Linux). Una
vez que hayas descargado el software, sigue las instrucciones en el
«README» para instalar los controladores necesarios para el USB. En este
punto, puedes usar el programa para administrar cualquier cantidad de
archivos de guardado y *rom* (para ambos, lectura y escritura). Si te
sientes cómodo utilizando la Consola de Comandos, hay [herramientas
disponibles](https://github.com/Drenn1/ems-flasher) para su uso en la
misma que pueden hacer el formateo y respaldo de información tan simple
como escribir un comando, dando excelentes resultados para los usuarios
expertos en programación.

Cartuchos flash que requieren de un *flasher*
---------------------------------------------

Cuando los cartuchos flash para Game Boy comenzaron a estar ampliamente
disponibles para el público, frecuentemente eran necesarios *flashers*
especiales y se requería de un manejo meticuloso. Aunque muchas personas
consideran la comodidad de los cartuchos USB o de tarjetas SD superior,
yo creo que es importante no dar por sentada esta categoría. La gente de
[insidegadgets.com](http://insidegadgets.com/) ha estado haciendo
algunos cartuchos y *flashers* de excelente calidad a precios bastante
razonables.

Un cartucho de 1 MB con 128 kb de SRAM es más que suficiente para correr
el LSDj y [solo cuesta veintinueve
dólares](https://shop.insidegadgets.com/product/gameboy-1mb-128kb-sram-flash-cart/).
La tienda programará el *rom* del LSDj de tu elección en el cartucho
antes de enviarlo, lo que quiere decir que puedes comenzar a componer
directamente en tu Game Boy tan pronto como te llegue el cartucho.

Sin embargo, si quisieras ser capaz de actualizar el LSDj, respaldar el
archivo de guardado, cambiar los samples del *rom* del LSDj o copiar un
nuevo archivo dentro en ese cartucho, necesitarías el [GBxCart-mini
flasher](https://shop.insidegadgets.com/product/gbxcart-rw/), además del
cartucho. Juntos tienen un precio de cincuenta dólares, lo que es un
poco más del costo del EZ Flash Jr. (sin incluir el costo de la tarjeta
microSD). Pero, si eres como yo y te gustaría tener dos cartuchos
diferentes (o incluso tres o cuatro), el costo sería menor por cada
cartucho adicional de lo que sería si comprarás el mismo número de EZ
Flash JR. y tarjetas microSD.

El GBxCart-mini flasher es un pequeño PCB con un puerto micro USB y un
zócalo para los cartuchos. Tienes la opción de utilizar una interfaz
basada en la Consola de Comandos o una interfaz gráfica para organizar
tus *rom* y tus archivos de guardado. Todos los programas se pueden
descargar de [insidegadgets.com](http://insidegadgets.com) y el código
fuente es abierto y de descarga gratuita. Yo he modificado el código
para mis propias necesidades, de manera que todo lo que tengo que hacer
es correr un solo comando para respaldar mi archivo de guardado en un
nuevo fichero con una marca de tiempo ---o *timestamp*---. Mi versión
incluso me permite arrastrar un archivo o una *rom* a un comando y
programarlo en el cartucho. Esta no es la opción más conveniente para
todos y, en ocasiones, puede llevar unos pocos ajustes lograr que la
computadora reconozca en cartucho, pero, dejando eso de lado, es tan
fácil como utilizar un cartucho EMS. Debería hacer mención de que el
cartucho de [4MB ROM 128kb
FRAM](https://shop.insidegadgets.com/product/gameboy-4mb-128kb-fram-flash-cart/)
utiliza una memoria que no depende de la batería, lo que quiere decir
que nunca tendrás que preocuparte por perder un archivo de guardado a
causa de una batería muerta en el cartucho. ¡Lo que es genial!

------------------------------------------

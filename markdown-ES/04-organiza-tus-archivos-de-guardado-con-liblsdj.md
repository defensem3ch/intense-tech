Intense Tech con Defense Mech -- ¡Organiza tus archivos de guardado con libLSDj! {#organiza-tus-archivos-de-guardado-con-liblsdj}
================================================================================

\- Posted February 20th, 2019 by [Pixel
Guy](https://apixelguy.com "Posts by Pixel Guy")\
*Artículo Original de [DEFENSE
MECHANISM](manage-your-lsdj-save-files-with-liblsdj.html). Traducción al
Español por [Pixel Guy](https://apixelguy.com).*

¡Hola y bienvenidos una vez más a *Intense Tech* con Defense Mech! En
esta entrega nos ensuciaremos las manos con la Consola de Comandos,
¡solo para que conozcan una herramienta verdaderamente poderosa para
ordenar sus archivos de guardado y canciones del LSDj! Al finalizar esta
lección sabrán cómo organizar una serie de carpetas para cada canción y
crear una lista principal con todas las pistas en sus archivos de
guardado. Si esto suena como algo que necesitas en tu vida, ¡sigue
leyendo!

------------------------------------------------------------------------

Si eres usuario de LSDj, hay probabilidades de que en algún punto hayas
tenido que lidiar con tener que respaldar tus archivos de guardado; ya
sea de un cartucho flash o de un emulador como el BGB. Tal vez estás
listo para presentar tu primer *set* en vivo y quieres acomodar tus
mejores canciones en orden dentro de un nuevo archivo de guardado.
Aunque existe el bien conocido
[LSDManager](https://github.com/jkotlinski/lsdmanager) para organizar
las pistas dentro de los archivos de guardado; su interfaz de usuario
vuelve molesto el importar y exportar cada canción manualmente. Dado que
esta es una tarea que representa tedio puro, es muy probable que olvides
lo que hay en tus archivos de guardado para la próxima vez que necesites
armar uno nuevo.

![](image3.png)\
\
***¿Cómo se supone que sepa qué es lo que está pasando aquí?***\
\

Por suerte, y para salvarnos de la pesada tarea, nuestro amigo
[4ntler](http://soundcloud.com/4ntler) ha estado trabajando duro en
crear algunas herramientas que usan una biblioteca que él mismo creó
llamada [libLSDj](https://github.com/stijnfrishert/liblsdj). La [versión
más reciente](https://github.com/stijnfrishert/liblsdj/releases) incluye
dos herramientas, las cuales analizaremos el día de hoy:
**lsdsng-export** y **lsdsnsg-import**. Antes de comenzar; tal vez
quieras descargar primero el archivo .zip de la versión más reciente
para tu sistema operativo (Mac o Windows)\*.

Para la lección de hoy, he creado una carpeta llamada "LSDJ" y extraje
el archivo lsdgsns\_tools.zip en esa misma carpeta. También creé una
subcarpeta dentro de «LSDj» llamada «saves», dentro de la cual puse los
archivos que quiero organizar; disponible en mi Página de Internet:\
[https://defensemech.com/songs.](https://defensemech.com/songs)
[Descarga una copia para tu propio uso](https://penzeys.com/), ¡o usa
tus propios archivos siguiendo las instrucciones a continuación!

Para comenzar, necesitamos abrir la Consola de Comandos o Ventana
Terminal. En Windows, teniendo abierta una ventana con la carpeta
«LSDj», puedes abrir la Consola al presionar *Shift*+clic derecho y
eligiendo «Abrir ventana de comandos aquí». En Mac puedes abrir la
Terminal desde Spotlight, después das clic y arrastras la carpeta «LSDj»
dentro de la\
Ventana Terminal para ponerla en la carpeta actual.

Para ver las canciones que hay dentro de un archivo de guardado, puedes
ingresar\
`lsdsng-export -p`\
y el archivo de guardado que deseas ver. Esto «imprimirá
(***p****rint*)» la lista de canciones dentro de la Consola de Comandos
o Ventana Terminal. En nuestro caso, ya que lsdsng-export también
reconoce carpetas, podemos ver los contenidos de cada archivo al mismo
tiempo ingresando\
`lsdsng-export -p saves`\
y ¡*violà*! Una lista aparece, por lo que ahora podemos leer al instante
lo que hay en cualquier archivo de guardado.  Cuando veas «WM» bajo el
nombre del archivo de guardado; eso indica que la canción está
precargada dentro de la memoria de trabajo de ese archivo. Esto puede
ser convertido en una «lista principal de archivos» para las canciones
que haya en cada archivo de guardado y exportado como un archivo de
texto. Esto es fácil de hacer en la Consola de Comandos, solo hay que
ingresar\
`lsdsng-export -p saves > songlist.txt`\
lo que creará un archivo de texto llamado «songlists txt», el cual
incluirá todos los datos de salida de cada archivo en la carpeta «saves»
y las canciones que estén ahí. Esto puede ser muy útil, aunque está
limitado a solo una carpeta. Si tienes otra carpeta que contenga
archivos de guardado dentro de la carpeta «saves», esta será ignorada.

Para ver un archivo de guardado, como SUNBURST.sav, tenemos que
ingresar\
`lsdsng-export -p saves/SUNBURST.sav`.\
(Usamos la diagonal para indicarle a lsdsng-export que busque a
SUNBURST.sav dentro de la carpeta «*saves*».) Los datos de salida se
verán así:

``` {.wp-block-code}
SUNBURST.sav
#   Name     Ver    Fmt
WM  ENAMORED *          7
0   ENAMORED 6D         7
1   ILLUMIN8 78         7
2   NEARMISS 7D         7
3   FRESH    92         7
4   BLONGING 52         7
```

Sin el argumento --**p**, introducir\
`lsdsng-export saves/SUNBURST.sav`\
extraerá todos los archivos lsdsng dentro de nuestra carpeta «LSDj». En
Windows también puedes arrastrar un archivo de guardado a lsdsng-export,
¡sin necesidad de abrir la Consola de Comandos en lo absoluto! Incluso
puedes extraer TODOS los archivos lsdsng en la carpeta «*saves*» al
ingresar\
`lsdsng-export saves`\
Si quieres organizar cada canción en su propia carpeta, también es
posible hacer esto especificándolo con el argumento --**f**:\
`lsdsng-export -f saves`\
Esto pondrá cada archivo lsdsng dentro de una carpeta con su nombre.
Esto puede ser de gran ayuda cuando se extraen múltiples archivos de
guardado, en caso de que tengas varios respaldos de tus canciones. ¡Cada
carpeta contendrá cada versión de esa canción extraída de tu archivo de
guardado!

Digamos que quiero extraer los archivos lsdsng de SUNBURST.sav en una
nueva carpeta llamada «songs». Le podemos indicar a lsdsng-export que
haga esto ingresando\
`lsdsng-export saves/SUNBURST.sav -o Sunburst`\
Esto hará que los archivos de salida (***o****utput*) de cada fichero
lsdsng se extraiga en una carpeta llamada «Sunburst». Si no hay una
carpeta llamada así, ¡será creada!

Si solo queremos extraer los archivos lsdsng de NEARMISS, podríamos
especificar el nombre o por número de índice (esto se refiere al número
que ocupa la canción en la lista debajo de un símbolo «\#»).\
Para extraerla por nombre se puede ingresar\
`lsdsng-export -n NEARMISS saves/SUNBURST.sav`\
Para extraerla por número de índice se puede ingresar\
`lsdsng-export -i 0 saves/SUNBURST.sav`\
Estas opciones pueden ser utilizadas más de una vez para extraer
canciones múltiples de la siguiente manera:\
`lsdsng-export -n NEARMISS -n ILLUMIN8 saves/SUNBURST.sav`\
y también pueden ser combinadas:\
`lsdsng-export -n NEARMISS -i 1 saves/SUNBURST.sav` (Es importante
recordar que la primera canción en el índice es 0, no 1.)\
Esto se puede combinar con la carpeta de salida:\
`lsdsng-export -n NEARMISS -i 1 saves/SUNBURST.sav -o songs`

También es posible extraer el archivo lsdsng para la canción que está
precargada en la memoria de trabajo. Esto te puede ser útil si se te
olvida guardar tu canción en LSDj; todos los cambios que hagas aún serán
cargados y se mantendrán intactos.\
Puedes hacer esto ingresando\
`lsdsng-export -w saves/SUNBURST.sav`

Hasta aquí todo bien, ¿cierto? ¡Muy bien! Una vez que hemos extraído
nuestras canciones, es hora de compilarlas dentro de un archivo de
guardado usando lsdsng-import. Una vez más, hay varias maneras de hacer
esto.

Supongamos que tengo uno o más archivos lsdsng que quiero convertir a un
solo archivo de guardado. En Windows, y sin necesidad de abrir la
Consola de Comandos, puedes arrastrar uno o todos los archivos lsdsng
dentro de lsdsng-import; lo que automáticamente creará un archivo
llamado «out*.*sav».

Para hacer esto en la Consola de Comandos, ingresa:\
`lsdsng-import`\
seguido de cualquier número de archivos lsdsng que serán combinados
dentro de «out*.*sav» de manera predeterminada. Puedes especificar el
nombre del archivo de guardado final usando el argumento -o:\
`lsdsng-import -o mysave.sav song1.lsdsng song2.lsdsng` (y así
sucesivamente).\
Si después quieres añadir otra canción a «mysave*.*sav», puedes usar el
argumento --s:\
`lsdsng-import song3.lsdsng -s mysave.sav`\
which will add song3.lsdsng\
lo que añadirá a «*song3.lsdsng*» a «mysave*.*sav».

Para combinar todas las canciones en la carpeta «songs» en un solo
archivo de guardado, puedes ingresar\
`lsdsng-import songs`\
lo que creará un archivo llamado «songs*.*sav». Este método colocará los
archivos por nombre, por lo que, antes de hacer esto,  tal vez quieras
renombrar los archivos a fin de que aparezcan correctamente cuando sean
ordenados por nombre.

Si en algún momento te olvidas de cómo operar lsdsng-export o
lsdsng-import, al ingresar lsdsng-export o lsdsng-import sin ningún
argumento; se mostrará un texto de ayuda que describe las opciones.

\*Nota para los usuarios de Linux: No es por excluirlos; es solo que es
muy posible que el compilar directo de la fuente y utilizar la Consola
de Comandos sea familiar para ustedes, ¡por lo que es probable que no
necesiten este tutorial!

Espero que este artículo les haya sido útil, y, de nuevo, ¡gracias a
4ntler por su maravilloso trabajo en estas herramientas y en libLSDj!
Siéntanse libres de contactarme a [DEFENSE
MECHANISM](mailto:defensem3ch@gmail.com).

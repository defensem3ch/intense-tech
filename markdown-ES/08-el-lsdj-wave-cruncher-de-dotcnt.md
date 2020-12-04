**Intense Tech con Defense Mech -- ¡El LSDj Wave Cruncher de DOTCNT!**
- Posted June 25th, 2019 by [Pixel
Guy](https://apixelguy.com)
*Artículo Original de [DEFENSE MECHANISM](../en/08-dotcnts-lsdj-wave-cruncher.md.html).
Traducción al Español por [Pixel Guy](https://apixelguy.com).*

¡Bienvenidos de vuelta a *Intense tech*! En esta
lección cubriremos el cómo utilizar el *[LSDj Wave
Cruncher](https://github.com/iLambda/lsdj-wave-cruncher)*, de
[DOTCNT](https://www.facebook.com/dotcnt/), para tomar muestras y
generar nuestros propios instrumentos personalizados en el sintetizador
del canal Wave, ¡mismos que podremos parchar en nuestras canciones y
archivos de guardado de LSDj!

------------------------------------------------------------------------

Tal vez recuerdes una lección anterior en la que hablé sobre [la
herramienta para
importar](biblioteca-de-instrumentos-lsdj-wave-cruncher.html)
*[wavetables](biblioteca-de-instrumentos-lsdj-wave-cruncher.html)* que
creó [4ntler](https://github.com/stijnfrishert/liblsdj/releases); la
cual nos permite parchar *wavetables* directamente en un archivo de
guardado de LSDj o en un archivo lsdsng, así como aquellos que provengan
de la [Biblioteca de instrumentos del sintetizador del canal Wave de
LSDj](https://github.com/psgcabal/lsdjsynths). Pero ¿cómo se genera una
*wavetable* partiendo de una muestra o *sample*? Hoy responderemos esa
pregunta al tiempo que hacemos un análisis profundo de la increíble obra
de [DOTCNT](https://www.facebook.com/dotcnt/): ¡[LSDj wave
cruncher](https://github.com/iLambda/lsdj-wave-cruncher)!

      <iframe
      style="height: 166px; width: 100%;"
        scrolling="no"
        allow="autoplay"
        src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/337969906&amp;color=%23ff5500&amp;auto_play=false&amp;hide_related=false&amp;show_comments=true&amp;show_user=true&amp;show_reposts=false&amp;show_teaser=true"
        width="100%"
        height="166"
        frameborder="no"
      ></iframe>

Tuve la fortuna de conocer a Ada, también conocida como
[DOTCNT](https://soundcloud.com/dotcnt), en Francia el año pasado; e
inmediatamente la elogié por el asombroso trabajo que ha hecho al
proveer a la comunidad del LSDj con esta herramienta. En esencia, el
Wave Cruncher es una forma de automatizar el *downsampling* (o
«reducción de resolución de muestreo») de una sola muestra para que
funcione en el sintetizador del canal Wave del LSDj, es decir:
convertirlo en un método de muestreo para las *wavetables*. Esto nos
permite jugar con la notas, hacer curvaturas de tono, arpegiar los
acordes, etc., en formas que no podrías lograr de tocar las muestras de
los kits en el ROM de LSDj. En esta lección haremos uso de un montón del
conocimiento ganado en los [artículos previos de esta
columna](https://defensemech.com/intense-tech/), ¡así que siéntanse libres de volver a
leerlos si lo necesitan!

La [herramienta original](https://github.com/iLambda/lsdj-wave-cruncher)
requiere que instalen Node, Python 2 y varias bibliotecas de archivos
para cada uno; pero he compilado [archivos
binarios](https://github.com/urbster1/lsdj-wave-cruncher/releases) que
deberían de correr en la Consola de Comandos o Ventana Terminal de
máquinas con Mac, Windows o Linux sin requerir de ninguna configuración.
(Si necesitas de un recordatorio sobre la Consola de Comandos/Ventana
Terminal, puedes revisar [el artículo que escribí sobre
libLSDj](04-organiza-tus-archivos-de-guardado-con-liblsdj.md.html).) Hay
algunos otros requerimientos importantes que necesitarás cumplir antes
de comenzar a «aplastar» algunas ondas. Primero necesitarás una muestra
del instrumento. Lo ideal sería un archivo WAV que contenga solo una
nota. También es importante que dicha nota sea tonal, es decir, necesita
tener un tono constante. Piensa en un instrumento que toque una nota y
tendrás una idea de la clase de sonidos que trabajarían bien en el Wave
Cruncher. Los sonidos con muchos
[armónicos](01-analisis-del-sintetizador-del-canal-wave-en-lsdj-parte-uno.md.html)
--como las campanas, pianos eléctricos, tambores metálicos de Trinidad y
Tobago, etc.-- funcionan particularmente bien. Los sonidos que no
funcionan adecuadamente son aquellos especialmente «sucios» o no
tonales, como las cajas, los silbatos de tren, los *vibraslap* o
muestras de canciones de los [Red Hot Chili
Peppers](https://penzeys.com).

Para este ejemplo utilicé una muestra de un piano eléctrico

![Muestra de un piano eléctrico (FM)](../media/epiano.mp3)

Lo siguiente que necesitarás es el [archivo binario del Wave
Cruncher](https://github.com/urbster1/lsdj-wave-cruncher/releases).
Descarga la versión apropiada para tu plataforma y colócala en la misma
carpeta que las muestras que busques «aplastar». Una vez hecho esto;
[abre la Consola de Comandos/Terminal en dicha
carpeta](organiza-tus-archivos-de-guardado-con-liblsdj.html).

Cuando trabajes con el Wave Cruncher, le proveerás determinados
parámetros o argumentos de la siguiente manera:

`crunch [SAMPLE.WAV] [NOTE|FREQUENCY|auto] --flag`

«Crunch» es como se llama al archivo binario que funcione en tu sistema;
en Windows sería: «crunch-win.exe», seguido por el nombre del archivo de
la muestra del instrumento que queramos usar --en este caso
«epiano.wav»--. Siguiendo al *sample* va, ya sea la nota (en notación
inglesa): «A4»; la frecuencia en Hertz (Hz): «440» o simplemente la
palabra «auto», la cual tratará de detectar de forma automática la
frecuencia de la muestra. La detección automática es muy conveniente
cuando funciona, pero, en ocasiones, esta falla al detectar el tono de
formas de onda sumamente complejas. Sin mencionar que le toma cerca de
un minuto el funcionar (o fallar), lo que puede retrasar tu proyecto.

A este punto puedes sentirte libre de correr el Cruncher y, si todo sale
bien, podrías ser recompensado con un archivo de salida .snt; el cual
puede ser [parchado en un archivo de
guardado](biblioteca-de-instrumentos-lsdj-wave-cruncher.html) usando el
[*wavetable patcher* incluido en el
libLSDj](https://github.com/stijnfrishert/liblsdj/releases).

Demos un vistazo al archivo de salida cuando corremos

`crunch-win.exe epiano.wav auto`

```none
$ crunch-win.exe epiano.wav auto
Crunching data...
Auto-detecting frequency...
Frequency detected: 136.47859664570356 Hz
Saving data as epiano.snt... Done!
Successfully output epiano.snt!
```

Ahora podemos parchar «epiano.snt» en nuestro archivo de guardado de
LSDj. Sin embargo, aún podemos añadir algunas banderas (o *flags*) para
hacer ajustes minuciosos en las *wavetables*.

La primera bandera opcional afectará los ciclos de onda que el Cruncher
ponga en la *wavetable* resultante. Este toma los primeros dieciséis
ciclos de manera predeterminada. Aunque puede que esto no refleje en su
totalidad el sonido de la muestra, especialmente si esta es larga. La
primera bandera, «`--linear`», toma un muestreo lineal de los ciclos de
la onda completa; de principio a fin. Podríamos decir que la muestra
entera es partida equitativamente en dieciséis fragmentos iguales y se
toma un ciclo de onda de cada uno.

La segunda bandera, «`--exp`», imita una especie de muestreo
exponencial. En otras palabras: toma más ciclos de onda del inicio de la
muestra y menos del final. Esto puede resultar útil si tratas de dar
énfasis al ataque de la muestra y no tanto al *decay* o al *release*.
Muy probablemente valga la pena el que juegues con estas opciones, ya
que estas pueden cambiar drásticamente el sonido resultante.

La siguiente bandera opcional, «`--normalize`», afecta el volumen de la
muestra. Al añadir esta bandera se maximizará el volumen de la misma
antes de que sea procesada por el programa. Esto es usualmente
recomendado para muestras que no han sido previamente amplificadas, ya
que muestras normalizadas usualmente resultan en sonidos sintetizados de
mejor calidad. Tus *samples* deben de ser normalizados con anticipación,
de esta forma es seguro el omitir esta bandera.

La tercera bandera opcional, «`--channel=0`» o «`--channel=1`», es para
archivos estéreo. Dado que el sintetizador del canal Wave del LSDj es
monofónico; el Wave Cruncher tiene que elegir que canal procesar, ya sea
el izquierdo o el derecho. La configuración por defecto es «channel 0»
(izquierda), pero, si lo prefieres, puedes ajustar la bandera a «channel
1» para procesar el canal derecho en su lugar.

La cuarta bandera opcional es «`--output=filename`», la cual te permite
especificar la salida del archivo .snt. De manera predeterminada, el
Wave Cruncher usa el nombre del archivo de muestra; pero esto puede
resultar confuso si estás tratando de probar los resultados de utilizar
diferentes parámetros sobre el mismo *sample*. Al especificar, por
ejemplo, «`--output=bell-exp.snt`», puedes saber que el archivo .snt
resultante usó la bandera «--exp» en lugar de la predeterminada o la de
muestreo lineal. Para acortar: es una opción diseñada para ayudar a
mantener las cosas organizadas.

Por último, hay una bandera, «`--analyze`», que está específicamente
diseñada para analizar la frecuencia. Esta no dará un archivo .snt como
producto. Puedes verla como el «modo de prueba». Puedes correr el Wave
Cruncher con «-analyze» para asegurarte de que la detección automática
del tono no falle. Esto puede ser útil al procesar lotes de muestras,
solo para asegurar que el proceso correrá suavemente y sin cortes, si la
detección automática falla, el sample no será procesado. La detección
automática añade de 30 a 60 segundos extra al procesamiento del archivo.
Dado que la bandera «`--analyze`» da salida a la frecuencia que detecta,
dicha frecuencia puede ser ofrecida en procesos posteriores para
acelerar el proceso.

Corramos el programa un par de veces más con nuestra muestra de piano
eléctrico para probar los resultados. Ya que toma alrededor de 45
segundos el detectar la frecuencia, especificaré el valor en lugar de
utilizar «auto», solo para apresurar las cosas. Veamos los sonidos
resultantes al añadir diferentes banderas.

```none
$ crunch-win.exe epiano.wav 136.47859664570356 --normalize --linear --output=epiano-lin.snt
Crunching data...
Samples: 311847
Sample rate: 44100
Cycles: 965
Linear interpolation
Taking frame every 60 cycles
Saving data as epiano-lin.snt...
Done!
Successfully output epiano-lin.snt!
```

```none
$ crunch-win.exe epiano.wav 136.47859664570356 --normalize --exp --output=epiano-exp.snt
Crunching data...
Samples: 311847
Sample rate: 44100
Cycles: 965
Exponential interpolation
Saving data as epiano-exp.snt...
Done!
Successfully output epiano-exp.snt!
```

Una vez que hayas corrido el Wave Cruncher; puedes seguir [las
instrucciones aquí](05-biblioteca-de-instrumentos-lsdj-wave-cruncher.md.html)
indicadas para parchar tus archivos .snt en tus archivos de guardado o
lsdsng. Recuerda que tienes que ajustar los parámetros de Play, Length y
Speed en la pantalla Instrument del canal Wave de manera apropiada.
Dependiendo del *tempo*, puedes intentar con Play: Once; Length: 3;
Speed: 3 y hacer ajustes a partir de ahí. Si el resultado suena bien,
¡por favor considera el contribuir con ellos a la [Biblioteca de
instrumentos sintetizados para
LSDj](https://github.com/psgcabal/lsdjsynths)! Abajo veremos los
resultados de nuestros instrumentos. He parchado cada instrumento en
Instrument 1, 2 y 3; además de los espacios Synth 1, 2 y 3
respectivamente. Las Chains y Phrases 01, 02 y 03 reproducirán los
sonidos correspondientes.


![Cada instrumento sintetizado requerirá de diferentes parámetros.](../media/epiano.mp4)

¡Espero que este artículo te dé una visión de lo que es el Wave Cruncher
y te motive a tratar de procesar tus propios *samples*!

Háganse un favor y revisen más del material de [DOTCNT
aquí](http://facebook.com/dotcnt/) y
[aquí](https://soundcloud.com/dotcnt), ¡por favor!

------------------------------------------

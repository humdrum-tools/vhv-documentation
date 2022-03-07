---
title: MusicXML import
lang: en es
ref: interface-musicxml
author: Craig Stuart Sapp
translator: Helena Martínez Olivas, Olga Francés Zoroa
creation_date: 6 Mar 2017
translation_date: 6 Jun 2021
verovio: "true"
last_updated: 6 Mar 2017
tags: [all, getting_started]
keywords: interface musicxml
summary: "MusicXML files can be dragged/dropped onto the VHV page to automatically convert them into Humdrum data."
sidebar: main_sidebar
permalink: /interface/musicxml/index-ES.html
---

## Arrastrar y soltar archivos MusicXML


La interfaz de VHV puede cargar archivos MusicXML arrastrándolos y soltándolos desde el escritorio a la página de VHV.  La siguiente imagen muestra la exportación de datos MusicXML desde[ MuseScore](http://www.musescore.org) al escritorio, y luego arrastrando el archivo al navegador para cargarlo en VHV.

Hay dos maneras de cargar un archivo MusicXML: arrastrando y soltando habitualmente cargará los datos MusicXML directamente al editor de texto, mientras que manteniendo pulsada la tecla <span class="keypress">shift</span> al arrastrar y soltar se convertirán los datos MusicXML en datos Humdrum, que se mostrarán en el editor de texto:


{% include image.html
file="export-import-musicxml.gif"
alt="MusicXML import example"
max-width="100%"
caption="Archivo MusicXML exportado desde MuseScore, luego importado con shift+arrastrar/soltar un archivo en VHV."
%}

Intenta descargar el [mismo archivo MusicXML](bwv1011-sarabande.xml) y cargarlo en VHV de forma similar (normalmente se guarda haciendo clic con el botón derecho del ratón en el enlace y luego eligiendo *guardar enlace como*).

{% include warning.html
content="Los archivos MXL (MusicXML comprimidos) no pueden cargarse directamente en VHV.   Primero descomprime el archivo MXL y luego arrastre y suelte el archivo MusicXML resultante (con la extensión `.xml`) en VHV, o cargue los archivos MXL en un editor de notación que entienda el formato MXL y vuelva a guardar como MusicXML sin comprimir."
%}


## Copiar/Pegar datos MusicXML


Los datos MusicXML también pueden ser copiados/pegados en el editor de texto VHV.   En este caso VHV se comporta como un editor de MusicXML, ya que los datos no se convierten al formato Humdrum dentro del editor de texto.


El [comando de congelación](/commands/alt-f) (<span class="keypress">alt-f</span>) es útil para pausar la representación de la notación dinámica mientras se editan los datos MusicXML.  Los datos MusicXML cargados de esta manera se convierten a Humdrum en segundo plano, pero la carga de los datos de Humdrum en el editor de texto aún no está implementada.   Sin embargo, puedes [convertir a datos MEI](/commands/alt-m) con la tecla <span class="keypress">alt-m</span> y mostrarlos en el editor de texto.


{% include warning.html
content="Los comandos de edición de notación gráfica no se pueden utilizar cuando los datos MusicXML se cargan en el editor de texto, ya que estos comandos operan solo con datos Humdrum."
%}

## Conversión de datos MusicXML en Humdrum


Si los datos MusicXML se muestran en el editor de texto, puedes utilizar la opción del menú Edición "Convertir a Humdrum" para convertir los datos MusicXML en datos Humdrum, que sustituyen a los datos MusicXML en el editor de texto.


## Incrustación de interpretaciones en tándem


El convertidor de MusicXML a Humdrum dentro de [VHV](https://verovio.humdrum.org) convertirá las expresiones de texto que comienzan con un asterisco (`*`) en interpretaciones en tándem en los datos de Humdrum.  Adjunta la expresión de texto a la nota que debe seguir inmediatamente después de la interpretación en tándem.  Aquí hay un ejemplo de incrustación de una interpretación `*Xtuplet` para desactivar la visualización de los números tuplet, y posteriormente `*tuplet` para volver a activarlos:


{% include image.html
file="musescore-tuplet.png"
alt="Adding tuplet interpretations in MuseScore"
max-width="100%"
caption="Añadir expresiones de texto para controlar el estilo de visualización de los números de tupla en MuseScore."
%}

Este <a target='_blank' href='tuplet.musicxml'>archivo MusicXML</a> que ha sido arrastrado y soltado en [VHV](https://verovio.humdrum.org) producirá los siguientes datos de Humdrum que conservan las interpretaciones tándem incrustadas que controlan el estilo de los números de tupla.

{% include verovio.html
source="musescore-tuplet"
scale="45"
pageWidth="1200"
humdrum-min-height="500px"
tabsize="8"
%}
<script type="application/json" id="musescore-tuplet">

**kern

*clefG2

*k[]

*M4/4

=1

12ccL

12dd

12ccJ

12ddL

12cc

12ddJ

*Xtuplet

12ddL

12ee

12ddJ

12ccL

12dd

12ccJ

=2

12ddL

12cc

12ddJ

*tuplet

12ccL

12dd

12ccJ

12ddL

12cc

12ddJ

12ccL

12ee

12ddJ

==

*-

</script>

### Ocultar el texto de marcado de Humdrum


Si no quieres mostrar el texto de marcado de Humdrum en la salida de PDF de un editor de música, puedes hacer que el texto sea invisible en la mayoría de los editores.  Este es un ejemplo de cómo hacer que el texto sea invisible en MuseScore: haz clic en el texto y abre el panel de inspección y luego desmarca la casilla de _Visibilidad_:

{% include image.html
file="musescore-visibility.png"
alt="Making text invisible inMuseScore"
max-width="100%"
caption="Hacer invisibles las expresiones de texto en MuseScore."
%}

Aquí está la salida PDF resultante de MuseScore, donde el marcado Humdrum no es visible:

{% include image.html
file="musescore-pdf.png"
alt="Making text invisible inMuseScore"
max-width="100%"
caption="Hacer invisibles las expresiones de texto en MuseScore."
%}

En MuseScore, también puedes ocultar el texto invisible en el editor deseleccionando la opción de menú Ver&rarr;Mostrar Invisible.


### Otro ejemplo



Aquí hay otro ejemplo que incorpora marcadores de coloración de notas en MuseScore:


{% include image.html
file="musescore-color.png"
alt="Adding tuplet interpretations in MuseScore for coloring notes"
max-width="100%"
caption="Añadiendo expresiones de texto para controlar los colores de las notas."
%}

Si arrastras y sueltas <a target="_blank" href="color.musicxml">estos datos MusicXML</a>, la conversión a Humdrum se verá y se mostrará así en [VHV](https://verovio.humdrum.org):

{% include verovio.html
source="musescore-color"
scale="45"
pageWidth="1200"
humdrum-min-height="500px"
tabsize="8"
%}
<script type="application/json" id="musescore-color">

**kern

*clefG2

*k[]

*M4/4

=1

4cc

4ee

*color:hotpink

4dd

4ff

=2

2gg

2aa

=3

*color:dodgerblue

2gg

2ff

=4

4gg

4ff

*color:black

4cc

4dd

==

*-

</script>


### Añadir interpretaciones después de las notas


Cuando las interpretaciones en tándem se adjuntan a las notas o silencios como expresiones de texto, se insertarán antes de la nota en los datos de Humdrum convertidos.  Para colocar interpretaciones después de una nota, utiliza dos asteriscos (`**`) en lugar de uno.  El segundo asterisco se eliminará automáticamente (ya que está reservado para interpretaciones exclusivas).
Este método de inserción después de las notas es necesario cuando se añaden interpretaciones al final de un compás, ya que los editores de música normalmente no pueden adjuntar expresiones de texto a las líneas de compás.

Aquí hay un ejemplo de codificación de un corchete de ligadura en MuseScore.  La nota final de la ligadura se produce al final del compás, y como la expresión de texto `*Xlig` no puede adjuntarse a la línea de compás, se codifica como `**Xlig` en la última nota del grupo de ligaduras:

{% include image.html
file="musescore-ligature.png"
alt="Adding ligature interpretations in MuseScore"
max-width="100%"
caption="Añadiendo expresiones de texto en MuseScore para mostrar un corchete de ligadura."
%}


Si arrastras y sueltas <a target="_blank" href="ligature.musicxml">estos datos MusicXML</a>, la conversión a Humdrum se verá y se mostrará así en VHV:

{% include verovio.html
source="musescore-ligature"
scale="45"
pageWidth="1200"
humdrum-min-height="375px"
tabsize="8"
%}
<script type="application/json" id="musescore-ligature">

**kern

*clefC3

*k[]

*M2/1

=1

1d

1B

=2

*lig

0c

=3

0d

*Xlig

=4

2e

2d

1B

=5

0c

==

*-

</script>





## Incrustar comentarios locales



Igualmente, los comentarios locales (que comienzan con `!`) pueden ser incrustados dentro de los datos MusicXML para ser convertidos en datos de Humdrum cuando se arrastra y suelta el archivo en [VHV](https://verovio.humdrum.org).

{% include image.html
file="musescore-comment.png"
alt="Adding local comments in MuseScore"
max-width="100%"
caption="Añadir comentarios locales incrustados en MuseScore."
%}

Si arrastras y sueltas <a target="_blank" href="comment.musicxml">estos datos MusicXML</a>, la conversión a Humdrum se verá y se mostrará así en [VHV](https://verovio.humdrum.org):

{% include verovio.html
source="musescore-comment"
scale="45"
pageWidth="1200"
humdrum-min-height="500px"
tabsize="8"
%}
<script type="application/json" id="musescore-comment">

**kern

*clefG2

*k[]

*M4/4

=1

4cc

!LO:TX:a:t=text

4ee

4dd

4ff

=2

!LO:TX:b:t=text2:color=red

2gg

2aa

=3

!comment

2gg

2ff

=4

!LO:N:vis=1

4gg

4ff

4cc

4dd

==

*-

</script>

Ten en cuenta que cualquier expresión de texto MusicXML que empiece por `!` se convertirá en comentarios locales en los datos de Humdrum.  Los comentarios también pueden ser parámetros de diseño, como en el ejemplo anterior, donde `!LO:N:vis=1` significa que la negra tiene una duración visual de nota entera.  El `!comment` es un comentario local normal que no se imprimirá en la partitura.  El texto que se mostrará en la partitura puede ser una expresión de texto plano que no empiece por `*` o `!`, y si no, el texto puede colocarse en un comando de disposición `TX` para añadir parámetros específicos a la representación del texto en VHV.

## Insertar registros de referencia



Los registros de referencia pueden insertarse en un comentario de texto comenzando por tres `!!!` en cualquier parte de la partitura.  Para insertar estas grabaciones en la parte superior de un archivo Humdrum, añádelas al área del título en un editor de partituras:


{% include image.html
file="musescore-reference.png"
alt="Adding reference records in MuseScore"
max-width="100%"
caption="Añadir registros de referencia insertados en MuseScore."
%}


Observa que, en este ejemplo insertando grabaciones de referencia, el texto se muestra invisible en el editor MuseScore si desmarcas la casilla en el panel inspector de la derecha.  Esto nos permite insertar la marca de Humdrum (incluyendo la interpretación tándem y los comentarios locales) en el editor de la partitura, pero evita que se vean en el PDF impreso de las anotaciones del MuseScore.

Si arrastras y sueltas <a target="_blank" href="reference.musicxml">estos datos MusicXML</a>, la conversión a Humdrum se verá y se mostrará así en VHV:

{% include verovio.html
source="musescore-reference"
scale="45"
pageWidth="1200"
humdrum-min-height="525px"
humdrum-min-width="325px"
tabsize="8"
%}
<script type="application/json" id="musescore-reference">

!!!COM: Composer's name

!!!CDT: Composer's dates

!!!CNT: Composer's nationality

!!!OTL: Composition title

!!!OMV: Movement 1

!!!ODT: Composition date

!!!LYR: Lyricist's name

!!!header-left: @{LYR}\n

!!!header-center: @{OTL}\n&lt;i&gt;@{OMV}&lt;/i&gt;

!!!header-right: @{COM}\n@{CDT}

**kern

*clefG2

*k[]

*M4/4

=1

1g

=2

1a

=3

2b

4b

4g

=4

4g

4b

2b

==

*-

</script>

Si la partitura en formato MusicXML contiene el título y el nombre del compositor en la codificación estándar para un archivo MusicXML, se van a convertir automáticamente en registros `!!!COM:` y `!!!OTL:`, pero si al documento maestro se le añade las entradas de `!!!COM:`
y `!!!OTL:` explícitas, se anularán el nombre del compositor y el título del trabajo deducidos.

Observa también en este ejemplo una demostración del sistema de plantillas de cabecera:


```
!!!header-left: @{LYR}\n
!!!header-center: @{OTL}\n<i>@{OMV}</i>
!!!header-right: @{COM}\n@{CDT}
```

Esto permite mostrar varios registros de referencia en la parte superior de la partitura, a la izquierda, a la derecha y en el centro de la cabecera.  La secuencia de caracteres `\n` representa un salto de línea.  También existe un sistema de plantillas de pie de página, que resulta útil para imprimir en PDF desde VHV (con el atajo de teclado  <span class="keypress">alt+shft+T</span>).


### Colocación de registros de referencia


Un sistema adicional para incrustar registros de referencia en la cabecera de MusicXML permite colocar los registros al principio o al final del archivo.  Sustituye `!!!` por `@` para indicar que un registro de referencia debe colocarse al principio del archivo, o sustituye `!!!` por `@@` para que el registro de referencia se añada al final del archivo:


{% include image.html
file="musescore-reference2.png"
alt="Adding reference records in MuseScore"
max-width="100%"
caption="Sistema alternativo para incrustar registros de referencia en MuseScore con controles arriba/abajo."
%}

Si arrastras y sueltas <a target="_blank" href="reference2.musicxml">estos datos MusicXML</a>, la conversión a Humdrum se verá y se mostrará así en VHV:

{% include verovio.html
source="musescore-reference2"
scale="45"
pageWidth="1200"
humdrum-min-height="525px"
humdrum-min-width="325px"
tabsize="8"
%}
<script type="application/json" id="musescore-reference2">

!!!COM: Composer's name

!!!OTL: Composition title

!!!OMV: Movement 1

**kern

*clefG2

*k[]

*M4/4

=1

1g

=2

1a

=3

2b

4b

4g

=4

4g

4b

2b

==

*-

!!!CDT: Composer's dates

!!!CNT: Composer's nationality

!!!ODT: Composition date

!!!LYR: Lyricist's name

!!!header-left: @{LYR}\n

!!!header-center: @{OTL}\n&lt;i&gt;@{OMV}&lt;/i&gt;

!!!header-right: @{COM}\n@{CDT}

</script>



## Conversión por lotes de MusicXML a Humdrum


Si quieres convertir muchos archivos MusicXML a Humdrum a la vez, puedes utilizar la herramienta de línea de comandos _musicxml2hum_ de <a target="_blank"
href="https://humlib.humdrum.org">humlib</a>, que es como el conversor MusicXML a Humdrum de [VHV](https://verovio.humdrum.org).  Para convertir múltiples archivos MusicXML en un directorio a Humdrum usando el shell bash:

```bash
for i in *.xml
do
	echo Converting $i
	musicxml2hum $i > $(basename $i .xml).krn
done
```


{% include warning.html
content="Hay una herramienta en los extras de Humdrum llamada _xml2hum_, pero _musicxml2hum_ de humlib es un conversor de MusicXML a Humdrum más avanzado y más reciente."
%}



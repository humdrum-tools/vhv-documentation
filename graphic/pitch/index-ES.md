---
title: Altura, tono
lang: en es
page_language: es
translator: David Rizo
translation_date: 9 Aug 2021
translation_update:
ref: graphic-pitch
tags: [all, graphic_editing, RDF]
sidebar: main_sidebar
keywords: graphic editing pitch
datatable: "true"
vim: ts=3 ft=javascript
summary: "Alterar gráficamente los tonos de las notas y las alteraciones en el editor de notación."
permalink: /graphic/pitch/index-ES.html
---

## Resumen de comandos clave ##

{% include keytable.html
	contentId="pitchkeysummary"
%}
<script type="text/JSON" id="pitchkeysummary">
{% include keypresses/pitchkeys.json %}
</script>

## Navegación con notación gráfica ##
Después de seleccionar una nota o un silencio en la notación gráfica, puedes desplazarte a otras notas de la partitura melódica o armónicamente.  Utiliza la tecla <span class="keypress">cursor izquierdo</span> para desplazarte a la nota melódica anterior, la tecla <span class="keypress">cursor derecha</span> para desplazarte a la siguiente nota melódica, la tecla <span class="keypress">cursor arriba</span> para desplazarte a la siguiente nota armónica superior de la partitura y la tecla <span class="keypress">cursor abajo</span> para desplazarte a la siguiente nota armónica inferior de la partitura.

A continuación se muestra una demostración de las teclas de cursor en acción.  Observa que la navegación armónica mueve alrededor de las notas, de modo que al intentar subir más allá de la nota superior en la partitura, el cursor se mueve a la nota armónica inferior en ese punto de la partitura.


{% include image.html
	file="navigation.gif"
	alt="navegar por las notas de una partitura con las teclas de cursor"
	max-width="75%"
	caption="Navegar por las notas/silencios de una partitura con las teclas de cursor."
%}
Ten en cuenta también que debe haber una nota o silencio en la misma marca de tiempo en un pentagrama o capa; de lo contrario, ese pentagrama o capa se saltará. Observa también que el cursor en el editor de texto de la izquierda se actualiza para coincidir con la nota/silencio actualmente seleccionado. Por último, ten en cuenta que si te desplazas melódicamente de una página, se cargará la página siguiente/anterior.


## Transposición por tonos ##
Las notas pueden transponerse a una línea de pentagrama o espacio diferente haciendo clic en una nota y utilizando las teclas de flecha <span class="keypress">mayúsculas arriba</span> y <span class="keypress">mayúsculas abajo</span> para moverla verticalmente.  A continuación se muestra una demostración en la que el tono D5 se mueve hacia abajo en un tono a D4:

{% include image.html
	file="transpose-note.gif"
	alt="transponer gráficamente una nota"
	max-width="75%"
	caption="Transposición gráfica por tonos de una nota con <span class='keypress'>mayúsculas-abajo</span>."
%}
Observa que a medida que la nota se desplaza hacia abajo en el editor de notación, la nota correspondiente en los datos de Humdrum cambiará automáticamente para coincidir con el nueva altura de la nota en la notación.

## Transposición por intervalo diatónico ##
Si necesitas transponer una nota más de un paso a la vez, un método de transposición más rápido prefija la pulsación de la tecla <span class="keypress">subir</span> o <span class="keypress">bajar</span> con un dígito desde <span class="keypress">3</span> hasta <span class="keypress">9</span> para transponer hacia arriba o hacia abajo en ese intervalo diatónico:

{% include image.html
	file="transpose-thirds.gif"
	alt="transponer gráficamente una nota por terceras"
	max-width="75%"
	caption="Transponer una nota en terceras con <span class='keypress'>3+shift-up</span>."
%}

{% include note.html
	content="En el futuro, al hacer doble clic en una nota de un acorde, se seleccionarán todas las notas del acorde y se transpondrán juntas. Además, esto podría implementarse también para compases enteros o notas de la barra o grupos de valoración irregular."
%}

## Transposición por octava ##
Las combinaciones de teclas <span class="keypress">control-arriba</span>/<span class="keypress">control-abajo</span> pueden utilizarse como atajo para transponer una nota una octava.  Esto equivale a <span class="keypress">8+mayúsculas arriba</span>/<span class="keypress">8+mayúsculas abajo</span>.

{% include image.html
	file="transpose-octave.gif"
	alt="transponer gráficamente una nota por octavas"
	max-width="75%"
	caption="Transponer una nota hacia arriba/abajo de octava con <span class='keypress'>control-arriba</span> class='keypress'>control-down</span>."
%}


## Alteraciones ##
Se pueden añadir alteraciones a una nota seleccionada pulsando <span class="keypress">menos</span> para un bemol, <span class="keypress">almohadilla</span> para un sostenido y <span class="keypress">n</span> para un natural / becuadro.  Para añadir un doble bemol o un doble sostenido, anteponga a la pulsación accidental el dígito <span class="keypress">2</span>.

Repetir la misma alteración en una nota que ya tiene esa alteración eliminará la alteración de la nota.  Una forma fácil de eliminar cualquier alteraación que no sea un signo natural sería escribir <span class="keypress">n+n</span>: una vez para convertir la alteración en un signo becuadro, y otra para eliminar el signo becuadro (la nota seguirá poseyendo un natural implícito, sin embargo).

{% include image.html
	file="accidentals.gif"
	alt="cambiar la alteración de una nota"
	caption="Añadir/eliminar gráficamente las alteraciones."
%}


{% comment %}
Alteraciones cruzados entre pentagramas
{% endcomment %}



## Alteraciones impresas vs. interpretadas ##
Las alturas de notas de `**kern` siempre codifican las alteraciones reales que se interpretan. VHV calcula automáticamente las alteraciones visuales al convertir a [MEI](http://www.music-encoding.org) para la representación en notación musical gráfica.

Sin embargo, puede haber excepciones a las reglas de cálculo de alteraciones visuales, que se demuestran en las subsecciones siguientes.

1. *Alteración forzada*: se puede forzar la visualización del alteración en una nota seleccionada pulsando <span class="keypress">x</span>.

1. *Alteración suprimida*: no mostrar la alteración independientemente de si debe mostrarse o no (actualmente no está disponible en la edición gráfica).

A continuación se muestra una demostración de cómo cambiar las alteraciones en la música. Observa que la alteración de la alteración en una nota puede añadir automáticamente una alteración visual diferente en una nota siguiente en el compás.

{% include image.html
	file="visual-accidentals.gif"
	alt="cálculos automáticos de las alteraciones impresas"
	caption="Demostración de cálculos sobre alteraciones impresas."
%}

Como se demuestra en la figura anterior, si una nota de ornamento tiene una alteración impresa, la siguiente nota en la misma línea del pentagrama o espacio en el compás recibirá una alteración forzada.  Si no quieres esta alteración automática de cortesía añade una `y` después de la alteración en los datos de Humdrum.


### Alteraciones forzadas ###
Las alteraciones pueden ser forzadas a mostrarse en la notación tecleando la tecla <span class="keypress">x</span> mientras se edita una nota (mnemónico: e**X**plícito).  Esto añadirá el carácter `X` (x mayúscula) después del accidental para los datos de la nota, lo que significa mostrar explícitamente el accidental en la notación.  Las alteraciones forzadas se utilizan normalmente para recordar al intérprete que la nota tiene la alteración dada, como cuando una alteración es cancelada por una línea de compás y una nota en el siguiente compás se escribe de nuevo según la armadura.  Las alteraciones forzadas usadas con este propósito se llaman alteraciones de cortesía o de advertencia.

{% include image.html
	file="forced-accidentals.gif"
	alt="forzar la visualización de las alteraciones"
	max-width="100%"
	caption="Forzar la visualización de las alteraciones con <span class='keypress'>x</span>."
%}

Los signos naturales (`n`) en los datos de `**kern` se tratan automáticamente como alteraciones forzadas al convertir los datos de Humdrum en notación.  Para crear un natural forzado, debe escribir <span class="keypress">n</span> para añadir un signo natural.

{% include note.html
	content="Hay que limpiar algunas cosas en la implementación de la edición gráfica de las alteraciones forzadas: (1) teclear <span class='keypress'>x</span> debería cambiar el signo de accidentalidad forzada, (2) teclear <span class='keypress'>x</span> en una nota con un natural implícito debería insertar una `n` para un natural explícito en lugar de `nX` que es un signo natural doblemente explícito, y (3) la `X` debería ser eliminada al borrar un accidental de la nota (convirtiendo el accidental en un natural implícito)."
%}

### Alteraciones suprimidas ###

VHV suprimirá automáticamente las alteraciones impresas en las notas que las requieran si están ligadas desde compases anteriores:

{% include image.html
	file="accidental-suppressed-tie.png"
	alt="transponer gráficamente una nota"
	max-width="75%"
	caption="Las alteraciones visuales se suprimen automáticamente para las notas ligadas sobre líneas de compás."
%}

La supresión explícita de las alteraciones visuales no puede hacerse en el editor de notación (todavía), pero puede hacerse añadiendo una sola `y` después de la alteración en el editor de texto.

### Alteraciones de los ornamentos ###

Los ornamentos que contienen alteraciones auxiliares forzarán automáticamente una alteración en una nota siguiente si es diferente a la del alteración auxiliar.

{% include image.html
	file="ornament-accidentals.gif"
	alt="Alteraciones ornamentales"
	caption="Alteraciones forzadas automáticamente después de los ornamentos.  (escribiendo <span class='keypress'>m</span>, <span class='keypress'>w</span>, y <span class='keypress'>T</span>)"
%}


## Alteraciones editoriales ##

El editor de notación VHV permite alternar las alteraciones entre las formas regulares y las *editoriales*. Pulse <span class="keypress">i</span> para cambiar entre estos dos tipos de alteraciones.

{% include image.html
	file="editorial-accidentals.gif"
	alt="Alteraciones editoriales"
	max-width="90%"
	caption="Creación, eliminación y modificación de alteraciones editoriales."
%}

Para indicar una redacción accidental, hay que añadir un significante RDF a los datos:


```
!!!RDF**kern: i = editorial accidental
```
También se puede utilizar cualquier significante de usuario que no sea `i`.  Si no se encuentra ningún RDF de alteración editorial en los datos, se insertará uno en la parte inferior del contenido de Humdrum automáticamente; de lo contrario, se utilizará el significante de una entrada RDF editorial accidental existente (aunque no sea&nbsp;`i`).

Las alteraciones editoriales se mostrarán siempre de forma forzada, por lo que no es necesario añadir un indicador de visualización forzada (`X`) con la tecla <span class="keypress">x</span>.

{% include note.html
	content="Tal vez se debería permitir la supresión de las alteraciones editoriales, pero actualmente no se puede."
%}

{% include warning.html
	content="La inserción automática de un RDF de alteración editorial está actualmente conectada al significante de usuario \"i\", por lo que no debe utilizar el mismo significante en el archivo para un significado diferente en los datos kern a menos que añadas manualmente un RDF de alteración editorial utilizando un significante de usuario diferente."
%}

{% include note.html
	content="Una pequeña alteración sobre una nota es el estilo común para las alteraciones editoriales en las ediciones de música del Renacimiento (normalmente para indicar una accidental *musica ficta* no escrita).  No existen (todavía) otros estilos de representación de las alteraciones editoriales."
%}

### Estilo de las alteraciones editoriales ###
Por defecto, las alteraciones editoriales se muestran como pequeñas alteraciones sobre la nota.  Este es el estilo de alteración editorial más común en la música del Renacimiento.  Para la música que incluye números de bajo continuo o acordes, las alteraciones editoriales se muestran normalmente entre paréntesis u ocasionalmente entre paréntesis.

Si se añade la cadena `bracket` o `brack` en algún lugar de la línea RDF de las alteraciones editoriales, se moverán las alteraciones editoriales delante de las notas y se colocarán corchetes alrededor de ellas:

{% include image.html
	file="editac-styles.png"
	alt="selección de un estilo de la alteración editorial"
	max-width="85%"
	caption="Ejemplos de cómo seleccionar un estilo de la alteración editorial."
%}

Se puede utilizar cualquier significante de usuario para las alteraciones editoriales, pero la última línea RDF de un archivo tiene prioridad para añadir/eliminar el estado editorial de las alteraciones cuando se utiliza el comando de edición gráfica `i`.


{% include note.html
	content="La selección de un estilo editorial accidental no puede hacerse gráficamente, sino que debe añadirse a la línea RDF."
%}



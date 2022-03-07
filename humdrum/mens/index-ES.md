---
title: Notación mensural
lang: en es
ref: humdrum-mens
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum mensural notation
creation_date: 8 May 2018
translation_date: 11 Aug 2021
last_updated: 14 Dec 2020
tags: [all, humdrum ]
verovio: "true"
vim: ts=3 ft=javascript
summary: Una descripción de cómo codificar la música mensural.
sidebar: main_sidebar
permalink: /humdrum/mens/index-ES.html
---

La notación musical mensural puede ser codificada en Humdrum utilizando la interpretación exclusiva `**mens`:

{% include verovio.html
	source="mens"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="200px"
%}
<script type="application/json" id="mens">
**mens
*I"Contra
*clefC4
*k[]
*M2/1
*met(C|)
=1-
sp:D
siF
miE
miD
Mp:F
miG
=3-
MiA
MiB-
MiA
sid
mic
miB
sid
=5-
Mir
sic
miB
miA
=6-
Mp:c
mid
sie
=7-
sie
Sie
sp:e
sic
miB
miA
=10-
Mp:B
miA
MiB
Mic
=11-
siA
sid
=12-
*-
</script>

Véase también el [filtro kern2mens](/filter/kern2mens) para convertir los datos `**kern` en datos `**mens`.

## Altura / tono ##

La codificación de la altura de las notas en `**mens` deriva de la representación de la de `**kern`.  Las letras a&ndash;g representan tonos diatónicos, con duplicación de letras y cambio de mayúsculas y minúsculas que controlan la octava:

{% include verovio.html
	source="octave"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="200px"
%}
<script type="application/json" id="octave">
**mens
*clefF4
*k[]
*M2/1
*met(C|)
=1-
SFF
SF
Sf
=-
*clefC3
SF
Sf
Sff
=||
*-
</script>


### Alteraciones ###

Las alteraciones también son similares a los datos de `**kern`:

Símbolo | Significado
-------|--------
`-`    | signo bemol
`n`    | signo natural / becuadro
`#`    | signo sostenido



{% include verovio.html
	source="accid"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="200px"
%}
<script type="application/json" id="accid">
**mens
*clefC3
*k[]
*M2/1
*met(C|)
=-
Sc#
Scn
SB-
SBn
=||
*-
</script>

El tratamiento de las alteraciones en los datos de `**mens` es sutilmente diferente al de los datos de `**kern`.  En los datos de `**mens`, las alteraciones se tratan por defecto como signos visuales, mientras que en los datos de `**kern` se tratan como alteraciones de ejecución que pueden ser o no alteraciones impresas. 

{% include verovio.html
	source="accid2"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="200px"
%}
<script type="application/json" id="accid2">
**mens
*clefC3
*k[]
*M2/1
*met(C|)
=-
Sc#
Sc
Sc#
Sc#
=||
*-
</script>

Compárese con una codificación análoga en los datos de `**kern`, donde la segunda nota es también un Do natural, pero las convenciones modernas para mostrar los estados cromáticos de las notas fuerzan un natural automático en la nota.  Y la última nota tiene un sostenido suprimido, ya que las notas anteriores establecen el estado cromático para ese tono diatónico en un sostenido.

{% include verovio.html
	source="accid3"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="200px"
%}
<script type="application/json" id="accid3">
**kern
*clefC3
*k[]
*M2/1
*met(C|)
=-
0c#
0c
0c#
0c#
=||
*-
</script>

### Alteraciones editoriales ###

Las alteraciones editoriales se utilizan para aclarar las alteraciones de interpretación que se aplicarán a la música.  Existen cuatro niveles de alteraciones editoriales, que se indican añadiendo los siguientes caracteres después de una alteración:

Calificador de la alteración | Significado
--------------------------|--------
`y`  | La alteración está fuertemente implícita en la notación musical.  Esto significa típicamente que el accidental se deriva de la armadura.  
`yy` | La alteración está débilmente implícita en la notación musical.  Se suele utilizar para indicar la anulación de una alteración visual.  Equivale aproximadamente a un accidental de cortesía.
`Y`  | Alteración de la interpretación.  La alteración no está directamente implícita en la notación musical, sino que sería deducida por un intérprete, por ejemplo para crear un tono principal (*leading tone*) antes de una nota de cadencia.
`YY` | Intervención editorial debido a un presunto error de redacción.  Se sospecha que falta una alteración visual en la nota.


Este es un uso típico del calificador `y` para indicar que una nota Si en la música es bemol aunque la nota no tenga un bemol delante ya que el bemol viene de la armadura:

{% include verovio.html
	source="accid4"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="200px"
%}
<script type="application/json" id="accid4">
**mens
*clefC3
*k[b-]
*M2/1
*met(C|)
=-
sF
sG
sA
sB-y
sc
sd
se
sf
=||
*-
</script>

Tal alteración puede mostrarse como una alteración editorial sobre la nota colocando `*acclev:y` en algún lugar antes de la nota.  Esto significa que el nivel de alteración editorial comienza en `y` (y también incluye los niveles `yy`, `Y` y `YY`).  Por defecto, sólo el nivel de alteraciones `YY` se mostrará como alteraciones editoriales.  Para suprimir también este nivel de alteración que se muestra como editorial, utiliza `*Xacclev`.

{% include verovio.html
	source="accid5"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="200px"
%}
<script type="application/json" id="accid5">
**mens
*clefC3
*k[b-]
*M2/1
*met(C|)
*acclev:y
=-
sF
sG
sA
sB-y
sc
sd
se
sf
=||
*-
</script>

Las armaduras en mensural sólo afectan a las notas de un determinado tono diatónico, a diferencia de las armaduras modernas que se aplican a la clase de tono diatónico.  Un ejemplo de uso del calificador `yy` es para advertir que un tono debe ser natural cuando la armadura tiene un bemol en otra octava:

{% include verovio.html
	source="accid6"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="200px"
%}
<script type="application/json" id="accid6">
**mens
*clefF4
*k[b-]
*M2/1
*met(C|)
*acclev:yy
=-
sBB-y
sC
sD
sE
sF
sG
sA
sBnyy
=||
*-
</script>

Para ver esta alteración de cortesía o precaución, debe utilizarse `*acclev:y` o `*acclev:yy`.


El nivel `Y` para las alteraciones se utiliza para indicar una alteración no escrita que se espera que un intérprete cante basándose en la práctica de la interpretación, como la creación de un tono principal (*leading tone*) antes de una cadencia:

{% include verovio.html
	source="accid7"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="200px"
%}
<script type="application/json" id="accid7">
**mens
*clefC3
*k[b-]
*M2/1
*met(C|)
=-
Sd
sc#Y
Sd
=
*acclev:Y
Sd
sc#Y
Sd
=||
*-
</script>

Por defecto, estas alteraciones estarán ocultas en la representación de la notación gráfica. Utiliza `*acclev:Y` para mostrar estas alteraciones como editoriales, o utiliza cualquiera de los niveles más generosos `*acclev:yy` o `*acclev:y` que también mostrarán las alteraciones de interpretación como editoriales visibles.

## Plicas de las notas ##

Las plicas son similares a las de los datos de `**kern`.  `/` significa plica hacia arriba y `\` significa plica hacia abajo:

{% include verovio.html
	source="stem1"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="200px"
%}
<script type="application/json" id="stem1">
**mens
*clefC3
*met(C|)
=-
Mc/
Mc\
=||
*-
</script>

### Direcciones automáticas de la plica ###

En general, las plicas ascendentes son más comunes en la música mensural, por lo que la interpretación `*stem` puede utilizarse para establecer las plicas en la música en una dirección fija.  La interpretación `*stem:/` forzará las plicas hacia arriba en todas las notas subsiguientes, mientras que `*stem:\` las forzará hacia abajo.  Para volver a permitir la dirección automática de las plicas, utiliza `*stem:X`:

{% include verovio.html
	source="stem2"
	pageWidth="800"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="200px"
%}
<script type="application/json" id="stem2">
**mens
*clefC3
=-
!LO:TX:b:i:color=skyblue:t=automatic stems
MF
MG
MA
MB
Mc
Md
Me
Mf
Mg
=-
*stem:/
!LO:TX:b:i:color=skyblue:t=forced up
MF
MG
MA
MB
Mc
Md
Me
Mf
Mg
=-
*stem:\
!LO:TX:b:i:color=skyblue:t=forced down
MF
MG
MA
MB
Mc
Md
Me
Mf
Mg
=-
*stem:X
!LO:TX:b:i:color=skyblue:t=automatic again
MF
MG
MA
MB
Mc
Md
Me
Mf
Mg
=||
*-
</script>


## Ritmo ##

Los ritmos de las notas se representan con letras:

<style>

.dense td {
	padding-top: 1px;
	padding-bottom: 1px;
	margin-top: 0;
	margin-bottom: 0;
}

.twocol td:first-child { width: 10%; text-align: center; vertical-align: middle}
.twocol td:nth-child(2) { width: 40%; vertical-align: middle}
.twocol td:nth-child(3) { width: 10%; text-align: center; vertical-align: middle}
.twocol td:nth-child(4) { width: 40%; vertical-align: middle}

.onecol td:first-child { width: 20%; text-align: center; vertical-align: middle}
.onecol td:nth-child(2) { width: 80%; vertical-align: middle}

</style>


<table class="dense twocol">
<tr><th>Carácter</th><th> Significaado</th>                             <th>Carácter</th><th> Significado</th>  </tr>
<tr><td> X </td><td> maxima (redonda óctuple)</td>    <td>   </td>  <td> </td>            </tr>
<tr><td> L </td><td> longa (redonda cuádruple)</td>     <td>   </td>  <td> </td>            </tr>
<tr><td> S </td><td> Brevi(S) (doble redonda)</td>     <td> s </td>  <td> semi-brevi(s) (redonda) </td>  </tr>
<tr><td> M </td><td> Minima (blanca)</td>     <td> m </td>  <td> semi-minim  (negra) </td> </tr>
<tr><td> U </td><td> Fusa (corchea)</td>       <td> u </td>  <td> semi-fusa (semicorchea) </td>   </tr>
</table>


{% include verovio.html
	source="rhythms"
	pageWidth="1100"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="280px"
%}
<script type="application/json" id="rhythms">
**mens	**mens
*I"Rests	*I"Notes
*clefC3	*clefC3
Xr	Xc
Lr	Lc
Sr	Sc
sr	sc
Mr	Mc
mr	mc
Ur	Uc
ur	uc
=||	=||
*-	*-
</script>



### Puntillos ###

Los puntillos que representan puntillos de prolongación o de separación. Este puntillos no afecta directamente a la duración de las notas, sino que se utiliza `p` para perfeccionar las notas.  En el futuro, este carácter de punto podría utilizarse para determinar automáticamente si las notas son perfectas o imperfectas, basándose en la medición predominante y en las notas circundantes.

## Signos de mensuración ##

Los signos de mensuración se indican con el patrón `*met(X)`, donde `X` es la descripción del signo de mensuración que figura en la tabla siguiente.  Las mensuraciones más comunes son `*met(O)` para la mensuración de círculos, y `*met(C|)` para la mensuración de Cut-C.  A continuación se muestra una tabla con algunas de las posibles mensuraciones:


<table class="dense twocol">
<tr><th>Mensuración</th><th> Representación gráfica</th>                             <th>Mensuración</th><th> Representación gráfica</th>  </tr>

<tr>
	<td> <tt>*met(C|)</tt> </td><td>  <img style="height:20px" src="c-pipe.svg"> </td>    
	<td> <tt>*met(O)</tt>  </td>  <td> <img style="height:20px" src="o.svg"> </td>
</tr>

<tr>
	<td> <tt>*met(C)</tt> </td><td>  <img style="height:20px" src="c.svg"> </td>    
	<td> <tt>*met(3)</tt>  </td>  <td> <img style="height:20px" src="n3.svg"> </td>
</tr>

<tr>
	<td> <tt>*met(C2)</tt> </td><td>  <img style="height:20px" src="c-2.svg"> </td>    
	<td> <tt>*met(O|)</tt>  </td>  <td> <img style="height:20px" src="o-pipe.svg"> </td>
</tr>

<tr>
	<td> <tt>*met(C|3)</tt> </td><td>  <img style="height:20px" src="c-pipe-3.svg"> </td>    
	<td> <tt>*met(O/3)</tt>  </td>  <td> <img style="height:20px" src="o-over-3.svg"> </td>
</tr>

<tr>
	<td> <tt>*met(O2)</tt> </td><td>  <img style="height:20px" src="o-2.svg"> </td>    
	<td> <tt>*met(C3)</tt>  </td>  <td> <img style="height:20px" src="c-3.svg"> </td>
</tr>

<tr>
	<td> <tt>*met(C.)</tt> </td><td>  <img style="height:20px" src="c-dot.svg"> </td>    
	<td> <tt>*met(O.)</tt>  </td>  <td> <img style="height:20px" src="o-dot.svg"> </td>
</tr>

<tr>
	<td> <tt>*met(3/2)</tt> </td><td>  <img style="height:20px" src="n3-over-2.svg"> </td>    
	<td> <tt>*met(O3)</tt>  </td>  <td> <img style="height:20px" src="o-3.svg"> </td>
</tr>

<tr>
	<td> <tt>*met(C|2)</tt> </td><td>  <img style="height:20px" src="c-pipe-2.svg"> </td>    
	<td> <tt>*met(2)</tt>  </td>  <td> <img style="height:20px" src="n2.svg"> </td>
</tr>

<tr>
	<td> <tt>*met(O|3)</tt> </td><td>  <img style="height:20px" src="o-pipe-3.svg"> </td>    
	<td> <tt>*met(C.|)</tt>  </td>  <td> <img style="height:20px" src="c-dot-pipe.svg"> </td>
</tr>

<tr>
	<td> <tt>*met(Cr)</tt> </td><td>  <img style="height:20px" src="c-reverse.svg"> </td>    
	<td> <tt>*met(C|/3)</tt>  </td>  <td> <img style="height:20px" src="c-pipe-over-3.svg"> </td>
</tr>

<tr>
	<td> <tt>*met(C|/2)</tt> </td><td>  <img style="height:20px" src="c-pipe-over-2.svg"> </td>    
	<td> <tt>*met(C|r)</tt>  </td>  <td> <img style="height:20px" src="c-pipe-reverse.svg"> </td>
</tr>

</table>

Prueba los signos de mensuración anteriores en este ejemplo:

{% include verovio.html
	source="mensuration"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="100"
%}

<script type="application/x-humdrum" id="mensuration">
**mens
*met(C)
Lr
*-
</script>


## Ligature ##

Las ligaduras se indican con corchetes para las ligaduras rectas, y con símbolos `<`y  `>` para las ligaduras oblicuas. 

{% include verovio.html
	source="ligature"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="250px"
%}

<script type="application/x-humdrum" id="ligature">
**mens
*clefC3
*met(C|)
Sc
[Sc
Sd]
Md/
Mc
sB
[Sc
Sd
SA]
*-
</script>

[Es necesario evitar &lt; y &gt; para que las ligaduras oblicuas no se interpreten como paréntesis HTML].


## Barras de compás ##

Las líneas de compás se comportan igual que en los datos de `**kern`.  Actualmente, las líneas de compás son necesarias en los datos para romper los pentagramas visuales en varios sistemas.  Añade un carácter de guión (`-`) a la línea de barras para hacerla invisible.  Las líneas de compás deben colocarse en los límites de las breves.


## Coloración ##

Las notas coloreadas se indican añadiendo `~` a cada nota coloreada.

Ejemplo en notación blanca:

{% include verovio.html
	source="color-white"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="250px"
%}

<script type="application/x-humdrum" id="color-white">
**mens
*clefC3
*met(C|)
Sc
S~B
s~A
s~B
sc~
s~G
Sc
*-
</script>

Ejemplo en notación negra:

{% include verovio.html
	source="color-black"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="250px"
%}

<script type="application/x-humdrum" id="color-black">
**mens
*black
*clefC3
*met(C|)
Sc
S~B
s~A
s~B
sc~
s~G
Sc
*-
</script>


### Perfección ###

La letra `p` añadida al valor rítmico básico significa que la nota/silencio es *perfecta*.  En la notación moderna, esto equivale a añadir un puntillo de prolongación después de una nota, como una blanca con puntillo.  La letra "i" indica un ritmo *imperfecto*.  En la notación moderna, todas las notas son imperfectas a menos que haya un puntillo de prolongación después de ellas para hacerlas perfectas.

Los calificadores rítmicos `p` y `i` no son necesarios a menos que esté creando una partitura polifónica.  En ese caso se requiere la duración exacta de las notas para alinear las partes.

## Alteratio ##

Por implementar/describir

## Referencias ##

<ul>

<li>  <a target="_blank" href="https://revista.uclm.es/index.php/cuadernosdeinvestigacionmusical/article/view/1953">White Mensural Manual Encoding: from Humdrum to MEI</a>
by David Rizo, Nieves Pascual and Craig Sapp, 2019.</li>

</ul>



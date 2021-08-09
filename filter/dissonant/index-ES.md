---
title: filtro dissonant
lang: en es
ref: filters-dissonant
author: ["Alexander Morgan", "Craig Sapp"]
translator: 
creation_date: 29 May 2017
translation_date: 
last_updated: 10 Jun 2017
tags: [all, filters]
sidebar: main_sidebar
examplewidth: 1200
vim: ft=html
verovio: "true"
keywords: "interface commands"
summary: "El filtro disonante etiqueta las notas no armónicas en las texturas contrapuntísticas."
permalink: /filter/dissonant/index-ES.html
---
*NOTA: La traducción de esta página necesita revisión*

El filtro dissonant etiqueta automáticamente la función de las notas no armónicas en las texturas contrapuntísticas.  Todas las segundas y séptimas armónicas se consideran disonantes, así como las cuartas por encima de la voz que suena más grave.

Se espera que cada columna de entrada `**kern` sea monofónica y no tenga subcolumnas ramificadas.  Si hay acordes en la música, sólo se utiliza la primera nota del acorde, y se ignoran las subcolumnas secundarias.

A continuación se muestra un ejemplo del filtro dissonant en acción utilizando un extracto de la chanson de Josquin <a href="http://josquin.stanford.edu/work/?id=Jos2705">Ce povre mendiant/Pauper sum ego</a>.  Para aplicar el filtro a un archivo, incluye la línea `!!!filter: dissonant` en cualquier lugar del archivo.  Las etiquetas de la función dissonant para cada voz se insertarán en las columnas inmediatamente a la derecha de cada columna `**kern`.  En la siguiente pantalla las etiquetas se muestran encima de las notas a las que se aplican.  `P` indica una nota de paso ascendente y `p` significa una nota de paso inferior.  Consulta la lista completa de abreviaturas de etiquetas más abajo.


{% include verovio.html
	source="josex"
	scale="40"
	spacingStaff="4"
	spacingSystem="4"
	pageWidth="1450"
	tabsize="10"
%}

<script type="application/x-humdrum" id="josex">
!!!filter: dissonant
**kern	**kern	**kern
*I"Bassus	*I"Tenor	*I"Discantus
*I'B	*I'T	*I'D
*clefF4	*clefGv2	*clefG2
*k[]	*k[]	*k[]
*M2/1	*M2/1	*M2/1
*met(C|)	*met(C|)	*met(C|)
=1-	=1-	=1-
0r	0A	0e
=2	=2	=2
0r	1.A	1.e
.	4G	2f
.	4F	.
=3	=3	=3
0r	1E	1g
.	[1F	[1a
=4	=4	=4
0A	2F]	2a]
.	2E	2g
.	2D	2f
.	4C	4e
.	4BB	4d
=5	=5	=5
0A	1AA	1c
.	4AA	1cc
.	4BB	.
.	4C	.
.	4D	.
=6	=6	=6
1G	1E	2.b
.	.	4a
1A	1AA	1cc
=7	=7	=7
0F	0A	4cc
.	.	4b
.	.	4a
.	.	4g
.	.	1a
=8	=8	=8
0E	1B	0g
.	[1c	.
=9	=9	=9
0r	2c]	1r
.	4B	.
.	4A	.
.	1B	1g
=10	=10	=10
0r	1.A	1a
.	.	1cc
.	4G	.
.	4F	.
=11	=11	=11
0G	0E	1b
.	.	4b
.	.	4a
.	.	4g
.	.	4f
=12	=12	=12
0G	1r	1e
.	1B	1d
=13	=13	=13
1F	1A	1d
1G	[1B	[1e
=14	=14	=14
0E	2B]	2e]
.	2.G	2f
.	.	[1g
.	4A	.
.	4B	.
.	4c	.
=15	=15	=15
0D	2d	2g]
.	1c	4f
.	.	4e
.	.	1f
.	2B	.
=16	=16	=16
0r	2.c	0e
.	4B	.
.	2G	.
.	[2A	.
=17	=17	=17
0r	2A]	1r
.	4G	.
.	4F	.
.	1E	1b
=18	=18	=18
0F	1r	1.a
.	1D	.
.	.	4b
.	.	4cc
=19	=19	=19
0F	4D	1dd
.	4E	.
.	4F	.
.	4G	.
.	1A	1cc
=	=	=
*-	*-	*-
!!!RDF**kern: i=editorial accidental
</script>

Prueba a editar la partitura Humdrum anterior para generar varios tipos de disonancias.  Si se elimina la primera línea (`!!!filter: dissonant`) se desactivará el análisis de disonancias, y si se añade `-u` a `!!!filter: dissonant -u` se fusionarán las subcategorías en una única categoría principal para los tipos de disonancias.

Otra variación interesante es utilizar el siguiente filtro:

```
!!!filter: dissonant --colorize | extract -i kern
```

La opción `--colorize` coloreará las disonancias en función de la posición métrica: rojo para los niveles semibreve y superiores, verde para el nivel mínima y azul para el nivel semínima.  La siguiente herramienta de extracción elimina las etiquetas de texto.

## Etiquetas de funciones disonantes ##
Las notas disonantes están marcadas con abreviaturas de etiquetas de una sola letra tanto en la notación como en la partitura de Humdrum.  La primera tabla de abajo ofrece las categorías detalladas de etiquetas por defecto utilizadas en el análisis de disonancias, mientras que la segunda tabla ofrece categorías más generalizadas que no distinguen direcciones melódicas.

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
<tr><th>Etiqueta</th><th> Significado</th>                             <th>Etiqueta</th><th> Significado</th>                                 </tr>
<tr><td> P </td><td> notaa de paso ascendente</td>                   <td> p </td>  <td> nota de paso descendente</td>                   </tr>
<tr><td> N </td><td> bordadura superior</td>                        <td> n </td>  <td> bordadura inferior</td>                          </tr>
<tr><td> D </td><td> doble bordadura, primero superior, luego inferior</td>      <td> d </td>  <td> doble bordadura, primero inferior, luego superior</td>        </tr>
<tr><td> E </td><td> escapada superior</td>          <td> e </td>  <td> escapada inferior</td>            </tr>
<tr><td> C </td><td> cambiata corta ascendente</td>         <td> c </td>  <td> cambiata corta descendente</td>          </tr>
<tr><td> K </td><td> cambiata larga ascendente</td>          <td> k </td>  <td> cambiata larga descendente</td>           </tr>
<tr><td> A </td><td> anticipación ascendente</td>                   <td> a </td>  <td> anticipación descendente</td>                 </tr>
<tr><td> I </td><td> cambiata inversa ascendente</td>       <td> i </td>  <td> cambiata inversa descendente</td>        </tr>
<tr><td> J </td><td> escapada inversa superior</td>  <td> j </td>  <td> escapada inversa inferior</td>    </tr>
<tr><td> S </td><td> suspensión ternaria</td>                    <td> s </td>  <td> suspensión binaria</td>                       </tr>
<tr><td> G </td><td> agente de suspensión ternaria</td>              <td> g </td>  <td> agente de suspensión binaria</td>                 </tr>
<tr><td> F </td><td> suspensión falsa por grado conjunto ascendente</td>      <td> f </td>  <td> suspensión falsa por grado conjunto descendente</td>      </tr>
<tr><td> x </td><td> resolución de la disonancia de la suspensión</td><td> r </td>  <td> nota repetida de la suspensión </td>              </tr>
<tr><td> M </td><td> agente de la suspensión ausente por tono ascendente</td> <td> m </td>  <td> agente de la suspensión ausente por tono descendente </td> </tr>
<tr><td> o </td><td> suspensión puramente ornamental</td>          <td> h </td>  <td> modismo de chanson</td>                           </tr>
<tr><td> Q </td><td> negra tercera disonante de la nota de paso ascendente</td>  <td> q </td>  <td> tercera negra disonante de la nota de paso descendente</td>      </tr>
<tr><td> B </td><td> tercera disonante de la bordadura superior</td>  <td> b </td>  <td> tercera disonante de la bordadura inferior</td>    </tr>
<tr><td> T </td><td> apoyatura ascendente</td>    <td> t </td>  <td> apoyatura descendente</td>      </tr>
<tr><td> V </td><td> nota de paso ascendente acentuada</td>       <td> v </td>  <td> nota de paso desdendente acentuada</td>        </tr>
<tr><td> W </td><td> bordadura superior acentuada</td>               <td> w </td>  <td> bordadura inferior acentuada</td>                 </tr>
<tr><td> Y </td><td> sólo disonancia contra disonancia conocida asc.</td> <td> y </td>  <td> sólo disonancia contra disonancia conocida desc.</td> </tr>
<tr><td> Z </td><td> disonancia sin clasificar, intervalo de 2ª o 7ª</td> <td> z </td ><td> unclassified dissonance,disonancia sin clasificar, intervalo de 4ª</td></tr>
</table>

La opción `-u` (que significa *undifferentiated*) reduce las subcategorizaciones arriba/abajo en una sola etiqueta designada por una letra mayúscula:

<table class="dense twocol">
<tr><th>Etiqueta</th><th> Meaning</th>                             <th>Etiqueta</th><th> Meaning</th>                                 </tr>
<tr><td> P </td><td> nota de paso</td>                          <td> F </td><td> suspensión falsa</td></tr>
<tr><td> N </td><td> bordadura</td>                         <td> D </td><td> bordadura doble</td></tr>
<tr><td> E </td><td> escapada</td>                <td> R </td><td> nota repetida de la suspensión</td></tr>
<tr><td> C </td><td> cambiata corta</td>                   <td> M </td><td> agente de supensión ausente</td></tr>
<tr><td> K </td><td> cambiata larga</td>                    <td> Q </td><td> negra disonante tercera de la nota de paso</td></tr>
<tr><td> A </td><td> anticipación</td>                          <td> B </td><td> dissonant 3rd quarter neighbor</td></tr>
<tr><td> T </td><td> apoyatura</td>                          <td> V </td><td> nota de paso acentuada</td></tr>
<tr><td> I </td><td> bordadura anterior incompleta</td>          <td> W </td><td> bordadura acentuada</td></tr>
<tr><td> J </td><td> bordadura posterior incompleta</td>         <td> H </td><td> modismo de chanson</td></tr>
<tr><td> S </td><td> suspensión binaria o ternaria</td>          <td> X </td><td> resolución de la disonancia de la suspensión</td></tr>
<tr><td> G </td><td> agente de la suspensión binaria o ternaria</td>    <td> Y </td><td> sólo disonancia contra la disonancia conocida</td></tr>
<tr><td> O </td><td> suspensión puramente ornamental</td>          <td> Z </td><td> disonancia sin clasificar</td></tr>
</table>

A continuación se ofrecen ejemplos de cada tipo de disonante.  Tenga en cuenta que los ejemplos musicales son [generados dinámicamente usando verovio](/myvhv/static) dentro de la página, y la herramienta *dissonant* etiqueta las notas mientras se carga la página web.



### Notas de paso (P, p) ###
Una nota de paso se aproxima por tono y se deja por tono en la misma dirección. La nota precedente debe ser métricamente más fuerte que la nota disonante, y la nota contra la que la nota de paso es disonante debe comenzar antes de la nota de paso y debe sostenerse al menos hasta el final de la nota de paso. Estas notas se etiquetan con "P" mayúscula y "p" minúscula para las notas de paso ascendentes y descendentes, respectivamente.


 {% include verovio.html
	humdrum-visible="false"
	source="passing"
	scale="50"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="passing">
**kern	**kern
*M2/4	*M2/4
4C	8cL
.	8dJ
4AA	4e
=2	=2
4FF	8fL
.	8eJ
4GG	4d
=	=
*-	*-
!!!filter: dissonant
</script>



### Bordaduras (N, n) ###
Las bordaduras tienen requisitos similares a los de los tonos de paso, excepto que en lugar de acercarse y salir por tono en la misma dirección, las bordaduras se acercan y salen por tono en direcciones opuestas. Los términos "N" y "n" se utilizan para etiquetar a las bordaduras superiores e inferiores, respectivamente.

{% include verovio.html
	humdrum-visible="false"
	source="nei"
	scale="50"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="nei">
**kern	**kern
*M2/4	*M2/4
4C	8ccL
.	8ddJ
4AA	4cc
=2	=2
4GG	8bL
.	8aJ
4EE	4b
=	=
*-	*-
!!!filter: dissonant
</script>



### Bordaduras dobles (D, d) ###
En una figura de bordaduraa doble, una nota principal es ornamentada por una bordadura superior y uno inferior antes de volver a la nota principal. Ambas notas disonantes reciben la misma etiqueta según el tipo de bordadura que aparece primero, `D` si la figura comienza con una bordadura superior, y `d` si comienza con una bordadura inferior. Mientras que la primera disonancia debe ser relativamente débil métricamente en comparación con la nota principal, la segunda de las dos dobles bordaduras puede ser acentuada, como en este fragmento de la chanson atribuida a Josquin [Mala se nea](http://josquin.stanford.edu/work/?id=Jos2915).

{% include verovio.html
	humdrum-visible="false"
	source="dbln"
	scale="50"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="dbln">
**kern	**kern
*Ivox	*Ivox
*I'B	*I'S
*clefF4	*clefG2
*k[b-]	*k[b-]
*M2/1	*M2/1
*met(C|)	*met(C|)
=50	=50
1C	2g
.	.
.	2g
.	.
[1FF	2a
.	2b-
=51	=51
0FF]	2.cc
.	.
.	4b-
.	4a
.	4g
.	4b-
.	4a/
=52	=52
2BB-	0b-
4BB-	.
4BB-	.
2BB-	.
.	.
2BB-	.
==	==
*_	*_
!!!filter: dissonant
</script>



### Escapada (E, e) ###
Una escapada se aproxima por grado conjunto y se aleja por salto en la dirección opuesta. La nota disonante debe ser métricamente más débil que la nota que la precede y una nota en otra voz debe comenzar antes de la escapada y mantenerse al menos hasta el final de la escapada.

{% include verovio.html
	humdrum-visible="false"
	source="chap"
	scale="50"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="chap">
**kern	**kern
*clefF4	*clefG2
*M2/4	*M2/4
4F	8aL
.	8gJ
4E	4cc
=2	=2
4F	8aL
.	8bJ
4G	4g
=	=
*-	*-
!!!filter: dissonant
</script>



###  Cambiatas (C, c, K, k) ###
Una cambiata se aproxima por grado conjunto y se deja por un salto de tercera en la misma dirección. Debe ser métricamente más débil que la nota que la precede. Si después de saltar una tercera, la melodía se mueve un tono en la dirección opuesta (rellenando así la nota que se saltó) la disonancia recibe una etiqueta `K` o `k` para la cambiata de forma larga. Si este cambio de dirección no se produce, se utiliza una etiqueta `C` o `c`.

{% include verovio.html
	humdrum-visible="false"
	source="camb_dn"
	scale="50"
	pageWidth="1400"
	tabsize="10"
	spacingLinear="0.15"
	spacingNonLinear="0.50"
%}
<script type="application/x-humdrum" id="camb_dn">
**kern	**kern
*clefF4	*clefG2
*M3/2	*M3/2
2G	2.g
2E	.
.	4f
2G	2d
=2	=2
2G	2.g
2E	.
.	4f
2G	4d
.	4e
=	=
*-	*-
!!!filter: dissonant
</script>
Al igual que con la mayoría de las otras etiquetas de disonancia (con la excepción de las etiquetas de suspensión y agente), una letra minúscula significa que fue abordada por el paso hacia abajo, como en el ejemplo anterior, y una letra mayúscula significa que la disonancia fue abordada por grado comjunto ascendente, como en el ejemplo siguiente. 

{% include verovio.html
	humdrum-visible="false"
	source="camb_up"
	scale="50"
	pageWidth="1300"
	tabsize="10"
	spacingLinear="0.10"
	spacingNonLinear="0.45"
%}
<script type="application/x-humdrum" id="camb_up">
**kern	**kern
*k[b-]	*k[b-]
*M4/2	*M4/2
2B-	2.d
2F	.
.	4e
2B-	2g
2C	2a
=2	=2
2B-	2.d
2F	.
.	4e
2B-	2g
2A	2f
=	=
*-	*-
!!!filter: dissonant
</script>



###  Anticipaciones (A, a) ###
Como se demuestra en el ejemplo siguiente, las anticipaciones que se aproximan por grado cojunto ascendente se etiquetan con `A`; de lo contrario, se etiquetan con `a` cuando se aproximan con por grado conjunto descendete, y luego se repiten en su lugar. Una anticipación es métricamente más débil que las notas que la preceden y la siguen.

{% include verovio.html
	humdrum-visible="false"
	source="ant"
	scale="50"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="ant">
**kern	**kern
*clefG2	*clefG2
*M4/2	*M4/2
4g	2ee
4f	.
1f	4dd
.	4cc
.	4dd
.	4ee
2e	2ee
=	=
*-	*-
!!!filter: dissonant
</script>



###  Cambiatas inversas (I, i) ###
Una nota cambiata "inversa" es una disonancia débil abordada por salto y resuelta por grado conjunto en la misma dirección.  Se etiqueta con una `I` o una `i` para sus versiones ascendente y descendente respectivamente. Éstas son relativamente raras en el Renacimiento. Este ejemplo de la [Missa Fors seulement] de Gloria Ockeghem (http://josquin.stanford.edu/work/?id=Ock1007) incluye una boardadura anterior inferior incompleta, etiquetada con una `i`.


{% include verovio.html
	humdrum-visible="false"
	source="rnc"
	scale="50"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="rnc">
**kern	**kern
*clefF4	*clefGv2
*k[]	*k[]
*M3/1	*M3/1
*met(O)	*met(O)
=8-	=8-
2.D	1A
4BB	.
1AA	1A
.	.
1F	1A
.	.
.	.
=	=
*-	*-
!!!filter: dissonant
</script>



###  Escapadas inversas (J, j) ###
La escapada "inversa" es una disonancia débil que se aproxima por salto y luego se resuelve por grado conjunto en la dirección opuesta. Se denomina `J` cuando ese salto inicial es hacia arriba, y `j` cuando es hacia abajo, de forma similar a las bordaduras. Esto ocurre a menudo como adorno de una suspensión. Aunque sólo se etiquetan las suspensiones disonantes, las consonantes también reciben este mismo tipo de ornamentación. El ejemplo siguiente, tomado del Sanctus de la [Missa Sub tuum presidium](http://josquin.stanford.edu/work/?id=Jos0405), contiene dos escapadas inversas paralelas, una que adorna una suspensión consonante en el Altus, y la otra que ornamenta una suspensión consonante (no etiquetada) en el Superius.

{% include verovio.html
	humdrum-visible="false"
	source="reve"
	scale="50"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="reve">
**kern	**kern	**kern	**kern
*I"Bassus	*I"Tenor	*I"Altus	*I"Superius
*clefF4	*clefGv2	*clefGv2	*clefG2
*k[]	*k[]	*k[]	*k[]
*M3/1	*M3/1	*M3/1	*M3/1
*met(O)	*met(O)	*met(O)	*met(O)
=166	=166	=166	=166
1AA	1A	2c	2r
.	.	2.A	2.cc
1r	1E	.	.
.	.	4F	4a
.	.	2G/	4b
.	.	.	4e
1r	2r	1A	2e
.	[2c	.	[2a
=	=	=	=
*-	*-	*-	*-
!!!filter: dissonant
</script>



###  Suspensiones (S, s, G, g) ###
Una suspensión consiste en una voz que se convierte en disonante, ya sea sosteniendo o volviendo a tocar una nota, antes de resolver la disonancia por grados conjuntos. Esta voz sostenida fue denominada por Artusi como "paciente", y recibe una etiqueta "S" o "s" en el momento de la disonancia. Otra voz ataca una nota que es disonante contra la nota suspendida, y esta voz recibe una etiqueta `G` o `g` de *agente*. Es común tener más de un agente por suspensión como en m.&nbsp;37 en el ejemplo de abajo. 

{% include verovio.html
	humdrum-visible="false"
	source="sus"
	scale="50"
	spacingLinear="0.05"
	spacingNonLinear="0.30"
	pageWidth="1400"
	tabsize="10"
	url="http://verovio.humdrum.org/?k=ey&filter=dissonant&file=jrp:Obr2018"
%}
<script type="application/x-humdrum" id="sus">
**kern	**kern	**kern	**kern
*clefF4	*clefGv2	*clefGv2	*clefG2
*k[]	*k[]	*k[]	*k[]
*M3/1	*M3/1	*M3/1	*M3/1
*met(O)	*met(O)	*met(O)	*met(O)
=34-	=34-	=34-	=34-
1AA	0.r	1e	2c
.	.	.	2cc
2BB	.	2d	2b
2C	.	2c	1a
2D	.	1B	.
2E	.	.	2g#i
=35	=35	=35	=35
1AA	0.E	1A	1a
1r	.	1B	1g
1AA	.	[1c	2a
.	.	.	4g
.	.	.	4f
=36	=36	=36	=36
1C	1E	1c]	1e
1D	1F	1A	1d
1GG	[1G	1B	2e
.	.	.	[2g
=37	=37	=37	=37
1C	1G]	1c	2g]
.	.	.	1e
0D	0F	0A	.
.	.	.	4d
.	.	.	4c
.	.	.	1d
=38	=38	=38	=38
2GG	0.E	2B	1e
2.AA	.	2.c	.
.	.	.	2r
4GG	.	4B	.
2.C	.	2.e	1g
4BB	.	4d	.
2GG	.	2B	2e
=	=	=	=
*-	*-	*-	*-
!!!filter: dissonant
</script>
Este ejemplo, tomado del motete de Obrecht [Mille quingentis](http://josquin.stanford.edu/work/?id=Obr2018), presenta una suspensión binaria y otra ternaria. La primera suspensión (en el m.&nbsp;34) es binaria, porque la fase de disonancia de la suspensión dura una unidad de tiempo (en este caso una mínima, o blanca) que se agrupa de dos en dos en la mensuración dada. La segunda suspensión anterior (en el m.&nbsp;37), su fase disonante dura un semibreve, o redonda, (cuando se prescinde de la ornamentación) por lo que esta suspensión es ternaria y recibe las etiquetas `S` y `G` en mayúsculas. Si prefieres no distinguir entre suspensiones binarias y ternarias, utiliza la opción `-u` y todas las suspensiones y agentes serán etiquetados con letras mayúsculas.

Las suspensiones consonantes son ignoradas por la herramienta dissonant.



### Suspensión rearticulada (r) ###
El tipo de suspensión más común en el Renacimiento consiste en saltar hacia abajo una tercera de la disonancia suspendida antes de resolver ambas disonancias por grado conjunto hacia arriba. Este tipo de ornamentación entra en la categoría más amplia de las escapadas inversas (véase más arriba). Otro tipo de ornamentación consiste en una simple rearticulación de la nota suspendida antes de resolverla con un grado conjunto hacia abajo. La nota rearticuladaa es generalmente un semínima (negra) y se etiqueta en los análisis con una `r`. Aunque esta figuración (mostrada a continuación) se da en la música tonal, casi no se da en toda la base de datos de partituras [JRP](http://josquin.stanford.edu). Esto demuestra que el análisis de la disonancia puede utilizarse para estudiar el cambio de estilo a lo largo del tiempo.

{% include verovio.html
	humdrum-visible="false"
	source="rsus"
	scale="50"
	spacingLinear="0.1"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="rsus">
**kern	**kern
*clefGv2	*clefG2
*M4/2	*M4/2
2e	2g
2d	2.f
1c	.
.	4f
.	2e
=	=
1d	2f
.	2r
2e	1cc
2f	.
=	=
*-	*-
!!!filter: dissonant
</script>



###  Suspensiones falsas (F, f) ###
A veces, la preparación de una suspensión es en sí misma disonante, como en el siguiente ejemplo del Kyrie de la [Missa Da pacem](http://josquin.stanford.edu/work/?id=Mou1020a) de Mouton. A menudo se denomina *suspensión falsa*, aunque sería más preciso llamarla una preparación falsa de una suspensión normal. Suele abordarse mediante un grado conjunto hacia arriba o hacia abajo y permanece en su lugar o se vuelve a tocar para convertirse en la parte disonante de una suspensión. Como sabemos que la suspensión se resolverá por grado conjunto hacia abajo, utilizamos una "F" mayúscula o una "f" minúscula para transmitir si la disonancia se abordó por salto o por grado conjunto respectivaamente. Como esto ocurre sobre un pedal, y también se necesita un agente para la suspensión, esto se encuentra generalmente sólo en tres o más voces, aunque podría ocurrir en dos voces si la nota del pedal fuera rearticulado en el momento en que sirve como agente de la suspensión.

{% include verovio.html
	humdrum-visible="false"
	source="fsus"
	scale="50"
	spacingLinear="1.75"
	spacingNonLinear="0.8"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="fsus">
**kern	**kern	**kern	**kern
*I'B	*I'T	*I'A	*I'S
*clefF4	*clefGv2	*clefGv2	*clefG2
*k[b-]	*k[b-]	*k[b-]	*k[b-]
*M2/1	*M2/1	*M2/1	*M2/1
=26	=26	=26	=26
2D	0A	4d]	2f
.	.	4c	.
2C	.	2e-i	1g
1D	.	[1d	.
.	.	.	2f#i
=27	=27	=27	=27
1GG	0G	2d]	0g
.	.	2.B-	.
1r	.	.	.
.	.	4c	.
.	.	2d	.
=	=	=	=
*-	*-	*-	*-
!!!filter: dissonant
</script>
En ocasiones, una suspensión falsa va precedida de una anticipación y éstas también se detectan, como en el ejemplo siguiente tomado del mismo Mouton Kyrie.

{% include verovio.html
	humdrum-visible="false"
	source="afsus"
	scale="50"
	spacingLinear="0.35"
	spacingNonLinear="0.7"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="afsus">
**kern	**kern	**kern	**kern
*I'B	*I'T	*I'A	*I'S
*clefF4	*clefGv2	*clefGv2	*clefG2
*k[b-]	*k[b-]	*k[b-]	*k[b-]
*M3/1	*M3/1	*M3/1	*M3/1
=9	=9	=9	=9
1C	0.c	1r	4a
.	.	.	4b-
.	.	.	2.cc
1E	.	1g	.
.	.	.	4b-
.	.	.	1b-
1F	.	2.f	.
.	.	.	2a
.	.	4e	.
=10	=10	=10	=10
2.G	0B-	4d	1b-
.	.	4c	.
.	.	2B-	.
4F	.	.	.
2D	.	2F	2r
2.E-i	.	2G	2.g
.	1r	1B-	.
4D	.	.	4f
2BB-	.	.	2d
=	=	=	=
*-	*-	*-	*-
!!!filter: dissonant
</script>

En ocasiones, una falsa suspensión va precedida de una anticipación, como en el ejemplo anterior tomado del mismo Kyrie de Mouton. En este caso, la etiqueta de la falsa suspensión toma el mismo caso que el de la anticipación.


###  Suspensiones con agentes ausentes (M, m) ###
En algunos casos, parece que falta un agente de ataque en la suspensión.  Esta figura consiste en una voz que se desplaza hacia arriba o hacia abajo por un grado conjunto, luego se sostiene en el siguiente tiempo y luego se resuelve hacia abajo por un grado conjunto, todo sobre un pedal. Esta disonancia se denomina "M" o "m" según que la nota disonante se acerque por salto o por grado conjunto respectivamente. El ejemplo siguiente está tomado del motete de Obrecht [Factor Orbis](http://josquin.stanford.edu/work/?id=Obr2010).


{% include verovio.html
	humdrum-visible="false"
	source="msus"
	scale="50"
	spacingLinear="1.75"
	spacingNonLinear="0.8"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="msus">
**kern	**kern	**kern	**kern
*clefF4	*clefGv2	*clefGv2	*clefG2
*k[]	*k[]	*k[]	*k[]
*M3/1	*M3/1	*M3/1	*M3/1
*met(O)	*met(O)	*met(O)	*met(O)
=59-	=59-	=59-	=59-
1F	1A	1d	2a]
.	.	.	4g
.	.	.	4f
0E	0B	0e	2g
.	.	.	1a
.	.	.	2g#i
=60	=60	=60	=60
1AA	1A	1e	1a
2r	2r	2r	1r
2AA	2A	2e	.
2AA	2A	2e	1r
2AA	2A	2e	.
=	=	=	=
*-	*-	*-	*-
!!!filter: dissonant
</script>



### Chanson idiom (h) ###
Un modismo de chanson funciona como una anticipación ornamentada al agente de una suspensión y se etiqueta con una "h". Suele producirse en la colocación de una mínima débil, (blanca) y consiste en una negra que es disonante frente a la preparación a la suspensión y se aproxima por grado conjunto hacia abajo.  Esta disonancia también se deja por grado conjunto hacia abajo a otra negra que luego es seguida por el agente de la suspensión un grado conjunto hacia arriba (en el mismo tono que el modismo de la chanson).  El ejemplo siguiente está tomado de las partes de contra y tenor de la chanson [Cela sans plus](http://josquin.stanford.edu/work/?id=Jos2704) atribuida a Josquin des Prez:

{% include verovio.html
	humdrum-visible="false"
	source="chi"
	url="http://verovio.humdrum.org/?k=ey&filter=dissonant&file=jrp:Jos2704"
	scale="50"
	linearSpacing="0.1"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="chi">
**kern	**kern
*clefG2	*clefG2
*clefGv2	*clefGv2
*k[]	*k[]
*M2/1	*M2/1
*met(C|)	*met(C|)
=35-	=35-
2d	2B
1g	4A
.	4G
.	1A
2f#i	.
=36	=36
1g	1G
1f	2r
.	[2d
=	=
*-	*-
!!!filter: dissonant
</script>



### Nota de paso disonante en la tercera negra ###
Una tercera nota de paso, una nota de paso normal. Corresponde a una disonancia en la posición métrica de una mínima débil que dura sólo una negra. Se aproxima y se deja por grado conjunto en la misma dirección y debe ser precedido por una nota con una duración de al menos una mínima (blanca). Si desciende, recibe la etiqueta `q` como en el siguiente ejemplo.

Una nota de paso disonante de la tercera negra, etiquetado como "q" en el ejemplo siguiente, es similar a una nota de paso descendente. Corresponde a una disonancia en la posición métrica de una mínima débil que dura sólo una negra. Se aproxima y se deja por un graado conjunto hacia abajo y debe ser precedido por una nota con una duración de al menos una mínima (blanca).  No existe una forma ascendente para este tipo de disonancia.

{% include verovio.html
	humdrum-visible="false"
	source="d3qpd"
	scale="50"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="d3qpd">
**kern	**kern
*clefG2	*clefG2
*M2/1	*M2/1
2f	1.a
2e	.
1d	.
.	4g
.	4f
=	=
*-	*-
!!!filter: dissonant
</script>
Aunque es menos común, cuando la misma figura ocurre en su forma ascendente, se etiqueta con una "Q" como en el siguiente ejemplo tomado del Superius y el Altus del Credo en la [Missa De beata virgine](http://josquin.stanford.edu/work/?id=Jos0303c) de Josquin .

{% include verovio.html
	humdrum-visible="false"
	source="d3qpu"
	scale="50"
	spacingLinear="1.75"
	spacingNonLinear="0.8"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="d3qpu">
**kern	**kern
*clefGv2	*clefG2
*k[]	*k[]
*M2/1	*M2/1
*met(C|)	*met(C|)
=113-	=113-
1r	1.g
1G	.
.	4a
.	4b
=114	=114
1E	1cc
[1A	1cc
=	=
*-	*-
!!!filter: dissonant
</script>


### Bordaduraa disonante de la tercera negra (B, b) ###
Esta disonancia es la versión de bordadura de la tercera nota de paso disonante. El ejemplo siguiente está tomado de las partes de altus y bassus del Credo de la [Missa La belle se siet](http://josquin.stanford.edu/work/?id=Jos1303c) (NJE&nbsp;13.3).

El tipo de disonancia consiste en una bordadura en la posición métrica de una mínima débil (blanca) que dura sólo una negra. Aunque detectamos variedades de este tipo de disonancia tanto en la bordadura superior como en el inferior, al igual que las bordaduras normales, la bordaduras inferior disonante de la tercera negra es mucho más común que la versión de la bordadura superior. Las versiones de la bordaduras superior e inferior de este tipo de disonancia se etiquetan con una "B" y una "b" respectivamente.

{% include verovio.html
	humdrum-visible="false"
	source="d3qn"
	scale="50"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="d3qn">
**kern	**kern
*I'B	*I'A
*clefF4	*clefGv2
*k[b-]	*k[b-]
*M3/1	*M3/1
*met(C|3)	*met(C|3)
=183-	=183-
1C	1G
1C	1.G
1C	.
.	4F
.	4G
=	=
*-	*-
!!!filter: dissonant
</script>



### Apoyatursa (T, t) ###
Una apoyatura es una disonancia relativamente acentuada con respecto a las notas que la preceden y la siguen. Se aborda mediante un salto y se resuelve hacia abajo por grado conjunto. Se etiqueta con una `T` cuando el salto es ascendente y `t` cuando el salto es descendente. Esta etiqueta sólo se asigna si se cumplen los requisitos y la nota sería inexplicable de otro modo. Este extracto del Sanctus de la [Missa Hercules dux Ferrarie](http://josquin.stanford.edu/work/?id=Jos1101) de Josquin presenta una apoyatura abordada desde abajo.

{% include verovio.html
	humdrum-visible="false"
	source="appgg"
	scale="50"
	pageWidth="1200"
	tabsize="10"
%}
<script type="application/x-humdrum" id="appgg">
**kern	**kern
*I"T	*I"A
*clefGv2	*clefGv2
*k[]	*k[]
*M2/1	*M2/1
*met(C|)	*met(C|)
=89||	=89||
0D	2.d
.	4e
.	2f
.	2d
=90	=90
0C	2f
.	1e
.	4d
.	4c
=91	=91
0D	2B
.	2A
.	2B
.	[2A
=	=
*-	*-
!!!filter: dissonant
</script>



### Notas de paso acentuadas (V, v) ###
Las notas de paso acentuados son métricamente fuertes con respecto a las notas que les preceden y les siguen, y no duran más que la nota siguiente. Se acercan y se van por grados conjuntos en la misma dirección y se etiquetan como `V` cuando esos grados conjuntos son ascendentes, y `v` cuando esos grados conjuntos son descendentes. Se detectarán incluso si están decoradas con una anticipación inmediatamente anterior. Esta definición de disonancia podría corresponder a las notas de paso disonantes de la tercera negra, y también al tipo de disonancia del modismo de chanson. Una nota de paso acentuado sólo se etiquetará como tal si no cumple los requisitos más estrictos para cualquier otro tipo de disonancia. En el Sanctus de la [Missa Cum iocunditate](http://josquin.stanford.edu/work/?id=Jos0304) atribuido a Josquin, las notas de paso acentuadas se encuentran en ciertas disposiciones contrapuntísticas en las que un motivo primario se contrapone a sí mismo en múltiples voces, como en el fragmento siguiente.
s
{% include verovio.html
	humdrum-visible="false"
	source="accp"
	scale="50"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="accp">
**kern	**kern	**kern	**kern
*I"B	*I"T	*I"A	*I"S
*clefF4	*clefGv2	*clefGv2	*clefG2
*k[]	*k[]	*k[]	*k[]
*M2/1	*M2/1	*M2/1	*M2/1
*met(C|)	*met(C|)	*met(C|)	*met(C|)
=138	=138	=138	=138
2r	0r	0A	2c
1D	.	.	2.A
.	.	.	4B
2D	.	.	4c
.	.	.	4d
=139	=139	=139	=139
2C	0r	2r	2e
2.AA	.	1c	2f
.	.	.	2.e
4BB	.	.	.
4C	.	2c	.
4D	.	.	4f
=	=	=	=
*-	*-	*-	*-
!!!filter: dissonant
</script>



### Bordaduras acentuadas (W, w) ###
Las bordaduras acentuados son métricamente fuertes con respecto a las notas anteriores y posteriores, y no duran más que la nota siguiente. Se acercan y se van por paso en direcciones opuestas y se etiquetan como `W` cuando se acercan por grado conjunto hacia arriba, y `w` cuando se acercan por grado conjunto hacia abajo. Se detectarán incluso si están decoradas con una anticipación inmediatamente anterior. Esta definición de disonancia también coincide con la de las bordaduras disonantes de la tercera negra, y potencialmente con los tipos `L` y `Y`. Una bordaduras acentuada sólo se etiquetará como tal si no cumple los requisitos más estrictos para cualquier otro tipo de disonancia. El siguiente fragmento, tomado del motete [Benedicite, omnia opera](http://josquin.stanford.edu/work/?id=Jos1402) atribuido a Josquin, contiene un vecino superior acentuado en el Altus.



{% include verovio.html
	humdrum-visible="false"
	source="accn"
	scale="50"
	pageWidth="1250"
	tabsize="10"
%}
<script type="application/x-humdrum" id="accn">
**kern	**kern	**kern	**kern
*clefF4	*clefGv2	*clefGv2	*clefG2
*k[b-]	*k[b-]	*k[b-]	*k[b-]
*M2/1	*M2/1	*M2/1	*M2/1
*met(C|)	*met(C|)	*met(C|)	*met(C|)
=78	=78	=78	=78
1G	2d	2r	2b-
.	2d	1g	2b-
1C	[1c	.	[1cc
.	.	2e	.
=79	=79	=79	=79
2r	1c]	2f	1cc]
1c	.	2e	.
.	2r	1c	1r
2A	[2c	.	.
=	=	=	=
*-	*-	*-	*-
!!!filter: dissonant
</script>



### Resolución contra la disonancia de la suspensión (X, x) ###
Cuando una voz suena la nota de resolución de una suspensión en una línea descendente contra la parte disonante de la suspensión en otra voz, se etiqueta con una `x`. No existe una forma ascendente de esta disonancia, por lo que sólo se utiliza una "X" mayúscula si se invoca el ajuste -u. Esta disonancia sólo se produce necesariamente cuando hay tres o más voces, ya que además de la propia disonancia, otras dos voces deben formar una suspensión. Sin embargo, a menudo se produce en texturas aún más gruesas, como el fragmento siguiente, tomado del motete [Victime paschali laudes](http://josquin.stanford.edu/work/?id=Jos2207) de Brunet.


{% include verovio.html
	humdrum-visible="false"
	source="resx"
	scale="50"
	pageWidth="1150"
	tabsize="10"
%}
<script type="application/x-humdrum" id="resx">
**kern	**kern	**kern	**kern	**kern	**kern
*staff6	*staff5	*staff4	*staff3	*staff2	*staff1
*Ivox	*Ivox	*Ivox	*Ivox	*Ivox	*Ivox
*I'B2	*I'B1	*I'T	*I'A2	*I'A1	*I'S
*clefF4	*clefF4	*clefGv2	*clefGv2	*clefGv2	*clefG2
*k[b-]	*k[b-]	*k[b-]	*k[b-]	*k[b-]	*k[b-]
*M2/1	*M2/1	*M2/1	*M2/1	*M2/1	*M2/1
*met(C|)	*met(C|)	*met(C|)	*met(C|)	*met(C|)	*met(C|)
=189	=189	=189	=189	=189	=189
2G	1E	4d]	2g	2B-	4a]
.	.	4B-	.	.	4g
2C	.	2c	2e	2G	1g
2.F	1D	1d	4f	1A	.
.	.	.	4e	.	.
.	.	.	4d	.	2f#i
4E	.	.	4c	.	.
=190	=190	=190	=190	=190	=190
2D	2GG	0d	1B-	[0Gl	[0gl
2.G	1G	.	.	.	.
.	.	.	2r	.	.
4F	.	.	.	.	.
4E-i	2F	.	2B-	.	.
4D	.	.	.	.	.
*-	*-	*-	*-	*-	*-
!!!filter: dissonant
</script>



### Acompañamiento paralelo (L, l) ###
Si una disonancia no corresponde a ninguna categoría identificable (y normalmente recibiría una etiqueta `Z`), y se desplaza en movimiento paralelo por otra voz que es una disonancia identificable, a este acompañamiento paralelo se le da una `L` si se aproxima por grado cojunto hacia arriba, o una `l` si se aproxima por grado conjunto hacia abajo. Este tipo de disonancia se produce a menudo en combinación con un modismo de chanson, como en el siguiente ejemplo tomado de [Cela sans plus](http://verovio.humdrum.org/?k=ey&filter=dissonant&file=jrp:Jos2704) de Lannoy.  Aunque las voces se siguen analizando por parejas, dado que este tipo de disonancia requiere que una segunda voz esté en una condición de disonancia identificable con una tercera voz, este tipo sólo se identifica en piezas con tres o más voces.

{% include verovio.html
	humdrum-visible="false"
	source="para"
	scale="50"
	pageWidth="1300"
	tabsize="10"
%}
<script type="application/x-humdrum" id="para">
**kern	**kern	**kern
*clefGv2	*clefGv2	*clefG2
*k[]	*k[]	*k[]
*M2/1	*M2/1	*M2/1
*met(C|)	*met(C|)	*met(C|)
=20-	=20-	=20-
1G	1.g	2ee
.	.	2.dd
1B	.	.
.	.	4cc
.	2f	4b
.	.	4a
=21	=21	=21
2c	2e	2g
4B	4d	1cc
4A	4c	.
1G	1d	.
.	.	2b
=22	=22	=22
1r	0c	0cc
1g	.	.
=	=	=
*-	*-	*-
!!!filter: dissonant
</script>



### Sólo contra la disonancia conocida (Y, y) ###
Cuando una nota sólo es disonante frente a los tipos de disonancia conocidos, recibe una etiqueta `Y` o `y` dependiendo de si se aborda desde abajo o desde arriba respectivamente. Este tipo de escenario se da a menudo en texturas más gruesas, como en el ejemplo de abajo con una "Y" y una "y" tomadas del Sanctus de la [Missa Pro defunctus](http://josquin.stanford.edu/work/?id=Jos0404) atribuida a Josquin.



{% include verovio.html
	humdrum-visible="false"
	source="only"
	scale="50"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="only">
**kern	**kern	**kern	**kern	**kern	**kern
*clefF4	*clefGv2	*clefGv2	*clefGv2	*clefGv2	*clefG2
*k[b-]	*k[b-]	*k[b-]	*k[b-]	*k[b-]	*k[b-]
*M2/1	*M2/1	*M2/1	*M2/1	*M2/1	*M2/1
*met(C|)	*met(C|)	*met(C|)	*met(C|)	*met(C|)	*met(C|)
=29-	=29-	=29-	=29-	=29-	=29-
1D	0F	1.d	4A	1A	2f
.	.	.	4G	.	.
.	.	.	4F	.	4g
.	.	.	4E	.	4a
1BB-	.	.	1D	1r	1b-
.	.	2d	.	.	.
=	=	=	=	=	=
*-	*-	*-	*-	*-	*-
!!!filter: dissonant
</script>



### Disonancias desconocidas (Z, z) ###
Las disonancias que no pueden asignarse a una de las categorías anteriores reciben una etiqueta "Z" para indicar que su función es desconocida.  Una "Z" mayúscula significa que el intervalo de la disonancia es una 2ª o una 7ª.  Una "z" minúscula significa que la disonancia es una 4ª contra la nota más grave de la sonoridad. En el ejemplo siguiente, tomado del Sanctus de la [Missa Hercules dux Ferrarie](http://josquin.stanford.edu/work/?id=Jos1101) de Josquin , lo que a primera vista parece ser una suspensión en el Altus no se resuelve correctamente, lo que hace que las voces del Bassus y del Superius reciban las etiquetas `Z` y `z` respectivamente.  

{% include verovio.html
	humdrum-visible="false"
	source="Zandz"
	scale="50"
	pageWidth="1600"
	tabsize="10"
%}
<script type="application/x-humdrum" id="Zandz">
**kern	**kern	**kern	**kern
*I"B	*I"T	*I"A	*I"S
*clefF4	*clefGv2	*clefGv2	*clefG2
*k[]	*k[]	*k[]	*k[]
*M2/1	*M2/1	*M2/1	*M2/1
*met(C|)	*met(C|)	*met(C|)	*met(C|)
=64	=64	=64	=64
2C	1E	4B-]	2e
.	.	4A	.
2AA	.	2.A	2c
1BB-i	1D	.	2d
.	.	4D	.
.	.	2d	[2f
=65	=65	=65	=65
1AA	0r	2.c	4f]
.	.	.	4e
.	.	.	2a
.	.	4A	.
1r	.	4c	2g
.	.	4B	.
.	.	[2e	2cc
=	=	=	=
*-	*-	*-	*-
!!!filter: dissonant
</script>



## Filtrado de URL de los repertorios ##
La herramienta dissonant puede utilizarse con los repertorios de VHV disponibles añadiendo el filtro a la URL de las obras, como con el proyecto Tasso in Music:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[http://verovio.humdrum.org/?k=ey&file=tmp&filter=dissonant](http://verovio.humdrum.org/?k=ey&file=tmp&filter=dissonant)

Para eliminar el texto lírico de los resultados del análisis, utiliza el filtro: `extract -i kern | dissonant`:


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[http://verovio.humdrum.org/?k=ey&file=tmp&filter=extract%20-ikern%7cdissonant](http://verovio.humdrum.org/?k=ey&file=tmp&filter=extract%20-ikern%7cdissonant)

El filtro `extract -i kern` extrae sólo las columnas `**kern` y filtra las columnas que no son kern.


{% include image.html
	file="textless.png"
	alt="removing lyric text before displaying analysis."
	max-width="90%"
	url="http://verovio.humdrum.org/?k=ey&file=tmp&filter=extract%20-ikern%7cdissonant"
	caption="<i>Dissonant</i> analysis after removing lyric text (click for live demo)."
%}

## Herramienta dissonant en JRP ##

<style>

.jrp-button {
	background: #c86843;
	color: white;
	font-size: 90%;
	display: inline-block;
	border: none;
	text-align: center;
	padding: 1px 3px;
}

</style>

Las páginas de las obras en el sitio web del Josquin Research Project tienen enlaces para la obra dada para ver el análisis del etiquetado disonante en VHV. Por ejemplo, la página


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[http://josquin.stanford.edu/work/?id=Jos2801](http://josquin.stanford.edu/work/?id=Jos2801)

contiene un botón denominado <span class="jrp-button">Dissonant</span> en la parte inferior izquierda de la página.  Al hacer clic en ese botón se cargará la partitura de la página actual en VHV y se hará un análisis en línea de las etiquetas disonantes:


{% include image.html
	file="jrp-dissonant.png"
	alt="dissonant button on JRP workpage."
	max-width="60%"
	url="http://josquin.stanford.edu/work/?id=Jos2801"
	caption="<i>Dissonant</i> analysis button on JRP work pages."
%}

### Resumen de dissonant ###

Éstas son más útiles para la versión de línea de comandos de la herramienta, pero pueden verse en VHV escribiendo command-c cuando se utiliza la opción. 

La opción `-c` muestra un recuento de los diferentes tipos de disonancias y del total de disonancias dentro de una obra:


``` bash
humcat jrp://Jos2721 | dissonant -c
```
```
**dis	**sum	**v1	**v2	**v3
P	31	17	6	8
p	13	9	1	3
N	2	0	0	2
n	21	5	3	13
E	1	0	0	1
e	1	0	1	0
Q	1	0	1	0
s	6	1	2	3
G	11	5	4	2
h	1	0	0	1
Z2	1	1	0	0
Z7	1	0	0	1
*-	*-	*-	*-	*-
!!total_dissonances:	90
```

La opción `-u` también puede utilizarse con la opción `-c` para contar las disonancias sin subagruparlas por dirección:

``` bash
humcat jrp://Jos2721 | dissonant -cu
```
```
**disu	**sum	**v1	**v2	**v3
P	44	26	7	11
N	23	5	3	15
E	2	0	1	1
Q	1	0	1	0
S	6	1	2	3
G	11	5	4	2
H	1	0	0	1
Z	2	1	0	1
*-	*-	*-	*-	*-
!!total_dissonances:	90
```
En este caso, el primer tipo de datos de la columna se etiqueta como `**disu` para indicar las direcciones indiferenciadas de cada categoría.


### Referencias ###

Antila, Christopher, Alexander Morgan, et al. VIS Framework (version 3.0.3). Python. Montreal: McGill University, 2016.

Bent, Margaret. “Grammar of Early Music: Preconditions for Analysis.” In Tonal Structures in Early Music, edited by Cristle Collins Judd, 15-59. London: Garland Publishing, 1998.

Burmeister, Joachim. Musical Poetics. Translation by Benito Rivera. New Haven: Yale University Press, 1993. Originally published 1606.

Cohen, David. “Metaphysics, Ideology, Discipline: Consonance, Dissonance, and the Foundations of Western Polyphony.” Theoria 7: 1–86.

DeFord, Ruth. Tactus Mensuration, and Rhythm in Renaissance Music. Cambridge: Cambridge University Press, 2015.

Fuller, Sarah. “Contrapunctus Theory, Dissonance Regulation, and French Polyphony of the Fourteenth Century.” In Medieval Music in Practice: Studies in Honor of Richard Crocker, edited by Judith Peraino, 113–52. Middleton, Wisconsin: American Institute of Musicology, 2013.

———. “Organum – discantus – contrapunctus in the Middle Ages.” In The Cambridge History of Western Music Theory, edited by Thomas Christensen, 477–502. Cambridge: Cambridge University Press, 2002.

Jeppesen, Knud. Counterpoint: The Polyphonic Vocal Style of the Sixteenth Century. Translated by Glen Haydon. New York: Dover Publications, 1992 (original Danish edition published by Wilhelm Hansen, in Copenhagen, 1931).

Melin, William Eugene. “The Music of Johannes Tinctoris: A Comparative Study of Theory and Practice.” PhD diss., Ohio State University, 1973.

Moll, Kevin. Counterpoint and Compositional Process in the Time of Dufay: Perspectives from German Musicology. Edited and translated by Kevin Moll. New York: Garland Publishing Inc., 1997.

Morgan, Alexander. "[Renaissance Interval-Succession Theory: Treatises and Analysis](http://digitool.library.mcgill.ca/R/DPIVYXI71HL5ILGG61U4D2N5YR6UMUAASGK4S4JC42B2BFPGCD-00398?func=results-jump-full&set_entry=000001&set_number=001123&base=GEN01)." PhD diss., McGill University, 2017.

Morris, R. O. Contrapuntal Technique. Oxford: Oxford University Press, 1922.

Patrick, P. H. & Strickler, K. (1978) "A Computer-Assisted Study of Dissonance in the Masses of Josquin Desprez." Computers and the Humanities. 12 (4), 341&ndash;364.

Pontio, Pietro. Ragionamento di musica. Compiled by Suzanne Clercx. Kassel: Bärenreiter, 1959. Originally published Parma: 1588.

———. [Ragionamento di musica](http://www.ums3323.paris-sorbonne.fr/TREMIR/TReMiR_Pontio/R0_start.htm). Electronic version published by Dupraz, Christophe. Traités Musicaux Romans, 2013. Accessed August 14, 2016.

Rothfarb, Lee. “Tinctoris vs. Tinctoris: Theory and Practice of Dissonance in Counterpoint.” In Theory Only 9.2–3 (1986): 3–31.

Sachs, Klaus-Jürgen. "[Counterpoint](http://www.oxfordmusiconline.com/subscriber/article/grove/music/06690)."  Grove Music Online. (accessed July 12, 2016).

———. Der Contrapunctus im 14. und 15. Jahrhundert: Untersuchungen zum Terminus, zur Lehre und zu den Quellen. Wiesbaden: Steiner, 1974.

Schubert, Peter. Modal Counterpoint, Renaissance Style, 2nd ed. New York: Oxford University Press, 2008.

Siegler, Andie, and Jon Wild. “Schematizing the Treatment of Dissonance in 16th-century Counterpoint.” In Proceedings of the International Society for Music Information Retrieval (2015): 645–650.

Tinctoris, Johannes. Liber de arte contrapuncti. In Johannes Tinctoris Opera Theoretica. Compiled by Albert Seay. n.p.: American Institute of Musicology, 1975. Originally written 1477.

———. Liber de arte contrapuncti. Translated by Albert Seay. Rome: American Institute of Musicology, 1961. Originally written c. 1477.

———. [Liber de arte contrapuncti](http://earlymusictheory.org/Tinctoris/texts/deartecontrapuncti/). Translated by Jeffrey Dean. Last accessed November 16, 2015. Originally written 1477.

Trachier, Olivier. Contrepoint du XVIe siècle. Paris: Durand, 1999.

Vicentino, Nicola. Ancient music adapted to modern practice (L’antica musica ridotta alla moderna prattica). Translated by Maria Rika Maniates and edited by Claude Palisca. New Haven, Yale University Press 1996. Originally published 1555.

Zarlino, Gioseffo. Art of Counterpoint. Translated by Guy Marco and Claude Palisca, edited by Claude Palisca. New Haven and London: Yale University Press, 1968. Originally published: 1558.




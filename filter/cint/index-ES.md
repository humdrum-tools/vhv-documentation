---
title: cint filter
lang: en es
page_language: es
translator: David Rizo
translation_date: 7 Aug 2021
translation_update:
ref: filters-cint
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/cint/index-ES.html
---

El filtro *cint* calcula y procesa la música basándose en los módulos
de contrapunto.  Consulta la [documentación técnica completa de
*cint](http://extras.humdrum.org/man/cint) en el sitio web de Humdrum
Extras para conocer todas las opciones.

Los módulos de contrapunto consisten en cuatro notas en dos voces
simultáneas que forman un módulo de dos intervalos armónicos y dos
melódicos. El nombre del filtro *cint* puede significar tanto
*intervalos de contrapunto* como *intervalos melódicos/armónicos
compuestos*, y funciona como una generalización de las herramientas
[hint](http://www.humdrum.org/man/hint) (intervalos armónicos)y
[mint](http://www.humdrum.org/man/mint) (intervalos melódicos) del
Toolkit Humdrum original.

A continuación se muestra un ejemplo de módulo.  El primer compás
del ejemplo siguiente representa un par de notas que suenan juntas
en dos voces separadas.  Estas cuatro notas comprenden cuatro
intervalos ilustrados en el segundo compás. las marcas rojas indican
los intervalos melódicos, y las marcas azules indican los intervalos
armónicos.

{% include image.html
	file="counterpoint-module.svg"
	alt="Módulo de contrapunto y su descripción."
	max-width="80%"
	caption="Intervalos melódicos y armónicos que forman un módulo de contrapunto."
%}


Dados tres intervalos cualesquiera en el módulo, el cuarto puede
calcularse automáticamente, por lo que el compás tres ilustra la
descripción típica de un módulo que omite el intervalo melódico
superior y se escribiría en línea como "10 -2 12", lo que significa
que el módulo comienza con un intervalo armónico de una décima,
luego la voz inferior baja un segundo y forma un intervalo armónico
de una duodécima con la voz superior (que implícitamente tuvo que
subir un paso para formar la duodécima).

El filtro cint puede describir intervalos en otras unidades como
los doce tonos y la base-40, así como intervalos diatónicos
cromáticamente alterados, y permitir la contracción de la octava
de los intervalos armónicos y las configuraciones de ataque de
notas.


## Módulo de búsqueda ##

### Búsqueda de terceras/décimas paralelas ascendentes ###

He aquí un ejemplo de búsqueda de terceras paralelas en la música
contrapuntística.  El módulo contrapuntístico básico para las
terceras paralelas que suben de paso es "3 2 3".  El filtro utilizado
en el siguiente ejemplo es:


```
!!!filter: cint -O --search "3 2 3"
```

La opción `-O` se utiliza para contraer intervalos compuestos, como
una 10ª a una 3ª, eliminando las transposiciones de octava de los
intervalos básicos.  Haz clic en los ejemplos siguientes para cargar
los mismos datos y filtros en VHV.

{% include image.html
	file="search3-2-3.png"
	alt="Searching for 3-2-3 module."
	url="http://verovio.humdrum.org?file=chorales/chor001.krn&k=ey&filter=cint%20-O%20--search%20%223%202%203%22"
	max-width="80%"
	shadow="false"
	caption="Búsqueda de terceras (o décimas) paralelas en un coral de Bach."
%}


### Búsqueda de terceras paralelas con ataques de notas solamente. ###

Añadir ataques de notas con la opción `-x` permitirá buscar intervalos
armónicos basados en si las notas fueron atacadas (`x)` o sostenidas
(`s`).  La búsqueda de terceras paralelas en las que las notas de
ambas voces atacan juntas sería "3xx 2 3xx":

```
!!!filter: cint -x -O --search "3xx 2 3xx"
```

o al fusionar opciones sin parámetros:

```
!!!filter: cint -xO --search "3xx 2 3xx"
```

{% include image.html
	file="search3xx-2-3xx.png"
	alt="Searching for 3-2-3 module."
	url="http://verovio.humdrum.org?file=chorales/chor001.krn&k=ey&filter=cint%20-xO%20--search%20%223xx%202%203xx%22"
	max-width="80%"
	shadow="false"
	caption="Búsqueda de terceras partes paralelas ascendentes con ataques de notas en un coral de Bach"
%}

Observa que las terceras paralelas en el compás 11 ya no están
resaltadas ya que el movimiento de terceras paralelas se introdujo
con una nota sostenida en una voz.

### Longitud del módulo ###

Se pueden buscar cadenas de módulos más largas añadiendo la opción
`-n #`, donde `#` es el número de módulos omitidos calculado para
la búsqueda.  Por ejemplo, si se utiliza `-n 2` en el filtro cint
sólo coincidirá con dos terceros movimientos paralelos sucesivos
subiendo de paso tres pares de notas en cada voz:

```
!!!filter: cint -xO -n 2 --search "3xx 2 3xx 2 3xx"
```

{% include image.html
	file="search3xx-2-3xx-2-3xx.png"
	alt="Searching for 3-2-3 module."
	url="http://verovio.humdrum.org?file=chorales/chor001.krn&k=ey&filter=cint%20-xOn2%20--search%20%223xx%202%203xx%202%203xx%22"
	max-width="80%"
	shadow="false"
	caption="Búsqueda de terceras paralelas ascendentes de dos módulos con ataques de notas en un coral de Bach"
%}

Obsérvese que hay menos coincidencias, ya que se ignoran los módulos de movimientos paralelos individuales.

{% include warning.html
	content="La búsqueda de una secuencia de módulos más corta cuando se especifica una longitud mayor con la opción -n resaltará toda la secuencia más larga.  Utiliza anclas de expresiones regulares como \"^3xx 2 3xx\" para buscar secuencias de módulos que comiencen con un movimiento escalonado de terceras paralelas hacia arriba seguido de cualquier otro módulo que comience con un intervalo de terceras armónicas cuando la secuencia de módulos sea 2 o superior; o \"3xx 2 3xx$\" para secuencias de módulos que terminen con un movimiento escalonado de terceras paralelas hacia arriba. Para asegurarte de que estás buscando la secuencia de módulos de longitud correcta, utiliza tanto `^` como `$`, como por ejemplo \"^3xx 2 3xx$`; cuando se utiliza -n2, esta búsqueda no devolverá ninguna coincidencia, ya que se trata de una secuencia de módulos de longitud 1."
%}


### Tercios paralelos descendentes ###

Utiliza `-2` como intervalo melódico cuando busque terceras paralelas descendentes:

```
!!!filter: cint -xO -n 2 --search "3xx -2 3xx -2 3xx"
```

{% include image.html
	file="search3xx-n2-3xx-n2-3xx.png"
	alt="Searching for 3xx -2 3xx -2 3xx module."
	url="http://verovio.humdrum.org?file=chorales/chor001.krn&k=ey&filter=cint%20-xOn2%20--search%20%223xx%20-2%203xx%20-2%203xx%22"
	max-width="80%"
	shadow="false"
	caption="Búsqueda de terceras paralelas descendentes de dos módulos"
%}



### Terceras paralelas sin dirección ###

Utiliza `-?2` como intervalo melódico cuando busques terceras paralelas que suban o bajen un tono.


```
!!!filter: cint -xO -n 2 --search "3xx -?2 3xx -?2 3xx"
```

{% include image.html
	file="searchupdown.png"
	alt="Searching for 3xx -?2 3xx -?2 3xx module."
	url="http://verovio.humdrum.org?file=chorales/chor001.krn&k=ey&filter=cint%20-xOn2%20--search%20%223xx%20-%3f2%203xx%20-%3f2%203xx%22"
	max-width="80%"
	shadow="false"
	caption="Búsqueda de terceras paralelas ascendentes o descendentes de dos módulos"
%}


## Suspensiones cadenciales ##


## Referencias ##

Bent, Margaret. “Grammar of Early Music: Preconditions for Analysis.” In Tonal Structures in Early Music, edited by Cristle Collins Judd, 15-59. London: Garland Publishing, 1998.

Burmeister, Joachim. Musical Poetics. Translation by Benito Rivera. New Haven: Yale University Press, 1993. Originally published 1606.

Conklin, Darrell, and Mathieu Bergeron, “Discovery of Contrapuntal Patterns.” In Proceedings of the International Society for Music Information Retrieval (2010): 201–206.

Cumming, Julie. “From Two-Part Framework to Movable Module.” In Medieval Music in Practice: Essays in Honor of Richard Crocker, edited by Judith Peraino, 175–213. Münster: American Institute of Musicology, 2013.

———. “Text-Setting and Imitative Technique.” In The Motet around 1500: On the Relationship of Imitation and Text Treatment, edited by Thomas Schmidt-Beste. Turnhout: Brepols, 2012.

Cumming, Julie, and Peter Schubert. “The Origins of Pervasive Imitation.” In The Cambridge History of Fifteenth-Century Music, ed. Anna Maria Busse Berger and Jesse Rodin, 200–28. New York: Cambridge University Press, 2015.
DeFord, Ruth. Tactus Mensuration, and Rhythm in Renaissance Music. Cambridge: Cambridge University Press, 2015.

Fuller, Sarah. “Contrapunctus Theory, Dissonance Regulation, and French Polyphony of the Fourteenth Century.” In Medieval Music in Practice: Studies in Honor of Richard Crocker, edited by Judith Peraino, 113–52. Middleton, Wisconsin: American Institute of Musicology, 2013.

———. “Organum – discantus – contrapunctus in the Middle Ages.” In The Cambridge History of Western Music Theory, edited by Thomas Christensen, 477–502. Cambridge: Cambridge University Press, 2002.

Milsom, John. “‘Imitatio,’ ‘intertextuality’, and early music.” In Citation and authority in Medieval and Renaissance musical culture: Learning from the learned, edited by Suzannah Clark and Elizabeth Eva Leach, 141–51. Woodbridge: Boydell & Brewer, 2005.

Morgan, Alexander. "[Renaissance Interval-Succession Theory: Treatises and Analysis](http://digitool.library.mcgill.ca/R/DPIVYXI71HL5ILGG61U4D2N5YR6UMUAASGK4S4JC42B2BFPGCD-00398?func=results-jump-full&set_entry=000001&set_number=001123&base=GEN01)". PhD diss., McGill University, 2017.

Pontio, Pietro. Ragionamento di musica. Compiled by Suzanne Clercx. Kassel: Bärenreiter, 1959. Originally published Parma: 1588.

———. [Ragionamento di musica](http://www.ums3323.paris-sorbonne.fr/TREMIR/TReMiR_Pontio/R0_start.htm). Electronic version published by Dupraz, Christophe. Traités Musicaux Romans, 2013. Accessed August 14, 2016.

Schubert, Peter. “Hidden Forms in Palestrina’s First Book of Four-Voice Motets.” Journal of the American Musicological Society 60 (2007), 483–556.

Schubert, Peter and Julie Cumming, “Another Lesson from Lassus: using Computers to Analyze Counterpoint.” Early Music 43.4 (November 2015): 577–86.

Tinctoris, Johannes. Liber de arte contrapuncti. In Johannes Tinctoris Opera Theoretica. Compiled by Albert Seay. n.p.: American Institute of Musicology, 1975. Originally written 1477.

———. Liber de arte contrapuncti. Translated by Albert Seay. Rome: American Institute of Musicology, 1961. Originally written c. 1477.

———. "[Liber de arte contrapuncti](http://earlymusictheory.org/Tinctoris/texts/deartecontrapuncti/). Translated by Jeffrey Dean. Last accessed November 16, 2015. Originally written 1477.

Vicentino, Nicola. Ancient music adapted to modern practice (L’antica musica ridotta alla moderna prattica). Translated by Maria Rika Maniates and edited by Claude Palisca. New Haven, Yale University Press 1996. Originally published 1555.

Zarlino, Gioseffo. Art of Counterpoint. Translated by Guy Marco and Claude Palisca, edited by Claude Palisca. New Haven and London: Yale University Press, 1968. Originally published: 1558.



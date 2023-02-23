---
title: Bajo cifrado
lang: en es
page_language: es
translator: David Rizo
translation_date: 10 Aug 2021
translation_update:
ref: humdrum-figured_bass
keywords: humdrum figured bass
tags: [all, humdrum, figured bass]
verovio: "true"
vim: ts=3 ft=javascript
summary: A description of how to encode figured bass (basso continuo) in **fb spines.
sidebar: main_sidebar
permalink: /humdrum/figured_bass/index-ES.html
---


Los bajos cifrados se pueden codificar en los datos de Humdrum utilizando la interpretación exclusiva `**fb`.  Aquí hay un ejemplo de codificación:

{% include verovio.html
	source="follia"
	humdrum-min-height="900px"
	scale="55"
	pageWidth="1000"
%}

<script type="application/x-humdrum" id="follia">
!!!COM: Corelli, Arcangelo
!!!OTL: Follia in D minor, Op. 5, No. 12
!!!OMD: Adagio
**kern	**fb	**kern
*clefF4	*	*clefG2
*k[b-]	*	*k[b-]
*M3/4	*	*M3/4
=1-	=1-	=1-
2.D	.	4dd
.	.	4.dd
.	.	8ee
=2	=2	=2
2.AA	#	2cc#
.	.	4cc#
=3	=3	=3
2.D	5	4dd
.	.	(4.dd
.	6nr	.
.	.	16ccLL
.	.	16ddJJ)
=4	=4	=4
2.C	.	2ee
.	.	4ee
=5	=5	=5
2.F	.	4ff
.	.	4.ff
.	.	8gg
=6	=6	=6
2C	.	2ee
4C#	6	4ee
=7	=7	=7
4D	.	(8ddL
.	.	8cc#J)
2BB-	7	4.dd
.	6	8ee
=8	=8	=8
2.AA	#	2cc#
.	.	4cc#
=9	=9	=9
2.D	.	4dd
.	.	4.dd
.	.	8ee
=10	=10	=10
2.AA	#	2cc#
.	.	4cc#
=11	=11	=11
2.D	5	4dd
.	.	(4.dd
.	6nr	.
.	.	16ccLL
.	.	16ddJJ)
=12	=12	=12
2.C	.	2ee
.	.	4ee
=13	=13	=13
2.F	.	4ff
.	.	4.ff
.	.	8gg
=14	=14	=14
4.C	.	4.ee
8C#	6	8ee
4D	.	4ff
=15	=15	=15
4GG	7 5	4dd
2AA	5 4	4.dd
.	X 3#r	.
.	.	8cc#
=16	=16	=16
2.D	.	2.dd
=||	=||	=||
*-	*-	*-
</script>

Prueba a cambiar/añadir/eliminar números en la segunda columna para cambiar el bajo cifrado en la música de la derecha.

Ten en cuenta que no es necesario adjuntar las cifras a las notas del pentagrama donde aparecen las cifras (como `3#` en el compás 15).

## Cifras apiladas ##

Las figuras apiladas, que especifican más de un intervalo por encima de la nota de bajo, se crean enumerando los números en orden de arriba a abajo y separando cada figura con un solo espacio.  Estos son algunos ejemplos de visualización de más de una cifra simultáneamente: 

{% include verovio.html
	source="stacked"
	scale="55"
	pageWidth="800"
%}

<script type="application/json" id="stacked">
**kern	**fb
*M4/4	*
=1	=1
4g	7
4g	7 5
4g	7 5 3
4g	6 4
==	==
*-	*-
</script>

### Marcadores de posición de la pila ###

Utiliza `X` o `x` para añadir un marcador de posición vacío en una pila de figuras. Los caracteres `X` en mayúscula significan que cualquier extensión de línea debe terminar en esta posición, mientras que `x` en minúscula significa que cualquier línea de extensión de una figura anterior debe pasar por esta posición.

{% include verovio.html
	source="placeholder"
	scale="55"
	pageWidth="800"
%}

<script type="application/json" id="placeholder">
**kern	**fb
*M4/4	*
=1	=1
2c	7_ 4:
2c	x 3
=2	=2
1c	7 4:3
=	=
*-	*-
</script>

Los dos puntos (:) indican que un guión debe seguir a la cifra, si está al final de una cifra.  Si está en medio de una cifra, los dos puntos también deben representarse como un guión, y separan dos cifras entre sí.


{% include warning.html
	content="Verovio todavía no representa las extensiones de línea para las cifras, por lo que actualmente se sustituye la línea de extensión por un guión bajo.  Del mismo modo, los guiones centrados entre cifras secuenciales aún no son representables en MEI (y por lo tanto no se pueden representar en Verovio, por lo que se muestra un guion de lugar después de la primera cifra)."
%}

### Intervalos implícitos ###

Una cifra como "6" es la abreviatura de "6 3".  Para fines analíticos, puede ser útil codificar explícitamente el intervalo "3" así como el "6", pero mostrar sólo el "6".  Para ello, añada una "K" a una cifra para suprimir su visualización.  Esto es similar a la "X" y la "x", pero en el caso de estos dos significantes, no hay ningún intervalo implícito. A diferencia de `X`/`x`, el significante `K` no conservará una posición vertical para la figura invisible; sin embargo, puede incluir los significantes `K` y `X` en la misma cifra para ocultar la cifra y conservar la posición de la pila.

{% include verovio.html
	source="hidden"
	humdrum-min-height="280px"
	scale="55"
	pageWidth="950"
	spacingNonLinear="0.35"
	spacingLinear="0.8"
%}

<script type="application/json" id="hidden">
**kern	**fb
*M4/4	*
=1	=1
4g	6
4g	6 3
2g	6 3K
=2	=2
4f	5K 3K
4f	6K 4 2
4f	X 4 2
4f	6KX 4 2
=	=
1f	7 5K 3K
=	=
*-	*-
</script>





## Posicionamiento en el pentagrama ##

Por defecto, las cifras se colocarán debajo del pentagrama.  Para moverlas por encima, añade la interpretación `*above` antes de la primera figura que deba colocarse por encima del pentagrama.  Utiliza `*abajo` para volver a la posición por defecto debajo del pentagrama.

{% include verovio.html
	source="above"
	scale="55"
	humdrum-min-height="320px"
	pageWidth="500"
%}

<script type="application/json" id="above">
**kern	**fb
*M4/4	*
*	*above
=1	=1
4e	6
4e	5
4e	4 2
4e	6 4 2
=2	=2
4e	6
4e	5
*	*below
4e	4 2
4e	6 4 2
==	==
*-	*-
</script>



## Alteraciones ##

Las codificaciones de las alteraciones coinciden con las de la altura de las notas de `**kern`:

| Carácter       | Significado            |
| --------------- | ------------------ | 
| #               | sostenido              | 
| n               | natural  / becuadro           | 
| &ndash; (dash)  | bemol               | 
| ##              | doble sostenido       | 
| &ndash;&ndash;  | doble bemol        |

### Codificación de las alteraciones escritas frente a las sonoras ###

En las codificaciones `**fb`, las alteraciones tienen un significado fijo similar al de la notación musical moderna: un sostenido significa un semitono por encima de un tono diatónico natural, y un bemol significa un semitono por debajo de un tono diatónico natural.  En la música del siglo XVII, el significado de una alteración puede ser relativo, de manera que un signo de sostenido para una nota/figura que de otro modo es bemol significa elevar la altura un semitono hasta la posición diatónica natural.  Del mismo modo, los signos de bemol pueden bajar un tono sostenido a su estado natural.

En estos casos, añade una "n" después del signo de sostenido o bemol.  Cuando un signo natural está presente al mismo tiempo que un sostenido o un bemol, el signo natural es el accidental sonoro de la figura, y el sostenido o el bemol es el signo escrito.  El siguiente ejemplo demuestra este comportamiento: en el primer compás hay un signo de sostenido escrito para un intervalo que de otro modo sería un si bemol debido a la armadura.  Esto debe interpretarse como una elevación del tono de si bemol a si natural.  En el segundo compás, se utiliza la convención moderna de escribir un natural para anular el bemol.

{% include verovio.html
	source="relative"
	tabsize="10"
	scale="55"
	pageWidth="800"
%}

<script type="application/json" id="relative">
**kern	**fb
*M4/4	*M4/4
*k[b-e-]	*k[b-e-]
=1	=1
1g	#n
=2||	=2||
1g	n
==	==
*-	*-
</script>

En los dos compases del ejemplo anterior, se debe tocar un acorde de Sol mayor. En el primer compás, el sostenido funciona como una alteración relativa, y en el segundo compás, el signo natural es una alteración absoluta.


### Cambio entre alteraciones visuales relativas y absolutas ###

Añade la interpretación tándem `*absolute` a la columna del bajo cifrado para mostrar las alteraciones en un estilo moderno en lugar del estilo accidental relativo del siglo XVII (si las alteraciones relativas están codificadas en los datos). Esto permite cambiar fácilmente entre la notación original y las convenciones modernas.  Para anular la visualización forzada de las alteraciones absolutas, inserta la interpretación en tándem `*Xabsolute` antes de las figuras a las que se aplica.

Aquí hay un ejemplo similar, pero una alteración absoluta reemplaza a la alteración relativo original en el primer compás:

{% include verovio.html
	source="absolute"
	tabsize="10"
	scale="55"
	pageWidth="580"
	spacingNonLinear="0.40"
	spacingLinear="0.45" 
	minLastJustification="0.50"
	humdrum-min-height="300px"
%}

<script type="application/json" id="absolute">
**kern	**fb
*M4/4	*M4/4
*k[b-e-]	*k[b-e-]
=1	=1
*	*absolute
!!LO:TX:a:i:t=absolute
1g	#n
=2	=2
1g	n
=3||	=3||
*	*Xabsolute
!!LO:TX:a:i:t=relative
1g	#n
=4	=4
1g	n
==	==
*-	*-
</script>

### Codificación del intervalo cromático  ###

El uso de alteraciones absolutas para los bajos cifrados puede causar problemas al transponer música con bajos cifrados.  Por ejemplo, "&#x266E;7" en Do mayor con una nota de bajo en Do producirá una séptima mayor en Si natural, mientras que la misma figura en Sol mayor con una nota de bajo en Sol producirá un Fa natural, que es una séptima menor.

El principal problema es que, para calcular el tono exacto de la cifra, se necesita tanto la alteración de la figura como la signatura de la música.  Así, para codificar el intervalo cromático exacto, se pueden anteponer al número de la cifra las letras `m`, `M`, `P`, `d` y `A`:

| Carácter       | Significado                    |
| --------------- | -------------------------- | 
| m               | intervalo menor             | 
| M               | intervalo mayor             | 
| P               | intervalo perfecto           | 
| d               | intervalo disminuido        | 
| dd              | intervalo doble disminuido | 
| A               | intervalo aumentado         | 

Los caracteres `d` y `A` pueden repetirse, y cada letra adicional baja o sube el tono en un semitono.

Estos significantes de intervalo cromático no afectarán directamente a la presentación visual de las alteraciones de las notas, pero son necesarios para ajustar las alteraciones absolutas al transponer la música.  Se escribirá una herramienta "fb" para insertar automáticamente las letras de alteración cromática.  Esta herramienta también debería ser capaz de ajustar las alteraciones del bajo cifrado después de la transposición.

### Alteraciones después de las cifras ###

Añade una `r` a una cifra para invertir el orden de las alteraciones y los números.  La posición del punto y el número no es importante en la codificación `**fb` como se demuestra a continuación:

{% include verovio.html
	source="reverse"
	tabsize="10"
	scale="55"
	pageWidth="800"
%}

<script type="application/json" id="reverse">
**kern	**fb
*M4/4	*M4/4
*k[b-e-]	*k[b-e-]
=1	=1
4f	n6 n6r
4f	n6 6nr
4f	n6 6rn
4f	n6 r6n
==	==
*-	*-
</script>

Alternativamente, da la interpretación tándem, `*reverse`, en algún lugar antes de la primera figura para invertir la posición de las accidentales y evitar codificar el estilo inverso con `r` en cada ficha.  Utiliza `*Xreverse` para desactivar la función de inversión.

{% include verovio.html
	source="reverse2"
	tabsize="10"
	humdrum-min-height="350px"
	scale="55"
	pageWidth="400"
%}

<script type="application/json" id="reverse2">
**kern	**fb
*M4/4	*M4/4
*k[b-e-]	*k[b-e-]
=1	=1
!!LO:TX:a:t=normal
2f	n6
2f	n6
=2	=2
*	*reverse
!!LO:TX:a:t=reverse
2f	n6
2f	n6
=3	=3
*	*Xreverse
!!LO:TX:a:t=individual
2f	n6r
2f	n6r
==	==
*-	*-
</script>


## Cifras con barras ##

En algunas convenciones de notación del bajo cifrado, se utilizan barras en lugar de alteraciones para subir o bajar la alteración cromática de una figura.  Las barras que se mueven hacia abajo de izquierda a derecha suelen significar que la alteración cromática debe elevarse un semitono, mientras que las barras que se mueven hacia arriba de izquierda a derecha significan que la afinación de la figura debe bajarse un semitono.  Otra variante es utilizar el signo "+" para indicar que se ha subido un tono. El signo `+` también se puede usar para adjuntarlo al número de la figura.

Se puede añadir una barra a cualquier cifra en los datos `**fb`, pero no todas son renderizables en notación Verovio.  Aquí hay un muestrario de las que están disponibles en notación gráfica:

{% include verovio.html
	source="slashes"
	tabsize="10"
	humdrum-min-height="400px"
	scale="55"
	pageWidth="800"
	spacingLinear="0.9"
	spacingNonLinear="0.2"
%}

<script type="application/json" id="slashes">
**kern	**fb
=-	=-
1f	#2 #2|
=-	=-
1f	#4 #4|
=-	=-
1f	#6 #6|
=-	=-
1f	-5 -5/
=-	=-
1f	#5 #5\
=-	=-
1f	#5 #5|
=-	=-
1f	#7 #7\
=-	=-
1f	-7 -7/
=-	=-
1f	#7 #7|
==	==
*-	*-
</script>

Estos son los tipos de barras que se pueden codificar:

| Carácter       | Renderización visual | Significado típico                       |
| --------------- | ---------------- | ------------------------------------- | 
| \               | barra que baja | subir un semitono desde la tonalidad | 
| /               | barra que sube   | bajar un semitono desde la tonalidad | 
| \|              | barra vertical   | subir un semitono desde la tonalidad | 

### Visualización de cifras sin barras ###

Las alteraciones también deben codificarse en las cifras para indicar explícitamente la alteración cromática de la figura.  Actualmente, MusicXML (véase más adelante) no añade dichas alteraciones.  La codificación paralela de las alteraciones es necesaria ya que el significado de las barras en los diferentes estilos no siempre es coherente, por lo que las barras en las codificaciones deben considerarse como elementos totalmente visuales, no analíticos. 

El bajo figurado puede convertirse automáticamente de la notación de barras a la notación de alteraciones para las cifras alteradas.  Añadae la interpretación tándem `*Xslash` para mostrar las alteraciones en lugar de las barras.

{% include verovio.html
	source="noslashes"
	tabsize="10"
	humdrum-min-height="400px"
	scale="55"
	pageWidth="800"
	spacingLinear="0.9"
	spacingNonLinear="0.2"
%}

<script type="application/json" id="noslashes">
**kern	**fb
=-	=-
1f	#2 #2|
=-	=-
1f	#4 #4|
=-	=-
1f	#6 #6|
=-	=-
1f	-5 -5/
=-	=-
1f	#5 #5\
=-	=-
1f	#5 #5|
=-	=-
1f	#7 #7\
=-	=-
1f	-7 -7/
=-	=-
1f	#7 #7|
==	==
*-	*-
</script>


## Editorial signifiers ##

Hay tres tipos de significantes editoriales para los datos de `**fb`: `i` indica la intervención editorial, mostrando las cifras/accidentes entre corchetes; `j` indica la intervención editorial, mostrando las cifras/alteraciones entre paréntesis; y `k` indica la intervención editorial, no visualizando las cifras/alteraciones.  A continuación se muestra una muestra de cada tipo de marcado editorial:

{% include verovio.html
	source="editorial"
	tabsize="10"
	humdrum-max-height="325px"
	lyricTopMinMargin="4.0"
	spacingLinear="0.30"
	scale="55"
	pageWidth="500"
	minLastJustification="0.25"
%}

<script type="application/json" id="editorial">
**kern	**fb	**text
*clefG2	*	*
*	*above	*
=1	=1	=1
4c	#6i	i
4c	#6ir	ir
4c	#6I	I
=2	=2	=2
4c	#6j	j
4c	#6jr	jr
4c	#6J	J
=3	=3	=3
4c	#6k	k
4ryy	.	.
4c	#6K	K
=	=	=
*-	*-	*-
</script>


Ten en cuenta que los códigos en minúscula sólo se aplican a la alteración, mientras que los códigos en mayúscula se aplican a toda la cifra.



## Añadir columnas de bajos cifrados en VHV ##

Para añadir una columna de bajo cifrado a la música en el editor VHV, sigue estos tres pasos:

1. Escribe esta línea de filtro (en cualquier lugar del archivo):
```
!!!filter: extract -s 1,0,2-$
```
El filtro asume que tiene múltiples partes o columnas, y que quieres insertar la columna de bajos cifrados como la segunda columna desde la izquierda. El "0" en la columna de extracción inserta una columna en blanco entre las columnas 1 y 2.  La cadena de extracción de la columna será diferente si desea colocar la columna `**fb` en otro lugar. 2. Compila el filtro escribiendo <span class="keypress">alt-c</span>.  Para algunas configuraciones de teclado/S.O., es posible que tenga que pulsar primero la partitura gráfica de la derecha (si <span class="keypress">alt-c</span> inserta un carácter en el texto, por ejemplo).  Después de compilar el filtro, la etiqueta del filtro debería cambiar a `Xfilter` y la columna en blanco debería ser visible en el editor de texto.

3. Cambia la interpretación exclusiva de la nueva columna de `**blanco` a `**fb`.  También puede eliminar la línea de filtro utilizada.

Aquí hay un vídeo que demuestra el proceso:


{% include image.html
	file="adding-fb.gif"
	alt="Demostración de la adición de una columna de bajo figurado."
	max-width="100%"
	caption="Demostración de la adición de una columna de bajo cifrado mediante el filtro de extracción."
%}


## Importación de bajo cifrado desde MusicXML ##

VHV puede importar bajo cifrado a partir de datos MusicXML.  Ten en cuenta que algunos editores de música, como MuseScore, pueden crear/exportar bajo cifrado, pero otros, como Finale, no.  Para convertir un archivo MusicXML con bajo cifrado, arrastra y suelta el archivo en la página web de VHV.

{% include image.html
	file="musicxml-fb.gif"
	alt="MusicXML import with figured bass"
	max-width="100%"
	caption="Archivo MusicXML que contiene bajos cifrado, exportado desde MuseScore, y luego importado por archivo de arrastrar/soltar en VHV."
%}

<a target="_blank" href="musicxml-fb.xml">Aquí</a> está el 
archivo de prueba MusicXML utilizado en el vídeo anterior.

## Pistas de realización ##

Este es un ejemplo de cómo añadir pistas de realización en una parte de bajo continuo:

{% include verovio.html
	source="beschrankt"
	humdrum-min-height="560px"
	scale="55"
	pageWidth="1000"
%}

<script type="application/json" id="beschrankt">
!!!COM: Bach, Johann Sebastian
!!!OTL: Beschränkt, ihr Weisen
!!!SCT: Riemenschneider no. 47/69
**kern	**fb
*clefF4	*
*k[f#c#g#]	*
*M3/4	*
*^	*
4G#N 4BN	4E	.
4AN 4eN	4C#	6
4AN 4c#N	4F#	.
=	=	=
*^	*	*
2F#N	4c#N	2D	7:
.	4BN	.	6
*v	*v	*	*
4BN 4eN	4Gn	6
=	=	=
4A#N 4c#N 4f#N	4F#	#
2F#N 2BN 2dN	8EL	7_ 5_ 2_
.	8D	.
.	8C#	.
.	8BBJ	.
=	=	=
2.A#N 2.c#N 2.f#N	4F#	#_
.	4FF#	.
.	4GG#	.
=	=	=
4C#N 4F#N	4AA#	6
4EN 4G#N	4BB	6 4
4EN 4F#N 4A#N	4C#	6#/ 4 3
=	=	=
*v	*v	*
*-	*-
!!!RDF**kern: N = no stem, cue size, color=#bbbbbb
!!!URL: https://en.wikipedia.org/wiki/File:Figured_bass.png
</script>


<script>

//////////////////////////////
//
// DOMContentLoaded event listener --
//

document.addEventListener("DOMContentLoaded", function () {
	var containerSelector = "#beschrankt-svg"
	var svgSelector = containerSelector + " svg";
	var color = "#aaa";
	var interval = setInterval(function () {
		var svgTargetElement = document.querySelector(containerSelector);
		if (!svgTargetElement) {
			return;
		}
		clearInterval(interval);
		var observer = new MutationObserver(function (mutations) {
			mutations.forEach(function (mutation) {
				color514(svgSelector, color);
   		});
		});
		var config = { attributes: false, childList: true, characterData: false };
		observer.observe(svgTargetElement, config);
		// Have to color manually the first time since SVG is already in place:
		color514(svgSelector, color);
	}, 100);
});


//////////////////////////////
//
// color514 -- color notes with size 514 in gray.
//

function color514(selector, color) {
	var item = document.querySelector(selector);
	var notes = item.querySelectorAll("g.note");
	for (var i=0; i<notes.length; i++) {
		var use = notes[i].querySelector("use");
		if (!use) {
			continue;
		}
		var height = use.getAttribute("height");
		if (height !== "514px") {
			continue;
		}

		var par = notes[i].parentNode;
		if (par.classList && par.classList[0] !== "chord") {
			notes[i].style.fill = color;
			notes[i].style.stroke = color;
		} else {
			par.style.fill = color;
			par.style.stroke = color;
		}
	}

}

</script>


<style>
svg g.ledgerLines.cue [stroke]
	 { fill: #999;     stroke: #999; }
</style>


Aquí está el código Javascript para implementar el ejemplo anterior:


```javascript
document.addEventListener("DOMContentLoaded", function () {
   var containerSelector = "#beschrankt-svg"
   var svgSelector = containerSelector + " svg";
   var color = "#aaa";
   var interval = setInterval(function () {
      var svgTargetElement = document.querySelector(containerSelector);
      if (!svgTargetElement) {
         return;
      }
      clearInterval(interval);
      var observer = new MutationObserver(function (mutations) {
         mutations.forEach(function (mutation) {
            color514(svgSelector, color);
         });
      });
      var config = { attributes: false, childList: true, characterData: false };
      observer.observe(svgTargetElement, config);
      // Have to color manually the first time since SVG is already in place:
      color514(svgSelector, color);
   }, 100);
});

function color514(selector, color) {
   var item = document.querySelector(selector);
   var notes = item.querySelectorAll("g.note");
   for (var i=0; i<notes.length; i++) {
      var use = notes[i].querySelector("use");
      if (!use) {
         continue;
      }
      var height = use.getAttribute("height");
      if (height !== "514px") {
         continue;
      }
      var par = notes[i].parentNode;
      if (par.classList && par.classList[0] !== "chord") {
         notes[i].style.fill = color;
         notes[i].style.stroke = color;
      } else {
         par.style.fill = color;
         par.style.stroke = color;
      }
   }
}

```

Y el estilo CSS del ejemplo para colorear también las líneas adicionales de las notas:

```css
svg g.ledgerLines.cue [stroke]
	 { fill: #999;     stroke: #999; }
```



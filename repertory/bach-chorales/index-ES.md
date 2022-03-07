---
title: J.S. Bach chorales
lang: en es
ref: repertory-bach-chorales
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum Bach chorales
creation_date: 18 Mar 2017
translation_date: 9 Aug 2021
last_updated: 18 Mar 2017
verovio: "true"
tags: [all, repertories]
vim: ts=3 ft=javascript
summary: J.S. Bach chorale repertory
sidebar: main_sidebar
permalink: /repertory/bach-chorales/index-ES.html
---
La URL [http://verovio.humdrum.org/?file=chorales](http://verovio.humdrum.org/?k=e&file=chorales) enumera un conjunto de 371 corales a cuatro partes que fueron recopiladas tras la muerte de J.S. Bach por su hijo C.P.E. Bach (y terminadas por Kirnberger, alumno de J.S. Bach, tras la muerte de C.P.E. Bach).  Los corales están ordenados por números de edición de Breitkopf & Härtel e incluyen todos los corales excepto el nº 150, que no está en cuatro partes.

La primera edición completa de los corales de este conjunto fue publicada por Breitkopf & Härtel entre 1784 y 1787 en cuatro volúmenes.  La primera edición incompleta consistió en 200 corales en dos volúmenes por Friedrich Wilhelm Birnstiel en 1765 y 1769, que fue reimpreso en 1975 por Georg Olms.

Esta edición digital está referenciada a la cuarta edición de los corales de Breitkopf & Härtel: *371 vierstimmige Choralgesänge von Johann Sebastian Bach*. 4ª edición de Alfred Dörffel. Breitkopf & Härtel, Leipzig [c. 1875]. 178 pp. Número de placa: V.A.10. Reeditado c. 1915 como Edición Breitkopf 10. Reimpreso por Associated Music Publishers, Inc., Nueva York [c. 1940].

Los escaneos de la edición original de los primeros 50 corales pueden verse pulsando <span class="keypress">alt-p</span> al mostrarse un coral concreto:

{% include image.html
	file="chorale-scan.png"
	alt="chorale scan"
	caption="Visualización de la edición original escaneada con con <span class=\"keypress\">alt-p</span>."
%}

Véase este artículo: [La historia de la colección Breitkopf de los corales a cuatro voces de J.S. Bach](http://www.bach-cantatas.com/Articles/Breitkopf-History.htm) de Thomas Braatz para más información sobre la edición fuente de los corales de Bach.


## Característica clave-original ##
El repertorio de corales de Bach muestra cómo codificar [claves originales](/commands/alt-o).  Escribe <span class="keypress">alt-o</span> en VHV para cambiar entre las claves modernas y las originales al ver los corales:

{% include image.html
	file="alt-o-clef-switching.png"
	alt="Demostración alt-o"
	caption="Demostración alt-o"
%}

La primera edición de esta colección de corales se publicó en realidad en gran pentagrama, utilizando la clave de soprano para el pentagrama superior y la clave de Fa en el pentagrama inferior:

{% include image.html
	file="chorale-first-edition.png"
	alt="primera edición"
	caption="Primera edición de los corales en claves de soprano y de Fa en un pentagrama."
%}
He aquí un ejemplo de disposición de la música que se ajusta más a la edición original:

{% include verovio.html
	source="chorale001"
	humdrum-max-width="220px"
	scale="50"
	pageWidth="1000"
%}

<script type="application/humdrum" id="chorale001">
!!!OTL:	Aus meines Herzens Grunde
!!!SCT:	BWV 269
!!!PC#:	1
**kern	**kern
*clefF4	*clefC1
*k[f#]	*k[f#]
*M3/4	*M3/4
*^	*^
4B	4GG	4g	4d
=1	=1	=1	=1
4B	4G	2g	4d
8cL	4E	.	4e
8BJ	.	.	.
4A	4F#	4dd	4d
=2	=2	=2	=2
4G	4G	4.b	2d
4F#	4D	.	.
.	.	8a	.
4G	4E	4g	4B
=3	=3	=3	=3
8cL	4C	4.g	8eL
8BJ	.	.	8d
4c	8BBL	.	8e
.	8AAJ	8a	8f#J
4d	4GG	4b	4g
=4	=4	=4	=4
2d;y	2D;	2a;	2f#;y
*v	*v	*	*
*	*v	*v
*-	*-
</script>





## Disposición gran pentagrama ##
Los datos de los corales de Same Bach se pueden ver en formato de gran pentagrama utilizando este enlace: [verovio.humdrum.org/?file=chorales&filter=satb2gs](http://verovio.humdrum.org/?file=chorales&filter=satb2gs).

{% include image.html
	file="chor027-grand-staff.png"
	alt="grand-staff layout"
	url="http://verovio.humdrum.org/?file=chorales/chor027.krn&filter=satb2gs"
	caption="Disposición de los corales mediante el filtro satb2gs."
	caption-margin-top="-20px"
%}


## Corales transpuestos ##

Los corales de Bach también pueden transponerse todos al mismo tono tónico en disposición de pentagrama añadiendo un filtro de transposición a la URL: [verovio.humdrum.org/?file=chorales&filter=satb2gs%7ctranspose%20-kc](http://verovio.humdrum.org/?file=chorales&filter=satb2gs%7ctranspose%20-kc).


{% include image.html
	file="chor027-c-tonic.png"
	alt="grand-staff layout and transposed to C"
	url="http://verovio.humdrum.org/?file=chorales/chor027.krn&filter=satb2gs%7ctranspose%20-kc"
	caption="Coral transpuesto a la tónica en C usando el filtro de transposición."
	caption-margin-top="-20px"
%}


Cambia la "c" al final de la URL de los corales transpuestos en Do para cambiar a otra tónica:


D
: [http://verovio.humdrum.org/?file=chorales/chor027.krn&filter=satb2gs%7ctranspose%20-kd](http://verovio.humdrum.org/?file=chorales/chor027.krn&filter=satb2gs%7ctranspose%20-kd)

E-flat
: [http://verovio.humdrum.org/?file=chorales/chor027.krn&filter=satb2gs%7ctranspose%20-ke-](http://verovio.humdrum.org/?file=chorales/chor027.krn&filter=satb2gs%7ctranspose%20-ke-)

F-sharp
: [http://verovio.humdrum.org/?file=chorales/chor027.krn&filter=satb2gs%7ctranspose%20-kf%23](http://verovio.humdrum.org/?file=chorales/chor027.krn&filter=satb2gs%7ctranspose%20-kf%23)

Los datos que se muestran en el editor de texto no están transpuestos (muestran los datos prefiltrados).  En la siguiente captura de pantalla, fíjate en que la música está en Fa mayor, pero la notación está en Fa mayor:

{% include image.html
	file="chor027-f-sharp.png"
	alt="coral 27 en fa sostenido mayor"
	caption="Coral 27 transpuesto a Fa sostenido mayor utilizando el filtro de transposición."
%}


Para ver la partitura transpuesta en el editor de texto, escribe <span class="keypress">alt-c</span> para compilar las instrucciones del filtro:

{% include image.html
	file="chor027-f-sharp2.png"
	alt="coral 27 en fa sostenido mayor"
	caption="Datos del coral 27 compilados en Fa sostenido mayor con <span class='keypress'>alt-c</span>."
%}


## Descarga y correcciones ##

Esta edición digital de los corales de J.S. Bach está [disponible en Github](https://github.com/craigsapp/bach-371-chorales) para su descarga.  Las correcciones a la edición pueden ser enviadas a Github, ya sea como un [issue](https://github.com/craigsapp/bach-371-chorales/issues) (en prosa), o preferiblemente como un [pull request](https://github.com/craigsapp/bach-371-chorales/pulls) (correcciones directas a los archivos de datos).  Las correcciones deben coincidir con los escaneos de la edición de origen (que se ven escribiendo <span class='keypress'>alt-p</span> en los primeros 50 corales, o de lo contrario debe enviarse una explicación con la corrección de por qué la corrección no coincide con los escaneos de origen.


## Sitio web de las Corales de Bach ##

{% include image.html
	file="chorales-website.jpg"
	alt="Sitio web de las corales de J.S. Bach"
	caption="Sitio web que utiliza las partituras digitales de los corales de Bach"
%}

<a target="_blank" href="https://chorales.sapp.org">Este sitio web</a> demuestra cómo publicar partituras en la web después de haberlas editado con Verovio Humdrum Viewer. El código fuente del sitio web puede verse <a target="_blank" href="https://github.com/craigsapp/bach-370-chorales/tree/gh-pages">aquí</a>. El sitio web de la coral utiliza el <a target="_blank" href="https://plugin.humdrum.org">Complemento de notación de la coral</a> para mostrar la notación de la coral dinámicamente en el sitio web de forma similar a VHV.  También puede consultar la página <a target="_blank" href="https://chorales.sapp.org/typesetter">Typesetter</a> donde puede ajustar el diseño del coral (controlando el tamaño, el espaciado, las partes, el rango de compases y la transposición), y luego copiar el código del plugin para insertar la notación dinámica de una partitura en su página web, o descargar un SVG para mostrarlo en una página web o insertarlo en un documento editado en Microsoft Word, por ejemplo.

{% include image.html
	file="chor273-mm6-7.svg"
	alt="Compases 6&ndash;7 del coral nº 273"
	caption="Compases 6&ndash;7 del coral nº 273 generados en la página de composición."
%}


La imagen SVG anterior también puede generarse dinámicamente en una página web utilizando el siguiente código:

```html
<html>
<head>
<title>My Example</title>
<script src="https://verovio-script.humdrum.org/scripts/verovio-toolkit.js"></script>
<script src="https://plugin.humdrum.org/scripts/humdrum-notation-plugin.js"></script>
<script>var vrvToolkit = new verovio.toolkit()</script>
</head>
<body>
<div style="width:590px">

<script>displayHumdrum({
   source: "chor273-mm6-7",
   scale: 60,
   spacingNonLinear: 0.58,
   filter: "myank -m 6-7 | satb2gs",
   uri: "github://craigsapp/bach-370-chorales/kern/chor273.krn"
})</script>
<script id="chor273-mm6-7" type="text/x-humdrum"></script>

</div>
</body>
</html>
```

Prueba a copiar y pegar el código HTML anterior en un archivo y ábrelo en un navegador web para ver la misma notación que en la figura anterior.




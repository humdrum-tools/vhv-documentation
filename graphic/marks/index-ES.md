---
title: Marcar notas con <span class='keypress'>at</span>
lang: en es
page_language: es
translator: David Rizo
translation_date: 9 Aug 2021
translation_update:
ref: graphic-marks
tags: [all, commands, RDF]
sidebar: main_sidebar
keywords: interface commands 
summary: El comando <span class='keypress'>at</span> resalta las notas en el editor de notación y añade un significante de marca al token de datos de la nota en el editor de texto.
permalink: /graphic/marks/index-ES.html
---
Al pulsar <span class="keypress">@</span> mientras una nota está seleccionada, se marcará la nota con un firmante de usuario basado en la última línea RDF de nota marcada en los datos de Humdrum con una forma como la siguiente:

```
!!!RDF**kern: @ = marked note
```
Si no hay una definición RDF de nota marcada en los datos de Humdrum, se añadirá una automáticamente al final de los datos.  Este es un ejemplo de marcado de notas en la notación, que añade `@` a los tokens de nota en los datos de Humdrum.

{% include image.html
	file="mark-notes.gif"
	alt="marcar notas en el editor de notación gráfica."
	caption="Marcar notas con <span class='keypress'>@</span> en el editor de notación."
%}


## Cambiar los colores de las marcas ##

El color por defecto para las notas marcadas en notación VHV es el rojo.  Si se desea utilizar otro color, se puede añadir un parámetro de color al RDF:

{% include image.html
	file="magenta-turquoise.gif"
	alt="marcar las notas en el editor de notación gráfica en diferentes colores."
	caption="Cambiar el color de las notas marcadas."
%}
El valor del parámetro de color debe ir entre comillas si contiene espacios, pero en caso contrario las comillas son opcionales.  Los colores pueden ser [colores con nombre](https://www.w3schools.com/cssref/css_colors.asp) así como `transparent`, o cualquier [formato numérico reconocido por SVG](https://www.w3schools.com/cssref/css_colors_legal.asp): colores hexadecimales de 3/6 dígitos, colores RGB, colores RGBA, colores HSL o colores HSLA.  Ejemplos:


{% include image.html
	file="hex-c03da2.png"
	alt="ejemplo de color hexadecimal."
	caption="Ejemplo de código hexadecimal \"#c03da2\"."
%}


El mismo color en formato `rgb`:

{% include image.html
	file="rgb-192-61-162.png"
	alt="ejemplo de color rgb."
	caption="Ejemplo de color rgb \"rgb(192,61,162)\"."
%}


Añadiendo un 50% de opacidad al mismo color en formato `rgba`:

{% include image.html
	file="rgb-192-61-162-05.png"
	alt="ejemplo de color rgba."
	caption="Ejemplo de color rgb \"rgba(192,61,162,0.5)\"."
%}

## Varias marcas ##

Se puede dar cualquier número de marcas RDF en los datos.  El último RDF marcado en los datos será el que el comando <span class="keypress">at</span> utilice al marcar las notas:

{% include image.html
	file="second-mark.gif"
	alt="ejemplo de dos colores de marca."
	caption="Ejemplo de segunda marca (notas de color <span style='color:coral;'>coral</span>)."
%}

En este caso hay dos líneas de marcado RDF:

```
!!!RDF**kern: @ = marked note color=turquoise
!!!RDF**kern: N = marked note color=coral
```
Dado que el último utiliza `N` para la marca, al escribir <span class="keypress">at</span> se añadirá el carácter `N` a los tokens de la nota marcada en lugar de `@`.


## Significado de la marca ##

Los registros RDF son textos de forma libre, por lo que puedes añadir su propio texto a la línea que explica el significado de la marca.


```
!!!RDF**kern: @ = marked note color="orchid" strange note
```

Si desea un sistema más formalizado, utiliza `meaning="..."`:

```
!!!RDF**kern: @ = marked note color="orchid" meaning="strange note"
```
Este parámetro todavía no tiene ningún significado en el propio VHV, pero tal vez podría asignarse a un tooltip en la nota en el futuro.

## Atributo de clase SVG ##
En la notación SVG, las notas marcadas también se etiquetan con la clase `marcada`.  Esta etiqueta de clase puede utilizarse para cambiar el color y el estilo de las notas con CSS si la imagen SVG se coloca directamente en un documento HTML (en lugar de cargarse con un elemento `<image>`):

<style>

svg .note.marked {
        filter: url(#DropShadow);
}

svg .note.marked rect {
        fill: red;
}

svg .note.marked  use {
        fill: url(#MyHighlight);
}

</style>

<center>
<svg width="660px" height="492px" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" overflow="visible">
	<defs id="#myDefs">
		<linearGradient id="MyHighlight">
			<stop offset="0%" stop-color="yellow"/>
			<stop offset="100%" stop-color="red"/>
		</linearGradient>
		<filter id="DropShadow" height="130%" width="300%">
  			<feGaussianBlur in="SourceAlpha" stdDeviation="20"/>
  			<feOffset dx="30" dy="30" result="offsetblur"/>
  			<feMerge> 
    				<feMergeNode/>
    				<feMergeNode in="SourceGraphic"/>
  			</feMerge>
		</filter>
	</defs>
	<defs>
		<symbol id="E050" viewBox="0 0 1000 1000" overflow="inherit">
			<path transform="scale(1,-1)" d="M441 -245c-23 -4 -48 -6 -76 -6c-59 0 -102 7 -130 20c-88 42 -150 93 -187 154c-26 44 -43 103 -48 176c-4 60 11 123 44 189c29 57 65 106 110 148s96 85 153 127c-3 16 -8 46 -13 92c-4 43 -5 73 -5 89c0 117 16 172 69 257c34 54 64 82 89 82c21 0 43 -30 69 -92 s39 -115 41 -159c2 -120 -19 -173 -67 -256c-13 -20 -63 -90 -98 -118c-13 -9 -25 -19 -37 -29l31 -181c8 1 18 2 28 2c58 0 102 -12 133 -35c59 -43 92 -104 98 -184c11 -135 -80 -229 -180 -270c8 -57 17 -110 25 -162c5 -31 6 -58 6 -80c0 -30 -5 -53 -14 -70 c-35 -64 -88 -99 -158 -103c-42 -3 -83 6 -124 26c-50 24 -77 59 -80 105c-2 34 5 63 20 87c18 28 45 42 79 44c51 4 99 -40 103 -87c4 -56 -30 -94 -105 -115c17 -24 51 -36 102 -36c62 0 116 43 140 85c9 16 13 41 13 74c0 20 -1 42 -5 67c-8 53 -18 106 -26 159zM461 939 c-95 0 -135 -175 -135 -286c0 -24 2 -48 5 -71c50 39 92 82 127 128c43 57 63 106 60 148c-4 54 -23 82 -57 81zM406 119l54 -326c80 27 116 88 109 184c-7 99 -62 146 -163 142zM382 117c-74 -2 -132 -50 -128 -127c2 -46 43 -99 75 -115c-3 -2 -7 -5 -10 -10 c-70 33 -116 88 -123 172c-5 73 42 135 88 170c23 17 49 29 78 36l-29 170c-21 -13 -52 -37 -92 -73c-50 -44 -86 -84 -109 -119c-49 -75 -71 -140 -67 -195c5 -68 35 -127 93 -176s125 -73 203 -73c25 0 50 3 75 9c-19 111 -36 221 -54 331z" />
		</symbol>
		<symbol id="E084" viewBox="0 0 1000 1000" overflow="inherit">
			<path transform="scale(1,-1)" d="M0 -78c84 97 114 180 134 329h170c-13 -32 -82 -132 -99 -151l-84 -97c-33 -36 -59 -63 -80 -81h162v102l127 123v-225h57v-39h-57v-34c0 -43 19 -65 57 -65v-34h-244v36c48 0 60 26 60 70v27h-203v39z" />
		</symbol>
		<symbol id="E0A4" viewBox="0 0 1000 1000" overflow="inherit">
			<path transform="scale(1,-1)" d="M0 -39c0 68 73 172 200 172c66 0 114 -37 114 -95c0 -84 -106 -171 -218 -171c-64 0 -96 30 -96 94z" />
		</symbol>
		<symbol id="E0A3" viewBox="0 0 1000 1000" overflow="inherit">
			<path transform="scale(1,-1)" d="M96 -132zM200 138l41 -5c-2 0 -41 5 -41 5zM278 64c0 22 -17 39 -43 39c-12 0 -26 -3 -41 -10c-85 -43 -165 -94 -165 -156c5 -25 15 -32 49 -32c67 11 200 95 200 159zM0 -36c0 68 73 174 200 174c66 0 114 -39 114 -97c0 -84 -106 -173 -218 -173c-64 0 -96 32 -96 96z " />
		</symbol>
		<symbol id="E4C0" viewBox="0 0 1000 1000" overflow="inherit">
			<path transform="scale(1,-1)" d="M605 21zM0 0c0 3 3 17 4 21c61 306 268 299 300 299c29 0 238 7 300 -299c1 -4 1 -18 1 -21h-32c-1 1 -4 22 -5 25c-10 38 -52 202 -265 202c-208 0 -252 -159 -264 -200c-1 -4 -6 -26 -6 -27h-33zM358 52c0 -30 -25 -55 -55 -55c-29 0 -54 25 -54 55c0 29 25 54 54 54 c30 0 55 -25 55 -54z" />
		</symbol>
	</defs>
	<style type="text/css">g.page-margin{font-family:Times;} g.tempo{font-weight:bold;} g.dir, g.dynam {font-style:italic;}</style>
	<svg id="definition-scale" viewBox="0 0 8270 6160">
		<g class="page-margin" transform="translate(200, 200)">
			<g class="system" id="system-0000001397893969">
				<g class="section boundaryStart" id="section-0000000125448793" />
				<g class="measure" id="measure-L3">
					<g class="staff" id="staff-L3F1N1">
						<path d="M0 1145 L4712 1145" stroke="#000000" stroke-width="20" />
						<path d="M0 1325 L4712 1325" stroke="#000000" stroke-width="20" />
						<path d="M0 1505 L4712 1505" stroke="#000000" stroke-width="20" />
						<path d="M0 1685 L4712 1685" stroke="#000000" stroke-width="20" />
						<path d="M0 1865 L4712 1865" stroke="#000000" stroke-width="20" />
						<g class="clef" id="clef-0000001156431783">
							<use xlink:href="#E050" x="90" y="1685" height="720px" width="720px" />
						</g>
						<g class="meterSig" id="msig-0000001392121996">
							<use xlink:href="#E084" x="735" y="1325" height="720px" width="720px" />
							<use xlink:href="#E084" x="735" y="1685" height="720px" width="720px" />
						</g>
						<g class="layer" id="layer-L3F1N1">
							<g class="note marked" fill="orange" stroke="orange" id="note-L4F1">
								<path d="M1348 2045 L1672 2045" stroke="#000000" stroke-width="20" />
								<use xlink:href="#E0A4" x="1397" y="2045" height="720px" width="720px" />
								<rect x="1603" y="1415" height="608" width="20" />
							</g>
							<g class="note" id="note-L5F1">
								<path d="M2145 2045 L2469 2045" stroke="#000000" stroke-width="20" />
								<use xlink:href="#E0A4" x="2194" y="2045" height="720px" width="720px" />
								<rect x="2400" y="1415" height="608" width="20" />
							</g>
							<g class="note marked" fill="orange" stroke="orange" id="note-L6F1">
								<use xlink:href="#E0A4" x="2990" y="1685" height="720px" width="720px" />
								<rect x="3196" y="1055" height="608" width="20" />
							</g>
							<g class="note" id="note-L7F1">
								<use xlink:href="#E0A4" x="3787" y="1685" height="720px" width="720px" />
								<rect x="3993" y="1055" height="608" width="20" />
							</g>
						</g>
					</g>
					<g class="barLineAttr" id="bline-0000000279148015">
						<path d="M4697 1145 L4697 1865" stroke="#000000" stroke-width="30" />
					</g>
				</g>
				<g class="measure" id="measure-L8">
					<g class="staff" id="staff-L8F1N1">
						<path d="M4712 1145 L7871 1145" stroke="#000000" stroke-width="20" />
						<path d="M4712 1325 L7871 1325" stroke="#000000" stroke-width="20" />
						<path d="M4712 1505 L7871 1505" stroke="#000000" stroke-width="20" />
						<path d="M4712 1685 L7871 1685" stroke="#000000" stroke-width="20" />
						<path d="M4712 1865 L7871 1865" stroke="#000000" stroke-width="20" />
						<g class="layer" id="layer-L8F1N1">
							<g class="note marked" id="note-L9F1" fill="orange" stroke="orange">
								<use xlink:href="#E0A4" x="4938" y="1595" height="720px" width="720px" />
								<rect x="5144" y="965" height="608" width="20" />
							</g>
							<g class="note" id="note-L10F1">
								<use xlink:href="#E0A4" x="5734" y="1595" height="720px" width="720px" />
								<rect x="5940" y="965" height="608" width="20" />
							</g>
							<g class="note marked" id="note-L11F1" fill="orange" stroke="orange">
								<use xlink:href="#E0A3" x="6531" y="1685" height="720px" width="720px" />
								<rect x="6737" y="1055" height="608" width="20" />
							</g>
						</g>
					</g>
					<g class="barLineAttr" id="bline-0000001644616442">
						<path d="M7856 1145 L7856 1865" stroke="#000000" stroke-width="30" />
					</g>
				</g>
			</g>
			<g class="system" id="system-0000000916715061">
				<g class="measure" id="measure-L12">
					<g class="staff" id="staff-L12F1N1">
						<path d="M0 4295 L4448 4295" stroke="#000000" stroke-width="20" />
						<path d="M0 4475 L4448 4475" stroke="#000000" stroke-width="20" />
						<path d="M0 4655 L4448 4655" stroke="#000000" stroke-width="20" />
						<path d="M0 4835 L4448 4835" stroke="#000000" stroke-width="20" />
						<path d="M0 5015 L4448 5015" stroke="#000000" stroke-width="20" />
						<g class="clef" id="clef-0000001156431783">
							<use xlink:href="#E050" x="90" y="4835" height="720px" width="720px" />
						</g>
						<g class="layer" id="layer-L12F1N1">
							<g class="note marked" id="note-L13F1" fill="orange" stroke="orange">
								<use xlink:href="#E0A4" x="896" y="4925" height="720px" width="720px" />
								<rect x="1102" y="4295" height="608" width="20" />
							</g>
							<g class="note" id="note-L14F1">
								<use xlink:href="#E0A4" x="1752" y="4925" height="720px" width="720px" />
								<rect x="1958" y="4295" height="608" width="20" />
							</g>
							<g class="note marked" id="note-L15F1" fill="orange" stroke="orange">
								<use xlink:href="#E0A4" x="2608" y="5015" height="720px" width="720px" />
								<rect x="2814" y="4385" height="608" width="20" />
							</g>
							<g class="note" id="note-L16F1">
								<use xlink:href="#E0A4" x="3464" y="5015" height="720px" width="720px" />
								<rect x="3670" y="4385" height="608" width="20" />
							</g>
						</g>
					</g>
					<g class="barLineAttr" id="bline-0000000393483605">
						<path d="M4433 4295 L4433 5015" stroke="#000000" stroke-width="30" />
					</g>
				</g>
				<g class="measure" id="measure-L17">
					<g class="staff" id="staff-L17F1N1">
						<path d="M4448 4295 L7871 4295" stroke="#000000" stroke-width="20" />
						<path d="M4448 4475 L7871 4475" stroke="#000000" stroke-width="20" />
						<path d="M4448 4655 L7871 4655" stroke="#000000" stroke-width="20" />
						<path d="M4448 4835 L7871 4835" stroke="#000000" stroke-width="20" />
						<path d="M4448 5015 L7871 5015" stroke="#000000" stroke-width="20" />
						<g class="layer" id="layer-L17F1N1">
							<g class="note marked" id="note-L18F1" fill="orange" stroke="orange">
								<use xlink:href="#E0A4" x="4699" y="5105" height="720px" width="720px" />
								<rect x="4905" y="4475" height="608" width="20" />
							</g>
							<g class="note" id="note-L19F1">
								<use xlink:href="#E0A4" x="5555" y="5105" height="720px" width="720px" />
								<rect x="5761" y="4475" height="608" width="20" />
							</g>
							<g class="note" id="note-L20F1">
								<path d="M6362 5195 L6686 5195" stroke="#000000" stroke-width="20" />
								<use xlink:href="#E0A3" x="6411" y="5195" height="720px" width="720px" />
								<rect x="6617" y="4565" height="608" width="20" />
							</g>
						</g>
					</g>
					<g class="fermata" id="fermata-L20F1">
						<use xlink:href="#E4C0" x="6307" y="4248" height="720px" width="720px" />
					</g>
					<g class="barLineAttr" id="bline-0000001226619365">
						<path d="M7706 4295 L7706 5015" stroke="#000000" stroke-width="30" />
						<path d="M7826 4295 L7826 5015" stroke="#000000" stroke-width="90" />
					</g>
				</g>
				<g class="boundaryEnd section-0000000125448793" id="bdend0000000697861596" />
			</g>
		</g>
	</svg>
</svg>
</center>

La imagen de arriba fue creada marcando primero las notas en VHV, luego guardando el SVG (código SVG hecho visible con <span class="keypress">alt-g</span>) y luego insertado directamente en la página HTML, usando este estilo CSS:

```css
<style>
   svg .note.marked { filter: url(#DropShadow); }
   svg .note.marked rect { fill: red; }
   svg .note.marked  use { fill: url(#MyHighlight); }
</style>
```


Y añadiendo estos filtros a la parte superior del SVG:

```xml
<defs id="#myDefs">
   <linearGradient id="MyHighlight">
      <stop offset="0%" stop-color="yellow"/>
      <stop offset="100%" stop-color="red"/>
   </linearGradient>
   <filter id="DropShadow" height="130%" width="300%">
      <feGaussianBlur in="SourceAlpha" stdDeviation="20"/>
      <feOffset dx="30" dy="30" result="offsetblur"/>
      <feMerge> 
         <feMergeNode/>
         <feMergeNode in="SourceGraphic"/>
      </feMerge>
   </filter>
</defs>
```

{% include note.html
	content="En el futuro, la etiqueta de clase 'marked' podrá cambiarse en la línea RDF añadiendo 'class=\"algo\"'.  Esto permitirá una etiqueta de clase distinta para cada significante de marca."
%}



{% include warning.html
	content="Si se coloca más de una marca en una misma nota, sólo se mostrará un color."
%}



---
title: parámetros URL
lang: en es
ref: url-parameters
author: Craig Stuart Sapp
translator: David Rizo
creation_date: 26 Dec 2020
translation_date: 21 Aug 2021
last_updated: 26 Dec 2020
tags: [all]
keywords: interface url
summary: "Esta página enumera los parámetros de la URL que configuran la VHV a medida que se carga."
sidebar: main_sidebar
permalink: /topics/url-parameters/index-ES.html
---

{% include_relative scripts-local.html %}

Las URLs pueden incluir parámetros que se pasan a la página web de VHV.  Los parámetros se añaden a la dirección URL principal después del carácter ``.  Cada parámetro está separado del siguiente por `&` y cada parámetro consiste en un par de clave y valor que están separados entre sí por `=`.   A continuación se muestra un ejemplo de URL que contiene todas estas características:

<div style="padding-left:50px; margin-bottom:10px">
<a target="_blank" href="https://verovio.humdrum.org?k=Ebey&file=beethoven/sonatas/sonata01-1.krn">
https://verovio.humdrum.org?k=Ebey&file=beethoven/sonatas/sonata01-1.krn
</a>
</div>

Las piezas de la URL completa son:

<div markdown="1" style="padding-left:50px;">


`https://verovio.humdrum.org` 
: La parte principal de la URL. 

`?` 
: El inicio de la lista de parámetros. 

`k=Ebey` 
: El primer parámetro, siendo `k` el nombre del parámetro y `Ebey` el valor del parámetro `k`.

`&` 
: Carácter separador de parámetros. 

`file=beethoven/sonatas/sonata01-1.krn` 
: El segundo parámetro de la URL llamado `file` con un valor de `beethoven/sonatas/sonata01-1.krn`. 


</div>

El orden de los parámetros es indiferente, por lo que `k` puede ir, de forma equivalente, después de `file`:

<div style="padding-left:50px; margin-bottom:10px">
<a target="_blank" href="https://verovio.humdrum.org?file=beethoven/sonatas/sonata01-1.krn&k=Ebey">
https://verovio.humdrum.org?file=beethoven/sonatas/sonata01-1.krn&k=Ebey
</a>
</div>

Ten también en cuenta que ciertos caracteres no están permitidos dentro de los valores de los parámetros, como `&`, obviamente.  En su lugar, estos caracteres deben escaparse utilizando <a target="_blank" href="https://en.wikipedia.org/wiki/Percent-encoding">codificación de porcentaje</a>.  Además de la lista de esa página, las nuevas líneas deben escaparse como los caracteres `%0A`, los tabuladores como `%09` y los espacios como `%20`.  La codificación porcentual es un valor hexadecimal para los códigos de bytes ASCII (o generalmente UTF-8) del carácter.


## Parámetros de configuración ##

### k/keys ###

El parámetro `k` (forma larga `keys`) se puede utilizar para emular los atajos de teclado que se ejecutan inmediatamente después de cargar VHV.  Los caracteres de la siguiente tabla se dan en una cadena al parámetro. Aquí hay un ejemplo de uso para mostrar los controles mínimos en VHV:

<a target="_blank" href="https://verovio.humdrum.org/?k=Ebey&file=beethoven/sonatas/sonata01-1.krn">
https://verovio.humdrum.org/?k=Ebey&file=beethoven/sonatas/sonata01-1.krn
</a>

La cadena `Ebey` equivale a escribir
<a href="/commands/alt-E"><span class="keypress">alt-shift-E</span></a>,
<a href="/commands/alt-b"><span class="keypress">alt-b</span></a>,
<a href="/commands/alt-e"><span class="keypress">alt-e</span></a>,
<a href="/commands/alt-y"><span class="keypress">alt-y</span></a> después de la carga de VHV.  El orden de las letras no importa, por lo que `Ebey` y `bEey` son equivalentes.

<div style="height:20px"></div>

<style>
#ktable table td:first-child {
	width: 50px;
}
</style>

<div id="ktable" markdown="1">

| Carácter | Atajo&nbsp;VHV | Significado |
| --------- | ------------ | ------- |
| `B`       |  <a href="/commands/alt-B"><span class="keypress">alt-shift-B</span></a> | Ocultar la barra de herramientas. |
| `b`       |  <a href="/commands/alt-b"><span class="keypress">alt-b</span></a>       | Suprimir el logotipo de VHV en la parte superior izquierda de la ventana de VHV. |
| `d`       |  <a href="/commands/alt-d"><span class="keypress">alt-d</span></a>       | Ocultar el menú de la cabecera de la VHV. |
| `E`       |  <a href="/commands/alt-E"><span class="keypress">alt-shift-E</span></a> | Ocultar tanto el menú como las áreas de la barra de herramientas. |
| `e`       |  <a href="/commands/alt-e"><span class="keypress">alt-e</span></a>       | "Borrar": Suprimir la música de bienvenida al abrir VHV (o cualquier contenido anterior de la última visita).    | |
| `w`       |  <a href="/commands/alt-w"><span class="keypress">alt-w</span></a>       | Amplía el espaciado de la notación. Se pueden utilizar varios caracteres `w` para aumentar más el espaciado.        |
| `W`       |  <a href="/commands/alt-W"><span class="keypress">alt-shift-W</span></a> | Disminuye el espaciado de la notación.  Se pueden utilizar varios caracteres `W` para disminuir más el espaciado.       |
| `y`       |  <a href="/commands/alt-y"><span class="keypress">alt-y</span></a>       | Ocultar el editor de texto. |

## Parámetros de datos ##

Los parámetros `t` y `f` pueden utilizarse para precargar una partitura digital desde la URL.

### t/text ###

El parámetro `t` (o la forma larga `text`) se utiliza para cargar el texto del valor del parámetro en el editor de texto mientras se carga VHV.  Se pueden cargar dos formas de datos utilizando este parámetro: texto sin procesar o texto codificado MIME.  Este método es muy útil para cargar partituras cortas de ejemplo en VHV.  La longitud total de la URL, incluyendo los datos del parámetro `t`, no debe exceder de unos 2000 caracteres, aunque algunos navegadores web permiten URLs más largas, con el máximo real dependiendo del navegador web específico.

#### Datos de texto sin procesar para el parámetro t ####

En el caso del texto en bruto, los caracteres especiales de la URL deben escaparse utilizando <a target="_blank" href="https://en.wikipedia.org/wiki/Percent-encoding">codificación por defecto</a>.  Además, las nuevas líneas deben codificarse como `%0A`, los tabuladores como `%09` y los espacios como `%20`.  Escriba un texto en el siguiente cuadro, y debajo aparecerá una URL con el texto en bruto codificado en el parámetro `t`.

<textarea style="font-family:Courier; tab-size:12; -moz-tab-size:12; width:500px; height:200px;" id="raw" oninput="displayRawTextUrl()"
onkeydown="if(event.keyCode===9){var v=this.value,s=this.selectionStart,e=this.selectionEnd;this.value=v.substring(0, s)+'\t'+v.substring(e);this.selectionStart=this.selectionEnd=s+1;return false;}"
>**kern	**kern
*M4/4	*M4/4
=1	=1
1CC	1cc
=	=
*-	*-</textarea>

<br/>

Aquí hay una URL que contiene el contenido anterior en el parámetro `t` (haz clic para ver en VHV):
<div style="margin-top:20px;"  id="raw-url"></div>
<div style="margin-top:20px" id="raw-counter"></div>


<div style="30px;"></div>

#### Datos codificados MIME para el parámetro t ####

Este es un ejemplo de texto codificado en MIME:

<a target="_blank" href="https://verovio.humdrum.org/?t=KiprZXJuCjFjCj0KKi0">
https://verovio.humdrum.org/?t=KiprZXJuCjFjCj0KKi0
</a>


La cadena `KiprZXJuCjFjCj0KKi0` es el siguiente texto codificado MIME:

```tsv
**kern
1c
=
*-
```

Esto será decodificado e insertado en el editor de texto VHV cuando se haga clic en el enlace anterior.

Puedes añadir algún texto en el cuadro de abajo y se mostrará una URL a VHV con el parámetro `t` rellenado con el texto codificado MIME:

<textarea style="font-family:Courier; tab-size:12; -moz-tab-size:12; width:500px; height:200px;" id="mime" oninput="displayMimeUrl()"
onkeydown="if(event.keyCode===9){var v=this.value,s=this.selectionStart,e=this.selectionEnd;this.value=v.substring(0, s)+'\t'+v.substring(e);this.selectionStart=this.selectionEnd=s+1;return false;}"
>**kern	**kern
*M4/4	*M4/4
=	=
1CC	1cc
=	=
*-	*-
</textarea>
<div style="margin-top:20px;"  id="mime-url"></div>
<div style="margin-top:20px" id="mime-counter"></div>


### f/file ###

El parámetro `f` (o la forma larga `file`) se utiliza para cargar una partitura digital en el editor.  El valor puede ser una partitura del repertorio incorporado, o una URL arbitraria a una partitura disponible en la web.  Si carga una partitura utilizando `http://` (HTTP no seguro), entonces debes utilizar la dirección no segura de VHV ([http://verovio.humdrum.org](http://verovio.humdrum.org)); de lo contrario, las partituras cargadas con `https://` pueden cargarse desde [http://verovio.humdrum.org](http://verovio.humdrum.org) o [https://verovio.humdrum.org](https://verovio.humdrum.org).


#### Repertorios ####

Se puede cargar un archivo [repertorio](/repertory) en el editor si no hay un prefijo `https://` en el valor del parámetro `archivo`.  Esto también colocará los botones de navegación del repertorio en la parte superior izquierda de la barra de navegación en VHV.  A continuación se muestran ejemplos de carga de archivos de repertorio.  Puede hacer clic en la flecha hacia arriba del repertorio para ver un índice de otras partituras en el mismo repertorio.

<dl>

<dt>
	Beethoven, Sonata para piano nº 1 en Fa mayor, mvmt. 1:
</dt>
<dd>
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=beethoven/sonatas/sonata01-1.krn">
	https://verovio.humdrum.org/?k=ey&file=beethoven/sonatas/sonata01-1.krn
	</a>
</dd>

<dt>
	Mozart, Sonata para piano nº 1 en Do mayor, K 279/189d, mvmt. 1:
</dt>
<dd>
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=mozart/sonatas/sonata01-1.krn">
	https://verovio.humdrum.org/?k=ey&file=mozart/sonatas/sonata01-1.krn
	</a>
</dd>

<dt>
	Scarlatti, Sonata para teclado en Do mayor, L.1/K.514:
</dt>
<dd>
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=scarlatti/sonatas/L001K514.krn">
	https://verovio.humdrum.org/?k=ey&file=scarlatti/sonatas/L001K514.krn
	</a>
</dd>

<dt>
	Chopin, Estudio en Do sostenido menor, op. 10, no. 3 del <a target="_blank" href="https://www.nifc.pl">Instituto Fryderyk Chopin</a>:
</dt>
<dd>
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=chopin-first-editions/010_1-6-1b-KI-004.krn">
	https://verovio.humdrum.org/?k=ey&file=chopin-first-editions/010_1-6-1b-KI-004.krn
	</a>
</dd>

<dt>
	J.S. Bach, Coral <i>Aus meines Herzens Grunde</i>, BWV 269:
</dt>
<dd>
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=chorales/chor001.krn">
	https://verovio.humdrum.org/?k=ey&file=chorales/chor001.krn
	</a>
</dd>

<dt>
	Givaonnelli, <i>Non è questa la mano</i>, (1588) madrigal del proyecto <a target="_blank" href="https://www.tassomusic.org/work?Trm0047m">Tasso in Music</a>.
</dt>
<dd>
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=tasso/Trm/Trm0047m-Non_e_questa_la_mano--Giovannelli_1588.krn">
	https://verovio.humdrum.org/?k=ey&file=tasso/Trm/Trm0047m-Non_e_questa_la_mano--Giovannelli_1588.krn
	</a>
</dd>

</dl>

Observa que cuando carga una partitura del repertorio, hay botones de navegación del repertorio en la esquina superior izquierda de VHV que le permiten navegar por otros archivos del repertorio o ver un índice de todas las partituras del repertorio.

#### Índices de repertorio #####

Puedes abrir VHV con la lista de todas las obras del repertorio enumerando la ruta del repertorio sin un nombre de archivo:


<div style="padding-left:50px; margin-bottom:10px">
<a target="_blank" href="https://verovio.humdrum.org?k=Ebey&file=beethoven/sonatas">
https://verovio.humdrum.org?k=Ebey&file=beethoven/sonatas
</a>
</div>

A continuación, puedes elegir un archivo específico del repertorio para verlo en VHV.  También puede pulsar la tecla <span class="keypress">esc</span> para cerrar el índice del repertorio sin elegir una partitura para cargar.


### URLs de archivos ###

VHV sabe dónde se encuentran los archivos de repertorio incorporados en la web, pero si necesitas cargar un archivo que desconoce, puedes dar la dirección URL completa del archivo digital.


Por ejemplo, la ubicación del repertorio del ejemplo del movimiento de la sonata de Beethoven dado anteriormente es:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=beethoven/sonatas/sonata01-1.krn">
	https://verovio.humdrum.org/?k=ey&file=beethoven/sonatas/sonata01-1.krn
	</a>
</div>

Esto puede ampliarse hasta convertirse en una URL completa que indique la ubicación real del archivo en la web:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata01-1.krn">
	https://verovio.humdrum.org/?k=ey&file=https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata01-1.krn
	</a>
</div>

que carga la partitura desde este enlace:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata01-1.krn">
	https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata01-1.krn
	</a>
</div>


#### Atajos #####

Varios repertorios y sitios web tienen métodos de acceso directo para evitar especificar un nombre de archivo o una URL completos.


##### Atajos de Github #####

Github URLs can be long:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata01-1.krn">
	https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata01-1.krn
	</a>
</div>

Estas URLs de Github se pueden condensar en esta forma para el parámetro `file`:

<div markdown="1" style="padding-left:20px; margin-bottom:10px;">
`github:username/repository/path-to-file/filename`
</div>

Observa que el nombre del directorio `master` se omite ya que es el directorio raíz real de los archivos del repositorio y no un nombre de directorio dentro del repositorio.  La URL completa de la partitura digital de Beethoven en Github se puede condensar en:

<div markdown="1" style="padding-left:20px; margin-bottom:10px;">
`github:craigsapp/beethoven-piano-sonatas/kern/sonata01-1.krn`
</div>

El resultado es que el enlace directo de la VHV a esa partitura se acorta a:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org?k=ey&file=github:craigsapp/beethoven-piano-sonatas/kern/sonata01-1.krn">
	https://verovio.humdrum.org?k=ey&file=github:craigsapp/beethoven-piano-sonatas/kern/sonata01-1.krn
	</a>
</div>

##### Accesos directos al repertorio #####

Varios repertorios tienen nombres largos para los archivos que consisten en un número de catálogo para el procesamiento computacional, seguido del título de la obra para la legibilidad humana.  VHV tiene un acceso directo que permite cargar la partitura del repertorio basándose en un número de catálogo en lugar de en el nombre completo del archivo y la ruta de acceso al mismo en el repositorio.

Por ejemplo, el enlace del repertorio para el ejemplo <a target="_blank" href="https://www.tassomusic.org">Tasso en el proyecto musical</a> funciona:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=tasso/Trm/Trm0047m-Non_e_questa_la_mano--Giovannelli_1588.krn">
	https://verovio.humdrum.org/?k=ey&file=tasso/Trm/Trm0047m-Non_e_questa_la_mano--Giovannelli_1588.krn
	</a>
</div>

Puede tener la ruta completa del repertorio y el nombre reducido de:

<div markdown="1" style="padding-left:20px; margin-bottom:10px;">
`tasso/Trm/Trm0047m-Non_e_questa_la_mano--Giovannelli_1588.krn`
</div>

to:

<div markdown="1" style="padding-left:20px; margin-bottom:10px;">
`tasso:Trm0047m`
</div>

en el enlace VHV a la partitura:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=tasso:Trm0047m">
	https://verovio.humdrum.org/?k=ey&file=tasso:Trm0047m
	</a>
</div>

<a target="_blank" href="https://josquin.stanford.edu">Las partituras del Josquin Research Project</a> también pueden cargarse desde un acceso directo al repertorio.  Los nombres completos del repertorio para estos archivos pueden ser condensados desde:


<div markdown="1" style="padding-left:20px; margin-bottom:10px;">
`jrp/Ock/Ock2002-Ave_Maria.krn`
</div>

to:

<div markdown="1" style="padding-left:20px; margin-bottom:10px;">
`jrp:Ock2002`
</div>

lo que resulta en una URL VHV más corta:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=jrp:Ock2002">
	https://verovio.humdrum.org/?k=ey&file=jrp:Ock2002
	</a>
</div>


## Parámetros de búsqueda ##

Los tres parámetros `p`, `r` e `i` pueden utilizarse para buscar tonos, ritmos y/o intervalos.  Estos parámetros se cargarán en la <a target="_blank" href="/interface/search">barra de herramientas de búsqueda</a> cuando se cargue VHV, y la herramienta de búsqueda se activará y se realizará una búsqueda tan pronto como se haya cargado la partitura.

### p/pitch (altura, tono) ###

Este es un ejemplo de búsqueda del tema inicial de la sonata para piano nº 1 de Beethoven. 1, mvmt. 1:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=beethoven/sonatas/sonata01-1.krn&p=cfacfagfef">
	https://verovio.humdrum.org/?k=ey&file=beethoven/sonatas/sonata01-1.krn&p=cfacfagfef
	</a>
</div>

Esto busca la secuencia de clase de nota diatónica `C F A C F A G F E F`.

### r/ritmo ###

Busca el patrón rítmico `16 8 16 8 16` en <i>The Entertainer</i> de Joplin:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=joplin/entertainer.krn&r=16,8,16,8,16">
	https://verovio.humdrum.org/?k=ey&file=joplin/entertainer.krn&r=16,8,16,8,16
	</a>
</div>


### i/intervalo ###

Buscar la secuencia de intervalos diatónicos `8 -2 2 -8` (subir una octava, bajar un tono, subir un tono, bajar una octava) en la sonata para piano nº 1 de Mozart. 1, mvmt. 1:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=mozart/sonatas/sonata01-1.krn&k=ey&i=8-22-8">
	https://verovio.humdrum.org/?k=ey&file=mozart/sonatas/sonata01-1.krn&k=ey&i=8-22-8
	</a>
</div>



## F/filtro ##

El parámetro `filter` puede utilizarse para procesar una partitura de entrada con uno o más <a target="_blank" href="/filter">filtros</a> después de que la partitura se haya cargado en VHV.  Ten en cuenta que, al igual que con todos los valores de los parámetros, algunos caracteres deben estar <a target="_blank" href="https://en.wikipedia.org/wiki/Percent-encoding">codificados</a>.

### Filtro único ###

He aquí un ejemplo de transposición del movimiento de la sonata para piano de Beethoven de Fa menor a La menor:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=beethoven/sonatas/sonata01-1.krn&filter=transpose%20-ka">
	https://verovio.humdrum.org/?k=ey&file=beethoven/sonatas/sonata01-1.krn&filter=transpose%20-ka
	</a>
</div>

El filtro es `transpose -ka`, que significa transponer la partitura a la tonalidad de La (menor en este caso, ya que se conserva la modalidad). Los caracteres `%20` es la codificación porcentual de un carácter de espacio.

### Varios filtros ###

Se pueden serializar filtros separados en el parámetro de filtro separándolos con un carácter de tubería (`|`).  Los filtros se aplicarán en el orden en que estén colocados en la cadena de filtros.  He aquí un ejemplo de visualización de un coral de Bach en formato de gran pentagrama y luego colorear las sonoridades triádicas:

`satb2gs|colortriads`

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?file=chorales/chor075.krn&filter=satb2gs%7Ccolortriads">
	https://verovio.humdrum.org/?file=chorales/chor075.krn&filter=satb2gs%7Ccolortriads
	</a>
</div>

El carácter de tubería es `%7C` en codificación porcentual.


### Filtrado y búsqueda ###

El parámetro `filter` puede mezclarse con las búsquedas musicales.  Este es un ejemplo de extracción de las notas superiores de los acordes antes de buscar el ritmo `16 8 16 8 16` en <i>The Entertainer</i> de Jopin.

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=joplin/entertainer.krn&r=16,8,16,8,16&filter=chord%20-t">
	https://verovio.humdrum.org/?k=ey&file=joplin/entertainer.krn&r=16,8,16,8,16&filter=chord%20-t
	</a>
</div>

Compara con la misma búsqueda sin el filtro:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=joplin/entertainer.krn&r=16,8,16,8,16">
	https://verovio.humdrum.org/?k=ey&file=joplin/entertainer.krn&r=16,8,16,8,16
	</a>
</div>


## tb/Toolbar (Barra de herramientas) ##

Establecer la barra de herramientas visible.


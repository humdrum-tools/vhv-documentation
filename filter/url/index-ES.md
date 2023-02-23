---
title: filtros URL
lang: en es
page_language: es
translator: David Rizo
translation_date: 9 Aug 2021
translation_update:
ref: filters-url
tags: [all, filters]
sidebar: main_sidebar
keywords: url filters
summary: Los filtros pueden aplicarse a través de una URL de VHV al cargar los repertorios en línea.  El filtro se aplicará a todas las obras/movimientos del mismo repertorio, incluso cuando se inicie en una obra/movimiento concreto. 
permalink: /filter/url/index-ES.html
---

Esta es una URL sencilla para cargar un coral de J.S. Bach:

```
http://verovio.humdrum.org/?file=chorales/chor025.krn
```

{% include image.html
	file="chor025.png"
	alt="Bach chorale #25"
	max-width="80%"
	caption="Viewing URL without filtering"
%}


## Filtro simple ##
Los filtros pueden incluirse en las URLs añadiendo un parámetro llamado `filter` seguido por el comando de filtro o una cadena de comandos de filtro. Este es un ejemplo en el que se añade la cadena `&filter=` al final de la URL, y luego un filtro, como [myank](/filter/myank) para extraer un rango de compases de la partitura completa:

```
http://verovio.humdrum.org/?file=chorales/chor025.krn&filter=myank%20-m3-5
```
Esto hará que los compases 3-5 del coral se extraigan de la partitura completa y se muestren en notación gráfica:

{% include image.html
	file="chor025-myank.png"
	alt="Bach chorale #25"
	max-width="80%"
	caption="Viewing result of URL with filter \"myank -m3-5\""
%}

El filtro incrustado correspondiente de Humdrum-data sería:

```
!!!filter: myank -m3-5
```

### Codificación porcentual ###

El carácter espacio debe convertirse en `%20` en las URL, ya que no se permite un espacio directamente en una URL.  Algunos otros caracteres no permitidos en las URL, y su [codificación porcentual](https://en.wikipedia.org/wiki/Percent-encoding), son:

| Carácter     |   Codificación |
|---------------|------------|
| espacio         |  %20       |
| "             |  %22       |
| %             |  %25       |
| \| (tubería)     |  %7C       |


## Filtro de tubería ##
Se puede aplicar más de un filtro desde la URL separando los filtros con un carácter de tubería, `|`.  Ten en cuenta que el carácter tubería no está permitido directamente en una URL, por lo que debe ser escapado como `%7c`.  Aquí hay una línea de tubería de filtro que primero extrae los compases 3 a 5 de la partitura, y luego cambia la disposición a gran pentagrama:


```
!!!filter: myank -m 3-5 | satb2gs
```

Algunos de los espacios son opcionales, por lo que es mejor eliminarlos cuando se utiliza como filtro de URL para evitar codificaciones innecesarias de `%20` de caracteres de espacio:

```
!!!filter: myank -m3-5|satb2gs
```

Converting this into a URL filter:

```
http://verovio.humdrum.org/?file=chorales/chor025.krn&filter=myank%20-m3-5%7csatb2gs
```

{% include image.html
	file="chor025-35gs.png"
	alt="Bach chorale #25"
	max-width="80%"
	caption="Viewing URL with filter \"myank -m3-5\""
%}

## Filtrado del repertorio ##
Al navegar a otras obras/movimientos del mismo repertorio, el filtro de URL se aplicará a todo el repertorio.  Además, el filtro puede añadirse a la URL del índice del repertorio.  He aquí un ejemplo de visualización de todas las sonatas para piano de Mozart transpuestas a una tónica en Do (conservando el modo original):

```
http://verovio.humdrum.org/?file=mozart/sonatas&filter=transpose%20-kc
```
El filtrado no será inmediatamente evidente, ya que se muestra el índice del repertorio:


{% include image.html
	file="mozart-index.png"
	alt="Mozart piano sonata index"
	max-width="80%"
	caption="Mozart piano sonata repertory index"
%}

Sin embargo, al seleccionar el movimiento 1 de la sonata D&uuml;nitz aparecerá la música en Do mayor en lugar de Re mayor:


{% include image.html
	file="mozart-cmajor.png"
	alt="Mozart sonata k284 transposed to C major"
	max-width="80%"
	caption="Sonata para piano de Mozart en Re mayor, K284/205b, mvmt. 1, transpuesta a Do mayor"
%}


## Compilación de filtros de URL ##
Los resultados del filtrado, tanto en la URL como incrustados directamente en los datos, son visibles en el editor de notación gráfica, pero no en los datos del editor de texto.  Para generar la notación, los filtros en los datos o en la URL se aplican antes de convertirlos a MEI y renderizarlos en imágenes SVG.  Si deseass ver los datos resultantes del filtrado, escriba [alt-c](/commands/alt-c) para compilar el filtro.  A continuación se muestra la vista del ejemplo de la sonata anterior, en la que los datos de Humdrum se han transpuesto ahora a Do mayor, así como en la notación gráfica:

{% include image.html
	file="mozart-altc.png"
	alt="Mozart sonata k284 transposed to C major, in data as well"
	max-width="80%"
	caption="Post-filtered Humdrum data displayed in text editor"
%}


{% include warning.html
	content="La edición gráfica no suele funcionar cuando se aplican filtros a una partitura en el editor de texto.  Al escribir <span class='keypress'>alt-c</span> se permitirá que la edición gráfica funcione correctamente en los datos."
%}

## Con los comandos de la interfaz URL ##
Los comandos de interfaz no son exactamente filtros, pero son útiles en combinación con los parámetros de los filtros. Muchos comandos de interfaz (que son combinaciones de teclas que empiezan por <span class="keypress">alt</span>) pueden añadirse a la URL.  Para añadir uno o varios comandos de interfaz, incluye el parámetro `&k=` seguido de la lista de caracteres del comando de interfaz, excluyendo el prefijo `alt-`.  Por ejemplo, <span class="keypress">alt-y</span> se convierte en `&k=y`.  En la cadena de parámetros `k` se pueden colocar varios comandos, sin necesidad de espacios entre los caracteres.  La siguiente URL:

```
http://verovio.humdrum.org/?file=mozart/sonatas/sonata06-1.krn&filter=transpose%20-kc&k=by
```
ocultará el editor de texto (equivalente a escribir <span class="keypress">alt-y</span> en VHV), y también ocultará el logo de VHV (equivalente a escribir <span class="keypress">alt-b</span> en VHV).  Aquí está la pantalla resultante para la URL anterior:

{% include image.html
	file="mozart-by.png"
	alt="La sonata de Mozart k284 transpuesta a Do mayor, también en datos"
	max-width="80%"
	caption="El editor de texto y el logotipo se suprimen al añadir '&k=by' a la URL"
%}




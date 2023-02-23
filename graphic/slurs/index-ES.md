---
title: Ligaduras de expresión
lang: en es
page_language: es
translator: David Rizo
translation_date: 9 Aug 2021
translation_update:
ref: graphic-slurs
tags: [all, graphic_editing, RDF]
sidebar: main_sidebar
datatable: "true"
vim: ts=3
keywords: graphic editing slurs
summary: Añadir y editar gráficamente las ligaduras en el editor de notación.
permalink: /graphic/slurs/index-ES.html
---

## Resumen de comandos clave ##

{% include keytable.html
	contentId="slurkeysummary"
%}
<script type="text/JSON" id="slurkeysummary">
{% include keypresses/slurkeys.json %}
</script>


## <span class="keypress">s</span>: Añadir una simple ligadura ##
Después de hacer clic en una nota en el editor de notación, pulsa la tecla <span class="keypress">s</span> para añadir una ligadura a la siguiente nota:

{% include image.html
	file="add-slurs.gif"
	alt="añadir ligaduras a la notación"
	max-width="75%"
	caption="Escribe <span class='keypress'>s</span> después de seleccionar una nota para añadir una ligadura."
%}

Observa que se añaden a los datos de Humdrum que un par de paréntesis para marcar el inicio y el final de la ligadura en el editor de texto de la izquierda a medida que las ligaduras aparecen en la notación.

Después de añadir la ligadura, el foco de atención se desplaza a la ligadura, que aparecerá resaltada en rojo, para permitir la edición posterior de la misma.

## <span class="keypress">a</span>, <span class="keypress">b</span>, <span class="keypress">c</span>: Orientación de las ligaduras ##

Las ligaduras se pueden forzar por encima o por debajo de las notas utilizando la tecla <span class="keypress">a</span> para forzar *por encima* o <span class="keypress">b</span> para forzar *por debajo*.  Estos dos comandos se buscarán en los datos de Humdrum como una línea RDF en el formulario:

```humdrum
!!!RDF**kern: > = above
!!!RDF**kern: < = below
```

Estos dos significantes RDF, que podrían asignarse a otros caracteres (aunque normalmente se utilizan "`<`" y "`>`"), se utilizan para indicar una dirección forzada en muchos elementos gráficos, incluidas las ligaduras.  Si los significantes "arriba"/"abajo" no se encuentran en los datos, se añadirán automáticamente la primera vez que se dé una orden de dirección forzada.  Puede eliminar una dirección forzada escribiendo <span class="keypress">c</span> para *borrarla*.

{% include image.html
	file="slur-orientation.gif"
	alt="añadir ligaduras a la notación"
	caption="Type <span class='keypress'>a</span> para forzar las ligaduras por encima, 
	              <span class='keypress'>b</span> para forzar las ligaduras abajo, y
	              <span class='keypress'>c</span> para quitar las direcciones forzadas."
%}

## <span class="keypress meta">#</span> <span class="keypress">s</span>: Añadir ligaduras extendidas ##
Si se escribe <span class="keypress">s</span> mientras se edita una nota, se añadirá una ligadura a la siguiente nota; sin embargo, la ligadura puede ampliarse a medida que se crea escribiendo un dígito desde <span class="keypress">2</span> hasta <span class="keypress">9</span> para extenderse de dos a nueve notas después de la nota actual.


{% include image.html
	file="add-long-slur.gif"
	alt="añadir ligaduras largas a la notación"
	max-width="75%"
	caption="Añadir ligaduras largas escribiendo un dígito antes de <span class='keypress'>s</span>."
%}

## Mover ligaduras ##
Una vez que se ha añadido una ligadura a la notación, se puede desplazar pulsando <span class="keypress">&larr;</span>/<span class="keypress">&rarr;</span> para mover el principio de la ligadura hacia delante o hacia atrás en la música, o <span class="keypress">shift-left</span>/<span class="keypress">shift-left</span> para mover el final de la ligadura.

{% include image.html
	file="move-slurs.gif"
	alt="mover las ligaduras después de haberlas creado"
	max-width="75%"
	caption="Mover las ligaduras después de haberlas creado."
%}

{% include note.html
	content="Mientras se edita una Ligadura, las teclas <span class='keypress'>&larr;</span>/<span class='keypress'>&rarr;</span> no están disponibles para sus funciones habituales de desplazamiento a la página siguiente/anterior.  Para pasar a una nueva página con las teclas de dirección, pulsa la tecla <span class='keypress'>esc</span> para anular la selección de la Ligadura."
%}




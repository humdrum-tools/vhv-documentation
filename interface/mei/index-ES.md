---
title: MEI export
lang: en es
page_language: es
translator: Olga Francés Zoroa
translation_date: 6 Jun 2021
translation_update:
ref: interface-mei
tags: [all, getting_started]
keywords: interface mei
summary: "MEI files can be generated from Humdrum data and saved to the local file-system."
sidebar: main_sidebar
permalink: /interface/mei/index-ES.html
---

## Arrastar y soltar archivos MEI
##

La interfaz VHV puede cargar archivos MEI si los arrastras y los sueltas desde el escritorio hasta la página de VHV.  Si además presionas la tecla <span class="keypress">shift</span> mientras arrastras y sueltas los datos MEI, primero aparecerán convertidos en datos Humdrum, y después estos se colocarán en el editor de texto.

{% include note.html
content="La conversión de MEI a Humdrum no es tan avanzada como la que realiza el conversor de MusicXML a Humdrum, por lo que datos MEI más complejos podrían no convertirse a Humdrum correctamente todavía."
%}

## Conversión de datos MEI a Humdrum
##

Si los datos MEI se muestran en el editor de texto, puedes usar la opción "convertir a Humdrum" que hay en el menú si presionas "Editar", para convertir los datos MEI en datos Humdrum, lo que remplazaría los datos MEI del editor de texto.

## Visualizar datos MEI en el editor de texto
##

VHV convierte dinámicamente los datos Humdrum a datos MEI para producir anotaciones gráficas de música.  La conversión a MEI normalmente se realiza de forma automática, pero estos datos se pueden visualizar en el editor de texto presionando <span class="keypress">alt-m</span>.  Para volver a visualizar los datos Humdrum presiona <span class="keypress">alt-h</span>.

{% include image.html
file="mei-humdrum-toggle.gif"
alt="MEI / humdrum toggle example"
caption="Los datos Humdrum convertidos a MEI con <span class=',eypress'>alt-m</span> y convertidos a Humdrum de nuevo con <span class=',eypress'>alt-h</span>."
%}

Los datos MEI pueden editarse, y el contenido del editor de notación se actualizará para que se muestren los cambios ([<span class='keypress'>alt-f</span>](/commands/alt-f) puede ser de utilidad al editar los datos MEI).  Puedes pinchar en una nota en el editor de notación y se visualizará su elemento MEI correspondiente; sin embargo, los comandos de edición gráfica no funcionarán con los datos MEI.


{% include warning.html
content=" Volver a la visualización Humdrum con el comando <span class='keypress'>alt-h</span> hará que se pierda cualquier cambio en los datos MEI."
%}

### Copiar y pegar para exportar
###

Los datos MEI se pueden seleccionar en el editor de texto y se pueden copiar y pegar en
otro editor de texto en el sistema operativo; en caso de que sea de otra forma, la siguiente sección
describe cómo guardar los datos MEI en un archivo local.

## Descarga de archivos MEI
##

Cuando veas los datos MEI en el editor de texto, escribe
<span class="keypress">alt-s</span> para guardar el contexto del
editor de texto en un archivo llamado `datos.txt`.  El archivo se guardará en cualquier lugar donde
tu navegador guarde archivos, como en **Documentos**.

A continuación, puedes ver una demostración de la conversión de los datos de Humdrum a datos MEI
pulsando
<span class="keypress">alt-m</span>
y luego guardándolos en un archivo en el disco local con la tecla
<span class="keypress">alt-s</span>:

{% include image.html
file="mei-save.gif"
alt="MEI save example"
max-width="100%"
caption="Contenido MEI mostrado con <span class='keypress'>alt-m</span> y luego guardado con <span class='keypress'>alt-s</span>."
%}


## Carga de archivos MEI al arrastrar y soltar
##

La interfaz de VHV puede cargar archivos MEI arrastrándolos y soltándolos desde el escritorio
en la página VHV:

{% include image.html
file="mei-import.gif"
alt="MEI import example"
max-width="100%"
caption="Archivo MEI importado al arrastrarlo y soltarlo en VHV."
%}

Intenta descargar el [mismo archivo MEI](bwv1011-sarabande.mei) y
cargarlo en VHV de forma similar (normalmente se guarda haciendo clic con el botón derecho
en el enlace y luego eligiendo *guardar enlace como*).


{% include warning.html
content="Los comandos de edición de notación gráfica no se pueden utilizar cuando los datos MEI se cargan en el editor de texto, ya que estos comandos operan solo con los datos de Humdrum."
%}

## Copiar y pegar los datos del MEI en un editor de texto
##

Los datos MEI pueden copiarse y pegarse desde otra fuente en el editor de texto VHV
en el editor de texto de la VHV.  La notación se generará dinámicamente a partir de los datos MEI
y se actualizará a medida que se modifique el contenido del MEI, pero si escribes
<span="keypress">alt-h</span> los datos MEI no se convertirán en
datos Humdrum.







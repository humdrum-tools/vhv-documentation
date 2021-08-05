---
title: Importación de datos EsAC
lang: en es
ref: interface-esac
author: Craig Stuart Sapp
translator: Olga Francés Zoroa
creation_date: 10 Jun 2017
translation_date: 6 Jun 2021
last_updated: 10 Jun 2017
tags: [all]
keywords: interface esac
summary: "Se pueden arrastrar ficheros EsAC en la página de VHV page para convertirlos automáticamente en datos Humdrum. También se pueden pegar datos EsAC en el editor de texto para editarlos como datos EsAC."
sidebar: main_sidebar
permalink: /interface/esac/index-ES.html
---

## Arrastrar y soltar archivos EsAC


La interfaz de VHV puede cargar archivos EsAC arrastrándolos y soltándolos desde el escritorio a la página de VHV.   La siguiente imagen muestra cómo arrastrar un
archivo de datos EsAC desde el escritorio al navegador,
cargar el archivo en VHV:


{% include image.html
file="import-esac.gif"
alt="EsAC import example"
max-width="100%"
caption="Los datos de EsAC se importan arrastrando y soltando en VHV."
%}

Intenta descargar el [mismo archivo EsAC](b0029.txt) y cargarlo en VHV de forma similar (normalmente se guarda haciendo clic con el botón derecho del ratón en el enlace y luego se elige *guardar enlace como*).


## Copiar/pegar datos de EsAC


Los datos EsAC también pueden copiarse/pegarse en el editor de texto de VHV.  En este caso VHV
se comporta como un editor EsAC, ya que los datos no se convierten al formato Humdrum
dentro del editor de texto:

{% include image.html
file="paste-esac.gif"
alt="EsAC data pasting example"
max-width="100%"
caption="Datos de EsAC pegados en VHV."
%}


El [comando para congelar](/commands/alt-f) (<span class="keypress">alt-f</span>)
es útil a la hora de pausar la representación de la notación dinámica mientras se editan los datos de EsAC.
A veces, el contenido no válido causará problemas si no se utiliza el
comando para congelar mientras se edita.

### Filtros Humdrum en EsAC


En los datos de EsAC se pueden utilizar filtros de tipo Humdrum.  Aquí puedes ver una demostración
de la adición del filtro *autobeam* para que las notas se transmitan automáticamente por el compás.

{% include image.html
file="autobeam-esac.gif"
alt="EsAC autobeam filtering example"
max-width="100%"
caption="Datos EsAC con el filtro de barras de Humdrum aplicado."
%}

### Guardar los datos EsAC


Los datos EsAC visibles en el editor de texto pueden descargarse con la combinación de teclas
<span class="keypress">alt-s</span>. El archivo se
guardará en cualquiera de los lugares en los que tu navegador descargue archivos.

Además, el contenido del editor de texto se puede copiar/pegar en otro diferente.


{% include warning.html
content="Los comandos de edición de la notación gráfica no pueden utilizarse cuando los datos de EsAC se carguen en el editor de texto, ya que estos comandos operan solo con los datos Humdrum."
%}


### Generar notación en el navegador


Para ver un ejemplo de generación de notación musical dentro de una página web a partir de los datos EsAC, vea [esta página](/myvhv/static-esac).


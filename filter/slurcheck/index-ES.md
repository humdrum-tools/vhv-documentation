---
title: filtro slurcheck
lang: en es
ref: filters-slurcheck
author: Craig Stuart Sapp
translator: David Rizo
creation_date: 31 Jul 2018
translation_date: 9 Aug 2021
last_updated: 31 Jul 2018
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
datatable: "true"
keywords: slur checking command
summary: "El filtro slurcheck puede utilizarse para identificar automáticamente los marcadores de ligaduras de expresión
en las columnas de datos de **kern."
permalink: /filter/slurcheck/index-ES.html
---


## Uso del filtro slurcheck en VHV

Aquí hay una demostración animada del uso de la herramienta `slurcheck` en [VHV](http://verovio.humdrum.org):

{% include image.html
	file="animated-slurcheck.gif"
	alt="Identifying and fixing unbalanced slurs"
	caption="Identifying and fixing unbalanced slurs in VHV."
%}

Las ligaduras de inicio, `(`, o de finalización `)` que no se emparejan con las respectivas marcas de finalización/comienzo se resaltan en rosa.

Intenta arreglar las ligaduras en el siguiente ejemplo, o añade finalizaciones de ligadura desemparejadas al ejemplo.  Las ligaduras se pueden arreglar eliminando el punto final de ligadura desequilibrado, o añadiendo un punto final de ligadura  para abrir/cerrar la ligadura.

{% include verovio.html
	source="slurcheck1"
	scale="60"
	humdrum-min-height="350px"
	pageWidth="1450"
	tabsize="16"
%}

<script type="application/json" id="slurcheck1">
!!!filter: slurcheck
**kern
*M4/4
=1
4c
4d)
(4e
(4f
=2
4g
4f)
4e
((4c 4e 4g
=
1g 1e 1c;)
==
*-
</script>

Sólo se marcará una ligadura desequilibrada adicional para cada nota/acorde. Después de arreglar uno de ellos, puede aparecer un segundo ligado problemático.



## Opciones del filtro
Aquí hay opciones útiles para usar con la versión de línea de comandos del filtro.  La herramienta `slurcheck` está disponible para la línea de comandos en la biblioteca [humlib](https://humlib.humdrum.org).

{% include keytable.html
	contentId="options"
%}
<script type="text/JSON" id="options">
{% include_relative options.json %}
</script>


### Recuento de ligaduras desemparejadas en un archivo/repertorio
La opción `-c` se puede utilizar con la herramienta `slurcheck` en la línea de comandos para contar el número ligaduras desemparejadas.  Para una sola obra, se informará de tres valores:  (1) El número total de ligaduras desemparejadas, (2) el número de inicios de ligadura desemparejadas, y (3) el número de ligaduras desemparejadas.

```bash
slurstart -c file.krn
```

Puede dar lugar a:

```
4	(:1	):3
```

Esto significa que hay cuatro puntos finales de ligaduras desemparejadas, con la apertura de ellas siendo una apertura de ligadura, y tres de ellas siendo un cierre de ligadura.

Se pueden dar varios archivos como entrada.  La opción `-Z` suprimirá los listados de archivos que no tengan ligaduras   colgantes, y la opción `-f` también mostrará el nombre del archivo al principio de la línea.


```bash
 humcat -s h://mozart/sonatas | slurcheck -cZf
```

```
sonata01-1.krn:	1	(:1	):0
sonata01-3.krn:	1	(:0	):1
sonata02-3.krn:	1	(:0	):1
sonata03-3.krn:	1	(:0	):1
sonata04-3.krn:	1	(:0	):1
sonata05-1.krn:	3	(:0	):3
sonata06-3l.krn:	2	(:0	):2
sonata07-2.krn:	1	(:1	):0
sonata07-3.krn:	1	(:0	):1
sonata08-1.krn:	1	(:1	):0
sonata08-2.krn:	2	(:1	):1
sonata09-1.krn:	1	(:1	):0
sonata11-1f.krn:	1	(:1	):0
sonata11-1g.krn:	1	(:0	):1
sonata12-2.krn:	3	(:2	):1
sonata13-2.krn:	1	(:0	):1
sonata14-3.krn:	3	(:1	):2
sonata15-2.krn:	1	(:0	):1
sonata16-1.krn:	1	(:1	):0
sonata16-2.krn:	1	(:0	):1
sonata17-1.krn:	1	(:0	):1
sonata17-3.krn:	4	(:1	):3
```


### Localización de fines de ligaduras desemparejadas en un fichero/repertorio

Para mostrar la ubicación de los puntos finales del la ligadura desemparejada, utiliza la opción `-l`.  En el siguiente ejemplo también se da la opción `-f` para mostrar en qué archivo se encuentra la ligadura:


```bash
humcat -s h://mozart/sonatas | bin/slurcheck -lf
```

```
sonata01-1.krn:	UNCLOSED SLUR	line:1443	field:3	token:(8ddJ)
sonata01-3.krn:	UNOPENED SLUR	line:1072	field:4	token:8ccJ)
sonata02-3.krn:	UNOPENED SLUR	line:607	field:1	token:8f) 8a))
sonata03-3.krn:	UNOPENED SLUR	line:738	field:3	token:4a)
sonata04-3.krn:	UNOPENED SLUR	line:143	field:2	token:8ddJ))
sonata05-1.krn:	UNOPENED SLUR	line:495	field:3	token:4dd)
sonata05-1.krn:	UNOPENED SLUR	line:504	field:3	token:4b)
sonata05-1.krn:	UNOPENED SLUR	line:1134	field:3	token:4gg)
sonata06-3l.krn:	UNOPENED SLUR	line:631	field:2	token:(64cc#qLLLL>)
sonata06-3l.krn:	UNOPENED SLUR	line:646	field:2	token:128gJ)
sonata07-2.krn:	UNCLOSED SLUR	line:1044	field:3	token:((4e
sonata07-3.krn:	UNOPENED SLUR	line:1282	field:2	token:16a)
sonata08-1.krn:	UNCLOSED SLUR	line:1308	field:2	token:(4F 4A (4c
sonata08-2.krn:	UNOPENED SLUR	line:1227	field:1	token:32fJJJ))
sonata08-2.krn:	UNCLOSED SLUR	line:490	field:3	token:(>(16ccqLL
sonata09-1.krn:	UNCLOSED SLUR	line:565	field:2	token:(1dd#
sonata11-1f.krn:	UNCLOSED SLUR	line:290	field:3	token:(16ee'JJ)
sonata11-1g.krn:	UNOPENED SLUR	line:243	field:3	token:8a)
sonata12-2.krn:	UNCLOSED SLUR	line:699	field:1	token:(&(>4G 4B 4d (4f
sonata12-2.krn:	UNOPENED SLUR	line:281	field:3	token:(16b-TLL)
sonata12-2.krn:	UNCLOSED SLUR	line:723	field:3	token:(64b-JJJJ)
sonata13-2.krn:	UNOPENED SLUR	line:275	field:2	token:(8ff)
sonata14-3.krn:	UNCLOSED SLUR	line:676	field:2	token:(4F
sonata14-3.krn:	UNOPENED SLUR	line:681	field:2	token:4e- 4g)
sonata14-3.krn:	UNOPENED SLUR	line:724	field:3	token:16ccJJ))
sonata15-2.krn:	UNOPENED SLUR	line:968	field:2	token:16b)
sonata16-1.krn:	UNCLOSED SLUR	line:1095	field:2	token:(16b-L
sonata16-2.krn:	UNOPENED SLUR	line:695	field:1	token:2B-_ 2a-_)
sonata17-1.krn:	UNOPENED SLUR	line:1034	field:1	token:8f#) 8a))
sonata17-3.krn:	UNOPENED SLUR	line:1634	field:2	token:8BL)
sonata17-3.krn:	UNOPENED SLUR	line:1134	field:2	token:8bJ))
sonata17-3.krn:	UNOPENED SLUR	line:1143	field:2	token:(8.cc#L])
sonata17-3.krn:	UNCLOSED SLUR	line:1626	field:2	token:((24ddLL
```
Para contar el número de ligaduras desequilibradas en un repertorio, utiliza el siguiente comando (33 en este caso):


```bash
humcat -s h://mozart/sonatas | slurcheck -l  | wc -l
33
```
Para contar el número de archivos de un repertorio que tienen ligaduras desequilibradas, utiliza el siguiente comando (22 en este caso):

```bash
humcat -s h://mozart/sonatas | slurcheck -Zc  | wc -l
22
```

## Trabajo futuro
En ocasiones, las ligaduras   colgantes están sangradas.  El trabajo futuro en la herramienta `slurcheck` permitirá detectar este tipo de casos y no marcarlos como posibles errores de codificación.

El propósito principal sería en los finales de repetición, donde una ligadura de la sección principal de la música entra en la primera y segunda finalización.  En este caso, el segundo final contendrá una ligadura  colgante que va al principio del segundo final.  Para esta situación, se creará un código de maquetación (*layout*) para las ligaduras que indique la duración de la ligadura  colgante si se identifica automáticamente que el punto final de la ligadura está  colgante.  Cuando se utiliza la herramienta `thru`/`thrux` para ampliar la versión de interpretación de una partitura, la ligadura del segundo final ya no estará  colgante, y el comando de disposición de la ligadura  colgante se ignorará para la ligadura.

Otro uso de las ligaduras colgantes es en el extracto de compases de una partitura completa.  En el caso de los extractos musicales generados manualmente, debería darse la misma orden de disposición para permitir las ligaduras colgantes.  La herramienta `myank` también debería manejar estos casos y etiquetar automáticamente las ligaduras colgantes.




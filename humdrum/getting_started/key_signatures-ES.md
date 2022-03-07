---
title: key signatures encoding tutorial
lang: en es
ref: humdrum-getting_started-key_signatures
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum encoding tutorial key signatures
creation_date: 20 Aug 2017
translation_date: 10 Aug 2021
last_updated: 25 Jan 2018
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: A tutorial on how to encode key signatures in **kern data.
sidebar: main_sidebar
permalink: /humdrum/getting_started/keysig-ES.html
---

<!--{% include humdrum/keysig.txt %}-->
## Armaduras ##
Las armaduras se representan mediante interpretaciones de la forma `*k[X]`, donde `X` es una lista de las alteraciones en el orden en que aparecen en la armadura.  Aquí una escala en Do sostenido mayor y Do bemol mayor, mostrando todas las alteraciones en su orden correcto:

{% include verovio.html
	humdrum-min-height="475px"
	source="key1"
	scale="55"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="key1">
**kern
*k[f#c#g#d#a#e#b#]
*clefG2
=1
4c#
4d#
4e#
4f#
4g#
4a#
4b#
4cc#
=2
*k[b-e-a-d-g-c-f-]
4c-
4d-
4e-
4f-
4g-
4a-
4b-
4cc-
==
*-
</script>


### Tonalidad ###
La *tonalidad* de la música es diferente de la *armadura*. Indica la tonalidad de la música añadiendo una interpretación de esta forma `*X:`, donde `X` es un nombre de tonalidad más una posible alteración, con nombres de tonalidad en minúsculas indicando tonalidades menores, y nombres de tonalidad en mayúsculas indicando tonalidades mayores.  Por ejemplo, `*C:` significa Do mayor, y `*a:` significa La menor (nótese que ambos tienen la armadura `*k[]` donde no hay sostenidos ni bemoles).


La designación de la tonalidad suele seguir a la armadura, o puede aparecer por sí sola si la tonalidad cambia pero la armadura no.

{% include verovio.html
	humdrum-min-height="450px"
	source="key2"
	scale="55"
	pageWidth="500"
%}
<script type="application/x-humdrum" id="key2">
**kern
*clefG2
*k[f#]
*G:
=1
4g
4dd
4b
4g
=2
*e:
4e
4b
4g
4e
=3
*c#:
4c#
4g#
4e
4c#
==
*-
</script>

Obsérvese que la música en el último compás no tiene un cambio de tonalidad aunque la música modula a Do sostenido menor.

### Designaciones de tonalidades modales ###

Los siguientes códigos pueden añadirse a la armadura para indicar un modo concreto:


|  código  | significado     | exjemplo
| ------ | ----------- | ---------
| `dor`  | dórico      | `*d:dor`
| `phr`  | frigio    | `*e:phr`
| `lyd`  | lidio      | `*F:lyd`
| `mix`  | mixolidio  | `*G:mix`
| `aeo`  | eolio     | `*a:aeo`
| `ion`  | jónico      | `*C:ion`
| `loc`  | locrio     | `*b:loc`


Si el modo está más cerca de una tonalidad menor, se utilizará una letra minúscula para la nota tónica; de lo contrario, los modos más cercanos a la mayor utilizan una letra mayúscula para la tónica.



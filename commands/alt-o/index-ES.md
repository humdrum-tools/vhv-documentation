---
title: <span class='keypress'>alt-o</span>
lang: en es pl
page_language: es
translator: David Rizo
translation_date: 5 Aug 2021
translation_update:
ref: commands-alt-o
tags: [all, commands]
sidebar: main_sidebar
keywords: interface commands original clef
summary: El comando <span class='keypress'>alt-o</span> alterna entre las claves 'originales' y 'modernas'.
permalink: /commands/alt-o/index-ES.html
---

Al pulsar <span class="keypress">alt-o</span> se alterna entre
visualización de claves modernas y originales.  Este es un ejemplo de la función
en acción:

{% include image.html
	file="original-clefs.gif"
	alt="show original/modern notation."
	max-width="100%"
	caption="Al pulsar <span class='keypress'>alt-o</span> se alternará entre las claves modernas y las originales."
%}

Este comando es útil para la corrección de pruebas de un documento que
que utiliza claves diferentes a las de la codificación final, y también es
útil para generar ejercicios de lectura de claves.

Las claves originales se codifican añadiendo "o" antes de "clave":

<style>
pre {
	tab-size: 12;
	-o-tab-size: 12;
	-moz-tab-size: 12;
	-webkit-tab-size: 12;
}
</style>

```
*oclefF4	*oclefC4	*oclefC3	*oclefC1
*clefF4	*clefGv2	*clefG2	*clefG2
```

Si no hay codificaciones `oclef` en los datos, entonces 
<span class="keypress">alt-o</span> obviamente no hará nada.

Prueba a utilizar <span class="keypress">alt-o</span> en el
[Bach chorale](http://verovio.humdrum.org/?file=chorales/chor074.krn) que se muestra
en la figura anterior.


## Notas de implementación ##
Al convertir de Humdrum a MEI, la línea de clave "original" se convierte en este código MEI que inserta las codificaciones opcionales para las claves originales:

```xml
<app>
   <lem/>
   <rdg label="original-clef">
      <scoreDef>
         <staffGrp>
            <staffDef clef.shape="C" clef.line="1" n="1" />
            <staffDef clef.shape="C" clef.line="3" n="2" />
            <staffDef clef.shape="C" clef.line="4" n="3" />
            <staffDef clef.shape="F" clef.line="4" n="4" />
         </staffGrp>
      </scoreDef>
   </rdg>
</app>
```

El elemento `<app>` se utiliza para proporcionar contenido alternativo en un archivo MEI. 
En este caso hay dos opciones, con `<lem>` que significa la opción por defecto (no añadir
claves originales), y un `<rdg>` que lleva la etiqueta `original-clef`.   La opción por defecto en este caso no hace nada, lo que significa que las asignaciones de claves al principio del archivo
no se modifican:

```xml
<scoreDef>
   <staffGrp symbol="bracket">
      <staffDef clef.shape="G" clef.line="2" key.sig="1f" meter.count="4" meter.unit="4" meter.sym="common" n="1" label="Soprano" lines="5" />
      <staffDef clef.shape="G" clef.line="2" key.sig="1f" meter.count="4" meter.unit="4" meter.sym="common" n="2" label="Alto" lines="5" />
      <staffDef clef.shape="G" clef.line="2" clef.dis="8" clef.dis.place="below" key.sig="1f" meter.count="4" meter.unit="4" meter.sym="common" n="3" label="Tenor" lines="5" />
      <staffDef clef.shape="F" clef.line="4" key.sig="1f" meter.count="4" meter.unit="4" meter.sym="common" n="4" label="Bass" lines="5" />
   </staffGrp>
</scoreDef>
```
En el toolkit JavaScript de Verovio, se puede usar la opción `appXPathQuery`  
para ejecutar un comando XPath sobre los datos de `<app>` en el archivo de entrada MEI. Para seleccionar las claves originales, las opciones se establecen en:

```javascript
var options = {
      format: "humdrum",
      pageWidth: 2000,
      pageHeight: 2500,
      appXPathQuery: "./rdg[contains(@label, 'original-clef')]"
   };
```
En este caso la consulta [XPath](https://en.wikipedia.org/wiki/XPath) busca la
lectura que contiene una etiqueta de atributo que tiene el valor `original-clef`.

La [línea de comandos](/myvhv/command_line) equivalente a las opciones anteriores sería:

```bash
humcat h://chorales/chor074.krn | verovio - -o chor074.svg -f humdrum -w 2000 -h 2500 --app-xpath-query="./rdg[contains(@label, 'original-clef')]"
```

Esto es similar al uso de [strophe](http://www.humdrum.org/Humdrum/commands/strophe.html) 
y/o [thru](http://www.humdrum.org/Humdrum/commands/thru.html) en los datos de Humdrum, 
aunque el sistema `*oclef` es un caso especial que no requiere 
usar *strophe* o *thru*.

Aquí está el equivalente usando *thru*:

```
**kern
*I"Soprano
*>[modern,rest]
*>original-clefs[original,rest]
*>modern
*clefG2
*>original
*clefC1
*>rest
*k[b-]
*M4/4
*met(c)
4a
=1
...
```
Entonces, para utilizar claves modernas:


```bash
thru chor074-thru.krn | verovio - -o chor074-modern.svg
```

y claves originales:

```bash
thru -v original-clefs chor074-thru.krn | verovio - -o chor074-original.svg
```
Aquí hay una funcionalidad similar usando *strophe*:

<style>
pre {
	tab-size: 15;
	-o-tab-size: 15;
	-moz-tab-size: 15;
	-webkit-tab-size: 15;
}
</style>

```
**kern
*I"Soprano
*strophe
*^
*S/modern	*S/original
*clefG2	*clefC1
*S/fin	*S/fin
*v	*v
*k[b-]
*M4/4
*met(c)
4a
=1
...
```
Para desempaquetar la versión moderna con *strophe*:

```bash
strophe -x modern chor074-thru.krn | verovio - -o chor074-modern.svg
```

Para desempaquetar la clave original con *strophe*:


```bash
strophe -x original chor074-thru.krn | verovio - -o chor074-original.svg
```




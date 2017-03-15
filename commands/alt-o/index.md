---
title: <span class='keypress'>alt-o</span>
author: Craig Stuart Sapp
creation_date: 15 Mar 2017
last_updated: 15 Mar 2017
tags: [all, commands]
sidebar: main_sidebar
keywords: interface commands original clef
summary: "The <span class='keypress'>alt-o</span> command toggles between \"original\" and \"modern\" clefs."
permalink: /commands/alt-o/index.html
---

Pressing <span class="keypress">alt-o</span> toggles between
display of modern and original clefs.  Here is an example of the feature
in action:

{% include image.html
	file="original-clefs.gif"
	alt="show original/modern notation."
	max-width="100%"
	caption="Pressing <span class='keypress'>alt-o</span> will toggle between modern and original clefs."
%}

This command is useful for proof-reading against a document that
uses different clefs than the final encoding will, and is also
useful for generating clef-reading exercises.

The original clefs are encoded by adding "o" before "clef":
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

If there are no `oclef` encodings in the data, then 
<span class="keypress">alt-o</span> obviously will not do anything.


Try using <span class="keypress">alt-o</span> on the
[Bach chorale](http://verovio.humdrum.org/?file=chorales/chor074.krn) shown
in the above figure.




## Implementation notes ##

When converting from Humdrum to MEI, the "original" clef line is converted into this MEI code that inserts the optional encodings for the original clefs:

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

The `<app>` element is used to provide alternate content in an MEI file. 
In this case there are two choices, with `<lem>` meaning the default choice (don't add
original clefs), and a `<rdg>` which is labeled `original-clef`.   The default in this
case does nothing, which means that the clef assignments at the start of the file
are not altered:

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

In the verovio JavaScript toolkit, the option `appXPathQuery` can be given to the 
toolkit to run an XPath command on `<app>` data in the MEI input file. To select
the original clefs, the options are set to:

```javascript
var options = {
      format: "humdrum",
      pageWidth: 2000,
      pageHeight: 2500,
      appXPathQuery: "./rdg[contains(@label, 'original-clef')]"
   };
```

In this case the [XPath](https://en.wikipedia.org/wiki/XPath) query searches for the
reading that contains an attribute label which has the value `original-clef`.

The [command-line](/myvhv/command_line) equivalent to the above options would be:

```bash
humcat h://chorales/chor074.krn | verovio - -o chor074.svg -f humdrum -w 2000 -h 2500 --app-xpath-query="./rdg[contains(@label, 'original-clef')]"
```

This is similar to using [strophe](http://www.humdrum.org/Humdrum/commands/strophe.html) 
and/or [thru](http://www.humdrum.org/Humdrum/commands/thru.html) in Humdrum data, 
although the `*oclef` system is a special case that does not require 
using *strophe* or *thru*.

Here is the equivalent using *thru*:

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

Then to use modern clefs:

```bash
thru chor074-thru.krn | verovio - -o chor074-modern.svg
```

and original clefs:

```bash
thru -v original-clefs chor074-thru.krn | verovio - -o chor074-original.svg
```

Here is similar functionality using *strophe*:

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

To unpack the modern version with strophe:

```bash
strophe -x modern chor074-thru.krn | verovio - -o chor074-modern.svg
```

To unpack the original-clef version with strophe:

```bash
strophe -x original chor074-thru.krn | verovio - -o chor074-original.svg
```




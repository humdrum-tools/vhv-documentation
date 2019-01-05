---
title: <span class='keypress'>alt-o</span>
lang: pl en
ref: commands-alt-o
author: Craig Stuart Sapp
translator: Marcin Konik
creation_date: 15 Mar 2017
translation_date: 2 Jan 2019
last_updated: 15 Mar 2017
tags: [all, commands]
sidebar: main_sidebar
keywords: polecenia interfejsu oryginalne klucze
summary: Komenda <span class='keypress'>alt-o</span> przełącza widok pomiędzy kluczami współczesnymi i oryginalnymi.
permalink: /commands/alt-o/index-PL.html
---

Naciśnięcie skrótu <span class="keypress">alt-o</span> przełącza widok pomiędzy
oryginalnymi kluczami, w jakich został zapisany utwór i kluczami współczesnymi w transkrypcji.
Poniższy przykład ilustryje działanie funkcji:

{% include image.html
	file="original-clefs.gif"
	alt="wyświetlanie starych/nowych kluczy"
	max-width="100%"
	caption="Efekt zastosowania skrótu <span class='keypress'>alt-o</span> przełącza widok pomiędzy starymi i współczesnymi kluczami."
%}

Ta funkcja programu jest przydatna w sytuacji, gdy oryginalne klucze,
w jakich zapisano utwór różnią się od tych, które zastosowano w transkrypcji.
Można ją też zastosować w celu ćwiczenia umiejętności czytania w różnych kluczach.

Oryginalne klucze zapisywane są w kodzie Humdrum poprzez dodanie "o" do określenia "clef":
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

Jeśeli w transkrypcji (kodzie Humdrum) brak linii zawierającej zapisaną
za pomocą `oclef` informację na temat kluczy, wciśnięcie <span class="keypress">alt-o</span>
nie przyniesie żadnego efektu.

Spróbuj zastosować <span class="keypress">alt-o</span> do
chorałów [Bacha](http://verovio.humdrum.org/?file=chorales/chor074.krn), jak na powyższym przykładzie.

## Uwagi dotyczące wdrażania funkcji ##

Kiedy dane są konwertowane z formatu Humdrum do MEI, oryginalne klucze są zapisywane w kodzie MEI jako opcjonalne:

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

Element `<app>` służy do zapewnienia alternatywnej zawartości w pliku MEI. W tym przypadku są
dwie opcje: z `<lem>` oznaczającym domyślny wybór (nie dodawaj oryginalnych kluczy) oraz `<rdg>`,
który jest oznaczony jako `original-clef`. Domyślnie w tym przypadku program nic nie robi, co oznacza,
że przypisane na początku pliku klucze nie są zmieniane:

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

W pakiecie narzędzi verovio JavaScript opcja "appXPathQuery" może zostać przekazana do zestawu narzędzi,
aby uruchomić polecenie XPath na danych `<app>` w pliku wejściowym MEI. Aby wybrać oryginalne klucze,
opcje są ustawione na:

```javascript
var options = {
      format: "humdrum",
      pageWidth: 2000,
      pageHeight: 2500,
      appXPathQuery: "./rdg[contains(@label, 'original-clef')]"
   };
```
W tym przypadku zapytanie [XPath] (https://en.wikipedia.org/wiki/XPath) wyszukuje fragment zawierający
etykietę atrybutu, która ma wartość `original-clef`.

[Wiersz polecenia] (/myvhv/command_line) równoważny powyższym opcjom będzie wyglądał następująco:

```bash
humcat h://chorales/chor074.krn | verovio - -o chor074.svg -f humdrum -w 2000 -h 2500 --app-xpath-query="./rdg[contains(@label, 'original-clef')]"
```
Jest to podobne do zastosowania narzędzi [strophe](http://www.humdrum.org/Humdrum/commands/strophe.htm) lub [thru](http://www.humdrum.org/Humdrum/commands/thru.html)
do danych Humdrum, chociaż system `*oclef` jest szczególnym przypadkiem, który nie wymaga używania *strophe* lub *thru*.

Oto równoważne działanie przy użyciu *thru*:

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

Następnie, aby użyć współczesnych kluczy:

```bash
thru chor074-thru.krn | verovio - -o chor074-modern.svg
```

oraz oryginalnych kluczy:

```bash
thru -v original-clefs chor074-thru.krn | verovio - -o chor074-original.svg
```

Poniżej podobna funkcjonalność z użyciem *strophe*:

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

Aby wyodrębnić współczesne klucze za pomocą *strophe*:

```bash
strophe -x modern chor074-thru.krn | verovio - -o chor074-modern.svg
```

Aby wyodrębnić oryginalne klucze za pomocą *strophe*:

```bash
strophe -x original chor074-thru.krn | verovio - -o chor074-original.svg
```

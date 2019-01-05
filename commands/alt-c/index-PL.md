---
title: <span class='keypress'>alt-c</span>
lang: pl en
ref: commands-alt-c
author: Craig Stuart Sapp
translator: Marcin Konik 
creation_date: 9 May 2017
translation_date: 1 Jan 2019
last_updated: 9 May 2017
tags: [all, commands]
sidebar: main_sidebar
keywords: polecenia interfejsu kompilacja filtrów
summary: "Skrót <span class='keypress'>alt-c</span> kompiluje zastosowane filtry."
permalink: /commands/alt-c/index-PL.html
---

Naciśnięcie kombinacji klawiszy <span class="keypress">alt-c</span> pozwala na zastosowanie
[filtrów](/filters/) (lub [URL filters](/filters/url)) zastosowanych do danych Humdrum w edytorze
tekstowym oraz zastąpienie danych poprzez dane przefiltrowane.

## Dodawanie pustej kolumny danych (spine) ##

Aby dodać pustą kolumnę do danych Humdrum
użyj [filtra extract](/filters/extract) oraz komendy 
<span class="keypress">alt-c</span>. Poniższy filtr
ekstrahuje wszystkie istniejące kolumny (spines) oraz
dodaje pustą kolumnę na końcu:

```
!!!filter: extract -s 1-$,0
```
Znak `$` oznacza ostatnią kolumnę w pliku zaś `0` oznacza pustą kolumnę.

Dane przed kompilacją filtra:

{% include image.html
	file="precompile.png"
	alt="widok przed kompilacją."
	caption="Dane Humdrum przed kompilacją filtra."
%}

Po naciśnięciu skrótu <span class="keypress">alt-c</span>:

{% include image.html
	file="postcompile.png"
	alt="widok po kompilacji"
	caption="Dane Humdrum po kompilacji filtra."
%}

Linia zawierająca filtr jest zamieniona po kompilacji na `!!!Xfilter:` 
co oznacza, że filtr został zastosowany (i nie będzie użyty ponownie).
Linia ta może zostać usunięta jeśli nie jest potrzebna - można też usunąć
`X`, jeśli filtr ma zostać zastosowany ponownie. 

## Przykład działania filtra do transpozycji ##

Poniżej znajduje się przykład ilustrujący działanie filtra [transpozycji](/filters/transpose):

{% include image.html
	file="transpose1.png"
	alt="widok przed skompilowaniem filtra transpozycji"
	caption="Dane Humdrum przed skompilowaniem filtra transpozycji."
%}

Zauważ, że zapis muzyczny wyświetlany jest w tonacji E-dur
podczas gdy dane zapisane są w C-dur. Dzieje się tak ponieważ
filtr jest zastosowany do danych Humdrum zanim zostaną one 
przekonwertowane do formatu MEI oraz wyrenderowane do obrazu SVG.

Aby zobaczyć te same dane, na podstawie których generowany jest zapis muzyczny
naciśnij skrót <span class="keypress">alt-c</span> aby skompilować filtr:

{% include image.html
	file="transpose2.png"
	alt="widok po kompilacji filtra tanspozycji"
	caption="Dane Humdrum po skompilowaniu filtra transpozycji."
%}

Teraz dane w edytorze tekstowym odpowiadają partyturze w edytorze graficznym.


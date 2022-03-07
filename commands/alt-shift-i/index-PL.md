---
title: <span class='keypress'>alt-shift-i</span>
lang: pl en es
ref: commands-alt-shift-i
author: Craig Stuart Sapp
translator: Marcin Konik
creation_date: 20 May 2018
translation_date: 2 Jan 2019
last_updated: 20 May 2018
tags: [all, commands]
sidebar: main_sidebar
keywords: polecenia interfejsu dodanie linii
summary: "Skrót <span class='keypress'>alt-shift-i</span> dodaje pustą linię powyżej bieżącego wiersza w edytorze tekstowym."
permalink: /commands/alt-shift-i/index-PL.html
---

Naciśnięcie <span class="keypress">alt-shift-i</span> spowoduje dodanie pustej linii danych powyżej bieżącej linii,
pod warunkiem, że bieżący wiersz zawiera dane (nie jest to komentarz globalny, pusta linia). Dodana linia
będzie miała taką samą liczbę kolumn jak bieżąca linia.

Po dodaniu pustego wiersza można dodać polecenia formatowania
(lub dowolne inne, jak np. lokalne komentarze). Poniżej znajduje się przykład, na którym
poprzez dodanie linii oraz fragmentu kodu, zmieniono klucz muzyczny:

{% include image.html
	file="clefchange.gif"
	alt="zmiana klucza"
	max-width="75%"
	caption="Zmiana klucza muzycznego po wciśnięciu alt-shift-i."
%}

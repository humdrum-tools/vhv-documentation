---
title: <span class='keypress'>alt-shift-l</span>
lang: en es pl
page_language: pl
translator: Marcin Konik
translation_date: 3 Jan 2019
translation_update:
ref: commands-alt-shift-l
tags: [all, commands]
sidebar: main_sidebar
keywords: polecenia interfejsu komentarz lokalny
summary: "Skrót <span class='keypress'>alt-shift-l</span> dodaje pustą linię komentarza lokalnego powyżej bieżącego wiersza danych."
permalink: /commands/alt-shift-l/index-PL.html
---

Naciśnięcie <span class = "keypress"> alt-shift-l </ span> spowoduje dodanie
pustej linii lokalnego komentarza nad bieżącym wierszem, pod warunkiem, że zawiera on dane
(nie jest to komentarz globalny, linia pusta lub linia interpretacji wykluczającej).
Dodana lokalna linia komentarza będzie miała taką samą liczbę kolumn, co bieżąca linia.

Po dodaniu pustego wiersza lokalnego komentarza można dodać polecenia formatowania
(lub użyć go do tworzenia lokalnych komentarzy). Poniżej znajduje się przykład 
dodania tekstu w partyturze poprzez komentarz lokalny.

{% include image.html
	file="textlayout.gif"
	alt="dodawanie komentarza formatowania"
	max-width="75%"
	caption="Dodawanie komentarza formatowania po naciśnięciu alt-shift-l."
%}


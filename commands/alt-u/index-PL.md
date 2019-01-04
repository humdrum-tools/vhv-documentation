---
title: <span class='keypress'>alt-u</span>
lang: pl
ref: commands-alt-u
author: Craig Stuart Sapp
translator: Marcin Konik
creation_date: 12 May 2018
translation_date: 3 Jan 2019
last_updated: 12 May 2018
tags: [all, commands]
sidebar: main_sidebar
keywords: polecenia interfejsu widok pliku TSV a CSV
summary: "Skrót <span class='keypress'>alt-u</span> zmienia widok pomiędzy wersją TSV a CSV pliku Humdrum."
permalink: /commands/alt-u/index.html
---

Komenda <span class="keypress">alt-u</span> zmienia widok pomiędzy
wersją TSV a CSV pliku Humdrum. Domyślnie pliki Humdrum są wyświetlane
jako TSV (z tabulatorami jako separatorami kolumn):

{% include image.html
	file="tsv.png"
	alt="widok TSV danych Humdrum"
	caption="Dane Humdrum w widoku TSV."
%}

Po naciśnięciu <span class="keypress">alt-u</span>, dane zostaną
wyświetlone w formacie CSV:

{% include image.html
	file="csv.png"
	alt="widok CSV danych Humdrum"
	caption="Dane Humdrum w widoku CSV."
%}

Ponowne wciśnięcie kombinacji <span class="keypress">alt-u</span> przywróci
widok danych w formacie TSV.

Formularz CSV jest przydatny przy przenoszeniu danych do oprogramowania, które posiada
opcję importu CSV, ale nie TSV. Ponadto format CSV jest przydatny w przypadkach, w których
znak tabulatora może zostać zniekształcony, na przykład w wiadomościach e-mail.

Rekordy referencyjne (zielony tekst na powyższym rysunku) mogą zawierać tabulatory,
które nie są konwertowane na przecinki podczas konwersji do formularza CSV.
Dzieje się tak dlatego, że znaki te nie są integralną częścią struktury danych Humdrum.
Tabulatory w komentarzach globalnych również nie zostaną zmienione z tego samego powodu.

---
title: <span class='keypress'>alt-g</span>
lang: pl
ref: commands-alt-g
author: Craig Stuart Sapp
translator: Marcin Konik 
creation_date: 23 Apr 2017
translation_date: 1 Jan 2019
last_updated: 23 Apr 2017
tags: [all, commands]
sidebar: main_sidebar
keywords: polecenia interfejsu svg
summary: Kombinacja klawiszy <span class='keypress'>alt-g</span> wyświetla kod SVG obrazu prezentowanego w edytorze graficznym.
permalink: /commands/alt-g/index-PL.html
---

Naciśnięcie <span class="keypress">alt-g</span> spowoduje otwarcie nowego okna
w którym wyświetlone są dane SVG dla aktualnego widoku strony
notacji muzycznej. Poniżej przykład działania funkcji: 

{% include image.html
	file="show-svg.gif"
	alt="Pokaż kod SVG notacji graficznej."
	max-width="50%"
	caption="Skrót <span class='keypress'>alt-g</span> otworzy okno z kodem SVG aktualnej strony notacji muzycznej."
%}

[Tutaj](sample.svg) zobaczysz obraz SVG przedstawiony na przukładzie powyżej
po zapisaniu go d pliku.
Kod SVG można skopiować/wkleić do edytora tekstowego i zapisać
na dysku twardym. Takie działanie może być przydatne w celu zapisania
fragmentu lub całości obrazu w celu użycia go jako statycznego 
obrazu w artykule lub na stronie internetowej.

## Konwertowanie notacji muzycznej do formatu obrazu bitmapowego ## 

Wiele programów (jak np. MS Word) nie obsługuje formatu obrazu SVG,
więc aby móc je wykorzystać w takich programach, należy je uprzednio
przekonwertować do pożądanego formatu. Są dwie podstawowe metody zapisywania
obrazu bitmapowego w VHV: najprosztą metodą jest wykonanie zrzutu
ekranu. Sposób wykonania zrzutu ekranu zależy od systemu operacyjnego.
W systemie MacOS naciśnij <span class="keypress">command-shift-4</span> a
następnie narysuj zaznaczenie wokół obrazu, których chcesz zapisać.
Możesz także użyć skrótu <span class="keypress">alt-f</span> aby uzyskać
niałe tło dla zapisanego obrazu.

{% include image.html
	file="screenshot.gif"
	alt="Tworzenie zrzutu ekranu notacji muzycznej"
	max-width="100%"
	caption="Tworzenie zrzutu ekranu fragmentu wyświetlanej notacji."
%}

Bardziej zaawansowaną metodą zachowania obrazu całej strony jest jej zapisanie
za pomocą skrótu <span class="keypress">alt-g</span> a następnie otwarcie obrazu
w programie [GIMP](https://www.gimp.org). Poniżej przedstawiono okno dialogowe
importu obrazu SVG w programie GIMP:

{% include image.html
	file="svgopen.png"
	alt="Importowanie SVG do programu GIMP"
	max-width="50%"
	caption="Okno z opcjami podczas importu SVG w programie GIMP."
%}

Aby uzyskać wysokiej rozdzielczości obraz z pliku SVG ustaw szerokość/wysokość obrazu
na odpowiednio wysokim poziomie (np. 2000 pikseli szerokości). Poniżej przykład
obrazu zamiportowanego do GIMPa:

{% include image.html
	file="ingimp.png"
	alt="Ładowanie SVG do GIMP"
	max-width="80%"
	caption="Okno z opcjami podczas otwierania SVG w programie GIMP."
%}

Szare tło szachownicy oznacza, że obraz jest przezroczysty. Jest to szzcególnie
przydatne w przypadku umieszczania obrazka na kolorowym tle. Możesz zapisać
obraz albo wybrać go i skopiować/wkleić to innego programu, jak mp. MS Word:

{% include image.html
	file="msword.png"
	alt="Eksport z GIMP do MS Word"
	max-width="60%"
	caption="Efekt kopiowania/wklejania obrazu z GIMP do MS Word."
%}


## Edytowanie obrazu grafiki wektorowej ##

Jeśli chcesz zachować grafikę wektorową obrazu SVG a następnie móc
go edytować lub wprowadzać zmiany (jak np. dodawanie strzałek lub innych
oznaczeń przydatnych w analizie) użyj programu [Inkscape](https://inkscape.org/en),
który jest darmowym, open-source'owym edytorem grafiki wektorowej. 

{% include image.html
	file="inkscape.png"
	alt="Inkscape"
	max-width="80%"
	caption="Ładowanie SVG do programu Inkscape oraz dodawanie oznaczeń."
%}

Z programu Inkscape może zapisać [Enhanced Metafile format](https://en.wikipedia.org/wiki/Windows_Metafile),
który jest starszym typem grafiki wektorowej Microsoft. Może on zostać wczytany do programu MS Word.
Zauważ, że niektóre elementy (jak przezroczystość oraz znaczniki warstw) mogą nie zostać poprawnie
wyeksportowane do formatu EMF: 

{% include image.html
	file="emfword.png"
	alt="EMF załadowany do Word"
	max-width="60%"
	caption="Ładowanie pliku EMF do MS Word z pliku zapisanego w Inkscape."
%}

Poniżej umieszczono przykład edytwanego i zapisanego ponownie obrazu SVG ([sample2.svg](sample2.svg)),
który następnie został użyty w przeglądarce internetowej: 

{% include image.html
	file="svgchrome.png"
	alt="Obraz z Inkscape załadowany do przeglądarki Chrome"
	max-width="60%"
	caption="Ładowanie zapisanego z Inkscape pliku SVG do przeglądarki Google Chrome."
%}


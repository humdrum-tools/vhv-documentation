---
title: <span class='keypress'>alt-f</span>
lang: en es pl
page_language: pl
translator: Marcin Konik 
translation_date: 1 Jan 2019
translation_update:
ref: commands-alt-f
tags: [all, commands]
sidebar: main_sidebar
keywords: polecenia interfejsu blokowanie renderowania notacji
summary: "Skrót <span class='keypress'>alt-f</span> blokuje/odblokowuje dynamiczne renderowanie notacji muzycznej."
permalink: /commands/alt-f/index-PL.html
---

Naciśnięcie skrótu <span class="keypress">alt-f</span> zablokuje/odblokuje automatyczne
renderowanie partytury. W normalnym trybie pracy wszelkie zmiany wprowadzone w edytorze tekstowym
są automatycznie renderowane do partytury. W przypadku szczególnie dużych utworów proces ten
może znacznie spowolnić działanie programu (przy aktualnej architekturze). Aby przyspieszyć
edycję danych w edytorze tekstowym, notacja muzyczne może zostać "zamrożona" za pomocą
skrótu klawiszowego <span class="keypress">alt-f</span>.

Podczas gdy renderowanie zostało zablokowane jakiekolwiek zmiany wprowadzone w edytorze
tekstowym nie zostaną wyświetlone na partyturze. Po dokonaniu zmian w celu ich
wizualizacji ponowne naciśnięcie <span class="keypress">alt-f</span> odblokuje 
renderowanie a wszystkie wprowadzone zmiany zostaną wyświetlone na partyturze.

Kiedy notacja jest "zamrożona" tło partytury zmienia kolor na biały. Odblokowanie
renderowania przywróci pierwotny kolor tła:

{% include image.html
	file="freeze-unfreeze.gif"
	alt="blokowanie i odblokowanie renderowania"
	caption="Blokowanie i odblokowanie renderowania podczas wprowadzania zmian w edytorze tekstowym."
%}


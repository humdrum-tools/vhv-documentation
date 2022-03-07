---
title: <span class='keypress'>alt-m</span>
lang: pl en es
ref: commands-alt-m
author: Craig Stuart Sapp
translator: Marcin Konik 
creation_date: 5 Mar 2017
translation_date: 1 Jan 2019
last_updated: 5 Mar 2017
tags: [all, commands]
sidebar: main_sidebar
keywords: polecenia interfejsu 
summary: "Komenda <span class='keypress'>alt-m</span> wyświetla dane w formacie MEI w edytorze tekstowym"
permalink: /commands/alt-m/index-PL.html
---

Naciśnięcie kombinacji klawiszy <span class="keypress">alt-m</span> zastąpi widok danych Humdrum
poprzez ich wersję w formacie MEI w edytorze tekstowym.
Dane w formacie MEI są używane przez edytor w celu wyświetlenia
partytury w formacie obrazu SVG. 

Podczas gdy dane w formacie MEI są wyświetlane w edytorze tekstowym,
mogą one być dowolnie edytowane, zaś wszystkie wprowadzone zmiany zostaną
wyświetlone w edytorze graficznym (na wygenerowanej partyturze).
Kliknięcie na wybrany element partytury w edytorze graficznym spowoduje,
że kursor w edytorze tekstowym zostanie przeniesiony do odpowiadającego
mu miejsca w kodzie MEI. Należy pamiętać, że wprowadzanie zmian w edytorze
graficznym nie pozwala na zmianę kodu MEI.

Możesz wrócić do pierwotnego widoku kodu Humdrum w edytorze tekstowym
naciskając kombinację klawiszy <span class="keypress">alt-h</span>. Pamiętaj
jednak, że wszelkie zmiany w kodzie MEI zostaną utracone. Poniżej można zobaczyć
jak wpisuje się do edytora kod Humdrum. Po naciśnięciu <span class="keypress">alt-m</span>
wyświetlane są dane MEI:

{% include image.html
	file="mei-data.gif"
	alt="wyświetlanie danych MEI"
	caption="Przełączanie edytora tekstowego do trybu MEI po wprowadzeniu danych."
%}




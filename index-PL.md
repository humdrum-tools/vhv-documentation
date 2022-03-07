---
title: Verovio Humdrum Viewer 
lang: en pl es
author: Craig Stuart Sapp
translator: Marcin Konik
creation_date: 3 Mar 2017
translation_date: 1 Jan 2019
last_updated: 4 Mar 2017
tags: [getting_started]
sidebar: main_sidebar
keywords: homepage
permalink: /index-PL.html
summary: 
---

Verovio Humdrum Viewer (VHV) to edytor muzyczny działający online w przeglądarce
internetowej. VHV za pomocą swojego interfejsu pozwala na interaktywne renderowanie 
partytury na podstawie pliku w formacie Humdrum znajdujacych się na stronie
[https://verovio.humdrum.org](https://verovio.humdrum.org). Zobacz także
stronę [Jak zacząć](/interface/getting_started) aby zapoznać się z samouczkami
dotyczącymi używania interfejsu VHV, lub przeglądnij strony dokumentacji
za pomocą menu bocznego lub nawigacji na górze strony. Strony pomocy 
zostały ułożone według tematów:

<style>

dl {
	margin-left: 10%;
	margin-right: 10%;

}

dd {
	margin-top: 0 !important;
}

</style>

Interfejs użytkownika
: Opis interfejsu VHV oraz sposobów jego używania.

Komendy
: Lista skrótów klawiaturowych pozwalających na interakcję z interfejsem VHV.

Edytowanie graficzne
: Opis działań pozwalających na edytowanie notacji muzycznej w edytorze graficznym.

Filtry
: Filtry, które po zastosowaniu modyfikują dane.

Zasoby
: Opis muzycznych zasobów dostępnych online, które mogą być użyte w VHV.

Kodowanie Humdrum
: Tematy związane z różnymi aspektami zapisu muzycznego w składni Humdrum,
w większości bezpośrednio powiązane z możliwościami VHV. Zobacz stronę [Jak zacząć](/humdrum/getting_started) 
aby zapoznać się z interaktywnym samouczkiem dotyczącym kodowania muzyki w formacie Humdrum.
Bardziej szczegółowa dokumentacja formatu znajduje się na stronie [Humdrum documentation](https://www.humdrum.org).

mojeVHV
: Instrukcje i przykładowe użycia programu [Verovio](https://www.verovio.org)
i [Humdrum](https://www.humdrum.org) w Twoich własnych projektaach.

Utrzymanie
: Tematy związane z tworzeniem i utrzymaniem tej strony. 

Indeksy
: Lista stron według kategorii tagów.


## Współtwórcy ##

<style>

ul.brief li {
	color: #aaa;
	padding: 0 !important;
	margin: 0 !important;
}

</style>

<dl>
<dt>Craig Stuart Sapp</dt>
<dd>Twórca</dd>
<dt>Alex Morgan</dt>
<dd>
<ul class="brief"> <li> algorytmy do oznaczania dysonansów za pomocą filtra <i><a href="/filter/dissonant">dissonant</a></i> </li> <li> definicje zawieszeń kadencyjnych w filtrze <i><a href="/filter/cint">cint</a></i> </li> </ul>
</dd>
<dt>Piotr Szyngiera</dt>
<dd>
<ul class="brief">
<li> walidacja poprawności składni Humdrum w edytorze ace</li>
<li> <a href="/interface/edit_modes">Podświetlanie składni Humdrum</a> </li> 
</ul>
</dd>
</dl>

Nie-programiści mogą uczestniczyć w projekcie poprzez zgłaszanie
<a href="https://github.com/humdrum-tools/verovio-humdrum-viewer/issues">błędów
oraz zapotrzebowania na nowe opcje</a> dla interfejsu VHV. Raporty błędów dla
<a href="/filters">filtrów</a> powinny być zgłaszane do <a
href="https://github.com/craigsapp/humlib/issues">humlib</a>, a raporty
błędów oraz poprawki do edytora graficznego do
<a href="https://github.com/rism-ch/verovio/issues">verovio</a>.
Większa część stron dokumentacji VHV posiada przyciski, które mogą
być użyte w celu poprawiania literówek lub dodawania treści, przez osoby
posiadająceo konto na <a href="https://github.com">Githubie</a>.

### Główne składniki oprogramowania ###

<dl>

<dt> <a href="https://www.verovio.org">verovio</a></dt>
<dd> Oprogramowanie renderujące w C++ (z wykorzystaniem formatu MEI, pozwalające na import plików w formacie Humdrum oraz MusicXML z możliwościę eksportu do formatów SVG oraz MIDI)</dd>

<dt> <a href="https://humlib.humdrum.org">humlib</a></dt>
<dd> Narzędzia C++ do konwertowania i analizy muzycznej (z wykorzystaniem Humdrum, z możliwością importu z formatów MusicXML oraz MEI oraz eksportu do MEI i MIDI)</dd>

<dt> <a href="https://ace.c9.io">edytor ace</a></dt>
<dd> Edytor tekstowy w JavaScript</dd>

</dl>

## Instytucjonalni partnerzy projektu ##

<style>

.logo {
	padding-top: 20px;
	padding-right: 20px;
}

.shadow {
	-webkit-filter: drop-shadow(3px 3px 2px rgba(0,0,0,0.2));
	drop-shadow(3px 3px 2px rgba(0,0,0,0.2));
}

</style>

<div style="margin-left: 100px">

<a class="logo" href="https://www.packhum.org"><img class="logo shadow" style="width:300px"  src="/images/phi-logo.png"></a>
<a class="logo" href="https://wiki.ccarh.org"><img class="logo shadow" style="width:300px" src="/images/ccarh-logo.png"></a>
<a class="logo" href="https://en.chopin.nifc.pl"><img class="logo shadow" style="width:350px" src="/images/nifc-logo.png"></a>
<a class="logo" href="https://simssa.ca/"><img class="logo shadow" style="width:250px" src="/images/simssa-logo.png"></a>

</div>

## Projekty korzystające z VHV ##

<div style="margin-left: 100px">

<a class="logo" href="https://www.tassomusic.org"><img class="logo shadow" style="width:300px" src="/images/tmp-logo.png"></a>
<a class="logo" href="https://josquin.stanford.edu"><img class="logo shadow" style="width:419px" src="/images/jrp-logo.png"></a>
<a class="logo" href="http://www.gaspar-van-weerbeke.sbg.ac.at/gaspar-online-edition"><img class="logo shadow" style="width:320px" src="/images/gaspar-online-edition.jpg"></a>


</div>

Po przygotowaniu składu nutowego w VHV może on zostać wykorzystany
do przeprowadzenia analizy za pomocą narzędzi komputerowych, jak np. <a target="_blank"
href="https://github.com/humdrum-tools/humdrum-tools">Humdrum
Tools</a>, oraz wyświetlania notacji muzycznej na stronach internetowych za pomocą <a target="_blank"
href="https://plugin.humdrum.org">wtyczki Humdrum notatio</a>.

Przykładowo, w projekcie Josquin Research Project (JRP) użyto zarówno
wtyczki "Humdrum notation" w celu wyświetlenia incypitów muzycznych na stronach <a target="_blank"
href="https://josquin.stanford.edu/work/?id=Jos2721">poszczególnych kompozycji</a>, jak i
w celu generowania przykładowych partytur z bazy JRP na stronie <a target="_blank"
href="https://josquin.stanford.edu">głównej</a>. Ponadto, niektóre z narzędzi analitycznych
zostały zaimplementowane online za pomocą VHV. Jednym z przykładów może być
filtr <a href="/filter/dissonant">dissonant</a>, który automatycznie wyświetla dysonanse.
Na stronach poszczególnych kompozycji <a target="_blank"
href="https://josquin.stanford.edu/work/?id=Jos2721">jak np. ta</a> w projekcie JRP 
znajdują się przyciski oznaczone jako "Dissonant", które przekierowują do VHV ładując wskazane dane
do edytora oraz wykonując analizę dysonansów <a target="_blank"
href="https://verovio.humdrum.org/?k=ey&filter=dissonant&file=jrp:Jos2721">za pomocą VHV</a>.

Pliki znajdujące sie na innych stronach internetowych mogą zostać automatycznie załadowane do VHV
poprzez wpisanie odpowiedniego adresu URL w parametrze CGI *file*. Na przykład 
poniższy link do VHV:

<a target="_blank" href="https://verovio.humdrum.org/?file=https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata14-1.krn">https://verovio.humdrum.org/?file=https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata14-1.krn</a>

pozwala pobrać spod adresu URL dane Humdrum pierwszej części <i>Sonaty księżycowej</i> Beethovena:

<a target="_blank" href="https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata14-1.krn">https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata14-1.krn</a>

Poniższa partytura stanowi część repozytorium Github zawierajacego sonaty Beethovena: 

<a target="_blank" href="https://github.com/craigsapp/beethoven-piano-sonatas">https://github.com/craigsapp/beethoven-piano-sonatas</a>

które są dostępne z pozimu menu pomocy w interfejsie VHV
(znak pytajnika w prawym górnym rogu na stronie VHV). 




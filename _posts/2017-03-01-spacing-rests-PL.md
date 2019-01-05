---
title:  "Podgląd ukrytych pauz"
lang: pl
ref: news-invisible-rests
author: Craig Stuart Sapp
translator: Marcin Konik
creation_date: 1 Mar 2017
translation_date: 3 Jan 2019
last_updated: 4 Mar 2017
categories: update
permalink: news-invisible-rests-PL.html
sidebar: main_sidebar
tags: [all, news]
---

Specjalne kody meta-RDF zostały dodane w celu korekty danych danych
w strukturze Humdrum podczas konwersji do danych MEI. Niewidoczne
pauzy, zwane `<space>` w formacie MEI, mogą być wyświetlane jako kolorowe pauzy.
spoczywają. Jedna instrukcja RDF pozwoli ustawić widoczność i kolor wszystkich
typów pauz, a trzy dodatkowe instrukcje RDF pozwalają kontrolować widoczność i
kolor każdej z kategorii `<space>`, która jest generowana podczas konwersji.

Zobacz dokumentację dla [ukrytych pauz](/humdrum/invisible_rests) w celu
uzyskania dodatkowych informacji.

[Poprawka oprogramowania](https://github.com/rism-ch/verovio/commit/ab44b7bfffb6869e372943c66c1a3ecd5975d534)
verovio, która wprowadza omawianą zmianę (wraz z przykładami na dole strony).

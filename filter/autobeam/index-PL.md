---
title: autobeam filter
lang: en es pl
page_language: pl
translator: Marcin Konik 
translation_date: 9 Jan 2019
translation_update:
ref: filters-autobeam
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: polecenia interfejsu 
summary: 
permalink: /filter/autobeam/index.html
---

Filtr "autobeam" może zostać użyty w celu dodania belkowania nut
na podstawie przyjętego metrum. Poniżej znajduje się przykład, na 
którym pokazano działanie filtra do zapisu w metrum 3/4 oraz 6/8.

{% include verovio.html
	source="meterchange"
	scale="60"
	pageWidth="1450"
	tabsize="16"
%}

<script type="application/json" id="meterchange">
!!!filter: autobeam
**kern
*M3/4
8c
8e
8d
8f
8g
8e
=
*M6/8
8c
8d
8e
8g
8f
8e
==
*-
</script>

Spróbuj usunąć filtr umieszczony powyżej danych Humdrum aby zobaczyć co się stanie.

W edytorze VHV możesz także użyć skrótu <span class="keypress">alt-c</span>
aby "skompilować" (zastosować) filtr. Spowoduje to, że oznaczenia belek
zostaną zapisane w kodzie Humdrum. (Skrót <span class="keypress">alt-c</span> 
zadziała w edytorze, jednak nie na powyższym przykładzie). 




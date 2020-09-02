---
title: VHV filters examples
lang: en
ref: filters
author: Craig Stuart Sapp
translator: 
creation_date: 31 Aug 2020
translation_date: 
last_updated: 23 Apr 2020
tags: [all, filters]
sidebar: main_sidebar
aton: "true"
verovio: "true"
keywords: interface commands 
summary:  "Example uses of filters in VHV."
permalink: /filter/examples/index.html
---

<script type="text/x-aton" id="example-data">
{% include_relative examples.aton %}
</script>

{% include_relative styles-local.html %}
{% include_relative listeners.html %}
{% include_relative scripts-local.html %}


Click on the blue filter text to load the filter into VHV and
apply to a sample piece of music.


## Transposition ##

The [transposition](/filter/transposition) filter can be used to transpose
the score in various ways that are illustrated below.

<div data-category="transposition"></div>



## Compound filters ##

Here are examples of how to mix multiple filters together.  Each filter 
is separated from the next with a pipe character (|).

<div data-category="pipeline"></div>


## Musical excerpts ##

The [myank](/filter/myank) filter can be used to extract musical examples
from longer scores.


<div data-category="excerpt"></div>



## Part extraction ##

The [extract](/filter/extract) filter can be used to extract parts
and other data spines from a full score.


<div data-category="extract"></div>




## Chords ##

The [chord](/filter/chord) filter can be used to manipulate chords.


<div data-category="chord"></div>



## Searching ##

The [msearch](/filter/chord) filter (meaning *music search*) can
be used to search for musical patterns.

<div data-category="search"></div>



## Search and replace ##

The [shed](/filter/shed) filter can be used to search and replace content
in Humdrum data.  "Shed" stands for "Humdrum <a target="_blank" href="https://www.gnu.org/software/sed/manual/sed.html">sed</a>" (dyslexic, but easier to pronounce).


<div data-category="regular_expressions"></div>



## Counterpoint ##

The [cint](/filter/cint) filter (meaning *composite intervals*) can
be used to study counterpoint.  The cint program is an intersection
of functionalities between the mint and hint programs of the Humdrum
Toolkit, and it creates counterpoint modules that consist of four
notes in two voices, which in turn generates two harmonic and two
melodic intervals for each module.


<div data-category="counterpoint"></div>





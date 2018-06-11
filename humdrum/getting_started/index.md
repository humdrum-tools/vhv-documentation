---
title: Humdrum music encoding tutorial
lang: en
ref: humdrum-getting_started
author: Craig Stuart Sapp
keywords: humdrum encoding tutorial
creation_date: 20 Aug 2017
last_updated: 25 Jan 2018
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: A tutorial on how to encode music in the Humdrum syntax for VHV.
sidebar: main_sidebar
permalink: /humdrum/getting_started/index.html
---

This tutorial covers the basics of representing graphic music
notation in the Humdrum syntax.  Mostly this involves encoding music
within the `**kern` data representation. For more advanced notational
features, other data types are used, such as `**dynam` for dynamics
and `**text` for lyrics.  Also see other pages in the *Humdrum
encoding* section of the navigation menu for special encoding topics
(to the left or above).

Each musical example in the tutorial below is interactive, so trying
tweaking the examples to see what happens.  A text box containing
the Humdrum data used to produce the notation is given on the left
side of each notation example.  The text in these boxes is editable,
and changing the text will update the notation as you type.
[If the notation no longer updates when editing the Humdrum text,
you will have to reload the webpage to restart verovio again.]

{% include_relative pitch.txt %}
{% include_relative clefs.txt %}
{% include_relative octaves.txt %}
{% include_relative barlines.txt %}
{% include_relative time_signatures.txt %}
{% include_relative accidentals.txt %}
{% include_relative key_signatures.txt %}
{% include_relative chords.txt %}
{% include_relative rhythm.txt %}
{% include_relative ties.txt %}
{% include_relative beaming.txt %}
{% include_relative tuplets.txt %}
{% include_relative rests.txt %}
{% include_relative slurs.txt %}
{% include_relative articulations.txt %}
{% include_relative lyrics.txt %}
{% include_relative dynamics.txt %}
{% include_relative multiple_voices.txt %}
{% include_relative multiple_staves.txt %}
{% include_relative cross_staff.txt %}
{% include_relative text_directions.txt %}
{% include_relative transposing.txt %}


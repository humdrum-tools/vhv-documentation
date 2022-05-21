---
title: Humdrum music encoding tutorial
lang: en es
ref: humdrum-getting_started
author: Craig Stuart Sapp
translator: 
keywords: humdrum encoding tutorial
creation_date: 20 Aug 2017
translation_date: 
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

{% include humdrum/pitch.txt %}
{% include humdrum/clefs.txt %}
{% include humdrum/octaves.txt %}
{% include humdrum/barlines.txt %}
{% include humdrum/timesig.txt %}
{% include humdrum/accidentals.txt %}
{% include humdrum/keysig.txt %}
See the [full description of key signatures](/humdrum/keysig/index.html) for more information.

{% include humdrum/chords.txt %}
{% include humdrum/rhythm.txt %}
{% include humdrum/ties.txt %}
[More information about ties](/humdrum/ties)

{% include humdrum/beaming.txt %}
{% include humdrum/tuplets.txt %}
{% include humdrum/rests.txt %}
{% include humdrum/slurs.txt %}
[More information about ties](/humdrum/ties)

{% include humdrum/articulations.txt %}
[More information about articulations](/humdrum/articulations)

{% include humdrum/ornaments.txt %}
{% include humdrum/lyrics.txt %}
{% include humdrum/dynamics.txt %}
{% include humdrum/multiple_voices.txt %}
{% include humdrum/multiple_staves.txt %}
{% include humdrum/cross_staff.txt %}
{% include humdrum/text_directions.txt %}
{% include humdrum/transposing.txt %}


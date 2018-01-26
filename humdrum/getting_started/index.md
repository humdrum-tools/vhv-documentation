---
title: Humdrum music encoding tutorial
author: Craig Stuart Sapp
keywords: humdrum ottava marks
creation_date: 20 Aug 2017
last_updated: 20 Aug 2017
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
[If the notation no longer updats when editing the Humdrum text,
you will have to reload the webpage to restart verovio again.]

{% include_relative pitch.md %}
{% include_relative clefs.md %}
{% include_relative octaves.md %}
{% include_relative barlines.md %}
{% include_relative time_signatures.md %}
{% include_relative accidentals.md %}
{% include_relative key_signatures.md %}
{% include_relative chords.md %}
{% include_relative rhythm.md %}
{% include_relative ties.md %}
{% include_relative beaming.md %}
{% include_relative tuplets.md %}
{% include_relative rests.md %}
{% include_relative slurs.md %}
{% include_relative articulations.md %}
{% include_relative lyrics.md %}
{% include_relative dynamics.md %}
{% include_relative multiple_voices.md %}
{% include_relative multiple_staves.md %}
{% include_relative cross_staff.md %}
{% include_relative text_directions.md %}


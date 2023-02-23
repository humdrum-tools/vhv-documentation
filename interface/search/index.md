---
title: Search toolbar
lang: en es
page_language: en
author: Craig Stuart Sapp
creation_date: 27 Aug 2020
last_updated: 3 Sep 2020
ref: interface-toolbar
tags: [all, getting_started]
keywords: interface search toolbar
summary: "How to use the search toolbar."
sidebar: main_sidebar
permalink: /interface/search/index.html
---

{% include_relative style-local.html %}

A [toolbar](/interface/toolbar) for searching for musical patterns in the score can be accessed
by clicking on the circular icon near the right side of the toolbars in the upper
right-hand corner of VHV:

{% include image.html
	file="search-toolbar.png"
	alt="VHV main page showing toolbar"
	caption="Search toolbar in VHV window, upper right corner."
%}

Alternativly use the keyboard shortcut <span class="keypress">4+alt-n</span> to
jump to the search toolbar directly.



## Pitch searches ##

The first field in the search toolbar is for pitch searching.  Letter
names "a" through "g" are used for note names, and "r" for rest.
Here is an example of searching for the pitch sequence "C D E":

{% include image.html
	file="pitch-search.png"
	alt="VHV main page showing toolbar"
	caption="Searching for C, D, E."
%}

This search will cause the diatonic pitch class melodic sequence
of C followed by D, followed by E to be highlighted.  Note that upper-case or lower-case
letters are interchangeable.  Spaces are optional between notes, but spaces between notes
and accidental are not allowed.



### Chromatic quality ###

When searching by pitch name, the default method is by diatonic pitch-classes.  This means
that "C" will match to C-sharp, C-natural, C-sharp, and so on.  To search for a particular
chromatic version of a pitch class, add an accidental after the pitch name (using `**kern`
accidental syntax):

| Accidental | Example | Meaning               |
| ---------- | ------- | --------------------- |
| `n`        | `Cn`    | natural               |
| `-`        | `C-`    | flat                  |
| `#`        | `C#`    | sharp                 |
| `--`       | `C--`   | double-flat           |
| `##`       | `C##`   | double-sharp          |
| *nothing*  | `C`     | any accidental state  |



## Interval searches ##

Intervals can be searched for in the middle box on the search toolbar.  Intervals are
diatonic interval numbers. 

| Interval   | Meaning               |
| ---------- | --------------------- |
| `1`        | repeated note         |
| `2`        | up a step             |
| `-2`       | down a step           |
| `3`        | up a third            |
| `-3`       | down a third          |


Spaces are optional between interval numbers; however, if you want to search
for multi-digit intervals (such as a tenth), the current interval search does not
allow them (this will be added in the future).



## Rhythm searches ##

| Rhythm     | Meaning               |
| ---------- | --------------------- |
| `1`        | whole note            |
| `2`        | half note             |
| `4`        | quarter note          |
| `8`        | eighth note           |
| `.`        | augmentation dot      |

Spaces are optional for rhythm searching.  More refinement of the search string will be
implemented in the future.  For example "116" will be parsed as a whole note followed
by a sixteenth note.  Tuplet searching will be also implemented in the future, such as
"6" for a triplet quarter note.



## Combined searches ##

You can search for multiple features at the same time.  Each search
will be done in parallel (an "AND" search).  For example, searching
for the pitch sequence "cde" and the rhythm sequence "2" will match
to a pitch sequence "cde" that starts on a half note (i.e., the C
pitch is a half note).  Since the rhythm sequence is shorter than
the pitch sequence, the rhythm of the D and E pitches can be anything.


{% include image.html
	file="combined-pitch-rhythm-search.png"
	alt="VHV main page showing toolbar"
	caption="Searching for pitch and rhythm at the same time."
%}

Notice that the pitch sequence "C, D, E" at the start of the second and
third measure does not match because the C does not start on a half note.


Here is a similar parallel search of pitch and interval:


{% include image.html
	file="combined-pitch-interval-search.png"
	alt="VHV main page showing toolbar"
	caption="Searching for pitch and interval at the same time."
%}


The pitch sequence "C, D, E" matches in the first two measures but not in the
third, because the interval between the first two notes (C and D), must be a
second.  In the third measure the interval is a falling seventh.



## Display search toolbar on VHV load from URL ##


Add the parameter "toolbar=search" to the VHV URL to display the search
toolbar when loading VHV:

<a target="_blank" href="https://verovio.humdrum.org?toolbar=search">verovio.humdrum.org?toolbar=search</a>



## Searching from URL parameters ##

A Search can be added to the URL.  This is useful if you want to load a specific file
and do a search on it immediately.


| Parameter  | Example   | Meaning               |
| ---------- | -------   | --------------------- |
| `p`        | `p=cdefg` | Search for the pitch sequence C, D, E, F, G |
| `i`        | `i=3-52`` | Search for the interval sequence 3, -5, 2 |
| `r`        | `r=4881`  | Search for the rhythm sequence 4, 8, 8, 1 |

There is also a special value for pitch: `p=bach` which searches
for the pitch sequence B-flat, A-natural, C-natural, B-natural:

<a target="_blank" href="https://verovio.humdrum.org/?k=ey&file=chorales/chor166.krn&p=bach">
https://verovio.humdrum.org/?k=ey&file=chorales/chor166.krn&p=bach
</a>

(check for the match highlighted in the last measure)




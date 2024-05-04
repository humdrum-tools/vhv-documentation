---
title: chint filter
lang: en
page_language: en
author: Craig Stuart Sapp
creation_date: 4 May 2024
last_updated: 4 May 2024
ref: filters-chint
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: "Set the tempo of the score"
permalink: /filter/chint/index.html
vim: nowrap:ft=text
---

The *chint* filter means "colorize harmonic intervals".  It compares
two monophonic parts to each other and colors the intervals for
visual analysis within a score.


## Options ##

{% include filter-options.html file="options.aton" lang="EN" %}



## Color mapping ##

Colors are assigned roughly as a heat map, where cooler colors are more 
dissonant:

{% include_relative chint-table-colors.md %}

Example of colors in music notation:

{% include_relative chint-example-scale.md %}



<a name="option-b"></a>
<a name="option-t"></a>

## Selecting analysis staves

<i>chint</i> currently processes only two staves at a time.  If
there are two staves in the score, these will be selected automatically;
otherwise, the bottom two staves are selected automatically.  To
change the top staff use `-t #` where `#` is the number of the staff
starting at 1 for the bottom staff.  You can use the special number
`$` to indicate the top staff on the system, and `$1` or `$-1` for
the next staff below the top staff on the system.

Here is an example that analyzes the inner voices of a four-part
chorale:

{% include_relative chint-example-staff.md %}

If the top and bottom staves are inverted, such that the lower staff is
higher on the system than the bottom staff, the <i>chint</i> filter will
automatically switch their roles.



<a name="option-i"></a>

## Displaying intervals

The `-i` option will show the harmonic intervals, by default above
the top analysis staff:

{% include_relative chint-example-interval.md %}



<a name="option-d"></a>

### Diatonic intervals

The `-d` option will simplify display of intervals, removing 
chromatic qualification on common intervals:

{% include_relative chint-table-diatonic.md %}

Diminished and augmented intervals retain their chromatic alterations:

{% include_relative chint-example-diatonic.md %}



<a name="option-n"></a>

### Negative intervals

When the voices cross, add `-n` to show a negative sign in front of the
interval.

{% include_relative chint-example-negative.md %}



<a name="option-8"></a>

### Preserving octave information

Add `-8` will preserve octave information in the displayed intervals; otherwise,
perfect octaves will be collapsed into perfect unisons:

{% include_relative chint-example-octave.md %}



<a name="option-O"></a>

### Do not collapse intervals to an octave

To be implemented.



<a name="option-m"></a>

### Middle placement of intervals.

By default, intervals are placed above the top analysis staff.   To place
below the top analysis staff, use the `-m` option (which will place in the
middle of the top and bottom analysis staves if they are adjacent).

{% include_relative chint-example-middle.md %}



<a name="option-T"></a>
<a name="option-B"></a>

## Suppressing colorization

The `-T` and `-B` option can be given to suppressing colorization of the
top and/or bottom staves.   Currently this only works correctly for `-B`
and `-T` will be fixed later.

{% include_relative chint-example-nobottomcolor.md %}

{% include_relative chint-example-notopcolor.md %}

No coloring, but show intervals between the staves, useful for
viewing only interval information:

{% include_relative chint-example-nocolor.md %}



<a name="option-c"></a>

### Alternate color mappings

Alternate color mappings can be used other than the default.  A test
mapping can be used by adding `-c` option, where augmented/diminished
intervals usually have their own unique colors:

{% include_relative chint-example-chromatic.md %}



## Musical examples

See examples using real music:

<a target="_blank" href="https://verovio.humdrum.org/?file=vivaldi/op02/vivaldi-op02n01m01.krn&k=ey&filter=chint%20-mid">Vivaldi op. 2 violin sonatas</a> 

Use left/right arrows in top left corner of VHV to navigate between movements.  
Options `-mid` used to display diatonic intervals between staves.

One practical use of the <i>chint</i> filter is to identify data errors 
where a common interval is incorrectly encoded as a diminished/augmented
interval, such as an augmented/diminished unison:

{% include_relative chint-example-error.md %}




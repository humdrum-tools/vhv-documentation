---
title: Scale degrees
lang: en 
page_language: en
author: "Craig Stuart Sapp"
creation_date: 31 Dec 2022
last_updated:
ref: humdrum-scale_degrees
keywords: humdrum scale degrees
tags: [all, humdrum, scale degrees]
verovio: "true"
datatable: "true"
vim: ts=3 ft=javascript
summary: A description of how to encode scale degrees in **deg and **degree spines.
sidebar: main_sidebar
permalink: /humdrum/scale_degrees/index.html
---

Scale degrees can be encoded in Humdrum data using the `**deg` or
`**degree` exclusive interpretations.  The difference between these two
representation is that `*degree` also encodes octave information,
while `**deg` does not.


{% include_relative scale-degrees.md %}

{% include_relative minor-degrees.md %}

{% include_relative melodic-contour.md %}

{% include_relative font-styling.md %}

{% include_relative solfege.md %}

{% include_relative hide-scale-degrees.md %}

{% include_relative chords.md %}

{% include_relative plain-text.md %}

{% include_relative embedded-verovio-options.md %}

{% include_relative command-line.md %}

## To do ##

* Implement key labels at key designation changes.
* Implement horizontal lines between degrees.
* melodic approaches across rests
* differentiate between repeated notes, secondary tied notes, initial notes



## Signifier summary ##


{% include signifiertable.html
	contentId="summary"
%}
<script type="text/JSON" id="summary">
{% include_relative degreeSignifiers.json %}
</script>



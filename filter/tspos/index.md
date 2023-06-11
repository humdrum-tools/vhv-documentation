---
title: tspos filter
lang: en
page_language: en
author: Wolfgang Drescher
creation_date: 7 Jun 2023
last_updated: 7 Jun 2023
ref: filters-tspos
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: "identify root/third/fifth positions of notes in triadic sonorities."
permalink: /filter/tspos/index.html
---

The `tspos` filter identifies, labels and analyzes triadic sonorities
(diminished, minor, major, and augmented triads).  The <span
style="color:#DC143C;">root</span> of the triad is colored red, the
<span style="color:#32CD32;">third</span> green, and the <span
style="color:#4169E1;">fifth</span> blue.  This tool is useful to
visualize the triadic degrees used in each voice, as well as
statistics about the inversions these triads.

Here is a basic example:

{% include verovio.html
	source="basic"
	humdrum-min-width="250px"
	humdrum-max-height="250px"
	pageMarginTop="60"
	scale="40"
%}
<script type="application/x-humdrum" id="basic">
!!!filter: tspos
**kern	**kern	**kern	**kern
4C	4G	4e	4cc
4CC	4G	4f	4cc
4B	4G	4g	4dd
=	=	=	=
*-	*-	*-	*-
</script>


## Options ##

{% include filter-options.html file="options.aton" lang="EN" %}



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
summary: "Analyze triadic positions in sonorities."
permalink: /filter/tspos/index.html
---

The `tspos` filter identifies triadic sonorities (diminished, minor,
major, and augmented triads).  The root of the triad is colored
red, the third green and the fifth blue.  This tool is useful to
visualize the triad degree used in each voice, as well as extra
statistics about the invarions these triads.

Here is a basic example:

{% include verovio.html
	source="basic"
	humdrum-min-width="250px"
	humdrum-max-height="250px"
	pageMarginTop="60"
	scale="50"
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





---
title: addkey filter
lang: en
page_language: en
author: Craig Stuart Sapp
creation_date: 22 Apr 2024
last_updated:
ref: filters-addkey
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: "Set the tempo of the score"
permalink: /filter/addkey/index.html
---

The *addkey* filter adds a key designation
of a Humdrum file.

Without options, the `addkey` tool searches the data for a `!!!key:
g:dor`, such as for G dorian.   This will be inserted as a key
designation in the header, such as `*g:dor` using this example.

The key designation can be created/change with the `-k` option

To also set the `!!!key:` record with the input `-k` key designation, use `-K`.


## Options ##

{% include filter-options.html file="options.aton" lang="EN" %}


## Future enhancements ##

* Allow adding/changing key signature.
* Allow adding key signatures/designations at specified points within the file.



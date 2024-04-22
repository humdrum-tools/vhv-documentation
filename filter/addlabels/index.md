---
title: addlabels filter
lang: en
page_language: en
author: Craig Stuart Sapp
creation_date: 22 Apr 2024
last_updated:
ref: filters-addlabels
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: "Set the tempo of the score"
permalink: /filter/addlabels/index.html
vim: nowrap:ft=text
---

The *addlabels* filter adds thru labels and expansion lists to a
Humdrum file.  See also the documentation for <a target="_blank"
href="/filter/thru">thru</a>.


## Options ##

{% include filter-options.html file="options.aton" lang="EN" %}


## Examples ##

| Option | Meaning |
| ------ | ------- |
| `-d "A,A,B,B1,B,B2,A"` | Default expansion list: <code>*>[A,A,B,B1,B,B2,A]</code> (including a *da capo* repeat |
| `-r "A,B,B2,A` | No-repetion expansion list: <code>*>norep[A,B,B2,A]</code>. |
| `-l "0:A; m15b:B; m20:B1; m22:B2"` | Labels to insert in score by measure locations (<code>0</code> means insert in header of file). "b" prefix for <code>B</code> label means the next barline after the first one labeled as measure numbered in score with 15". |





---
title: Splits
lang: en
page_language: en
author: Craig Stuart Sapp
creation_date: 25 Apr 2022
last_updated:
ref: splits
tags: [all]
keywords: interface url
summary: "Splits are used to speed up data correction on long scores."
sidebar: main_sidebar
permalink: /howto/splits/index.html
---

The View&rarr;Splits menu list splitting options.

A "split" is a selected region of the music that will be displayed while
other regions are hidden.  This allows redrawing of the music only 
in the split area, speeding up the time from when you make an edit
to when it is rendered.

Available options:

<dl>

<dt> Start splitting (32-measure splits) </dt>
<dd> Starts splitting at the beginning of the score in 32 measure increments. </dd>

<dt> Next measure split </dt>
<dd> Display the next 32 measures of the score</dd>

<dt> Previous measure split </dt>
<dd> Display the previous 32 measures of the score. </dd>

<dt> Start splitting (8-system splits) </dt>
<dd> Start splitting at the beginning of the score in 8 system increments. </dd>

<dt> Next system split </dt>
<dd> Display the next 8 system of the score. </dd>

<dt> Previous system split </dt>
<dd> Display the previous 8 systems of the score. </dd>

<dt> Remove splits </dt>
<dd> Stop splitting the score. (return to full view)</dd>

</dl>


Splitting can be done manually by adding `!!ignore` at the start of sections
that you want to hide, and `!!Xignore` to start displaying the score again.




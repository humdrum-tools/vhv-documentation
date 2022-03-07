---
title: Syntax validation
lang: en es
ref: interface-validation
author: Craig Stuart Sapp
translator: 
creation_date: 19 Aug 2017
translation_date: 
last_updated: 19 Aug 2017
tags: [all, getting_started]
keywords: interface syntax validation
summary: "VHV will validate the structure and rhythmic syntax of Humdrum files before attempting to render them to graphical notation."
sidebar: main_sidebar
permalink: /interface/validation/index.html
---

## Syntax errors ##

When editing a Humdrum file in [Verovio Humdrum
Viewer](http://verovio.humdrum.org), the [ace](https://ace.c9.io/)
editor automatically validates the Humdrum file structure as data
is typed.  If it detects invalid structure in the Humdrum content,
the graphical music notation windows will be highlighted in pink,
and an error message can be viewed by moving the mouse over any
"x" boxes displayed in the line-number gutter to the left of the
editor window.

Here is a demonstration of structural syntax errors:

{% include image.html
	file="syntax-error-1.png"
	max-width="80%"
	alt="Syntax errors"
	caption="Structural syntax errors."
%}

The first problem is that the spine was not split properly into two
sub-spines.  Adding `*^` after line 2 will fix that problem:

{% include image.html
	file="syntax-error-2.png"
	max-width="80%"
	alt="Syntax error 1 fixed"
	caption="First structural syntax error fixed."
%}

Now there is just a single syntax error on line 8.  Fix this error by
adding two `*v` merge tokens to combine the subspines into a single
spine again:

{% include image.html
	file="syntax-error-3.png"
	max-width="80%"
	alt="Syntax error 2 fixed"
	caption="Second structural syntax error fixed."
%}

Notice that the graphic notation is not highlighted in pink, which
indicates that the data was rendered successfully.  Also notice that
when the graphic music is highlighted in pink, the last valid state of 
the humdrum data will be shown, and any new content added after 
the invalid structure was identified will not be shown.


## Syntax warnings ##

Syntax warnings are shown as an exclamation mark in a yellow caution
triangle within the line-number gutter on the left side of the text
editor.  These errors are non-critical, but should be fixed if
preparing a score for public distribution.

Here is an example warning icon that appears on blank lines:

{% include image.html
	file="blank-line-warning.png"
	max-width="80%"
	alt="blank line warning"
	caption="Warning icon displayed for a blank line."
%}

If you move your mouse over the warning icon, and explanation of the
warning will be displayed:

{% include image.html
	file="blank-line-warning-message.png"
	max-width="80%"
	alt="blank line warning message"
	caption="Warning message for a blank line, viewable when mousing over warning icon."
%}

### End-of-spine syntax warning ###

The end-of-spine syntax warning is a special case where a warning
message is displayed when a spine is not terminated properly using 
a `*-` token:

{% include image.html
	file="end-of-spine-warning.png"
	max-width="80%"
	alt="end-of-spine warning message"
	caption="Warning message for missing spine terminator."
%}

For command-line parsing of Humdrum data, this warning is an error
in the file structure that will be identified by the *humdrum*
command.  However it is treated as a warning in VHV so that graphical
music notation can be displayed while the data is being typed into the
text editor.  Remember to terminate the spine properly when finished
entering the music.


## Rhythmic syntax ##

Rhythmic syntax in VHV is also dynamically checked in a similar
manner to the file structure.  The error messages in this case are
displayed on the line where the rhythmic error is noticed rather
than on the line where the rhythmic error occurs (since it is not
always possible to identify which spine has the rhythmic error.

Here is an example rhythmic error, where the data for the top staff of
music contains a dotted quarter note instead of a regular quarter note:

{% include image.html
	file="rhythm-error.png"
	max-width="80%"
	alt="rhythm syntax error"
	caption="Rhythm syntax error."
%}

Notice that the error is found on the 11th line, but the error
is actually on the 10th line.  Moving the mouse over the error
icon will display an explanation about the warning:

{% include image.html
	file="rhythm-error-warning.png"
	max-width="80%"
	alt="rhythm syntax error warning "
	caption="Rhythm syntax error warning."
%}

This means that at field (column) 2 the rhythm is advanced an
eighth note ahead of field (column) 1, since there is a
dotted eighth-note instead of a quarter note in the second spine at
line 10.


Fixing the rhythmic error allows the Humdrum data to be sent to the
verovio toolkit for rendering into graphical notation:

{% include image.html
	file="rhythm-error-fixed.png"
	max-width="80%"
	alt="rhythm syntax error fixed "
	caption="Rhythm syntax error fixed."
%}



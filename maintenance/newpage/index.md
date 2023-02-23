---
title: Creating a new documentation page
lang: en
page_language: en
author: Craig Stuart Sapp
creation_date: 14 Mar 2017
last_updated:
ref: maintenance-newpage
search: exclude
tags: [all, maintenance]
sidebar: main_sidebar
keywords: maintenance new page
summary: This page describes how to create a new documentation page and add it to the sidebar menu.
permalink: /maintenance/newpage/index.html
---

## Topic directories ##

To create a new page, several steps need to be done.  First create a new directory
within the directory for a sidebar topic (or create a new directory for a new topic).
The current topic directories are:


commands
: Description of keyboard commands and other interations for controlling the VHV interface.

graphic
: keyboard comands, clicks, etc., for doing graphic editing in the music notation editor.

humdrum
: encoding topics for Humdrum data format.

interface
: Description of the VHV user interface.

maintenance
: Descriptions of how to create and maintain the documentation website.

myvhv
: Examples of how to use verovio and humdrum in your own projects.


## Subtopic directory ##

After creating a subtopic directory, copy an `index.md` file from a related
subtopic directory.  For exmple, this page is called `index.md` is in the 
`maintenance` topic directory, and the `newpage` subtopic directory.


## Liquid header ##

Each documentation page contains a liquid header, such as the one for this file:


```liquid
---
search: exclude
title: Creating a new documentation page
author: Craig Stuart Sapp
creation_date: 14 Mar 2017
last_updated: 14 Mar 2017
tags: [all, maintenance]
sidebar: main_sidebar
keywords: maintenance new page
summary: This page describes how to create a new documentation page and add it to the sicebar menu.
permalink: /maintenance/newpage/index.html
---
```


Recognized parameter names and their meanings:

search: exclude
: Add this line if you do not want the page to turn up in the search results.

title
: the main title of the page, shown in large font underneath the top
navigation bar.

author
: The primary author, or a list such as `[author1, author2]` if there is more
than one author.

editor
: A non-author editor (improving text, adding only a little content), or a list such as `[editor1, editor2]` if there is more than one editor.

creation_date
: The date that the page was created.

last_updated
: The date that the page was last edited.

tags
: A list of all topic tags which apply to the page.

sidebar: main_sidebar
: This is the main sidebar for the website (should be added to most any page).

keywords
: Search times for interaction with search engine indexing.

summary
: Short description of the page which is shown immediately underneath the title at the top of the page.

datatable: true
: Enable [datatables](..//tables/#datatables) on the page.  This variable is used in the
[default.html layout file](https://github.com/humdrum-tools/vhv-documentation/tree/master/_layouts/default.html).


verovio: true
: Enable verovio javascript toolkit on the webpage for [interactive humdrum figures](../verovio).
This variable is used in the
[default.html layout file](https://github.com/humdrum-tools/vhv-documentation/tree/master/_layouts/default.html).

permalink
: the URL pathname for the compiled HTML page.  This should almost always be the same location and name as `index.md`, but renamed `index.html`.

{% include warning.html
	content="The `permalink` parameter is important, and should be set correctly, particularly when copying an existing page and modifying it to create a new page.  This parameter instructs jekyll where to save the final HTML file generated from the page."
%}

## Adding a new page to main sidebar ##

After content has been added to the page, you can add a link to the page
on the main sidebar.  The sidebar is located in
[_data/sidebars/main_sidebar.yml](https://github.com/humdrum-tools/vhv-documentation/tree/master/_data/sidebars/main_sidebar.yml)
It should be obvious what to add when you see the file.




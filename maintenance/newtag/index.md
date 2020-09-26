---
search: exclude
title: Creating a new tag
lang: en
ref: maintenance-newtag
author: Craig Stuart Sapp
translator: 
creation_date: 14 Mar 2017
translation_date: 
last_updated: 14 Mar 2017
tags: [all, maintenance]
sidebar: main_sidebar
keywords: maintenance new tag
summary: This page describes how to create a new tag and add it to the page indexes.
permalink: /maintenance/newtag/index.html
---

## Tag ##

A *tag* is a topic subject which can be used to group related pages together.

## Allowed tags ##

The file [_data/tags.yml](https://github.com/humdrum-tools/vhv-documentation/tree/master/_data/tags.yml) contains a list of allowed tags for the website. If you want to
create a new tag, add it to this list.

## Using a tag ##

At the top of a documentation paage, there should be `tags` parameter that lists
the tags that apply to the page.  The tags for this page are:

```liquid
tags: [all, maintenance]
```

All pages should contain the tag `all`.


## Creating an index page for a tag ##

The `Indexes` entry in the sidebar contains a list of pages grouped by tags.
If you create a new tag, then you should also create a new index page.  If the new
tag is `xxx`, then you should also create the file `pages/tags/tag_xxx.md`, with the 
content:

{% assign specialstart = '{%' %}
{% assign specialend1 = '%' %}
{% assign specialend2 = '}' %}

```liquid
---
title: "Xxx pages index"
tagName: xxx
search: exclude
permalink: tag_xxx.html
sidebar: main_sidebar
folder: tags
---
{{ specialstart }} include taglogic.html {{ specialend1 }}{{ specialend2 }}
```

## Add tag index file to sidebar ##

The tag index file should be linked to from the sidebar.  Edit the 
[_data/sidebars/main_sidebar.yml](https://github.com/humdrum-tools/vhv-documentation/tree/master/_data/sidebars/main_sidebar.yml), and add an entry for the tag index in the `Indexes` section.

The entry for the xxx tag would be:

```yml
    - title: Xxx pages
      output: web, pdf
      url: /tag_xxx.html
```


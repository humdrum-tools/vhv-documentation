---
search: exclude
title: Keypress icons
author: Craig Stuart Sapp
creation_date: 11 Mar 2017
last_updated: 11 Mar 2017
tags: [all, maintenance]
datatable: true
sidebar: main_sidebar
keywords: maintenance key press
summary: "This page describes how to add key icons to documentation text."
permalink: /maintenance/keypresses/index.html
---

Keypresses can be added by enclosing the keys within a span element that is
marked with the class `keypress`.  For example the key <span class="keypress">@</span>
is encoded with this text:

```html
<span class="keypress">@</span>
```

## Key combinations ##

Keypress combinations are enclosed in a single span element, with a dash separating
the separate keystrokes that are supposed to be pressed at the same time.  For example
the key combination <span class="keypress">alt-s</span> is created with the text:

```html
<span class="keypress">alt-s</span>
```

## Key sequences ##

A sequence of keys to press in succession is encoded by placing a plus sign between
each key.  For example <span class="keypress">3+s</span> is created with the text:

```html
<span class="keypress">3+s</span>
```

## Key sequences and combinations mixtures ##

Key sequences and combinations can be mixed in the same span content.  For example
the keys <span class="keypress">3+alt-s</span>, which means press the
<span class="keypress">3</span> key followed by <span class="keypress">alt-s</span>,
is created by the text:

```html
<span class="keypress">3+alt-s</span>
```

## Special key names ##

Here is a list of keys which have special names:

{% include keytable.html
	contentId="specialkeys"
%}

<script type="text/json" id="specialkeys">
{
	"tableColumns":
	[
		{ "data": "key",  "title": "Key" },
		{ "data": "text", "title": "Text"}
	],

	"categoryList":
	[
		{
			"categoryName": "special keys",
			"keyList": 
			[

				{
					"key": "<span class='keypress'>command</span>",
					"text": "<code>&lt;span class='keypress'&gt;command&lt;span&gt;</code>"
				},

				{
					"key": "<span class='keypress'>control</span>",
					"text": "<code>&lt;span class='keypress'&gt;control&lt;span&gt;</code>"
				},

				{
					"key": "<span class='keypress'>alt</span>",
					"text": "<code>&lt;span class='keypress'&gt;alt&lt;span&gt;</code>"
				},

				{
					"key": "<span class='keypress'>shift</span>",
					"text": "<code>&lt;span class='keypress'&gt;shift&lt;span&gt;</code>"
				},

				{
					"key": "<span class='keypress'>hash</span>",
					"text": "<code>&lt;span class='keypress'&gt;hash&lt;span&gt;</code>"
				},

				{
					"key": "<span class='keypress'>at</span>",
					"text": "<code>&lt;span class='keypress'&gt;at&lt;span&gt;</code>"
				},

				{
					"key": "<span class='keypress'>minus</span>",
					"text": "<code>&lt;span class='keypress'&gt;minus&lt;span&gt;</code>"
				},
			
				{
					"key": "<span class='keypress'>plus</span>",
					"text": "<code>&lt;span class='keypress'&gt;plus&lt;span&gt;</code>"
				},
			
				{
					"key": "<span class='keypress'>escape</span>",
					"text": "<code>&lt;span class='keypress'&gt;escape&lt;span&gt;</code>"
				},
			
				{
					"key": "<span class='keypress'>space</span>",
					"text": "<code>&lt;span class='keypress'&gt;space&lt;span&gt;</code>"
				},
			
				{
					"key": "<span class='keypress'>up</span>",
					"text": "<code>&lt;span class='keypress'&gt;up&lt;span&gt;</code>"
				},
			
				{
					"key": "<span class='keypress'>down</span>",
					"text": "<code>&lt;span class='keypress'&gt;down&lt;span&gt;</code>"
				},
			
				{
					"key": "<span class='keypress'>left</span>",
					"text": "<code>&lt;span class='keypress'&gt;left&lt;span&gt;</code>"
				},
			
				{
					"key": "<span class='keypress'>right</span>",
					"text": "<code>&lt;span class='keypress'&gt;right&lt;span&gt;</code>"
				}
			]
		}
	]
}
</script>




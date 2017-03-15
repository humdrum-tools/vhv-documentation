---
search: exclude
title: Tables
author: Craig Stuart Sapp
creation_date: 12 Mar 2017
last_updated: 12 Mar 2017
tags: [all, maintenance]
datatable: true
vim: ts=3
sidebar: main_sidebar
keywords: maintenance datatables table
summary: This page describes how to create tables for VHV documentation.
permalink: /maintenance/tables/index.html
---

{% assign specialstart = '{% include keytable.html' %}
{% assign specialend1 = '%' %}
{% assign specialend2 = '}' %}

Tables for the VHV documentation can be created in several ways, depending
on the complexity of the contents.

## Markdown tables ##

For pages encoded using Markdown, simple tables can be encoded in 
[Markdown syntax](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#tables):

```markdown
| Left justified | Centered      |     Right |
| -------------- |:-------------:| ---------:|
| row 1          | A             |      1492 |
| row 2          | BB            |       492 |
| row 3          | CCC           |        42 |
```

which renders on the page as:

| Left justified | Centered      | Right |
| -------------- |:-------------:| -----:|
| row 1          | A             |  1492 |
| row 2          | BB            |   492 |
| row 3          | CCC           |    42 |

The Markdown table must have a blank line before and after it in
order for the parser to recognize that it is supposed to be a table
to convert into HTML format.  Markdown tables cannot be enclosed
in HTML elements, but may contain HTML formatting.  The Markdown
table rows will automatically be [zebra
striped](https://alistapart.com/article/zebrastripingmoredataforthecase),
and will have no borders between cells on a row.

## HTML tables ###

HTML tables can be used for more complicated cases that require more
control over layout:


```html
<style>
   #mytable td:nth-of-type(1), #mytable th:nth-of-type(1) { text-align: left; }
   #mytable td:nth-of-type(2), #mytable th:nth-of-type(2) { text-align: center; }
   #mytable td:nth-of-type(3), #mytable th:nth-of-type(3) { text-align: right; min-width: 100px }
   #mytable td.marked { background-color: red; border-radius: 20px; }
</style>
<table id="mytable">
   <thead>
      <tr>
         <th> Left justified </th>
         <th> Centered       </th>
         <th> Right          </th>
      </tr>
   </thead>
   <tbody>
      <tr>
         <td> row 1 </td>
         <td> A     </td>
         <td> 1492  </td>
      </tr>
      <tr>
         <td> row 2 </td>
         <td class="marked"> BB </td>
         <td> 492 </td>
      </tr>
      <tr>
         <td> row 3 </td>
         <td> CCC   </td>
         <td> 42    </td>
      </tr>
   </tbody>
</table>
```

<style>
   #mytable td:nth-of-type(1), #mytable th:nth-of-type(1) { text-align: left; }
   #mytable td:nth-of-type(2), #mytable th:nth-of-type(2) { text-align: center; }
   #mytable td:nth-of-type(3), #mytable th:nth-of-type(3) { text-align: right; min-width: 100px }
   #mytable td.marked { background-color: red; border-radius: 20px; }
</style>
<table id="mytable">
   <thead>
      <tr>
         <th> Left justified </th>
         <th> Centered       </th>
         <th> Right          </th>
      </tr>
   </thead>
   <tbody>
      <tr>
         <td> row 1 </td>
         <td> A     </td>
         <td> 1492  </td>
      </tr>
      <tr>
         <td> row 2 </td>
         <td class="marked"> BB </td>
         <td> 492 </td>
      </tr>
      <tr>
         <td> row 3 </td>
         <td> CCC   </td>
         <td> 42    </td>
      </tr>
   </tbody>
</table>

The HTML-constructed table looks similar to the Markdown version,
but the last column was given extra width to not be crowded with
the second column.  And of course, the middle cell of the table has
been highlighted in red.


## Datatables ###

For more sophisticated tables, such as being able to sort by different
columns, a jQuery plugin called [datatables](http://idratherbewriting.com/documentation-theme-jekyll/mydoc_tables.html) is available in the documentation.

To use datatables, you must add this line to the page header:

```liquid
datatable: true
```

This will enable the datatables plugin on the current page.  Then
give each table an id (or a shared class name if all tables have
the same style on the page), and include a short piece JavaScript
code that processes the table with the datatables plugin:

```javascript
<script>
$(document).ready(function() {
	$("table#mytable2").DataTable({
		paging: true,
		stateSave: true,
		searching: true
	});
});
</script>
```

In this case three parameters are set:

paging: true
: For long tables, only show one page of the data at a time.

stateSave: true
: Keep track of the state of the table when returning to the page (keeping track
of the page number if paged, and the search text if searching is enabled.

searching: true
: Enable searching the datables content.

Datatables has [lots of other options](https://www.datatables.net/manual/options).  Also 
see the [datatable examples page](https://datatables.net/examples).


{% include warning.html
	content="You must also activate datatables on the page by including the page header parameter \"`datatable: true`\" &nbsp;&nbsp; (at the top of the file). Also not that the parameter name is singular."
%}

### Sortable column table ###

Here is an example of creating a table with sortable columns using datatables.

```html
<script>
$(document).ready(function() {
	$("table#mytable2").DataTable({
		paging: true,
		stateSave: true,
		searching: true
	});
});
</script>
<style>
   #mytable2 td:nth-of-type(1), #mytable th:nth-of-type(1) { text-align: left; }
   #mytable2 td:nth-of-type(2), #mytable th:nth-of-type(2) { text-align: center; }
   #mytable2 td:nth-of-type(3), #mytable th:nth-of-type(3) { text-align: right; min-width: 100px }
   #mytable2_info { display: none; }
</style>
<table id="mytable2">
   <thead>
      <tr>
         <th> Left justified </th>
         <th> Centered       </th>
         <th> Right          </th>
      </tr>
   </thead>
   <tbody>
      <tr>
         <td> row 1 </td>
         <td> A     </td>
         <td> 1492  </td>
      </tr>
      <tr>
         <td> row 2 </td>
         <td> CC    </td>
         <td> 92    </td>
      </tr>
      <tr>
         <td> row 3 </td>
         <td> BBB   </td>
         <td> 142   </td>
      </tr>
      <tr>
         <td> row 4 </td>
         <td> ZZZZ   </td>
         <td> 942   </td>
      </tr>
      <tr>
         <td> row 5 </td>
         <td> IIIII </td>
         <td> 642   </td>
      </tr>
   </tbody>
</table>
```

here is the reuslting table that is displayed on the page:

<script>
$(document).ready(function() {
	$("table#mytable2").DataTable({
		paging: false,
		stateSave: false,
		searching: false
	});
});
</script>
<style>
   #mytable2 td:nth-of-type(1), #mytable2 th:nth-of-type(1) { text-align: left; }
   #mytable2 td:nth-of-type(2), #mytable2 th:nth-of-type(2) { text-align: center; }
   #mytable2 td:nth-of-type(3), #mytable2 th:nth-of-type(3) { text-align: right; max-width: 100px; }
   table.dataTable.no-footer { border-bottom: 1px solid #ddd; }
   #mytable2_info { display: none; }
</style>
<table id="mytable2">
   <thead>
      <tr>
         <th> Left justified </th>
         <th> Centered       </th>
         <th> Right          </th>
      </tr>
   </thead>
   <tbody>
      <tr>
         <td> row 1 </td>
         <td> A     </td>
         <td> 1492  </td>
      </tr>
      <tr>
         <td> row 2 </td>
         <td> CC    </td>
         <td> 92    </td>
      </tr>
      <tr>
         <td> row 3 </td>
         <td> BBB   </td>
         <td> 142   </td>
      </tr>
      <tr>
         <td> row 4 </td>
         <td> ZZZZ   </td>
         <td> 942   </td>
      </tr>
      <tr>
         <td> row 5 </td>
         <td> IIIII </td>
         <td> 642   </td>
      </tr>
   </tbody>
</table>


## Table templates ##

This section describes table templates to use on the document pages, mostly to interface with datatables.


### Keypress tables ###

For graphical commands, a template called `keytable.html` is used to create a summary table of keys and key combinations
at the top of each graphical editing page.  The template consists of two
components: (1) a liquid template for including the keypress table on the page, and 
(2) a script containing a JSON object describing the information with which to buile the table.

The template requires a parameter called `content` which specifies the ID of the JSON script from
which it will load the data.

The JSON object contains two parameters in the main level of the object:

tableColumns
: This is an array describing the column type and column title.

categoryList
: An array of groups of keys.

The *categoryList* is an array of objects, each object containing a list of keys for the category the containing two parameters:

categoryName
: The name of the group, which will be shown in the table as a subject heading.

keyList
: An array of keys and descriptions of the keys..

The *groupsList[].keyList* array contains two parameters with the contents of a regular row in the table:

keys
: The key press(es) that do something.

description
: A description of what the key(s) do.

<style>

code {
	-moz-tab-size: 1;
	-o-tab-size: 1;
	tab-size: 1;
}

</style>


```javascript

{{ specialstart }}
	content="slurkeysummary"
{{ specialend1 }}{{ specialend2 }}

<script type="text/JSON" id="slurkeysummary">
{
	"tableColumns":
	[
		{ "data": "keys",   "title": "Key(s)" },
		{ "data": "description", "title": "Action"}
	],
	"categoryList": 
	[
		{
			"categoryName": "adding a slur to a note",
			"keyList":
			[
 				{
					"keys": "<span class='keypress'>s</span>",
					"description": "Add a slur to the next note"
				},
	
				{
					"keys": "<span class='keypress'>2+s</span>",
					"description": "Add slur starting on current note and including next two notes"
				},
			
				{
					"keys": "<span class='keypress'>9+s</span>",
					"description": "Add slur starting on current note and including next nine notes"
				}
			]
		},
		{
			"groupName": "editing slurs",
			"keyList":
			[
				{
					"keys": "<span class='keypress'>a</span>",
					"description": "force slur above notes"
				},
			
				{
					"keys": "<span class='keypress'>b</span>",
					"description": "force slur below notes"
				},
			
				{
					"keys": "<span class='keypress'>c</span>",
					"description": "clear forced slur direction"
				},
			
				{
					"keys": "<span class='keypress'>left</span>",
					"description": "move slur start one note to the left"
				},
			
				{
					"keys": "<span class='keypress'>right</span>",
					"description": "move slur start one note to the right"
				},
			
				{
					"keys": "<span class='keypress'>shift-left</span>",
					"description": "move slur end one note to the left"
				},
			
				{
					"keys": "<span class='keypress'>shift-right</span>",
					"description": "move slur end one note to the right"
				},
			
				{
					"keys": "<span class='keypress'>escape</span>",
					"description": "deselect the slur"
				}
			]	
		}
	]
}
</script>
```

This renders as:

{% include keytable.html
	contentId="slurkeysummary"
%}
<script type="text/JSON" id="slurkeysummary">
{
	"tableColumns":
	[
		{ "data": "keys",   "title": "Key(s)" },
		{ "data": "description", "title": "Action"}
	],
	"categoryList": 
	[
		{
			"categoryName": "adding a slur to a note",
			"keyList":
			[
 				{
					"keys": "<span class='keypress'>s</span>",
					"description": "Add a slur to the next note"
				},
	
				{
					"keys": "<span class='keypress'>2+s</span>",
					"description": "Add slur starting on current note and including next two notes"
				},
			
				{
					"keys": "<span class='keypress'>9+s</span>",
					"description": "Add slur starting on current note and including next nine notes"
				}
			]
		},
		{
			"categoryName": "editing slurs",
			"keyList":
			[
				{
					"keys": "<span class='keypress'>a</span>",
					"description": "force slur above notes"
				},
			
				{
					"keys": "<span class='keypress'>b</span>",
					"description": "force slur below notes"
				},
			
				{
					"keys": "<span class='keypress'>c</span>",
					"description": "clear forced slur direction"
				},
			
				{
					"keys": "<span class='keypress'>left</span>",
					"description": "move slur start one note to the left"
				},
			
				{
					"keys": "<span class='keypress'>right</span>",
					"description": "move slur start one note to the right"
				},
			
				{
					"keys": "<span class='keypress'>shift-left</span>",
					"description": "move slur end one note to the left"
				},
			
				{
					"keys": "<span class='keypress'>shift-right</span>",
					"description": "move slur end one note to the right"
				},
			
				{
					"keys": "<span class='keypress'>escape</span>",
					"description": "deselect the slur"
				}
			]	
		}
	]
}
</script>



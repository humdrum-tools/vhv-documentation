---
title: Spreadsheet Toolbar
lang: en
ref: interface-toolbar
author: Craig Stuart Sapp
translator: 
creation_date: 20 Sep 2020
translation_date: 
last_updated: 2 Oct 2020
tags: [all, getting_started]
keywords: interface toolbar
summary: "A Description of the spreadsheet toolbar."
sidebar: main_sidebar
vim: ts=3
permalink: /interface/toolbar/spreadsheet/index.html
---

{% include_relative style-local.html %}
{% include_relative scripts-local.html %}

The spreadsheet toolbar is used for setting up interaction between
VHV and Google Sheets.  This allows for doing more advanced editing
of Humdrum text in a spreadsheet than can be done in the plain-text
editor of VHV, such as adding and deleting columns, hiding columns,
or adding temporary columns for data entry or analysis.  Working
with orchestral scores is also easier in a spreadsheet, where you can
freeze a header at the row showing the instrument names while you
edit the music further below.

The spreadsheet toolbar contains a text box and five icons:

<br>

<div class="toolbar" id="toolbar-6">
	<input id="macroid"  type="text" spellcheck="false" placeholder="Spreadsheet script ID">
	<div title="Upload data to spreadsheet" class='nav-icon fa fa-cloud-upload'></div>
	<div title="Download data from spreadsheet" class='nav-icon fa fa-cloud-download'></div>
	<div title="open linked spreadsheet" class='nav-icon fa fa-file-text'></div>
	<div title="About spreadsheets" class='nav-icon fas fa-question-circle'></div>
	<span id="line-break-icon">
		<div title="Go to next toolbar menu (alt-n)" class='nav-icon fa fa-superpowers'></div>
	</span>
</div>

<br><br>

<table class="toolbar-info">

<tr><td>
<div style="font-size:3rem !important;" class="toolbar">
	<span id="search-group">
		<input id="scriptid2" type="text" autocomplete="off" spellcheck="false" placeholder="script ID">
	</span>
</div>
</td>
<td>

	<span class="summary-icon">Spreadsheet script ID.</span>

	See instructions below for creating a spreadsheet and getting
	its script ID to paste into this box to interact with the
	spreadsheet.  The spreadsheet ID can be appended to the script
	ID, which will cause a "open linked spreadsheet" icon to
	appear in the toolbar.

</td>
</tr>


<tr><td>
<div class="toolbar">
	<div title="Upload editor contents to spreadsheet" class='nav-icon fa fa-cloud-upload'></div>
</div>
</td>
<td>

	<span class="summary-icon">Upload to spreadsheet.</span>

	The contents of the VHV text editor will be uploaded to the linked
	spreadsheet, replacing any current contents of the spreadsheet.

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="Download spreadsheet contents to editor" class='nav-icon fa fa-cloud-download'></div>
</div>
</td>
<td>

	<span class="summary-icon">Download from spreadsheet.</span>

	The contents of the linked spreadsheet will be downloaded and
	replace the current contents of the VHV text editor.

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="Open linked spreadsheet" class='nav-icon fa fa-file-text'></div>
</div>
</td>
<td>

	<span class="summary-icon">Open linked spreadsheet.</span>

	The spreadsheet ID can be appended to the script ID in the
	input text box, seprating them with a pipe character (|)
	or a space.  When a spreadsheet ID is present, this icon
	will appear, and you can click on it to open the linked
	spreadsheet in another tab.  Once you add the spreadsheet ID
	to the Spreadsheet script ID box, this icon will only appear
	after you click on the upload or download button; however, it
	will show up when reloading the VHV webpage after that.

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="About the toolbar" class='nav-icon fa fa-question-circle'></div>
</div>
</td>
<td>

	<span class="summary-icon">Spreadsheet toolbar documentation.</span>

	This page.

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="Go to next toolbar menu (alt-n)" class='nav-icon fa fa-superpowers'></div>
</div>
	<span class="keypress">alt-n</span>
	<span class="keypress">#-alt-n</span>
</td>
<td>

	<span class="summary-icon">Go to next toolbar.</span>

	To return to this toolbar directly, press <span
	class="keypress">6+alt-n</span> (when not focused on the text editor).  Press the <span
	class="keypress">shift</span> key while clicking to cycle
	through the toolbars in the opposite direction.

</td>
</tr>

</table>


## Setting up a link to Google Sheets ##

To make a connection between VHV and <a target="_blank"
href="https://www.google.com/sheets/about">Google Sheets</a>, you
first need to create a Google spreadsheet, then copy and paste and
publish this <a target="_blank" href="http://bit.ly/humdrum-io">Google
Apps Script</a> for the spreadsheet, and finally copy and paste the
published script's ID into the input box on spreadsheet toolbar.
The instructions for setting up the script are given in the following
sub-sections.


### Step one: create a spreadsheet ###

Create a new spreadsheet in <a target="_blank"
href="https://sheets.google.com">Google Sheets</a>.  You need to
have a Google account to do this step.


{% include image.html
	file="blank-spreadsheet.png"
	alt="Create a blank spreadsheet"
	caption="Create a blank spreadsheet."
%}


### Step two: open the script editor ###

Save the spreadsheet with a name of your choosing, such as "Humdrum
interaction" in the following example.  Then go to the menu Tools &rarr; Script editor:

{% include image.html
	file="tools-script-editor.png"
	alt="Open the script editor"
	caption="Open the script editor."
%}

A new tab will open, displaying the script editor:

{% include image.html
	file="script-editor.png"
	alt="The script editor"
	caption="The script editor."
%}


### Step three: copy and save the script ###


<br>
<br>
<button class="copy-button" onclick="copyToClipboard()">Copy script to clipboard</button>
<br>
<br>

Copy the current Humdrum interaction script from <a target="_blank"
href="https://sheet.humdrum.org">this link</a>, or click on the
copy button above this paragraph.  Then paste into the `Code.gs`
tab in the script editor, replacing the original contents.  This
script will be updated over time, so you can recopy it every once
in a while to get the script with more features and/or bug fixes
(as well as new bugs).



{% include image.html
	file="script.png"
	alt="The script editor"
	caption="The script editor."
%}

Then save the script, giving a name of your choice to the script project:

{% include image.html
	file="script-save.png"
	alt="Save the script project"
	caption="Save the script project."
%}


### Step four: deploy the script ###

To use the script, it must be "deployed".  Press the blue "Deploy" button
and select "New development":


{% include image.html
	file="script-deploy.png"
	alt="Deploy the script"
	caption="Deploy the script."
%}


A sub-window will appear.  Click on the gear icon next to the "Select type" and choose "Web app":

{% include image.html
	file="script-deploy2.png"
	alt="Script deployment type"
	caption="Script deployment type."
%}

The following subwindow will appear.  Add a description of your choosing,
change "Who has access" to "anyone", and then click on the blue "Deploy" button:


{% include image.html
	file="script-deploy3.png"
	alt="Script deployment"
	caption="Script deployment."
%}


{% include warning.html
	content="In the future, less permissive settings may be possible.  In the meantime, do not share the final script ID unless you want other people to use the same spreadsheet, such as for collaborative editing."
%}


The first time you deploy, you will have to authorize the script:

{% include image.html
	file="script-authorize.png"
	alt="Script authorization"
	caption="Script authorization."
%}

In the next window, choose that account that you use with Google Sheets:

{% include image.html
	file="script-authorize2.png"
	alt="Select account for script authorization"
	caption="Select account for script authorization."
	max-width="50%"
%}

A warning window will appear.  Click on the Advanced link:

{% include image.html
	file="script-authorize3.png"
	alt="Click on Advanced"
	caption="Click on Advanced."
	max-width="60%"
%}

Then click on the link "Go to Humdrum interaction (unsafe)" (or
whatever you named the script). And then finally click on the "Allow"
button to activate the script:

{% include image.html
	file="script-authorize5.png"
	alt="Click on Allow to finish authorization"
	caption="Click on Allow to finish authorization."
	max-width="60%"
%}

A window such as the following will appear if the deployment 
is successful:

{% include image.html
	file="deployment.png"
	alt="Final deployment window."
	caption="Final deployment window."
	max-width="60%"
%}

Copy the Deployment ID and click on the blue "Done" button.

If you want to edit the script to add your own functionalities
(which you could post to the <a target="_blank"
href="https://github.com/humdrum-tools/verovio-humdrum-viewer/issues">Verovio
Humdrum Viewer issues</a> if you want to share), see the <a
target="_blank"
href="https://developers.google.com/apps-script/reference/spreadsheet">Google
Apps Script documentation</a>.  The script is in the JavaScript
language, integrated with Google Sheets API functionality.


## Linking VHV to Google Sheets ##

After deploying the script, you now are ready to connect VHV to Google Sheets.

The script deployment ID will be something like this:

```
AKfycbxIXX29Z3qsWzhhrurmmoQ9MNcLfhS-z5gyejXLTIn2VcHXzMZ50Qha-VcoJLjzi5xm
```

Paste this deployment ID into the "Spreadsheet script ID" box on
the spreadsheet toolbar in VHV.  Once the Deployment ID is pasted into the
script ID box, the cloud upload/download buttons will work to copy
data between the VHV and the Google Spreadsheet:

{% include image.html
	file="spreadsheet-buttons.png"
	alt="Spreadsheet toolbar with Script ID added."
	caption="Spreadsheet toolbar with Script ID added."
	max-width="60%"
%}

You can use the above script ID for testing purposes,
which links to this <a target="_blank"
href="http://bit.ly/humdrum-public-spreadsheet">publicly editable
spreadsheet</a>.  But don't use this particular spreadsheet for
actual work, since other people testing spreadsheet interaction can
delete your data on it and/or copy your data on the spreadsheet to
their own VHV editor.
However, you can set up a collaborative editing spreadsheet with
other people by sharing your script/spreadsheet IDs with them to
copy into their VHV spreadsheet toolbar text box.

## Adding spreadsheet URL to script toolbar ##

For easy access to the spreadsheet you can optionally add a link to the
spreadsheet to the toolbar.  To do this, not the URL of the spreadsheet
(not the script), such as:

```
https://docs.google.com/spreadsheets/d/1_E31WEm8_u8dg0zgBTC2SJnKRm1OuJBCl_ameYv64m8/edit#gid=0
```

In this case the spreadsheet ID is `1_E31WEm8_u8dg0zgBTC2SJnKRm1OuJBCl_ameYv64m8`.

Add this spreadsheet ID after the script ID in the text box on the spreadsheet toolbar, separating
the two IDs with a pipe character (`|`):

```
AKfycbxIXX29Z3qsWzhhrurmmoQ9MNcLfhS-z5gyejXLTIn2VcHXzMZ50Qha-VcoJLjzi5xm|1_E31WEm8_u8dg0zgBTC2SJnKRm1OuJBCl_ameYv64m8
```

This will enable an icon on the spreadsheet toolbar that opens up
the linked spreadsheet: 

{% include image.html
	file="spreadsheet-url-icon.png"
	alt="Spreadsheet toolbar with link to spreadsheet added."
	caption="Spreadsheet toolbar with link to spreadsheet added."
	max-width="60%"
%}


The spreadsheet icon will display after you do your first
upload or download from VHV.  Once you have set up the script ID
and sheet ID, VVH will remember it as long as you use the same
browser.

## Interacting with the spreadsheet ##

You are now ready to transfer Humdrum data between VHV and Google Sheets.
Click on the cloud-upload button immediately to the right of the 
script ID box.  This will cause the contents of the VHV editor to be uploaded
to the Google Sheet you created for that script ID:


{% include image.html
	file="google-sheet-upload.png"
	alt="Contents of spreadsheet after upload."
	caption="Contents of Google spreadsheet after pressing the upload button."
%}

After you finish editing the Humdrum file in Google Sheets, click
on the cloud-download button on the VHV spreadsheet toolbar to
transfer the data back into the text editor.  Here is an example
where all parts except the Bass part are deleted from the spreadsheet,
and then the Humdrum data is downloaded data back into VHV:

{% include image.html
	file="spreadsheet-edit.png"
	alt="Spreadsheet editing."
	caption="Deleting all parts except the bass part."
%}

Then clicking on the cloud-download button in the VHV spreadsheet toolbar,
will copy the contents of the spreadsheet back into the VHV text editor:


{% include image.html
	file="spreadsheet-download.png"
	alt="Spreadsheet download."
	caption="Downloading the edited data back into the VHV text editor."
%}


Placing the spreadsheet and VHV side-by-side in separate browser windows
is a good method for working with this feature.  You can make edits in
the spreadsheet, then move to the VHV editor and click on the cloud-download
button to view the changes as often as desired.

{% include image.html
	file="dual-windows.png"
	alt="Spreadsheet and VHV windows side-by-side."
	caption="Spreadsheet and VHV windows side-by-side."
	max-width="100%"
	width="100%"
%}

In the above example configuration, the VHV text editor is hidden with the
<span class="keypress">alt-y</span> keyboard shortcut, since editing the
Humdrum text in both windows is not necessary and frees up display real-estate
for the music notation.


## Cell text escaping ##

When uploading Humdrum data into the spreadsheet, all cells are
formatted to be text cells.  The spreadsheet will still try to
interpret some text cells, such as when an equals sign starts the
text for Humdrum barlines.  A single quote character is added at
the start of barline cells to force the cell's contents to be
treated as text without further interpretation.  This single quote
will be stripped off of the data automatically when downloading
from the Google spreadsheet back into VHV.  Also, tokens starting
with a single quote will have an additional quote added to escape
the initial single quote.

Below is a demonstration of the effect the single quote has on the
display of barlines.  The text `=9||` will be interpreted as a
formula, but this produces a syntax error due to the double-barline
styling, resulting in the text `#ERROR!` being show in the
spreadsheet.  This text will be downloaded into VHV if the barline
token does not have a single quote added at the start of the cell.
In cell A4, the cell text is `'=9||`, which prevents formula
interpretation of the text.

{% include image.html
	file="formula.png"
	alt="Escaping text to prevent formula interpretations."
	caption="Escaping text to prevent formula interpretations."
%}

So if you are entering barlines on the spreadsheet, ensure that you
type a single quote character before the barline.  The problem
mostly only involves text starting with an `=` sign.  Since all
cells on the sheet are set to be text rather than numbers, unescaped
numbers will be treated as text by default.  If you want to do
numeric operations on data in the Humdrum content, you should
reformat them as numbers from the Format &rarr; Number menu.



## Expanded-tab formatting ##

When uploading data to a spreadsheet, it will first be run through the
`tabber` filter to straighten out spines into columns.  When the data
is downloaded back to the text editor, the state of the current data
in the text editor will be matched.  If the text editor contains
data with expanded tabs, the downloaded data will be left expanded. 
If the text editor contains data with compressed tabbing, the downloaded
data will be run through the `tabber -r` filter to remove the alignment
tabs before it is placed in the text editor.


## Freezing rows ##

For orchestral works, freezing the spreadsheet row with instrument names is useful.

{% include image.html
	file="freeze.png"
	alt="Freezing a row."
	caption="Freezing the instrument name row."
%}

After freezing, the header lines will always remain visible.  In the example
below, measure 4 is being displayed, yet the instrument names remain visible.

{% include image.html
	file="freeze2.png"
	alt="Navigating after freezing."
	caption="The text above the freeze line remains visible."
%}

If there are a lot of reference records above the instrument name row, you
can hide the unwanted rows by selecting them by clicking on the first row 
number and shift-click on the last row number to hide.  Then right-click in the
row number area to bring up the following menu and select the hide-rows option:

{% include image.html
	file="freeze-hide.png"
	alt="Hiding rows."
	caption="Select rows then right-click to select the hide-rows option."
%}

After hiding the first three rows, the spreadsheet looks like this:

{% include image.html
	file="freeze-hide2.png"
	alt="After hiding rows."
	caption="After hiding the first three rows."
%}

Notice that there is a little arrow for row 4, which indicates the presence
of the hidden rows.  You do not need to unhide the rows when downloading
the spreadsheet's contents into VHV, since the hidden rows will always
be included in the download.





## IGNORE columns ##


If you place the text `IGNORE` in a cell in the first row of the spreadsheet,
that column will not be exported back into VHV when you download the data.  This
is useful for adding scratch columns for data processing purposes or doing
calculations interleaved within the data.  Here is an example use of the `IGNORE` 
feature:



{% include image.html
	file="ignore.png"
	alt="Adding IGNORE columns."
	caption="Adding IGNORE columns."
%}

When downloading back into VHV, the `IGNORE` columns are ignored:

{% include image.html
	file="ignore2.png"
	alt="IGNORE columns removed."
	caption="IGNORE columns removed when downloading from the spreadsheet."
%}


{% include warning.html
	content="If you upload data from VHV into the spreadsheet, any existing IGNORE columns will be erased.  This may be changed in the future."
%}



## Moving music between subspines ##

A useful function of spreadsheet editing is the ability to move notes
between voices/layers much more quickly than is possible in the VHV text editor.
Here is an example of how to switch the order of two subspines to get the
voices in the desired order for automatic stem assignments.  Starting with
this data where the two subspines are in the wrong order:

{% include image.html
	file="layers1.png"
	alt="Layers in the wrong order."
	caption="Subspines in the wrong order for automatic stem assignments."
%}

Expand the tabs and upload to a spreadsheet:

{% include image.html
	file="layers2.png"
	alt="Spreadsheet with data in the wrong subspines."
	caption="Spreadsheet with data in the wrong subspines."
%}

Then copy a region in the right-hand subspine and paste into an
unused column (column G in this example).  You can optionally
add an "IGNORE" marker at the top of the scratch column so that
you do not need to delete the leftover content when finished 
swapping the subspines:

{% include image.html
	file="layers3.png"
	alt="Copying the right subspine."
	caption="Copying the right subspine in column D to temporary column G."
%}

Then copy the left subspine tokens from column C to D:

{% include image.html
	file="layers4.png"
	alt="Copying the left subspine to right subspine."
	caption="Copying the left subspine in column C to column D."
%}


And finally, copy the new left spine data from column G to C:

{% include image.html
	file="layers5.png"
	alt="Copying the new left subspine from column G to column C."
	caption="Copying the new left subspine from column G to column C."
%}


Downloading the Humdrum score back into VHV shows the voices in their
proper positions:


{% include image.html
	file="layers6.png"
	alt="Downloaded score with updated subspine positions."
	caption="Downloaded score with updated subspine positions."
%}

However, this manual process of switching subspines can be handled
faster and automatically with the [flipper](/filter/flipper) filter
in a single step, using `-a` to flip all subspines in the score:


{% include image.html
	file="layers7.png"
	alt="Flipper tool."
	caption="Flipper tool being used to switch the order of subspines."
%}

## Humdrum menu ##

A custom Humdrum entry is added to the spreadsheet menu by the Humdrum script:


{% include image.html
	file="menu.png"
	alt="Humdrum menu."
	caption="Humdrum menu added by the script."
%}

Each option is describe below.  In the future, more capabilities will be added.

### Fix barlines rows ###

If you add barlines to the spreadsheet, but do not add a single quote 
in front of the equals sign, run this script to add the single quote so
that the barline cells are not interpreted as formulas.


### Colorize data ###

If you add data lines or columns to the Humdrumd data and the colorization
is no longer valid, select this menu item to recolorize the Humdrum data.
This item is also useful to run after copy and pasting Humdrum data onto
the spreadsheet.


### Add above current line... ###

{% include image.html
	file="menu-line.png"
	alt="Line insertion options."
	max-width="50%"
	caption="Line insertion options."
%}

Options that add null-token lines above the current line to fill
in with content, such as layout parameters, a new sonority or interpretations
such as clef changes.

#### Interpretation line ####

Add a empty interpretation above the current row (or top cell in the selection), which
will add a new row with `*` above each non-empty column in the selected row.


#### Local comment line ####

Add an empty local comment line above the current row (`!`).


#### Data line ####

Add an null data line above the current row (`.`).


### Show/hide columns... ###

{% include image.html
	file="menu-column.png"
	alt="Column show/hide options."
	max-width="50%"
	caption="Column show/hide options."
%}

Options to selectivly show or hide data spines.  These options are
useful to select a subset of spines for data entry.



#### Hide non-kern spines ####

Hide add data spines that are not `**kern`.  In other words hide
lyrics, dynamics, text, harmony, etc., and only show the notes.  This is
useful for cases where you want to edit/view notes.

{% include image.html
	file="kern-hide-before.png"
	alt="Before hiding non-kern spines."
	caption="Before hiding non-kern spines."
%}

{% include image.html
	file="kern-hide-after.png"
	alt="Before hiding non-kern spines."
	caption="After hiding non-kern spines."
%}



#### Show only selected spines ####

Select one or more columns to display, hiding other columns.
Any rows can be used for the selection.  If the tabs are expanded, the
selection will include all subspines even if they are not in the selection.



#### Hide selected spines ####

Select one or more columns to hide, showing other columns.
Any rows can be used for the selection.  If the tabs are expanded, the
selection will include all subspines even if they are not in the selection.



#### Show all spines ####

Unhide all columns of data on the spreadsheet.





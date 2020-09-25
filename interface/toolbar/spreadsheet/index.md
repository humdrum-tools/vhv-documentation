---
title: Spreadsheet Toolbar
lang: en
ref: interface-toolbar
author: Craig Stuart Sapp
translator: 
creation_date: 24 Aug 2020
translation_date: 
last_updated: 3 Sep 2020
tags: [all, getting_started]
keywords: interface toolbar
summary: "A Description of the spreadsheet toolbar."
sidebar: main_sidebar
vim: ts=3
permalink: /interface/toolbar/spreadsheet/index.html
---

The spreadsheet toolbar allows for interaction between VHV and Google Sheets.

{% include_relative style-local.html %}

<div class="toolbar" id="toolbar-6">
	<input id="macroid"  type="text" spellcheck="false" placeholder="Spreadsheet script ID">
	<div title="Upload data to spreadsheet" onclick="uploadDataToSpreadsheet()" class='nav-icon fa fa-cloud-upload'></div>
	<div title="Download data from spreadsheet" onclick="downloadDataFromSpreadsheet()" class='nav-icon fa fa-cloud-download'></div>
	<div title="About spreadsheets" onclick="showSpreadsheetHelp()" class='nav-icon fas fa-question-circle'></div>
	<span id="line-break-icon" onclick="gotoNextToolbar(6, event)">
		<div title="Go to next toolbar menu (alt-n)" class='nav-icon fa fa-superpowers'></div>
	</span>
</div>



## Setting up a link to Google Sheets ##

### Step one: create a spreadsheet ###

Create a new spreadsheet in <a target="_blank"
href="https://sheets.google.com">Google Sheets</a>.  You need to
have a Google account to do this step.


{% include image.html
	file="blank-spreadsheet.png"
	alt="Create a blank spreadsheet"
	caption="Create blank spreadsheet."
%}


### Step two: open the script editor ###

Save the spreadsheet with a name of your choosing, such as "Humdrum
interaction" in the following example.  Then go to the menu Tools &rarr; Script editor:

{% include image.html
	file="tools-script-editor.png"
	alt="Open the script editor"
	caption="Open the script editor."
%}

A new tab will open with the script editor in it:


{% include image.html
	file="script-editor.png"
	alt="The script editor"
	caption="The script editor."
%}


### Step three: copy and save interaction script ###

Copy the current Humdrum interaction script from 
<a target="_blank" href="http://bit.ly/humdrum-io-raw">this link</a>
from a
<a target="_blank" href="http://bit.ly/humdrum-io">Github gist</a>.
Then replace the contents of `Code.gs` with the copied script:


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


### Step four: publish the script ###

In order to use the script is has to be "published".  Go to the menu Publish 
&rarr; Deploy as a web app...:


{% include image.html
	file="script-publish.png"
	alt="Publish the script"
	caption="Publish the script."
%}


A subwindow will appear in which you should select "Anyone, even anonymous"
for the section "Who has access to the app:".


{% include image.html
	file="script-deployment-options.png"
	alt="Script deployment options"
	caption="Script deployment options."
	max-width="50%"
%}


{% include warning.html
	content="In the future, less permissive settings may be possible.  In the meantime, do not share the final script ID unless you want other people to use the same spreadsheet."
%}

Then click on the blue "Deploy" button.  The first time you publish the script,
you will be asked for permission to do so:

{% include image.html
	file="script-permissions.png"
	alt="Review script permissions"
	caption="Review script permissions."
	max-width="60%"
%}

Click on the "Review Permissions" button.  Then choose your acocunt from the
window that opens:

{% include image.html
	file="login.png"
	alt="Log into your Google account"
	caption="Log into your Google account."
	max-width="60%"
%}

Then click on the blue "Allow" button that appears in the next window:

{% include image.html
	file="allow.png"
	alt="Allow the script to run"
	caption="Allow the script to run."
	max-width="60%"
%}

A final depolyment subwindow will appear like this one:

{% include image.html
	file="deployment.png"
	alt="Final depolyment window."
	caption="Final depolyment window."
	max-width="60%"
%}

Take note of the link in the "Current wep app URL:" box.  This link 
is necessary to connect VHV to Google Sheets.

{% include warning.html
	content="If you change the script, you must republish the script in order to activate the updated script.  You will probably also have to update the \"Project version\" to a new version."
%}

## Linking VHV to Google Sheets ##

After publishing the script, you now are ready to connect VHV to Google Sheets.

The script deployment URL will be something like this:

https://script.google.com/macros/s/AKfycbwPSnUPffm_A_voZXkYy0sks9sWLr9-ig_m2UOPes9DP1Sod3A/exec

Copy the ID from the middle of the script:

<input style="width:525px" type="text" value="AKfycbwPSnUPffm_A_voZXkYy0sks9sWLr9-ig_m2UOPes9DP1Sod3A">

and paste it into the "Spreadsheet script ID" box on the spreadsheet
toolbar in VHV.  You can use the above script ID for testing purposes
since it links to a publically editable spreadsheet.  But don't use it for actual
work, since other people testing spreadsheet interaction can delete your 
data on the spreadsheet and/or copy your data to their own VHV editor while they
are also testing this feature.

{% include image.html
	file="spreadsheet-id-paste.png"
	alt="Pasting spreadsheet script ID into VHV spreadsheet toolbar."
	caption="Pasting spreadsheet script ID into VHV spreadsheet toolbar."
%}

You are now ready to transfer Humdrum data between VHV and Google Sheets.
Click on the Cloud-upload button immediately to the right of the 
script ID box.  This will cause the contents of the VHV editor to be uploaded
to the Google Sheet that you created for that script ID:


{% include image.html
	file="google-sheet-upload.png"
	alt="Contents of spreadsheet after upload."
	caption="Contents of Google spreadsheet after pressing the upload button."
%}

You can now edit the Humdrum file content in Google Sheets.  Not
that it is advisable to place a single quote in front of every token
in the sheet.  This enforces that the contents is text rather than 
numeric, or in particular equations (which are easily confused with
Humdrum barlines, since both start with an equals sign).  This quote
will be stripped off of the data automatically when downloading from the 
Google spreadsheet back to VHV.

After you finished editing the Humdrum file in Google Sheets, click on the
cloud-download button on the VHV spreadsheet toolbar to transfer the data
back into the text editor.  Here is an example where I deleted all of the parts
except the Bass part on the spreadsheet, and then download the Humdrum data
back into VHV:


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



## Tip: expanded tab formatting ##

If you are editing music that contains spine splits (`*^`)  and merges (`*v`), 
then you should click on the expand-tab icon in the main toolbar to straighten
out the spines into columns:

Starting with single tabs between every token:

{% include image.html
	file="before-expanding.png"
	alt="Before expanding."
	caption="Before expanding tabs."
%}

{% include image.html
	file="after-expanding.png"
	alt="After expanding."
	caption="After expanding tabs."
%}


## Tip: freezing rows ##



## IGNORE columns ##



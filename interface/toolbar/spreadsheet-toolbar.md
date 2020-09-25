

<div class="toolbar" id="toolbar-6">
	<input id="scriptid"  type="text" spellcheck="false" placeholder="Spreadsheet script ID">
	<div title="Upload data to spreadsheet" onclick="uploadDataToSpreadsheet()" class='nav-icon fa fa-cloud-upload'></div>
	<div title="Download data from spreadsheet" onclick="downloadDataFromSpreadsheet()" class='nav-icon fa fa-cloud-download'></div>
	<div title="About spreadsheets" onclick="showSpreadsheetHelp()" class='nav-icon fas fa-question-circle'></div>
	<span id="line-break-icon" onclick="gotoNextToolbar(6, event)">
		<div title="Go to next toolbar menu (alt-n)" class='nav-icon fa fa-superpowers'></div>
	</span>
</div>

<br><br>

The spreadsheet toolbar allows bidirectional communiction between
VHV and Google Sheets.  This is particularly useful for editing
orchesteral scores, since the instrument label line can be frozen
at the top of the sheet while editing within the score.

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

	<span class="summary-icon">Spreadsheet script id.</span>

	See the [documentation page for spreadsheet interaction](spreadsheet) 
	for how to create a script and get its ID to paste in this box to
	connect to a particular spreadsheet.

</td>
</tr>


<tr><td>
<div class="toolbar">
	<div title="Upload editor contents to spreadsheet" class='nav-icon fa fa-cloud-upload'></div>
</div>
</td>
<td>

	<span class="summary-icon">Upload to spreadsheet.</span>

	The contents of the text editor will replace the current contents
	of the linked spreadsheet.

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="Download spreadsheet contents to editor" class='nav-icon fa fa-cloud-download'></div>
</div>
</td>
<td>

	<span class="summary-icon">Download to spreadsheet.</span>

	The contents of the linked spreadsheet will replace the current contents
	of the VHV text editor.

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="About the toolbar" class='nav-icon fa fa-question-circle'></div>
</div>
</td>
<td>

	<span class="summary-icon"><a href="spreadsheet">Spreadsheet toolbar documentation.</a></span>

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

	To return to this toolbar directly, press <span class="keypress">6+alt-n</span>.

</td>
</tr>

</table>


<br><br>
See the [documentation page for spreadsheet interaction](spreadsheet) for 
information about how to set up spreadsheet interaction and use the system.




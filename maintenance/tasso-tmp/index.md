---
search: exclude
title: Tables
author: Craig Stuart Sapp
creation_date: 12 Mar 2017
last_updated: 12 Mar 2017
tags: [all, maintenance]
datatable: true
aton: true
vim: ts=3 ft=javascript
sidebar: dull
keywords: maintenance datatables table
summary: Test browse tables for TMP website
permalink: /maintenance/tasso-tmp/index.html
---

<style>

table.dataTable.display tbody tr.odd > .sorting_1 {
	background-color: #f2eede !important;
}

table.dataTable.display tbody tr.even > .sorting_1 {
	background-color: #f8f4e6 !important;
}

</style>

## Literary Prints ##

<script id="literary-prints-data" type="x-application/aton">
{% include aton/literary-prints.aton %}
</script>


<script>
var aton;
var LIT;


window.addEventListener("DOMContentLoaded", function () {
	aton = new ATON;
	var litprints = document.querySelector("#literary-prints-data").textContent;
	LIT = aton.parse(litprints).PRINT;

	$('#example').DataTable( {
		data: LIT,
		columns: [
            { data: "SPRINTNUM", title: "Solerti print", width: "50px" },
            { data: "PUBYEAR", title: "Year" },
            { data: "PUBLISHER", title: "Publisher" },
            { data: "PUBLOCATION", title: "Location" },
            { data: "PRINTTITLE", title: "Title" }
		]
	});

/*
	var table = $("#example").DataTable();

	// Setup - add a text input to each footer cell
	$('#example tfoot th').each( function () {
        var title = $(this).text();
console.log("TTLE", title);
        $(this).html( '<input type="text" placeholder="Search '+title+'" />' );
    } );
 
	console.log("TABLE", table);
	console.log("TC", table.columns());

 	// Apply the search
    table.columns().every( function () {
        var that = this;
 
        $('input', this.footer()).on('keyup change', function () {
            if (that.search() !== this.value) {
                that.search(this.value).draw();
            }
        } );
    } );

*/

});
</script>

<table id="example" class="display" width="1000px">
</table>



## Settings ##

<script id="settings-data" type="x-application/aton">
{% include aton/settings.aton %}
</script>


<script>
var aton;
var SET;


window.addEventListener("DOMContentLoaded", function () {
	aton = new ATON;
	var settings = document.querySelector("#settings-data").textContent;
	SET = aton.parse(settings).SETTING;

	for (var i=0; i<SET.length; i++) {
		SET[i].SOLERTI = SET[i].SOLERTI.replace(/sm/, "");
	}

	$('#example2').DataTable( {
		data: SET,
		columns: [
            { data: "SOLERTI", title: "Solerti #"},
            { data: "COMPOSER", title: "Composer" },
            { data: "POEMTITLE", title: "Title" },
            { data: "PRINCEPSYEAR", title: "Year" },
            { data: "PRINCEPSLOC", title: "Location" },
		]
	});

/*
	var table = $("#example").DataTable();

	// Setup - add a text input to each footer cell
	$('#example tfoot th').each( function () {
        var title = $(this).text();
console.log("TTLE", title);
        $(this).html( '<input type="text" placeholder="Search '+title+'" />' );
    } );
 
	console.log("TABLE", table);
	console.log("TC", table.columns());

 	// Apply the search
    table.columns().every( function () {
        var that = this;
 
        $('input', this.footer()).on('keyup change', function () {
            if (that.search() !== this.value) {
                that.search(this.value).draw();
            }
        } );
    } );

*/

});
</script>

<table id="example2" class="display" width="1000px">
</table>

<!--

## Rime ##

<script id="rime-data" type="x-application/aton">
{% include aton/rime-verses.aton %}
</script>


<script>
var aton;
var RIME;


window.addEventListener("DOMContentLoaded", function () {
	aton = new ATON;
	var rime = document.querySelector("#rime-data").textContent;
	RIME = aton.parse(rime).RIME;
console.log("RIME", RIME);

	$('#example3').DataTable( {
		data: RIME,
		columns: [
            { data: "SOLERTI", title: "Solerti #"},
            { data: "GENRE", title: "Genre" },
            { data: "TITLE", title: "Title" }
		]
	});

/*
	var table = $("#example").DataTable();

	// Setup - add a text input to each footer cell
	$('#example tfoot th').each( function () {
        var title = $(this).text();
console.log("TTLE", title);
        $(this).html( '<input type="text" placeholder="Search '+title+'" />' );
    } );
 
	console.log("TABLE", table);
	console.log("TC", table.columns());

 	// Apply the search
    table.columns().every( function () {
        var that = this;
 
        $('input', this.footer()).on('keyup change', function () {
            if (that.search() !== this.value) {
                that.search(this.value).draw();
            }
        } );
    } );

*/

});
</script>

<table id="example3" class="display" width="1000px">
</table>

-->


## Rime by Print Source ##

<script id="rime-data" type="x-application/aton">
{% include aton/rime-verses.aton %}
</script>


<script>
var RIME2;


window.addEventListener("DOMContentLoaded", function () {
	var aton = new ATON;
	var rime = document.querySelector("#rime-data").textContent;
	RIME2 = aton.parse(rime).RIME;
	var PRINTRIME = [];
	for (var i=0; i<RIME2.length; i++) {
		var printsrc = RIME2[i].PRINTSRC.split(/[, ]+/);
		for (var j=0; j<printsrc.length; j++) {
			var obj = JSON.parse(JSON.stringify(RIME2[i]));
			obj.PRINTNUM = "_" + printsrc[j] + "_";
			PRINTRIME.push(obj);
		}
	}

console.log("PRINTRIME", PRINTRIME);

	$('#example4').DataTable( {
		data: PRINTRIME,
		columns: [
            { data: "PRINTNUM", title: "Solerti print"},
            { data: "SOLERTI", title: "Solerti rime"},
            { data: "GENRE", title: "Genre" },
            { data: "TITLE", title: "Title" }
		]
	});

/*
	var table = $("#example").DataTable();

	// Setup - add a text input to each footer cell
	$('#example tfoot th').each( function () {
        var title = $(this).text();
console.log("TTLE", title);
        $(this).html( '<input type="text" placeholder="Search '+title+'" />' );
    } );
 
	console.log("TABLE", table);
	console.log("TC", table.columns());

 	// Apply the search
    table.columns().every( function () {
        var that = this;
 
        $('input', this.footer()).on('keyup change', function () {
            if (that.search() !== this.value) {
                that.search(this.value).draw();
            }
        } );
    } );

*/

});
</script>

<table id="example4" class="display" width="1000px">
</table>






---
title: Embedded verovio options list
lang: en es
page_language: en
author: Craig Stuart Sapp
creation_date: 20 Mar 2019
last_updated:
ref: verovio options
tags: [all, options]
sidebar: main_sidebar
verovio: "true"
keywords: embedded verovio options
vim: ts=3
summary: 
permalink: /options/list/index.html
---

Here is a list of verovio options that can be [embedded](/options) in the
Humdrum data.

<div id="list"></div>


<script>

var OPTIONS = {% include_relative verovio-options.json %}["OPTION"];

document.addEventListener("DOMContentLoaded", function() {
	var element = document.querySelector("#list");
	if (!element) {
		return;
	}
	var table = createOptionTable(OPTIONS);
	element.innerHTML = table;
});


//////////////////////////////
//
// createOptionTable --
//

function createOptionTable(options) {
console.log("OPTIONS", options);
	var output = "";
	output += "<table>";

	output += "<tr>";
	output += "<th>option name</th>";
	output += "<th>type</th>";
	output += "<th>VHV default</th>";
	output += "<th>verovio default</th>";
	output += "<th>min</th>";
	output += "<th>max</th>";
	output += "<th>description</th>";
	output += "</tr>";
	var t;
	var name;

	for (var i=0; i<options.length; i++) {
		if ((typeof options[i].CLI_ONLY !== 'undefined') && options[i].CLI_ONLY.match(/true/)) {
			continue;
		}
		if (typeof options[i].NAME === 'undefined') {
			continue;
		}
	
		output += "<tr>";

		output += "<td><span style='white-space:pre;'>";
		output += options[i].NAME;
		output += "</span></td>";
		name = options[i].NAME;

		output += "<td style='text-align:center;'><span style='white-space:pre;'>";
		if (typeof options[i].ARG !== 'undefined') {
			t = options[i].ARG;
			if (t.match(/none/)) {
				t = "bool";
			}
			output += t;
		}
		output += "</span></td>";

		output += "<td style='text-align:center;'>";
		if (name === "noHeader") {
			output += "1";
		} else if (name === "adjustPageHeight") {
			output += "1";
		} else if (name === "barLineWidth") {
			output += "0.12";
		} else if (name === "breaks") {
			output += "auto";
		} else if (name === "leftMarginClef") {
			output += "1.50";
		} else if (name === "inputFormat") {
			output += "auto";
		} else if (name === "font") {
			output += "Leipzig";
		} else if (name === "humType") {
			output += "1";
		} else if (name === "noFooter") {
			output += "1";
		} else if (name === "scale") {
			output += "40";
		} else if (name === "spacingLinear") {
			output += "0.25";
		} else if (name === "spacingNonLinear") {
			output += "0.60";
		} else if (name === "staffLineWidth") {
			output += "0.12";
		}
		output += "</td>";

		output += "<td style='text-align:center;'>";
		if (typeof options[i].DEF !== 'undefined') {
			if (t === "bool") {
				output += "0";
			} else {
				output += options[i].DEF;
			}
		} else if (t === "bool") {
			output += "0";
		}
		output += "</td>";

		output += "<td style='text-align:center;'>";
		if (typeof options[i].MIN !== 'undefined') {
			if (t === "bool") {
				output += "0";
			} else {
				output += options[i].MIN;
			}
		} else if (t === "bool") {
			output += "0";
		}
		output += "</td>";
		
		output += "<td style='text-align:center;'>";
		if (typeof options[i].MAX !== 'undefined') {
			if (t === "bool") {
				output += "1";
			} else {
				output += options[i].MAX;
			}
		} else if (t === "bool") {
			output += "1";
		}
		output += "</td>";
		
		output += "<td>";
		if (typeof options[i].INFO !== 'undefined') {
			output += options[i].INFO;
		}
		output += "</td>";
		
		output += "<tr>";
	}

	return output;
}


</script>



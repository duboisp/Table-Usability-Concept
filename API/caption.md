caption - DOM interface API
=======================

_[The caption element](http://dev.w3.org/html5/spec/the-caption-element.html)_

## Current 

	interface HTMLTableCaptionElement : HTMLElement {};

## Table Usability

	interface HTMLTableCaptionElement : HTMLElement {
				attribute HTMLElement header;
		readonly attribute HTMLCollection descriptions;
	};

### Parameters

* **header**: The table caption
* **descriptions**: Elements that define the table description

### Idea behind

To be able to take off the description and move it inside a resulting container created from a data table.

For example, a dynamicly generated chart in a figure element. The table description is moved in the figcaption element.

## Table Parser - WET 3.0 release

	jQuery.data tblparser  {
		jQuery caption; // equivalent to "header"
		colcaption {
			array dataset;
			jQuery elem;
			array summaryset;
			long type;
			long uid;
		}
		jQuery description;
		jQuery elem;
		groupZero {
			// Reference to the structure attached to the table element
		}
		rowcaption {
			array dataset;
			jQuery elem;
			array summaryset;
			long type;
			long uid;
		}
		long type;
	}

-----
_HTML5 specification refer to the Editor's Draft dated of September 21 2012, $Revision 1.1998 $_

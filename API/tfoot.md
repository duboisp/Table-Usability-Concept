tgoot - DOM interface API
=======================

_[The tfoot element](http://dev.w3.org/html5/spec/the-tfoot-element.html)_

## Current 

	HTMLTableSectionElement, as defined for tbody elements.

## Table Usability

	interface HTMLTableGroupElement : HTMLElement {
		readonly attribute HTMLCollection vectors;
		readonly attribute HTMLCollection headers;
		readonly attribute DOMString scope;
		readonly attribute long level;
	};
	
	HTMLTableGroupElement, defined in the colgroup elements.


## Table Parser - WET 3.0 release

	jQuery.data tblparser  {
		jQuery elem;
		groupZero {
			// Reference to the structure attached to the table element
		};
		array headerlevel;
		long lastHeadingColPos;
		long level;
		array row;
		long type;
		long uid;
	}
	
-----
_HTML5 specification refer to the Editor's Draft dated of September 21 2012, $Revision 1.1998 $_

colgroup - DOM interface API
=======================

_[The colgroup element](http://dev.w3.org/html5/spec/the-colgroup-element.html)_

## Current 

	interface HTMLTableColElement : HTMLElement {
			attribute unsigned long span;
	};

## Table Usability

	interface HTMLTableGroupElement : HTMLElement {
		readonly attribute HTMLCollection vectors;
		readonly attribute HTMLCollection headers;
		readonly attribute DOMString scope;
		readonly attribute long level;
	};
	
	interface HTMLTableColgroupElement : HTMLTableGroupElement {
		readonly attribute long start;
		readonly attribute long end;
	}

## Table Parser - WET 3.0 release

	jQuery.data tblparser  {
		array col;
		jQuery elem;
		long end;
		groupZero {
			// Reference to the structure attached to the table element
		};
		array header;
		long level;
		array parentHeader;
		string parentHeader;
		long start;
		long type;
		long uid;
	}

-----
_HTML5 specification refer to the Editor's Draft dated of September 21 2012, $Revision 1.1998 $_

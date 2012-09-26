td - DOM interface API
=======================

_[The td element](http://dev.w3.org/html5/spec/the-td-element.html)_

## Current 

	interface HTMLTableCellElement : HTMLElement {
		attribute unsigned long colSpan;
		attribute unsigned long rowSpan;
		[PutForwards=value] readonly attribute DOMSettableTokenList headers;
		readonly attribute long cellIndex;
	};

	interface HTMLTableDataCellElement : HTMLTableCellElement {};

## Table Usability

	interface HTMLTableCellElement : HTMLElement {
		readonly attribute HTMLCollection cols;
		readonly attribute HTMLCollection rows;
		readonly attribute long rowIndex;
		readonly attribute long colIndex;
		attribute long height;
		attribute long width;
		readonly attribute DOMString scope;
		readonly attribute DOMString context; 
	};
	
For an descriptive and key Cell

	interface HTMLTableDescCellElement : HTMLTableCellElement {
		attribute HTMLElement describe;
	}



-----
_HTML5 specification refer to the Editor's Draft dated of September 21 2012, $Revision 1.1998 $_

th - DOM interface API
=======================

_[The th element](http://dev.w3.org/html5/spec/the-th-element.html)_

## Current 

	interface HTMLTableCellElement : HTMLElement {
		attribute unsigned long colSpan;
		attribute unsigned long rowSpan;
		[PutForwards=value] readonly attribute DOMSettableTokenList headers;
		readonly attribute long cellIndex;
	};
	
	interface HTMLTableHeaderCellElement : HTMLTableCellElement {
		attribute DOMString scope;
	};

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
	
	interface HTMLTableHeaderCellElement : HTMLTableCellElement {
		attribute HTMLTableCellElement description;
		attribute HTMLTableCellElement key;
	}

_context can be either "col" or "row"_

-----
_HTML5 specification refer to the Editor's Draft dated of September 21 2012, $Revision 1.1998 $_

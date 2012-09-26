thead - DOM interface API
=======================

_[The thead element](http://dev.w3.org/html5/spec/the-thead-element.html)_

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


-----
_HTML5 specification refer to the Editor's Draft dated of September 21 2012, $Revision 1.1998 $_

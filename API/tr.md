tr - DOM interface API
=======================

_[The tr element](http://dev.w3.org/html5/spec/the-tr-element.html)_

## Current 

	interface HTMLTableRowElement : HTMLElement {
		readonly attribute long rowIndex;
		readonly attribute long sectionRowIndex;
		readonly attribute HTMLCollection cells;
		HTMLElement insertCell(optional long index);
		void deleteCell(long index);
	};

## Table Usability
	
	interface HTMLTableVectorElement : HTMLElement {
		readonly attribute HTMLCollection cells;
		readonly attribute HTMLCollection headers;
		readonly attribute HTMLCollection headersGroup;
		readonly attribute long level;
		readonly attribute long index;
		readonly attribute long groupIndex;
		readonly attribute DOMString scope;
	};
	
	HTMLTableVectorElement, defined in the col elements.
	
-----
_HTML5 specification refer to the Editor's Draft dated of September 21 2012, $Revision 1.1998 $_

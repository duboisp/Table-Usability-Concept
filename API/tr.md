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

## Table Parser - WET 3.0 release

	jQuery.data tblparser  {
		array cell;
		array datacell;
		array desccell;
		jQuery elem;
		groupZero {
			// Reference to the structure attached to the table element
		};
		array header;
		array headerset;
		array keycell;
		long lastHeadingColPos;
		long level;
		rowgroup {
			// Reference to the structure attached to the associated tbody, tfoot element 
		}
		long rowpos;
		long type;
		long uid;
	}
	
-----
_HTML5 specification refer to the Editor's Draft dated of September 21 2012, $Revision 1.1998 $_

col - DOM interface API
=======================

_[The col element](http://dev.w3.org/html5/spec/the-col-element.html)_

## Current 

	HTMLTableColElement, same as for colgroup elements. This interface defines one member, span.

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

	interface HTMLTableColElement : HTMLTableVectorElement {
		readonly attribute long start;
		readonly attribute long end;
	}

## Table Parser - WET 3.0 release

	jQuery.data tblparser  {
		array cell;
		jQuery elem;
		long end;
		groupZero {
			// Reference to the structure attached to the table element
		};
		groupstruct {
			// Reference to the structure attached to the associated colgroup element
		};
		array header;
		long start;
		long type;
		long uid;
	}
	
-----
_HTML5 specification refer to the Editor's Draft dated of September 21 2012, $Revision 1.1998 $_

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
	};
	
	interface HTMLTableHeaderCellElement : HTMLTableCellElement {
		readonly attribute DOMString context; 
		attribute HTMLTableCellElement description;
		attribute HTMLTableCellElement key;
	}

_context can be either "col" or "row"_


## Table Parser - WET 3.0 release

Header cell used for a column

	jQuery.data tblparser  {
		colgroup {
			// Reference to the structure attached to the associated colgroup element 
		};
		long colpos;
		array data;
		jQuery elem;
		groupZero {
			// Reference to the structure attached to the table element
		};
		long height;
		long level;
		object parent;
		long rowpos;
		string scope;
		array summary;
		long type;
		long uid;
		long width;
	}

Header cell used for a row
	
	jQuery.data tblparser  {
		col {
			// Reference to the structure attached to the associated col element 
		};
		long colpos;
		array data;
		descCell {
			// Reference to the structure attached to the associated td element 
		}
		jQuery elem;
		groupZero {
			// Reference to the structure attached to the table element
		}
		long height;
		boolean isgroup;
		keycell {
			// Reference to the structure attached to the associated td element 
		}
		long level; // Used for row group cell header
		object parent;
		row {
			// Reference to the structure attached to the associated tr element 
		}
		rowgroup {
			// Reference to the structure attached to the associated tbody, tfoot element 
		}
		long rowlevel;
		array rowlevelheader;
		long rowpos;
		string scope;
		long spanHeight;
		array subheader;
		array summary;
		long type;
		long uid;
		long width;
	}

Layout header cell
	
	jQuery.data tblparser  {
		long colpos;
		array data;
		jQuery elem;
		groupZero {
			// Reference to the structure attached to the table element
		}
		long height;
		object parent;
		long rowpos;
		string scope;
		array summary;
		long type;
		long uid;
		long width;
	}
-----
_HTML5 specification refer to the Editor's Draft dated of September 21 2012, $Revision 1.1998 $_

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

### Idea Behind

The colgroup would be used in the same intention of the row group (thead, tbody, tfoot). 

FYI - The table parser are able to determine 3 kind of colgroup. 
* [Header colgroup](http://wet-boew.github.com/wet-boew/demos/tableparser/colgroupheader-techniques.html) : Same concept of a <code>thead</code> row group but for column
* [Data colgroup](http://wet-boew.github.com/wet-boew/demos/tableparser/datacolgroup-techniques.html): Same concept of a <code>tbody</code> row group but for column
* [Summary colgroup](http://wet-boew.github.com/wet-boew/demos/tableparser/colgroupsummary-techniques.html): Same concept of a <code>tfoot</code> row group but for column

That allow to build a responsive web design for complex tables. In general, summary group (computed data eg. total, sub-total) is smaller than the data (raw) and both could be considerate equivalent. That can allow the possibility to shrink the table size by providing a mechanism to expand the data. I am currently thinking of implementing the responsive web design like a [treegrid](http://www.w3.org/TR/wai-aria/roles#treegrid).

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

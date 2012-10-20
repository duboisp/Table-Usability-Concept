table - DOM interface API
=======================

_[The table element](http://dev.w3.org/html5/spec/the-table-element.html#the-table-element)_

## Current 

	interface HTMLTableElement : HTMLElement {
				attribute HTMLTableCaptionElement? caption;
		HTMLElement createCaption();
		void deleteCaption();
				attribute HTMLTableSectionElement? tHead;
		HTMLElement createTHead();
		void deleteTHead();
				attribute HTMLTableSectionElement? tFoot;
		HTMLElement createTFoot();
		void deleteTFoot();
		readonly attribute HTMLCollection tBodies;
		HTMLElement createTBody();
		readonly attribute HTMLCollection rows;
		HTMLElement insertRow(optional long index);
		void deleteRow(long index);
				attribute DOMString border;
	};

## Table Usability

	interface HTMLTableElement : HTMLElement {
				attribute HTMLTableCaptionElement? caption;

				attribute HTMLTableGroupElement? rowHeaderGroups;
				attribute HTMLTableGroupElement? colHeaderGoups;
				attribute boolean hassum;

		readonly attribute HTMLCollection rowGroups;
		readonly attribute HTMLCollection colGroups;

		readonly attribute HTMLCollection keys;
		readonly attribute HTMLCollection descriptions;
		readonly attribute HTMLCollection layouts;
		readonly attribute HTMLCollection rows;
		readonly attribute HTMLCollection cols;

	};

## Table Parser - WET 3.0 release

	jQuery.data tblparser  {
		array allParserObj;
		array col;
		colcaption {
			array dataset;
			jQuery elem;
			array summaryset;
			long type;
			long uid;
		}
		array colgroup;
		colgrouphead {
			// Reference to the header colgroup
		}
		array colgrouplevel  [
			Level => [
				// Reference to the colgroup at specified level
			]
		];
		array desccell;
		jQuery elem;
		groupheadercell {
			jQuery caption;
			colcaption {
				// Reference
			};
			jQuery description;
			jQuery elem;
			groupZero {
				// Reference to the structure attached to the table element
			};
			rowcaption {
				// Reference
			}
			long type;
		}
		array keycell;
		array lstrowgroup;
		array row;
		rowcaption {
			array dataset;
			jQuery elem;
			array summaryset;
			long type;
			long uid;
		}
		array rowgroup;
		array theadRowStack;
		long uid;
		array virtualColgroup;
	}

-----
_HTML5 specification refer to the Editor's Draft dated of September 21 2012, $Revision 1.1998 $_

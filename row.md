Row Parsing - Table Parsing Algorithm
=======================

## Purpose

This part is the node of the table usability concept. With this algorithm, the column group _(colgroup element)_ is validated agains the data cell. Visual row group that are not supported by the appropriate row group element is also validated.

The begin of this algorithm is the similar as the [algorithm for processing rows defined in the HTML5 specification](http://dev.w3.org/html5/spec/attributes-common-to-td-and-th-elements.html#algorithm-for-processing-rows) but there is additional task done after the initial parsing.

## Term

* **Header row:** A row that his last cell is an header cell, _th element_.
* **Data row:** A row that his last cell is a data cell, _td element_.
* **table width:** Calculated from the number of cell by taking in consideration any rowspan and colspan attribute for a givin row.

## Algorithm

* Get an array where the length is the table width and each items are refering to an cell. This is based on the cell contained in the current table row.
* If the row is processed under the thead algorithm: stack the row and exit
* If the last cell is an header cell
	* Mark the row as an header row
	* If the first cell not equal the last cell
		* If the row header are not defined, and current no data row is found
			* Stack the row in the thead stack
			* exit
		* else 
			* Raise an structural error, the column can only defined into the first rows of the table
			* exit
	* else (this means we have a cell that is colspanned for the full table width)
		* Stack the row in the header cell row group for future processing by the row group setup algorithm
		* exit
* The last cell is an data cell 
* Mark the row as data row
* Flag that the header row group is finished

* td cell used as description for the preceding row header






## Existing Implementation

[row Parser](https://github.com/wet-boew/wet-boew/blob/master/src/js/workers/parser.table.js#L962)

-----
_HTML5 specification refer to the Editor's Draft dated of September 21 2012, $Revision 1.1998 $_

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
* If the row is processed under the [thead algorithm](https://github.com/duboisp/Table-Usability-Concept/blob/master/Algorithm//thead.md): stack the row and exit
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
* If the previous row is a header row and it's contain a group header cell
	* If the first cell equal the last cell
		* Associate this cell as the description of the previous group header cell
		* exit
* if the current group have not being processed: Run the [row group setup algorithm](https://github.com/duboisp/Table-Usability-Concept/blob/master/Algorithm//rowGroupSetup.md) 
* Get the last highest column position of the cell header (called here lastHeadingColPos) _(last th element column position)_
	* If there the colgroup element is used, let the lastHeadingColPos to be the width of the first colgroup if the first colgroup width is the same as the  lastHeadingColPos or the lastHeadingColPos plus "1". 
* If the current row is the first data row, the value of lastHeadingColPos would be used to determine if there is an change about data vs summary row
* If the current row is the second or subsequent data row
	* If the lastHeadingColPos do not equal to the lastHeadingColPos of the preceding data row
		* If the lastHeadingColPos do not exist for a data summary row
			* Let the current lastHeadingColPos to be the patern for a data summary row
			* [Finalise the row group](https://github.com/duboisp/Table-Usability-Concept/blob/master/Algorithm//rowGroupFinalize.md)
			* [Initiate the row group](https://github.com/duboisp/Table-Usability-Concept/blob/master/Algorithm//rowGroupInitialize.md)
			* [Row group setup](https://github.com/duboisp/Table-Usability-Concept/blob/master/Algorithm//rowGroupSetup.md)
		* If a summary partern is know and the current lastHeadingColPos match the lastHeadingColPos for the previous data row
			* [Finalise the row group](https://github.com/duboisp/Table-Usability-Concept/blob/master/Algorithm//rowGroupFinalize.md)
			* [Initiate the row group](https://github.com/duboisp/Table-Usability-Concept/blob/master/Algorithm//rowGroupInitialize.md)
			* Force the [row group setup](https://github.com/duboisp/Table-Usability-Concept/blob/master/Algorithm//rowGroupSetup.md) to be a data row group
			* Raise a warning that this data row group are not identified by a group header cell
		* else
			* Raise an structural error, only two row partern can be defined per data table
* From the column 1 until the lastHeadingColPos
	* If the current cell is a data cell
		* If the cell at column pos minus 1 is an header cell
			* If both cell get a match as per his height
				* Mark the current cell as a description cell
	* If the current cell is an header cell
		* From column position 1 to the current cell column position 
			* If there is a data cell that match his height
				* Let the first cell found to be his associated key cell
				* For subsequent matching cell, Raise an structural error because may be those cell can be data cell.
			* If there is a header cell that his height is higher or equal to the current cell
				* Set the relationships between both header cell. The current header cell would be a children.
* If there is lastHeadingColPos is undefined and there is no colgroup element defined
	* Create one colgroup with column that cover the table width
* Run the [row group header algorithm](https://github.com/duboisp/Table-Usability-Concept/blob/master/Algorithm//processRowGroupHeaders.md) based on the lastHeadingColPos _(This would validate the colgroup structure)_
* From the column lastHeadingColPos more "1" to the last column
	* Navigate along with the corresponding column group for the current cell
		* Let's the data cell type to match the row type (summary or data) with the column group type (summary or data)
		* If the row type is summary and the colgroup type is summary and the current cell cover both group as per width and height
			* If the current cell is an empty cell, mark it as a layout cell
	* If there is column group, assume we have data column group
	* Set the associate any row cell heading that is out of scope of the current cell when the current cell height is larger than 1 row
* Associate each cell from the current row to the appropriate column
* Associate the row and column level to each cell from the current row
	* Set any additional column header associated to the current cell when his width is larger than 1 column


## Existing Implementation

[row Parser](https://github.com/duboisp/Table-Usability-Concept/blob/master/Polyfill/parser.table.js#L962)

-----
_HTML5 specification refer to the Editor's Draft dated of September 21 2012, $Revision 1.1998 $_

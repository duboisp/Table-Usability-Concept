Row Group Setup - Table Parsing Algorithm
=======================

## Purpose

* Mark header cell considerated as header group cell
* Calculate the level of the contained data
* Find out if the row group is a data row group or a summary row group

## Term

**Level:** This represent the hierchical relationships between cell that belong into an other group. Here is about other row group.

## Algorithm

* With the header row array
	* if the cell cover the full table width
		* Mark the cell as group header cell
* If the current row group is the first row group, excluding the header row group
	* Check if the current row group need to be initiated. This is to handle simple table markup without row grouping 
	* Set the default data level at "1" and mark the current row group as a data row group
* Check agains the column group if an header column group exist
	* If exist: Check if the row group can be marked as a summary row group. The header row array should be empty before the execution of this algorithm
	* Otherwise: mark the row group as a data row group
* Check if the current row is a summary group and if the table is not in "hassum" mode
	* Mark the current group as a data group
	* Use the same data level as the preceding row group
	* exit
* Calculate the data level if not set
	The data level is based on the current and previous row group.
	* if the current row group is marked as a data row group
		* if the number of header group cell is equal for both row group: The level is the same as the previous group.
		* if the number of header group cell is lower than the previous row group
			* The current level is calculated based on the level of the previous row group minus the number of header group cell of the current row group
			* Update the relationships of the header group cell than is also represented in the current row group
			* The current level would be the same as the previous row group
		* if the number of header group cell is greater than the previous row group
			* Increase the current row group level by the number of header group cell more "1"
	* if the current row group is marked as a summary row group
		* if the previous row group are a summary row grou
			* Reduce the level by "1"
		* else
			* The level is the same as the previous row group
		* Associate the appropriate header group cell for the level based on the previous row group
	* If there are no previous row group
		* The level is calculated based on the number of header group cell more "1"
* Empty the header row array

At the end of this algorithm, a level greater or equal to zero should be defined for the row group. If the calculated level are under "0", this is an structural error.


## Existing Implementation

[rowgroupSetup](https://github.com/duboisp/Table-Usability-Concept/blob/master/Polyfill/parser.table.js#L826)

-----
_HTML5 specification refer to the Editor's Draft dated of September 21 2012, $Revision 1.1998 $_

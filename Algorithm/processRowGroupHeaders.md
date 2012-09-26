Process Row Group Headers - Table Parsing Algorithm
=======================

## Purpose

Define the row group header and validate the colgroup markup agains the cell headers defined in the header row group.

## Algorithm

* If the there is an lastHeadingColPos, the first colgroup should match.
	* if false: Raise an structural error and reset the colgroup structure 
* Associate any descriptive cell with the cell header above.
The following algorithm are not considerating any row included in the row group header that are providing a description for cell headers.
* If the table markup do not have any colgroup defined
	This can result to one colgroup or two colgroup only
	* Create the new colgroup and col structure by taking in consideration the lastHeadingColPos
* else the table markup have colgroup element defined
	* For each colgroup element
		* If a summary group at level 0 already exist
			* Raise an structural error
			* return
		* If is the first colgroup and lastHeadingColPos is greater than 0
			* Mark the current colgroup as the header group
			* go to the next colgroup
		* Get the colgroup data level
			The colgroup level is calculated by the row position of the larger (width) cell header that cover the colgroup but closer to the colgroup width. 
		* If the colgroup data level is undefined, let the colgroup data level to be 1
		* If the cell bellow the colgroup data level found is larger than the current colgroup: raise an structural error
		* Create virtual colgroup for the group cell header that is on lower data level of the current colgroup data level
			This identify the group header cell for the column grouping
		* Set the relationships between the group header cell for the current group and the virtual column group
		* If the number of virtual column group is lower than the current colgroup level
			* Let the current colgroup to be a data column group
		* If the preceding colgroup are in the same data level or the current colgroup level is higher to the preceding colgroup
			* Let the current colgroup to be a summary column group
		* If the current colgroup level is 1 and it's exist other colgroup at level 1
			* Let the current colgroup to be a summary column group
			* If there exist summary colgroup at level 1
				* Let current colgroup to be at level 0
		* For each col defined in the current colgroup
			* Assign the type and the level defined by the current colgroup
			* Create the relationships between the column header cell and the columns that a match can be found

## Existing Implementation

[row Parser](https://github.com/wet-boew/wet-boew/blob/master/src/js/workers/parser.table.js#L261)

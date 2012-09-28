Algorithm - Table-Usability-Concept
=======================


* While the current element is not one of the following elements, advance the current element to the next child of the table:
	* _caption_
	* _colgroup_
	* _thead_
	* _tbody_
	* _tfoot_
	* _tr_
* If the _current element_ is a _caption_, run the [Long Description Extract algorithm](https://github.com/duboisp/Table-Usability-Concept/blob/master/Algorithm//LongDescriptionExtract.md)
* While the current element is not one of the following elements, advance the current element to the next child of the table:
	* _colgroup_
	* _thead_
	* _tbody_
	* _tfoot_
	* _tr_
* If the _current element_ is a _colgroup_, run the [colgroup-col algorithm](https://github.com/duboisp/Table-Usability-Concept/blob/master/Algorithm//colgroup-col.md)
* _Rows:_ While the current element is not one of the following elements, advance the current element to the next child of the table:
	* _thead_
	* _tbody_
	* _tfoot_
	* _tr_
* If the _current element_ is a _thead_, run the [thead algorithm](https://github.com/duboisp/Table-Usability-Concept/blob/master/Algorithm//thead.md)
* While the current element is not one of the following elements, advance the current element to the next child of the table:
	* _tbody_
	* _tfoot_
	* _tr_
* If the _current element_ is a _tbody_ or a _tfoot_, run the [tbody algorithm](https://github.com/duboisp/Table-Usability-Concept/blob/master/Algorithm//tbody.md)
* If the current element is a tr, then run the [algorithm for processing rows](https://github.com/duboisp/Table-Usability-Concept/blob/master/Algorithm//row.md), advance the current element to the next child of the table, and return to the step labeled rows.
* If there exists a row or column in the table containing only slots that do not have a cell anchored to them, then this is a table model error.
* Return the table.

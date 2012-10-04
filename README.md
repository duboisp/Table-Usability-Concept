Table-Usability-Concept
=======================

The Table Usability define a concept on how to create the relationship between the informative elements versus the tables structure elements. That is accomplished with guidance of the [Table Processing model](http://dev.w3.org/html5/spec/attributes-common-to-td-and-th-elements.html#processing-model-0) defined in the HTML 5 specification and the WCAG 2.0 Technique [G57: Ordering the content in a meaningful sequence](http://www.w3.org/TR/2010/NOTE-WCAG20-TECHS-20101014/G57). The Table Usability Concept is supported by a Javascript Parser build with the jQuery framework and integrated in the [Web Experience Toolkit Project](https://github.com/wet-boew/wet-boew).

There is an existing implementation variant of this Table Usability Concept. You will find the documentation to the attention of any web editor on the [Web Experience Toolkit (WET) - HTML Tables and WET Table Parser](http://wet-boew.github.com/wet-boew/demos/tableparser/index-eng.html) working examples. 

The [HTML Table Validator](http://wet-boew.github.com/wet-boew/demos/tableparser/validator-htmltable.html) show how this table usability concept are interpretating the relationships between cells and the markup used.

Javascript Table Parser source code: [Original location in the WET Toolbox](https://github.com/wet-boew/wet-boew/blob/master/src/js/dependencies/parserTable.js), [Copy in this repository](https://github.com/duboisp/Table-Usability-Concept/blob/master/Polyfill/parser.table.js)

[whatwg - Proposal: new Table Parser Algorithm - new Table API - removal of the headers attribute - removal of the scope attribute](http://lists.whatwg.org/htdig.cgi/whatwg-whatwg.org/2012-September/037475.html)

##Element Type

* **Informative:** The informative element is related to the visual look of the table. In the HTML the table informative element are: _caption, th, td_

* **Structural:** A structural element is used to classify and give a particular sementic to the informative element and their styling would affect the informative element associated to them. In the HTML the table structural element are: _table, colgroup, col, thead, tbody, tfoot, tr_.


##Element Classification

The Informative and Structural element are classified in forth category

* **Matrix:** The matrix is the global container for a givin table. The matrix have a reference to all the group, all the vector and all the cell. The _table_ HTML element is used to represent the matrix.

* **Group:** A group is a data-set or a header-set inside a table. A group is normally represented by a cell header (th). The _colgroup_, _thead_, _tbody_, _tfoot_ is used to represent each group. Here, the grouping concept is related but not directly associated to the visual representation of the data inside the table. Special note regarding the attribute _scope_: With this concept of element grouping, I recommend to do not set the scope attribute because a summary row group may don't have a representive header and this create inconsistancy in the table structure.

* **Vector:** A vector is the linear representation of the table as per his column and row. The _col_ and _row_ is used to represent a vector.

* **Cell:** A cell is a visual element in a table. The _caption_, _th_ and _td_ is used to represent a cell.


##Element Category

The category is use to give a particular sementic to a classified element.

* **Header:** Basicly used to represent a header cell (th) and a header row group (thead), this concept is applied to the Group, Vector and Cell classification.

* **Data:** Basicly used to represent a data cell (td), this concept is applied to the Group, Vector and Cell

* **Summary:** Always preceded by a &quot;Data&quot;, the summary category is determined on how the group and the cell is defined in a table. The _tfoot_ element belong in the summary category.

* **Key:** Similar to a primary key in a relational database, the key cell can only be defined for a row (Vector). The header cell associated is alway next to the key cell. Generally the key is not to intended to provide actual data but to provide a faster access to the data or to give a unique name for a cell header as reference. It's important that the key cell have the same width and height of his assoicated cell header.

* **Description:** Used to provide additional information for a cell header. The description are not part of the actual tabular data. The description help to understand the cell header and/or provide additional information about the Vector. For a row (Vector), the cell description is next to the cell header for witch is providing a description. For a column (Vector), the cell description is directly bellow the cell header in the next row. It's important that the cell description have the same width and height of his assoicated cell header.

* **Layout:** Only applicable to a cell, a layout cell don't provide any information. His location can only be at the intersection of two header group or at the insection of two summary group. His width and height need to correspond to the group intersection. Also to be considerated as a layout cell, the element _th, td_ identified at the intersection need to be an empty tag.


##Combinaison of Element Classification with the Element Category

* **Header Group:** Represent a set of heading. In a row perpective this are represented by the _thead_ element. In a column perpective this are represented by the first _colgroup_ element. The key and the description is defined in the header group.

* **Data Group:** Represent a data set. In a row perpective this are represented by the _tbody_ element. In a column perpective this are represented by the first _colgroup_ element if no column header group, Or by the second _colgroup_ if a column header group exist. A table always have at least one data group for the column and one data group for the row. A Data Group can be represented by a group header cell.

* **Summary Group:** Often smaller than his associated data group, the summary group include all the vector that show information like sub-total, total. The summary group share with his associated data group the same group header cell. However, it's possible, for a summary to do not share a group header cell with a data group. In this particular case the summary is set at the level 0 and no other group is allowed after.

* **Header Vector:** A row or a column that is last cell is a header cell.

* **Data Vector:** A row or a column that is last cell is a data cell. The only exception is a vector contained inside a header group, that define the concept of the key and description cell.

* **Summary Vector:** Similar to a data vector but defined inside a summary group.

* **Key Vector:** Only defined inside a column header group, the key vector is simply the column of key cell.

* **Description Vector:** Only defined inside a header group, the description vector represent the column or/and the row that is used to describe a cell header.

* **Header Cell:** Represent a group or a vector. The table _caption_ and _th_ element is considerated to be header cell.

* **Group Header Cell:** Derivated from a header cell, a group header cell represent a data group or a combinaison of a data group with a summary group. The table _caption_ is considerated to be a group header cell.

* **Data Cell:** Defined inside a data group and represented by the _td_ element.

* **Summary Cell:** Defined inside a summary group and represented by the _td_ element.

* **Key Cell:** His relation is defined by the column header group. Similar to a primary key in a relational database, the key cell can only be defined for a row (Vector). The header cell associated is alway next to the key cell. Generally the key is not to intended to provide actual data but to provide a faster access to the data or to give a unique name for a cell header as reference. It's important that the key cell have the same width and height of his assoicated cell header.

* **Description Cell:** His relation is defined by the header group. Used to provide additional information for a cell header. The description category is not a data but help to understand the cell header and/or provide additional information about the Vector. For a row (Vector), the cell description is next to the cell header that his providing a description. For a column (Vector), the cell description is directly bellow the cell header in the next row. It's important that the cell description have the same width and height of his assoicated cell header.

* **Layout Cell:** A layout cell don't provide any information. A layout cell need to be empty tag without any spaces inside. His location can only be at the intersection of the header group or at the insection of summary group. His width and height need to correspond to the group intersection. The layout cell can be a _th_ or a _td_ element.

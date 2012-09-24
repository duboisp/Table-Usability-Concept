colgroup / col - Table Parsing Algorithm
=======================

* [The colgroup Element](http://dev.w3.org/html5/spec/the-colgroup-element.html)
* [The col Element](http://dev.w3.org/html5/spec/the-col-element.html)


## Purpose

Initiate the data structure, by default any colgroup is considerated as a data colgroup.

**Note:** 

If the table do not have any colgroup/col element defined, they would be created just before the first the data row processing.

The header colgroup and summary colgroup relationships would be defined just before the first the data row processing. It is possible that the colgroup structure processed here do not match the tabular data structure. In that case, this structure would be ignored and a markup error would be reported on validation. 

## Algorithm

* Initiate an HTMLTableGroupElement interface for the current colgroup.
* Set the appropriate colgroup starting position, based on the previous parsed colgroup element. _(used for internal reference)_
* For each col element
** Initiate an HTMLTableVectorElement
** Set the appropriate colgroup starting position, based on the previous parsed colgroup element and on the previous parsed col element. _(used for internal reference)_
** Set the appropriate column width if application with his span attribute.
** Add the HTMLTableVectorElement in the HTMLTableGroupElement
* No col element found
** Calculate the width of the colgroup with his span attribute.
** Create an HTMLTableVectorElement for each column that his colgroup are convering.
** Set a width of one for the column
** Add the HTMLTableVectorElement in the HTMLTableGroupElement
* Stack the HTMLTableDataGroup. _(The colgroup structure would be validated later)_

## Existing Implementation

[Colgroup Parser](https://github.com/wet-boew/wet-boew/blob/master/src/js/workers/parser.table.js#L178)

-----
_HTML5 specification refer to the Editor's Draft dated of September 21 2012, $Revision 1.1998 $_

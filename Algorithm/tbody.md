tbody - Table Parsing Algorithm
=======================

* [The tbody Element](http://dev.w3.org/html5/spec/the-tbody-element.html)

## Algorithm

* Run the [algorithm to initiate an row group](https://github.com/duboisp/Table-Usability-Concept/blob/master/Algorithm/rowGroupInitialize.md).
* [Digest each row](https://github.com/duboisp/Table-Usability-Concept/blob/master/Algorithm//row.md)
* Run the algorithm for [Finalizing a row group](https://github.com/duboisp/Table-Usability-Concept/blob/master/Algorithm//rowGroupFinalize.md)
* Discard any cell that is spanned outside this row group

## Existing Implementation

[tbody Parser](https://github.com/duboisp/Table-Usability-Concept/blob/master/Polyfill/parser.table.js#L1709)

-----
_HTML5 specification refer to the Editor's Draft dated of September 21 2012, $Revision 1.1998 $_

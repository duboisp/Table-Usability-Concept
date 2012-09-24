tbody - Table Parsing Algorithm
=======================

* [The tbody Element](http://dev.w3.org/html5/spec/the-tbody-element.html)

## Algorithm

* Run the algorithm to initiate an row group.
* Digest each row 
* Run the algorithm for closing an row group
* Discard any cell that is spanned outside this row group

## Existing Implementation

[tbody Parser](https://github.com/wet-boew/wet-boew/blob/master/src/js/workers/parser.table.js#L1709)

-----
_HTML5 specification refer to the Editor's Draft dated of September 21 2012, $Revision 1.1998 $_

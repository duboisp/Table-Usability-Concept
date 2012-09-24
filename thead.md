thead - Table Parsing Algorithm
=======================

* [The thead Element](http://dev.w3.org/html5/spec/the-thead-element.html)

## Algorithm

* No row should be processed at this point
* Initiate an HTMLTableHeaderGroupElement interface.
* Digest each row 
* Stack the digested row _(used later)_

## Existing Implementation

[thead Parser](https://github.com/wet-boew/wet-boew/blob/master/src/js/workers/parser.table.js#L1685)

-----
_HTML5 specification refer to the Editor's Draft dated of September 21 2012, $Revision 1.1998 $_

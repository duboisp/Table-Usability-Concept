Long Description Extract - Table Parsing Algorithm
=======================

In the [HTML5 specification regarding the caption element](http://dev.w3.org/html5/spec/the-caption-element.html#the-caption-element) there is a technique on how to provide a long description for table by having it included in the caption element. 

For now, only the caption element run the following algorithm

## Term Definition

* **title** : _HTMLElement_ Use to represent the text that an description is added to. Similar concept as the summary element.
* **description**: _HTMLCollection_ Represent all the element that would describe the title. Eg, the content of the details element excluding the summary element

## Algorithm

* The first text node found is considerated as the title.
* If that text node is wrapped inside a node element, the parent node element would be considerated as the title.
** ? _If the text node are not wrapped, do an auto wrapping with a strong element should be done._
* Other node that is next to the caption would be considerated as the description of the caption element.


## Existing Implementation

[Caption Parser](https://github.com/wet-boew/wet-boew/blob/master/src/js/workers/parser.table.js#L115)

-----
_HTML5 specification refer to the Editor's Draft dated of September 21 2012, $Revision 1.1998 $_

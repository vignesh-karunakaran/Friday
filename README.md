# Friday

intercooler clone. 

# Learning

Proxy, Symbols, Structural sharing, Copy-on-write mechanism.

# Flow



Init

  Intit function used to initialize the javascript function of the intercooler.

  body tag node is queried and passed to processnode function to get all sub-nodes of the body tag.

  

processNodes

  the function iterates nodes till that length is 1. uses recurse function to get a node's length is 1.

  if the node length is less than then node element passed to belows  functions

      processMacros(elt);

      processEnhancement(elt);

      processSources(elt);

      processPolling(elt);

      processEventSources(elt);

      processTriggerOn(elt);

      processRemoveAfter(elt);

      processAddClasses(elt);

      processRemoveClasses(elt);

      

processMacros

  parameter - elt 

  elt - element

  function calls elemet.closet function to ignores nodes when a node or parent node or grandparent nodes have ic-ignore macro.

  function iterate macros and check that macro matches with a node or all child nodes of the passed node.

  if the node has macro then processMacro function called with parameters of macro name and node.

  

processMacro

  parameter - macro, elt

  macro - macro name of the elemet 

  elt - element

  functions match macros of a node with the default configuration.

  the function sets the default values to the node for future use.

  for example, if the macro name is ic-post-to below properties will be set for future use.

  

   if (macroIs(macro, 'ic-post-to')) {

      setIfAbsent(elt, 'ic-src', getICAttribute(elt, 'ic-post-to'));

      setIfAbsent(elt, 'ic-verb', 'POST');

      setIfAbsent(elt, 'ic-trigger-on', 'default');

      setIfAbsent(elt, 'ic-deps', 'ignore');

    }



macroIs

  parametrs - macro, constant

  macro - macro name

  constatnt - node's macro name

  Returns boolean value if gives macro is eqals to const value.



setIfAbsent

  Parameters -  elt, attr, value

  elt - elemet 

  attr - attribute name

  value - attribute value

  function checks the element contaisn attribute or not.

  if the element doesn't have the attribute then attributes will be set the value.

  

setICAttribute

    parameter - element, attributeName

    function returns attribute based on attribute name.

   

fixICAttributeName

  parameter -s 

  s is name of the attribute.

  the function returns the attribute name based USE_DATA variables 

  if USE_DATA value is true then data- string prefix added to the attribute name.

 

 USE_DATA value is true if $('meta[name="intercoolerjs:use-data-prefix"]').attr("content") == "true"; statified.

 
--------------


Process Enhancement:


starts with if conditions with non ic-ignore :


and has ic-enhance attribute in it


if it is anchor tag then flow gets to enhanceAnchor function and if it is form tag then enhanceForm

[<audio src=x onerror=alert`1`>](http://vv.com)

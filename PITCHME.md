#HSLIDE
## DOM
### Document Object Model
(C) Pedro Miguel Moreira 2016

#HSLIDE
## The Document Object Model
* programming interface for HTML, XML, SVG
* document as a tree
* nodes and objects 

#HSLIDE
## sample HTML document
### html code
```html
<!doctype html>
<html>
  <head>
    <title>My home page</title>
  </head>
  <body>
    <h1>My home page</h1>
    <p>Hello, I am Marijn and this is my home page.</p>
    <p>I also wrote a book! Read it
      <a href="http://eloquentjavascript.net">here</a>.</p>
  </body>
</html>
```
#HSLIDE
## sample HTML document
#### layout structure
<img src="html-boxes.svg.png" alt="Drawing" style="width: 400px;"/>

#HSLIDE
## sample HTML document
#### tree
<img src="html-tree.svg.png" alt="Drawing" style="width: 400px;"/>

#HSLIDE
## sample HTML document
#### dom navigation
<img src="html-links.svg.png" alt="Drawing" style="width: 400px;"/>

#HSLIDE
#### dom navigation, children

Node.children returns a live HTMLCollection of child elements.

Node.childNodes returns a live NodeList of child nodes (inluding text nodes and comments)

```javascript
var elements = element.children; 
var nodes = element.childNodes; 
```

#HSLIDE
#### dom navigation, children

Node.firstChild and Node.lastChild return the first/last child of a given node (or null, if none)

```javascript
var childNode = node.firstChild;
var childNode = node.lastChild;
```

#HSLIDE
#### dom navigation, parents

Node.parentNode returns the parent node of a given Node (it can be a Node, a Document or a DocumentFragment). Returns null if no parent is set.

Node.parentElement returns the parent Element of a given Node (always a DOM Element or null).

```javascript
parentNode = node.parentNode;
parentElement = node.parentElement;
```

#HSLIDE
#### dom navigation, brothers

// nodes can be Text

```javascript
nextNode = node.nextSibling;
prevNode = node.previousSibling;

var nextElement = element.nextElementSibling; 
var prevElement = element.previousElementSibling; 
```

#HSLIDE
#### locating elements

**Locating by id**

returns an `Element`

```
// returns an element
var e = document.getElementById(id);
```
#HSLIDE
#### locating elements

**Locating by Tag Name**

returns a **live** `HTMLCollection`

```
var nl = document.getElementsByTagName(tagName);
var nl = <element>.getElementsByTagName(tagName);
```

#HSLIDE
#### locating elements

**Locating by Class Name**

returns a **live** ```HTMLCollection```

```
var nl = document.getElementsByClassName(classNames);
var nl = <element>.getElementsByClassName(classNames);
```

#HSLIDE
#### selecting nodes

**selecting by query selector**

retuns the first Element that matches

```
var e = document.querySelector(cssQuery);
// also available at the Element interface
var e = <element>.querySelector(cssQuery);
```

retuns a **non-live** NodeList that matches

```
// returns a nl NodeList that matches
var nl = document.querySelectorAll(cssQuery);
// also available at the Element interface
var nl = <element>.querySelector(cssQuery);

```

#HSLIDE
#### creating nodes

In an HTML document, the Document.createElement() method creates the HTML element specified by tagName.
Document.createTextNode() creates a new Text node.

```
var e = document.createElement(tagName[, options]);
var new = document.createTextNode(text); 
```

#HSLIDE
#### set/get HTML content

The Element.innerHTML property sets or gets the HTML syntax describing the element's descendants.

```
// get
var content = element.innerHTML;
// set
element.innerHTML = content;
```

#HSLIDE
#### insert HTML content

Element.insertAdjacentHTML() parses the specified text as HTML and inserts the resulting nodes into a specified position.

```
element.insertAdjacentHTML(position, text);
```
position can take the following values:
 
 * `'beforebegin'` : just before the element 
 * `'afterbegin'` : before first child
 * `'beforeend'` : after last child
 * `'afterend'` : after the element

#HSLIDE
#### replacing nodes

The Node.replaceChild() method replaces one child node of the specified node with another.

```
var old = parentNode.replaceChild(new, old);
```

#HSLIDE
#### inserting nodes

The Node.appendChild() method adds a node to the end of the list of children of a specified parent node. If the node is already parented then it is reparented.

The Node.insertBefore() method inserts the specified node before the reference node as a child of the current node.

```
var n = element.appendChild(n); 
var iNode = parentNode.insertBefore(new, reference);
```
#HSLIDE
#### cloning nodes

The Node.cloneNode() method returns a duplicate of the node on which this method was called.

deep is a boolean flag. `deee=true` if the node should be deep cloned , i.e., with its children, or `deep=false` if only the node is cloned.

```
var clonedNode = node.cloneNode([deep]);
```

#HSLIDE
#### removing nodes

The Node.removeChild() method removes a child node from the DOM. Returns the removed node.

```
// to keep a reference (to later reuse)
var removed = node.removeChild(child);
// to free it from memory ASAP
element.removeChild(child);
```

#HSLIDE
#### get / set classes and ids

className gets and sets the value of the class attribute of the specified element (a space-separeted list of classes).

id gets and sets the value of the id attribute of the specified element.

```javascript
var cName = element.className; // Get the classes
element.className = cName; // Set the classes

var idName = elt.id; // Get the id
element.id = idName; // Set the id

```

#HSLIDE
#### get / set arbitrary attributes

getAttribute() returns the value of a specified attribute on the element.

setAttribute() sets the value of a specified attribute on the element

```javascript
element.setAttribute(attName, attValue);
var attValue = element.getAttribute(attNamne);
```

**hint :** use 'data-' prefix for custom attributes to avoid conflicts.


#HSLIDE
#### styles, set
```
// Multiple style properties via style
element.style.cssText = "color: blue"; 

//Multiple style properties via attribute
element.setAttribute("style", "color: blue");

// Direct property assignment
elt.style.color = "blue";
```

#HSLIDE
#### styles, get
```
var style = window.getComputedStyle(element);
```

#HSLIDE
#### Event
The Event represents any event which takes place in the DOM

* user-generated
 * mouse or keyboard events
* generated by APIs
 * animation has finished running
 * a video has been paused

#HSLIDE
#### target
The target represents the object where the event originated
#### currentTarget
The currentTarget represents the object where the event handler was attached (may be not the same as the target, as events bubble through the DOM).

#HSLIDE
#### Event, adding listeners
```
target.addEventListener(type, listener, [, options]);
target.addEventListener(type, listener, [, useCapture]);
```

type : event type
 
 * 'click', 'mouseover', 'load', ...
 
#HSLIDE
#### Event, adding listeners

listener : a callback function or a EventListener object


```
div = document.getElementById('div001');
p.addEventListener('click', function (e) {
  console.log(e); // function logic
  }
p.addEventListener('click', sayHi);
function sayHi(event) {
  // function logic
  console.log(e);
}
 
```

#HSLIDE
#### Event, adding listeners

**Benefits usin addEventListener**

* more than a single handler
* finer-grained control of the phase when the listener gets activated (capturing vs. bubbling)
* It works on any DOM element, not just HTML elements.

#HSLIDE
#### Event, adding listeners

**the 'old' way **

// 1. Pass a function reference (just the name without, ()'s)
el.onclick = modifyText;

// 2. Using a function expression
element.onclick = function() {
  // ... function logic ...
};


#HSLIDE
#### Event, mouse Events

 * click
 * dblclick
 * mouseover
 * mouseenter
 * mouseleave
 * mouseout
 * mousemove
 * mouseup
 * mousedown
 * wheel
 * select

#HSLIDE
#### Event, Drag & Drop

 * dragstart
 * drag
 * dragend
 * dragenter
 * dragover
 * dragleave
 * drop

#HSLIDE
#### Event, key

 * keydown
 * keyup
 * keypress



#HSLIDE
#### Event, key events

```
<p>This page turns violet when you hold the V key.</p>
<script>
  addEventListener("keydown", function(event) {
    if (event.keyCode == 86)
      document.body.style.background = "violet";
  });
  addEventListener("keyup", function(event) {
    if (event.keyCode == 86)
      document.body.style.background = "";
  });
</script>

```

#HSLIDE
#### Event, mouse Events

```
<style>
  body {
    height: 200px;
    background: beige;
  }
  .dot {
    height: 8px; width: 8px;
    border-radius: 4px; /* rounds corners */
    background: blue;
    position: absolute;
  }
</style>
<script>
  addEventListener("click", function(event) {
    var dot = document.createElement("div");
    dot.className = "dot";
    dot.style.left = (event.pageX - 4) + "px";
    dot.style.top = (event.pageY - 4) + "px";
    document.body.appendChild(dot);
  });
</script>

```

#HSLIDE
#### Event, cancelling default behaviour

```
<a href="https://developer.mozilla.org/">MDN</a>
<script>
  var link = document.querySelector("a");
  link.addEventListener("click", function(event) {
    console.log("Nope.");
    event.preventDefault();
  });
</script>
```

#HSLIDE
#### disclaimer
part of these slides were based on several sources of information, namely:

* Eloquent JavaScript by Marijn Haverbeke
* MDN by Mozilla Contributors.






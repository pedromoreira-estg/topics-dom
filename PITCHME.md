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
#### dom navigation, parents

Node.parentNode returns the parent node of a given Node (it can be a Node, a Document or a DocumentFragment). Returns null if no parent is set.

Node.parentElement returns the parent Element of a given Node (always a DOM Element or null).

```javascript
parentNode = node.parentNode;
parentElement = node.parentElement;
```

#HSLIDE
#### locating elements

**Locating by id**

returns an ```Element```

```
// returns an element
var e = document.getElementById(id);
```

**Locating by Tag Name**

returns a **live** ```HTMLCollection```

```
var nl = document.getElementsByTagName(tagName);
var nl = <element>.getElementsByTagName(tagName);
```

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
#### layout


#HSLIDE
#### disclaimer
part of these slides were based on several sources of information, namely:

* Eloquent JavaScript by Marijn Haverbeke
* MDN by Mozilla Contributors.






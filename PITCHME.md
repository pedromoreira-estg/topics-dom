#HSLIDE
## DOM
### Document Object Model

#HSLIDE
#### disclaimer
part of these slides were based on several sources of information, namely:

* Eloquent JavaScript by Marijn Haverbeke
* MDN by Mozilla Contributors.



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
#### locating elements

##### Locating by id:

```
// returns an element
e = document.getElementById(id);
```

##### Locating by Tag Name:

```
// returns a node list
nl = document.getElementsByTagName(tagName);
nl = <element>.getElementsByTagName(tagName);
```

##### Locating by Class Name

```
// returns a node list
nl = document.getElementsByClassName(className);
nl = <element>.getElementsByClassName(className);
```

#HSLIDE
#### selecting nodes

##### selecting by query selector:

```
// retuns the first Element e that match
e = document.querySelector(cssQuery);
// also available at the Element interface
e = <element>.querySelector(cssQuery);

// returns a nl NodeList that match
nl = document.querySelectorAll(cssQuery);
// also available at the Element interface
nl = <element>.querySelector(cssQuery);

```



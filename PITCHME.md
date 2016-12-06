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
### layout structure
<img src="html-boxes.svg.png" alt="Drawing" style="width: 400px;"/>

#HSLIDE
## sample HTML document
### tree
![](html-tree.svg.png)


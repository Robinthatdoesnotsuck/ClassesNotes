# Getting some style

<img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fi.pinimg.com%2F736x%2F6e%2F3a%2F71%2F6e3a71eac5c3f7376d9938bada623850.jpg&f=1&nofb=1&ipt=1081b46180aa62a65dde751941c20fc40aa98caf0d96ac94e4889309069d2d5b" alt="placeholder" width="50%" height="50%">

CSS stands for Cascading Style Sheets:

- It let developers to add some needed style and color to the web
- It is a simple yet super powerful and complex tool
- The most complex topic in web page design is CSS so buckle up

## Basic CSS structure

Css needs something we call selector:

- A selector is the element you want to stlye
- Then we need a declaration with a property and the value we want to change from that property and it goes something like this

```css
body {
        background: plum;
        color: black;
    }
```

In this case we want to modify the body element and we want the background color to be plum color and that stand alone property called color modifies the text color of the element and we change that to black.

But CSS not only let's us select elements by type of element it can modify elements by class, ID and even handle inheritance in some weird css way and not only that it lets us group the styling so that we don't have to repeat code.

In the [repository of presentations for the class](https://github.com/Robinthatdoesnotsuck/ClassPresentations) under the second week branch you can observe different style selector for css in action.

## Selectors

Selectors are the way we specify what elements we want to style and they come in different in different flavors, mostly regarding the scope of the styling we want to apply

### Basic selectors

- By ID:
  - We can select them by refering to an ID like this
  
  ```css
  #some_id {
    font-family: Consolas,monaco,monospace;
  }
  ```

- By Class
  - We make the reference to a class with

  ```css
  .some_class {
    font-family: Consolas,monaco,monospace;
  }
  ```

- By Element
  - This will affect every element of that type

  ```css
  b {
    font-family: Consolas,monaco,monospace;
  }
  ```

## The hardest (in my opinion) part of css

Let us talk about positioning an element where want to on the page, like how do we do that?
Css lets us manage well everything regarding style on the html elements but the important thing is well, where in the layout will the element be?

Css has many tools for this or that try to help us with it (I say try cause positioning gets kinda funky).

The first thing we have to take into account is the cell area that an element occupies on the HTML layout, but how do we see that???

We can go to any page, in this example let us open the inspector on our browser with F12 it shoul look something like this

<img src="./assets/InspectorExample.png" alt="placeholder" width="100%" height="100%">

Here we can explore the source code of our page and we can use the <img src="./assets/select_elment_icon.png" alt="placeholder" > to hover over the element we want to inspect.

Once you hover over the element you will see something change in the layout sub-tab on the inspector, in that sub-tab we have some boxes that display data, the name of these boxes are Flexbox, Grid and the Box Model. What matters now is the Box Model so lets check it out and what does that weird boxes mean.

First we have a yellow box, that determines the margin of the element <img src = "./assets/margin_box.png" width="50%" height="50%">
that is the distance or the space around other elements. We use this mostly for spacing our layout and the elements in it, this starts giving a format to our page in a way that elements start positioning each other depending on the other elements next to them, between them or as above so below them.

To actually move our elements on the viewport we use 4 properties for positioning:
Each one of this properties can be modified specifying different values like pixels, size of the font, etc. When we modify or specify the value of this properties css will add like a margin distance from the viewport, that means the WHOLE VIEWPORT to the element so you kinda position elements like a coordinate system, BUT AND THAT IS A BIG BUTT, the way we can position the elements depends on the positioning behaviour we can specify for the elements.

- Top
- Bottom
- Right
- Left

Now that we gave space to our elements we have to determine their positioning and that is also one of the hardest part of this job, cause since we are now modifying how its global positioning behaviours and there are 5 ways to do it:

### Static

Static positioning is the defaul positioning type for elements in HTML this means that their position is determined by the order they are rendered on the viewport.

### Relative

Relative gives you the power to position the element relative well to its position, what does this means? that you can position the element anywhere you want, event overlapping other elements on the viewport but the way it moves it is ALWAYS RELATIVE TO ITS ORIGINAL POSITION:

```css
.relative {
  position: relative;
  left: 30px;
  bottom:100px;
  border: 3px solid #2181adff;
}
```

### Fixed

This fixes the position into a place like literally just sticks them in there even if you move the page or modify the size of it, it will stay in there.

### Absolute

This makes the position of an element relative to the position of its closest parent, this means that the origin position of the element will be well its parent element

### Sticky

An sticky elements remains, well stuck into place when it reaches certain position relative to the viewport, this makes elements stick to certain border on the viewport when scrolling

## Floats another way to position elements

The pain in the ass of css, well for beginners in css, the float property, the property makes other elements flow right around them, this helps building a layout of elements depending on how we float them and how they float inside their oun container elements or parent ones, this is easier to understand if we view it, to view it create three divs that have a css that assigns the ``float:left;``property and check how instead of creating 3 new lines for the rendered content it just kinda squish them to the left like columns 

This float property has 4 options:

- Right:
  This makes elements stick to the right relative to the position of their parent element and it lets elements flow around it.
- Left:
  This makes elements stick to the left relative to the position of their parent element and it lets elements flow around it.
- none:
  This is the default value of any raw html element rendered on the scene
- inherit:
  Just inherits the float property of the parent

## How to learn more of the CSS jargon



## References

[W3 schools css positioning reference](https://www.w3schools.com/css/css_positioning.asp)

[Mozilla reference](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/CSS_layout/Positioning)

[Webflow reference](https://help.webflow.com/hc/en-us/articles/33961228002963-CSS-position-properties)

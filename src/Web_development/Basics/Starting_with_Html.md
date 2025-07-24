# HTML not a programming language

ALWAYS REMEMBER THAT HTML IS NOT A PROGRAMMING LANGUAGE

## What is, how and when with HTML

HTML stand for hyper-text-markup-language as we explained before html is the language that defines how we see the web or web pages:

- It structures web-pages
- It consists on different elements with different type of relationships
- These elements are called tags and each different tag determines how an element will be rendered on the browser

So lets look at an example of a super simple web page

```html,editable
    <!DOCTYPE html>
    <html>
      <head>
        <title>some page title</title>
      </head>
      <body>

        <h1>My First Heading</h1>
        <p>My first paragraph.</p>

      </body>
    </html> 
  ```

An html has a simple initial structure:

1. We have the ``<!DOCTYPE>`` declarion, this determines the document type and version (there has been a lot of html version through out the years)
2. Next we have the ``<html>`` tag, this is actually the beginning of our html structure.
3. Next we have the ``<head>`` tag, here we declared the metadata for our page, that would be scripts, style sheets, our page title, etc.
4. Finally we have the ``<body>`` tag, this is the actual content that we will see on the browser when openning a page.

In html we have different tags to describe the content we want, the tags that we want rendered on the web page goes inside the ``<body>`` tag.
We can add paragraphs, headings, images, forms, text boxes, buttons, links, videos, etc. Whatever it has been added to the HTML 5 version standard.

To see an example go to the [repository of presentations for the class](https://github.com/Robinthatdoesnotsuck/ClassPresentations) go into the first week branch
and under the HtmlJavascriptCss directory you can look into a simple page

## Doing some cool stuff with html files

Lets make some crappy 90s-2000s style web blog style with our basics:

Go to the [repository of presentations for the class](https://github.com/Robinthatdoesnotsuck/ClassPresentations) and into the second week branch and under the HtmlJavascriptCss directory
you can look into a more detailed page

## Complexity of HTML

Most of the complex parts of html falls down on how much you are willing to do to achieve certain style or functionality on your page, so let's look down into some of the most complicated stuff:

### Block and Inline elements

In HTML there are some elements that ocupies the whole we can call it line of text in a web page, like the div, the headers, the paragraphs, etc.
And the other side there are the inline elements these only occupy what is needed like the span, the links, image, labels, buttons, etc.

Whhat we use and how we style depends a lot on the properties of elements of being inline or block elements so be careful with that.

### Divs

The div is the default block element, you can interpret them as a divider or grouper of elements inside a webpage and if you don't believe me you can inspect your favourite web page with F12 on the browser to check the source code of the page and see that practically every section is divided well by a div.

Divs are the most used, style and modified elements in a web page, per their grouping function in a html page, so they are mostly used to group styling, script behaviour and page layout.

### Classes, Ids

Classes are like classes in a OOP language helps us in templating a particular element so that we can style multiple elements by referencing only that class instead of adding style singularly to each element, or with javascript to affect only a particular class, but the coolest part of this is that in HTML elements can be multiple class and different elements can be of the same class. This is a powerful tool but it can easily backfired if you are abusing of one class and coupling your changes with that pseudo-superclass.

Id lets us add an unique well ID to an element, this can be referenced by css or javascript, this thing gives us the power to give specific functinality to an element and it is unique so it can't be share by other elements. On of its unique uses is to bookmark certain sections with a link since the ID gives us a reference to the particular element we added an ID to.

### Iframes

This is an element that gives us access to embed web pages inside a web page, this gives us a lot of tools to make previews, embed apps into other apps, etc. But it can backfire heavily, giving us poor performance or soft-locking the page. Also when it comes to automation this thing becomes a pain in the ass.

### Responsiveness

If you think you page will behave the same for each type of screen, oh man you are wrong and a little bit silly, one of the most important things we have to handle cause if you change just the windows size in your computer you will apreciate that your page looks like utter horseradish, but there are easier modern ways to handle and personally I don't know how to add responsiveness with just plain HTML.

## Inputs and handling forms

Input elements are well a way that HTML gives us to handle data input:

- It can be buttons, text, radio buttons, checkboxes, etc.
- But the after logic of a submit button is handled by whatever we have programmed in the backend of our web page

And here comes more complicated stuff for handling the submition of data with something called http requests:

### HTTP requests

HYPER TEXT TRANSFER PROTOCOL it is a protocol that uses TCP to transfer well HTML resources, this protocol is the basis of mostly all communication on the web between services.
It is a high level protocol, this means that we only have to make a petition to whatever entity that gives us the power to do an HTTP petition and we don't have to worry about the intermediate parts between ourselves and the server that we are making the petition to.

This protocol has something called HTTP VERBS this is what we use to differentiate what type of request we are making, BUT we will see this methods in more detail in the future.

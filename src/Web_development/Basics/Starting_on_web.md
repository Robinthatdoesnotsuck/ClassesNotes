# First part of three

The basic structure of a web page is divided in three essentials parts, base HTML, styling with css and programming with javascript.
Anything else after this, been libraries or specific programming languages to manage this elements (like php, or typescript) just manipulates these three components in some way.

So knowing these three basic elements are essential to learn how to develop web pages:

- HTML stands for hypertext markup language
  - This controls how content is arranged in a web page, manages the whole structure of the web page with elements in a tree like structure

  ```html,editable
    <!DOCTYPE html>
    <html>
      <head>
        <title>Page Title</title>
      </head>
      <body>

        <h1>My First Heading</h1>
        <p>My first paragraph.</p>

      </body>
    </html> 
  ```

- CSS stands for cascading style sheets
  - This controls how the content renders in the web page, adding styling to each element

  ```css
    body {
      background-color: lightblue;
    }

    h1 {
      color: white;
      text-align: center;
    }

    p {
      font-family: verdana;
      font-size: 20px;
    }
  ```

- Javascript(god forsaken thing) is the scripting language of the web
  - This handles the behaviour of the elements in the page adding flow control and logic to the web page.

```javascript
     console.log("Hello, world!")
```

## What do we do as engineers with this knowledge?

*If you find the mistake in this section you get extra credit*

Most of our work when we are involved in a web app we have three main tasks:

- Maintaing the existing app
- Extending the functionality of the app
- Creating a web app or a solution that involves the web

And you may think that knowing the essential parts of a web page are enough to make a modern web app (kinda)
cause as mentioned before we use other tools to enable even more complex functions on the web page and its interactions
with other tools.

So first we have to ask the question "how do we serve data to the web?" and to answer another question "how does the computer exposes data to another computer?".

The computer as you should already know has an interface for processes called ports, these ports are free for us to use as users, but some of them are assign ports for different use cases inside the operating system and there are some assigned ports that handle the internet comunication by default:
  
| Port number | Port function |
|-------------|---------------|
|  80 | Handles the HTTP data ( Hypertext transfer protocol) |
| 443 | Handles secure http (Secure hypertext transfer protocol) |
| 22  | Secure shell connection |
| 530 | Remote procedure call |

The computer opens this port to handle the intake of data from the web, but us as engineers have access to the programming interface that can manage this
resource however we like and handle how it communicates, structures the data and the after logic needed for it to do what we want.
But to do this we need to create something called a socket and the first part to handle ports is to invoke a way to create a datagram socket:

*End of error section*

- This is the type of socket needed to communicate two computers across a network
- The syscall available to it is the socket(7) docs available on the [linux man-pages](https://man7.org/linux/man-pages/man7/socket.7.html)
- If you see the syscall for socket() we se that we need three parameters

```c,readonly
  int socket (int family, int type, int protocol)

```

- First we establish the family of socket we have to use in this case AF_INET for ipv4 protocols cause we want to be able
to communicate with the internet protocol
- We have to specify the type of socket in our use case we will use a stream socket SOCK_STREAM that enables tcp communication

The socket that is created following these instructions is the one most used to service common web apps, that means that a socket that it is:

- From the ipv4 protocol family
- It is a TCP type socket ( [there is another](https://www.youtube.com/watch?v=sLlu_RpElBs&pp=ygUQdGhlcmUgaXMgYW5vdGhlcg%3D%3D) type that we will look up more into the course)
- Has a port assigned to it(in the usable range)
- Has an Ip direction, since it is from the internet protocol family

This is all done to let our puter transfer data to other puters

## How does a network works(kinda)

![Lain with a lot of puters](https://blog.jlist.com/wp-content/uploads/2020/01/lain-computers.gif)

The operating system leverages a lot of the fundamentals of networking using something called layers.
These layers are configured as an stack of different software and hardware componets than in unison helps us in establishing a network
connection.

The puter transmits data through the network cable in chunks, this chunks are called packets that have two parts, a header and a payload:

- The header contains metadata regarding the source host, the destination host and the protocol used for transfering the packet
- The payload is the actual data you want to send, this can be a http request data, a photo or even HTML

The operating system practically handles this kind of unraveling of the packet from the network so we as programmers can concentrate in
only having any type of logic we need to use that data.

But Why do we care about networking? cause well that is how we serve HTML content and web pages, it is data that gets transported through the network and only then our web browser can interpret it and render HTML pages.

## Well and how does the browser uses this data to render a web page?

That is a more complicated question and we will have to explain some compiler theory and data structures:

We already explained that data in the network is served through packets, these packets are raw byte data and this raw data has to be
interpreted by a program to be useful, in this case the web browser.

The browser has something in its innards called a browser engine, the browser engine handles a process called painting the web page by creating a structure needed called the rendering tree, the how what and when it renders stuff is determined by the browser engine used by your web browser (this sometimes matters as some more advanced frameworks are kinda buggy with some engines).

But the important thing is this entity called "The rendering tree" and this is the sum of the DOM tree and the CSSOM tree:

But what is the DOM? some kind of weird kink or are they just magic words?

Well we already know that what describes a web page it's a file with a .html termination, but I've already explained that the browser just reads raw bytes from the network and you might think "Are you telling me that the browser interprets raw byte data that looks like this 0x68732f6e into HTML text?" and the short answer is:

![Jotaro saying yes](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fmedia1.tenor.com%2Fimages%2F48d17d8943220852f4b5c90d73485fae%2Ftenor.gif%3Fitemid%3D17161748&f=1&nofb=1&ipt=72aaa6b8b1001dc5ff4e5d8b497e36d1dbd23aedd9f2d937b9d87d3148223fa9)

The web engine first receives the raw bytes, then it transforms those bytes into characters (like ascii and stuff), then the browser takes these characters and it parses them into tokens -> The tokens and its meaning is determined by another data structure that matches the tokens with it's meaning so that the browser engine can interpret this so called source code into html tags with its attributes.
After this tokenization the engine groups these tokens into something called nodes, the node is the grouping by properties related to an element, property and text within it and finaly the grouping of these nodes by relationship is what creates a DOM object.

And This is done to render only the HTML that means the raw HTML file into a web browser.

What about the other stuff like css and javascript, well it kinda does the same for CSS, it receives raw CSS bytes and does the same process to transform it into something called a CSSOM.

![Bad dom diagram](./assets/Web%20Development-2.jpg)

Now that we have both the CSSOM and the DOM the browser engine sums both tree like structures into one creating what we know as the *rendering tree*, the browser now has the information of what to render and in what style it has to be but first it determines the position of each element on the page itself while taking consideration on how we style it, the screen size, the canvas size, etc.

This behaves a lot like a rendering pipeline (Almost the same if you ask me) so knowing the parallels between this and a graphics pipeline might help us in the future wink wink ;) ;)

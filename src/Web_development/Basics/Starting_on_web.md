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

* End of error section*

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

## How does the network works(kinda)

![Lain with a lot of puters](https://blog.jlist.com/wp-content/uploads/2020/01/lain-computers.gif)

# Architecturing systems

So lets talk about distributed systems or distributed computing or whatever you want to call it, but to understand this little monster we gotta ask a question.

Why do we have to do distributed systems/computing? In a sense we have been doing distributed computing since the mainframe days, people use to log from remote terminals across the wire on universities or military facilites and share resources from that mainframe.

But what we will be learning in this class is not that old school computing with old ass monitors and a keyboard, we will look into moder distributed systems and this have a more simple origin story.

Most of it comes as a system architecture necessity, what do I mean by that? well that shit was getting hard and I don't mean it like shit got hard in one specific area I mean it as everything regarding computer systems was getting really hard to get done across the growing IT and web boom.


## Necessities of dividing and conquering

In the past, like past past from some 20-30 years ago most systems were something we called a monolith, monoliths were a solution a massive program and obelisk of the business domain a single entity system that grew as the babel tower, a sign of humanity hubris and a challenge to god. So going into the topic again this monolith in our Systems Domain was just an application that grew more in code, complexity, collaborators and the scope it managed, but this came at a cost and that was time to deploy, time to develop, time to debug and latency on the different apps that use to work like this.

So we have to evolve the model of system architecture we were using and thus microservices were born as a way to decouple the monolith into smaller chunks that worked together to do what the monolith was doing but with some advantages:

- We can have a smaller code base for each part of logic necessary for our application
- Since application logic is decoupled from the large grouping of the monolith we can almos change everything we want from our microservice in a dirty way.
- It makes easier the job of scope, since microservices are practically parts of an app if we want to add something like sending emails, we just have to worry about sending emails instead of ideating a way of expanding a whole monstrous code base.

With those advantages we have to understand something first:

MICROSERVICES IS THE LOGICAL NEXT STEP OF THE ARCHITECTURE -> I use all caps cause we don't start an app with microservices we usually decompose a monolith into microservices or we just add microservices to an already microservice architecture.

WHY? cause as everything regarding computers, nothing is an all fit solution and everything has compromises as:

- A monolith is hard to debug not because of the complex structure, it is hard to debug cause building and debugging might be time consuming, but in microservices debuging involves integration testing or finding the bug might be the most time consuming task since everything is decouple and all over the place, you have to read logs, retry errors and failing to do so cause a specific path of the microservices was the one that failed.
- It is costly, since a lot of the architecture involves on demand load some spikes on hardware usage or services usage make microservices not that cost effective as a monolith
- Consistency and divergence, since we are deploying decoupled services some of them could differ in library versions, language versions, scattered data or different data formats or even programming languages.
- Overengineering -> this is one of the most common problems in microservices, cuase we might be doing to much on our solution and we might not need(yet) microservices.

## ![gopher journey](https://github.com/egonelbre/gophers/raw/master/.thumb/vector/adventure/hiking.png) Why Go you sick bastard?

Go was created for this -> quite literally, go was created to tackle the problems of a google in the desperate need to solve its scalability problems.

Go in its standard package has enough power to deal with the modern concurrency, multithreading, networking and scaling problems that arise from needing a microservice architecture.

Why don't we use other language?:

- Because most problems now in day have a tool to solve it cause even though personally I really like programming on C++ but I would be insane if I think to use it to build an entire app that relies on interactions with web services, databases, communication between cloud services, etc.
- It is a language born to solve this, literally we could program the final project with only the standard library.
- It is easy to program, easy to build/compile, easy to deploy and easy to learn.

So with this knowledge we can start building stuff or something.

## <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fprogrammerhumor.io%2Fwp-content%2Fuploads%2F2024%2F02%2Fprogrammerhumor-io-programming-memes-e24ae51b0f60969.png&f=1&nofb=1&ipt=ca5bd1a36057e8db573e6ccff1eb5584396afa0e98b5e430407a0bbae8d951cd" alt="placeholder" width="25%" height="25%"> Why rust you sick bastard?

Rust kinda was created for this, rust was created as a modern approach to modern system programming and with that came the addition of tackling something C or C++ ain't that great for:

Multithreading and handling context for multi-network distributed systems, so Rust even though not being intended for distributed systems has a robust standard library for handling everything go does, even been better in some areas, but lacking the specific strenghts of rust for handling that so you'll have to implement a lot by yourself or doing some more convoluted work around unlike go, but it is a more general purpose language and one of its biggest strenghts is that Rust is great at accelerating the power or speed of different modules of other heavier languages (aka python).

(On other notes, learning Rust takes you closer to the furry spectrum so good look with that)

## <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fprogrammerhumor.io%2Fwp-content%2Fuploads%2F2024%2F10%2Fprogrammerhumor-io-programming-memes-3cd9a99f43eb997-758x685.png&f=1&nofb=1&ipt=b9c5b77f855697a82baa3d5bc3e6bf4f1dae374328f2c905d66bdd01b9e79fdd" alt="placeholder" width="25%" height="25%"> Why elixir you sick bastard?

Elixir was also created for this well it was mostly created on top of a technology made for this called erlang and BEAM The Erlang virtual machine that has an interesting way of handling distributed by itself that we will explore in this course.

It is a powerful and a must language(in my opinion) if you want to do serious distributed systems since its message passing structure and hot reload options when updating code makes it extremely resilient, fast to ship and amicable programming language.

(On other note, I didn't find any funny elixir related meme)
## Lets talk about system design

![neither do i](https://c.tenor.com/JFhbBE5yn_IAAAAC/tenor.gif)

First things first, let us think about an app we might want to build and that actually has the need or the time-line to be first a monolith like we mentioned before then a microservice architecture

BUT here it comes a fundamental question now that we kinda know what to build, how does that data looks?
Well there is something more important than the looks and that is the how the data behaves, cause the thing here is we are programming an app we are not just storing data into a massive data lake or a warehouse or whatever you use to save static data we have dinamyc data,
This means that we are modifying that data, deleting it, inserting new data that is been inputted by a user, etc.
Then this gives another layer of complexity on how does data will behave, how do we structure the project to be in sync on how our data grows, what additional tech would we need if we want our users to always have certain ideal experience etc.

This thinking or this type of seeing the problems when it comes to the extra problems of architecting a system is what we call system design, let us just refer it now as an even more complex layer than just architecting systems.

## So it is a distributed systems course or a microservices one or an architecture or what?

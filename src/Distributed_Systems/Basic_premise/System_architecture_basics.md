# Architecturing systems

So lets talk about distributed systems or distributed computing or whatever you want to call it, but to understand this little monster we gotta ask a question.

Why do we have to do distributed systems/computing? In a sense we have been doing distributed computing since the mainframe days, people use to log from remote terminals across the wire on universities or military facilites and share resources from that mainframe.

But what we will be learning in this class is not that old school computing with old ass monitors and a keyboard, we will look into moder distributed systems and this have a more simple origin story.

Most of it comes as a system architecture necessity, what do I mean by that? well that shit was getting hard and I don't mean it like shit got hard in one specific area I mean it as everything regarding computer systems was getting really hard to get done across the growing IT and web boom.

![strawberry](https://scontent.fmex32-1.fna.fbcdn.net/v/t39.30808-6/490470375_1083809920430636_3503122141523932049_n.jpg?_nc_cat=107&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeHVQTeqm068ipeLIjiCl9UzbCMlq-mE2O1sIyWr6YTY7UsahaDTfwoDixc7F7f8-lkWGFscHs1B6wLdz_lumUR5&_nc_ohc=bsReUcJyQOwQ7kNvwGy1BD0&_nc_oc=AdnD5uTiu0vFfI_1QJSfNYdgclZ_uZhCroGVQuyrtt2iW_9WBXtuz-IBxn7bUx_AEsxXWCs_l_jQUMktYRy9SF8_&_nc_zt=23&_nc_ht=scontent.fmex32-1.fna&_nc_gid=Niz7VV1fwhcx1bQczrWCGA&oh=00_AfTxejRgOucRvVgrkapqwoYiDnwNBkQEqpojjCmZPvh8Vw&oe=689096A7)}

## Necesities of dividing and conquering

In the past, like past past from some 20-30 years ago most systems were something we called a monolith, monoliths were a solution a massive program and obelisk of the business domain a single entity system that grew as the babel tower, a sign of humanity hubris and a challenge to god. So going into the topic again this monolith in our Systems Domain was just an application that grew more in code, complexity, collaborators and the scope it managed, but this came at a cost and that was time to deploy, time to develop, time to debug and latency on the different apps that use to work like this.

So we have to evolve the model of system architecture we were using and thus microservices were born as a way to decouple the monolith into smaller chunks that worked together to do what the monolith was doing but with some advantages:

- We can have a smaller code base for each part of logic necessary for our application
- Since application logic is decoupled from the large grouping of the monolith we can almos change everything we want from our microservice in a dirty way.
- It makes easier the job of scope, since microservices are practically parts of an app if we want to add something like sending emails, we just have to worry about sending emails instead of ideating a way of expanding a whole monstrous code base.

With those advantages we have to understand something first:

MICROSERVICES IS THE LOGICAL NEXT STEP OF THE ARCHITECTURE -> I use all caps cause we don't start an app with microservices we usually decompose a monolith into microservices or we just add microservices to an already microservice architecture.

WHY? cause as everything regarding computers, nothing is an all fit solution and everything has compromises

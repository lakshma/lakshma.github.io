---
layout: post
title: State(less/ful)ness in web apps
---

What is state ? In the world of computer science, state is a technical term for all the stored information, at a given instant in time. Output of a computer program 
at any time is completely determined by its current inputs and its state.

In this context, Web application can be defined as a computer program which generates output based on input and the current state of the program. Do you agree ? Well this 
need not be the case always. Not all computer programs are stateful, Lets have look. Consider a typical client server communication of a web application,

![a stateful client server communication]({{ site.url }}/img/stateful.png)

In the above scenario, server needs to remember (or) store the value of 'a' for every client, so that it can generate the right output. What problems can server face in this 
case,

* What happens when client base grows and the request rate is high enough ? We decide to scale the servers by adding couple more server instances and have a load balancer
upfront. What happens now ? clients state information is now spread across server boxes. This model won't work now. As load balancer forwards client requests to random server
 boxes based on demand and availability, server boxes cant always respond. Lets get matured. There is a solution to it,
 
If we host a database server in the network which all the server boxes can access, we can get around this problem. Great. Are we ok now ? Wait

* Did you realize that by doing so, we introduced a **_single point of failure_** in this architecture ? Indeed, we did.
* Shall we improve the performance by introducing **_caching_** and offloading the requests to cache if available ? Not at all. Cache & State don't go hand in hand. When you 
have a state you can't cache. To be able to cache, the fundamental requirement is that thing to be _idempotent_.

Lets redesign,

![a stateless client server communication]({{ site.url }}/img/stateless.png)

Just imagine the computational power we have now. Most of the requests don't even need to computed by the server, we have a cache, 5 + 1 = 6 is idempotent which is the right candidate 
for caching and adds a huge performance gain. On top of it we have an _elastic_ web layer which can scale on demand. **_Statelessness_** is one of the core constraints of 
being **_RESTFul_**. Lets embrace it.

> Having said so, please keep in mind that we are strictly stateless only from the perspective of server. We didn't offload the state to client either. What we essentially 
have done is made the client server communication stateless.




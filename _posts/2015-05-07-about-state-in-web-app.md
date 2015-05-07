---
layout: post
title: Role of state in web apps
---

What is state ? In the world of computer science, state is a technical term for all the stored information, at a given instant in time. Output of a computer program 
at any time is completely determined by its current inputs and its state.

In this context, Web application can be defined as a computer program which generates output based on input and the current state of the program. Do you agree ? Well this 
need not be the case always. Not all computer programs are stateful, Lets have look. Consider a typical client server communication of a web application,

![a stateful client server communication]({{ site.url }}/img/stateful.png)

In the above scenario, client needs to remember (or) store the value of 'a' for every client, so that it can generate the right output. What problems can server face in this 
case,

* What happens when client base grows and the request rate is high enough ? We decide to scale the servers by adding couple more server instances and have a load balancer
upfront. What happens now ? clients state information is now spread across server boxes. This won't work now as load balancer would forward client requests to random server
 boxes based on demand and availability. Lets get matured. There is a solution to it,
 
If we host a database server in the network which all the server boxes can access, we can get around this problem. Are we ok now ? Wait

Did you realize that by doing so, we introduced a **_single point of failure_** in this architecture ? Indeed, we did.





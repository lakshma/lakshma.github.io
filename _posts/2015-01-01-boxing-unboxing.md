---
layout: post
title: Boxing & Unboxing
---

We all know that boxing and unboxing are expensive operations. Lets take it one step deep,

Boxing is the process of converting a value type to a reference type. Why would one do that ? Well, when you are not sure about the datatype of the value type in scenarios like dynamic, non generic collections etc. When you do such a thing, then the runtime has to allocate a memory slot in heap and copy the value of your value type.

{% highlight c# %}
int i = 1; //i refers to a slot in stack memory which holds the value 1
/* Boxing */
object o = i; //o resides in stack and has a pointer to a memory slot in heap which hold the value 1
/* Unboxing */
int i  = (int)o; //now the runtime will walk the pointer link, fetch the data and typecast and stores the value in stack for i

{% endhighlight %}
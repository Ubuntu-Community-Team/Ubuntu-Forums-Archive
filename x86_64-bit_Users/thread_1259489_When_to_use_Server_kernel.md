---
title: "When to use Server kernel?"
date: 2009-09-06
forum: x86 64-bit Users
---

### Post by nixgeek on 2009-09-06
Hey All,

I did try some searching to no avail to this question.

Would using the ubuntu server kernel provide better performance
when using an Intel i7 CPU? It seems to be this CPU is
getting closer to a Server type of CPU like the Intel Xeon.

Is there any possible issues with Nvidia drivers, sound cards?

I am tempted to try this... but I am using Kubuntu 64bit and do
not want any sort of future issues with updates and upgrades
later.

I am doing Virtualization: kvm another reason I was curious
about using the Sever flavor of the Kernel. 

Any {useful} info would be great...

---

### Post by fela on 2009-09-06
I **think** that the main advantage with a server kernel is that the task scheduler favors througput to latency. Of course, on a desktop you'll always want the desktop kernel so you can play music and stuff without latency issues, and on a server you want the server kernel.

I don't think you have to worry about speed or latency though on that CPU, no matter what kernel you're using. That's one monster of a CPU you've got there.

EDIT: the difference between a server CPU and a desktop CPU is more silicon quality (sever > desktop) and therefore reliability. You don't want a server to be unreliable :lol:

---


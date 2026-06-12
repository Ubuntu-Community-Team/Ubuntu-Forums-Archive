---
title: "Best Kernel for Numerical Simulations"
date: 2009-03-07
forum: x86 64-bit Users
---

### Post by 3Miro on 2009-03-07
Hi to all Computational Scientists,

I am running some numerical simulations on my 64-bit ubuntu and was wondering if the generic kernel was best for that. I don't expect it would make a huge difference, but if the server kernel is better I would like to use it. 10% improvement for me would mean an hour of computation less.

The biggest thing is that I am using openMP and my code is spawning treads like crazy, if the server kernel can handle that better, then it would benefit my program.

Any thoughts, ideas, share experience?

---

### Post by marcelkoopman on 2009-03-07
> **3Miro said:**
> Hi to all Computational Scientists,

I am running some numerical simulations on my 64-bit ubuntu and was wondering if the generic kernel was best for that. I don't expect it would make a huge difference, but if the server kernel is better I would like to use it. 10% improvement for me would mean an hour of computation less.

The biggest thing is that I am using openMP and my code is spawning treads like crazy, if the server kernel can handle that better, then it would benefit my program.

Any thoughts, ideas, share experience?
You could try a realtime kernel (the linux-image-rt ones), but i suspect your application isnt realtime. 

In what language was this application written?

---

### Post by 3Miro on 2009-03-07
> **marcelkoopman said:**
> You could try a realtime kernel (the linux-image-rt ones), but i suspect your application isnt realtime. 

In what language was this application written?

It is not real time, it is scientific, it takes me 3 hours to simulate 120 seconds of fluid flow and that is at a course mesh (i.e. with a lot of approximations).

I used g++-4.3 with the openMP enabled + ACML.

---

### Post by marcelkoopman on 2009-03-07
> **3Miro said:**
> It is not real time, it is scientific, it takes me 3 hours to simulate 120 seconds of fluid flow and that is at a course mesh (i.e. with a lot of approximations).

I used g++-4.3 with the openMP enabled + ACML.

If you want to experiment you could try creating your own custom kernel. There's lots of options for thread scheduling etc.

---

### Post by Yashiro on 2009-03-07
If you're really keen you could try OpenSolaris instead. It may or may not offer a significant boost. Just a suggestion anyway.

---

### Post by dcstar on 2009-03-07
> **3Miro said:**
> Hi to all Computational Scientists,

I am running some numerical simulations on my 64-bit ubuntu and was wondering if the generic kernel was best for that. I don't expect it would make a huge difference, but if the server kernel is better I would like to use it. 10% improvement for me would mean an hour of computation less.

The biggest thing is that I am using openMP and my code is spawning treads like crazy, if the server kernel can handle that better, then it would benefit my program.


Just install all the different types and benchmark them yourself with your app.

I would imagine that the vast majority of system load would be in your app, and anything the kernel could do would be marginal, at best.

---

### Post by 3Miro on 2009-03-08
Thanks all for the input. I am rather busy right now and definitely have no time to experiment with a new OS, but I may try to install the server kernel to see if it makes a difference. I was just hoping that someone ele had already done that.

If the server kernel handles forking and joining treads better, it would do a better job for my problem.

---


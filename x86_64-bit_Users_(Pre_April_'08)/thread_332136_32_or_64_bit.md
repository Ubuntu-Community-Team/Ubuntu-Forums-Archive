---
title: "32 or 64 bit"
date: 2007-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Doug11 on 2007-01-05
I'm thinking of getting a new notebook this weekend. I will definately be running a lone OS of Ubuntu on it. Just wondering if I should upgrade to the 64bit or stay at the 32bit.

---

### Post by kidders on 2007-01-05
Hi there,

Questions like this have a habit of setting off idealogical wars, but before one starts, I just thought I should mention that choosing a 64-bit architecture would not be an "upgrade" per se ... 32-bit and 64-bit processors are just ... well ... different.

There's plenty of discussion on this forum and all over the web on the various pros and cons of each.

---

### Post by Doug11 on 2007-01-05
Yea,,that's sort of what I thought. 64 seems to be the thing of the future so I think that's what my choice is gonna be. Always up for a challenge anyway. Thx

---

### Post by kidders on 2007-01-06
No problem. :-)

---

### Post by Doug11 on 2007-01-06
I'll be going in a few hours to echange machines. My one question is,,,The install disc is the same for 32 and 64 right? It's just all the apps that you plan to install where you have to choose between the two?

---

### Post by kidders on 2007-01-06
No, not exactly.

Unlike Windoze, Linux can be properly optimised for specific processor architectures, so the natural choice for a 64-bit processor is a 64-bit operating system. Application builds you install subsequently depend on which architecture your kernel/etc. was compiled for. Having said that, most 64-bit machines can emulate 32-bit behaviour, but if you're going to make use of emulated 32-bit processing on a 64-bit CPU architecture, you would have to wonder why you bought a 64-bit machine in the first place. In any case, 32-bit applications go with a 32-bit _kernel_ (ie the processor architecture has nothing to do with it), and 64-bit with 64-bit.

Imo, the primary advantages of 64-bit Linux are very application-specific, so if they don't apply specifically to what you're planning on doing with your PC, you'll probably find that the disadvantages of working with 64-bit systems will outweight any practical benefit.

I suppose another way of answering your question is to say that I'm sure you could put an Intel x86 kernel on a Sempron, and it would work fine ... but it seems like a strange thing to do. Similarly, you could put one on an AMD64, but why would you want to? I have a Sempron, a G4, a couple of Pentiums and an AMD64, but I've always used correctly optimised kernels on each.

---

### Post by Doug11 on 2007-01-07
So what your saying is that to get the full advantage of a 64bit machine,,is to run a 64bit OS.It would be like putting a firefly motor in a Ferrari.  I havn't searched yet,,but I'm assuming there is a 64 version of Ubuntu?

---

### Post by kidders on 2007-01-07
> **Doug11 said:**
> So what your saying is that to get the full advantage of a 64bit machine,,is to run a 64bit OS.It would be like putting a firefly motor in a Ferrari.Well... sort of. Running a 32-bit kernel would be a bit like giving your Ferrari to a three-foot-tall chap with one arm and one leg. I'm sure he could drive it, but he might not be able to work all the controls.

> **Doug11 said:**
> I havn't searched yet,,but I'm assuming there is a 64 version of Ubuntu?Yes there is, but it's not necessarily safe to assume that about *all* linuxes. My 64-bit box currently has a Ubuntu server release on it (so I haven't had to contend with the whole proprietary 32-bit codebase nightmare for a while now), but I imagine 64-bit Ubuntu is quite friendly on desktops. I haven't tried it though.

---

### Post by Kreuger on 2007-01-07
> but if you're going to make use of emulated 32-bit processing on a 64-bit CPU architecture, you would have to wonder why you bought a 64-bit machine in the first place Maybe it has something to do with this:

> 64 seems to be the thing of the future  he's right. it is the future. so I could see running 32bit on a 64bit cpu until everything needed is supported by the 64bit, that way he wouldnt have to upgrade his computer later.

---

### Post by Elvish Legion on 2007-01-07
Well after using 32bit Linux for years (and getting frustrated with 64 bit) I decided to give 64bit ubuntu a shot, and I must say its running fine, though I don't notice a huge difference.

I used Automatix to help me get up and running, including 32bit swiftfox/plugs (I know a lot of people hate swiftfox, but it works)

---


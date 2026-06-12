---
title: "Cedega Licensing Question"
date: 2007-12-13
forum: Wine
---

### Post by MaindotC on 2007-12-13
How is it that products such as Cedega must be sold instead of being publicly available for free download like most other open source software?  Doesn't that violate the GPL?

You know what I just checked the GPL wiki and it explains about "dual licensing".  I got it - no need to reply.

---

### Post by Vadi on 2007-12-13
Free can also mean "freedom", not "no cost", you know. These things do cost more than 0 time/money to make.

(not that I consider Cedega a good example of this. I don't)

---

### Post by cogadh on 2007-12-13
Besides, Cedega itself is not Open Source or covered by the GPL. The CVS version of Cedega is covered by the LGPL, but that is never updated anyway.

---

### Post by MaindotC on 2007-12-14
After reading the wiki on the GPL, it seemed to me that the part that distinguishes Cedega over all other software is that it must interact or contain proprietary code like whatever files make it ideal for interacting with windows-based games.  I don't know if that's dll's or something but that's the conclusion I drew from the wiki.

I understand your point about it not being free because of time and effort put into it, but I thought under the GPL that whoever uses the Linux kernel (or whatever Stallman specifies) are welcome to modify it and to create software but must release their creations to the public domain.

I'm glad someone is making money off Linux programs because I think SOMEONE should be rewarded for their efforts - I just thought if that particular firm is not allowing their software for free download then it would be a violation of the GPL.  I mean obviously it isn't otherwise Red Hat would be buried in lawsuits by now, but I just thought about it and finally mustered up the courage to ask someone :)

Please let me know if my assumptions are correct and thanks for your time.

---

### Post by CarpKing on 2007-12-14
Actually, open-source programs are not in the public domain at all.  The licenses all have slightly different terms, but i believe all of them have stipulations about giving attribution to the people who worked on the code before you.  Some are closer to public domain, and don't require the changes you make to be released as open-source (this is how Cedega forked from WINE before WINE went GPL), but you still have to give credit.  If the code was in the public domain, anyone could do whatever they wanted with it without giving credit to the author (or so is my understanding.  I've never actually seen code that was in the public domain).

---

### Post by Beren Camlost on 2007-12-14
> **CarpKing said:**
> I've never actually seen code that was in the public domain

Releasing software as public domain was quite common and popular back in the Amiga days.

---

### Post by markharding557 on 2007-12-14
gpled software is licenced software where you must give the exact same rights that you have,as stated in the gpl,to everyone else, as you had when you aquired it

---

### Post by Samhain13 on 2007-12-14
strAlan,

I believe GPL is less about making stuff free for download and more about making the source available. It's like if I'm I'm a developer and I built something on top of existing GPL'ed software, I have to release the new source of the software that came as a result of my building on top of it. It doesn't necessarily mean that the new software that I made should be free for downloading, just that if another developer wanted to build on top of the software that I built, which I built on top of someone else's software, that other developer should be able to do it. Otherwise, I shouldn't have built on top of the original GPL'ed software in the first place.

But, I could be wrong. It's just the way I think it works. :)

---

### Post by Vadi on 2007-12-14
That is how it works, I think.

Why shouldn't be people allowed to make a living off their work anyway?

---

### Post by MaindotC on 2007-12-15
> **Vadi said:**
> That is how it works, I think.

Why shouldn't be people allowed to make a living off their work anyway?

In the movie Revolution OS, which you can watch for free on google video, Linus was asked how he felt about his kernel being in use today by so many people but not directly receiving a sale or commission from each use.  Paraphrasing, he stated that it was more important to benefit society than it was to worry about a paycheque.  I agree that people need to make a living doing something, but don't you feel that the "hobbyist" community has done pretty well for a majority of their programs being distributed freely?  Isn't the reward more in knowing what you have contributed to society and receiving appreciation for it?  

I think Stallman had a very radical thinking but was more concerned about removing the constraints of proprietary source code and enabling as much access and control as possible to the user that was seated in front of the machine.

CrapKing - how do you define public domain?  Without scrutinizing the gnu.org site at this very moment, I interpret the GPL as being produced under the Free Software Foundation.  I'll read it in more detail but I recall Stallman saying all source code produced under the GPL (which is via the FSF) must be released.  Again, I'll read it in more detail.  Darn you all - I have finals till Wednesday!

---

### Post by SunnyRabbiera on 2007-12-15
well from what I know though both crossover and cedega give most of their development code back to wine, its just that they are commercial thats all.

---

### Post by MaindotC on 2007-12-15
I appreciate all of your replies but I'd like to suggest if you make a claim, please be able to reference or cite it.  I know mine regarding the movie was a little sketchy, but I'll read the GPL before I state any more "I think" or "I believe".

---

### Post by karth on 2007-12-15
Actually, Cedega hasn't much things to do with Wine anymore, besides being on of the few softs able to run windows software on linux.

In fact, Transgaming (makers of Cedega), took Wine's source code when it was under a license that enabled them to do proprietary, commercial software out of it. This has led the Wine project to migrate to a GPL license, to prevent this to happen again. Cedega does not contribute to Wine's code, and Wine does not contribute to Cedega.

On the other hand, CrossOver is really close to Wine. It's commercial software, and it is the main financial backer of Wine. WIne's source goes into CrossOver, and CrossOver's goes back. Even some CrossOver devs are Wine devs.

---

### Post by Samhain13 on 2007-12-15
> **strAlan said:**
> I appreciate all of your replies but I'd like to suggest if you make a claim, please be able to reference or cite it.  I know mine regarding the movie was a little sketchy, but I'll read the GPL before I state any more "I think" or "I believe".

We say "I think" or "I believe", not because we have not read the GPL, it's just that we are allowing people who are experts in the subject to shed light on our opinion. It will be helpful to the discussion too if you can quote provisions in the GPL that **specifically prohibit the sale** of GPL'ed software and their derivatives.

Where one doesn't exist, there's the answer to your original question:
> How is it that products such as Cedega must be sold instead of being publicly available for free download like most other open source software?

:)

---

### Post by MaindotC on 2007-12-15
> **Samhain13 said:**
> We say "I think" or "I believe", not because we have not read the GPL, it's just that we are allowing people who are experts in the subject to shed light on our opinion. It will be helpful to the discussion too if you can quote provisions in the GPL that **specifically prohibit the sale** of GPL'ed software and their derivatives.

Where one doesn't exist, there's the answer to your original question:


:)

Well, I'm assuming that Cedega and Red Hat are selling their software because it is not freely available for download.  I curious to understand the business in selling something that is freely available.

---

### Post by Vadi on 2007-12-15
Configuration.

Not every business customer has time/patience to set things up as they're needed, so thats where linux companies are making money. See Impi Linux, & canonical's huge list of commercial partners.

---

### Post by Samhain13 on 2007-12-15
I hope this clears things up. Here are snippets from the **GNU General Public License Preamble** that I think are relevant to this discussion (with my emphasis):

> 
When we speak of free software, we are referring to freedom, **not price**...

For example, if you **distribute copies of such a program, whether gratis or for a fee**, you must pass on to the recipients the same freedoms that you received...

[http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html)


---


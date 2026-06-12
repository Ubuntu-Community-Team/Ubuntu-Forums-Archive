---
title: "firefox is slow in gutsy only after enabling Desktop effects"
date: 2008-01-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by dayanandasaraswati on 2008-01-06
I've just now installed gutsy. I also downloaded the flash plugin for firefox and has also enabled desktop effects. I find that when i load sites with a lot of photos and multimedia, my browser becomes terribly slow. It struggles to even open a second tab. And switching between tabs is pathetically slow. Most of the time firefox blacks out. I also use swiftweasel and the situation is no better there. What can be done about this problem. Without desktop effects my browsers are running perfectly fine. What can i do about it. Whats my solution. I'm using Intel 102GGC mother board with on board graphics card (ATI) with 1GB DDR2 RAM and dual core processor.

---

### Post by luisromangz on 2008-01-06
Well that's happening here with another completely different config, so it should be compiz related. I made the choice, and selected swiftness over coolness, and now I seldom run compiz.

---

### Post by LeDechaine on 2008-01-19
Also waiting for a fix.. it's a known bug.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/110384](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/110384)

---

### Post by Kilz on 2008-01-19
Has anyone here tried [Swiftweasel]("http://swiftweasel.tuxfamily.org/"), its an optimized build of Firefox that is very quick.

---

### Post by dayanandasaraswati on 2008-01-19
yeah i used swiftweasel in 7.04. It works splendid there but in 7.10 i just open swiftweasel and it blacks out..Opening one tab itself makes it black out in 7.10..Its much worse than normal firefox..:(
Do you have same problems..
i'm using a intel dual core processor 1GB ram

---

### Post by Kilz on 2008-01-19
> **dayanandasaraswati said:**
> yeah i used swiftweasel in 7.04. It works splendid there but in 7.10 i just open swiftweasel and it blacks out..Opening one tab itself makes it black out in 7.10..Its much worse than normal firefox..:(
Do you have same problems..
i'm using a intel dual core processor 1GB ram

Do the problems of it blacking out happen when desktop effects are turned off?

---

### Post by dayanandasaraswati on 2008-01-19
no it does not black out so badly. But still swiftweasel also doesnt run as good as it used to do in 7.04..In 7.04 i used to stream flash movies in 15 tabs concurrently and still the system will run like a horse..Now its really pathetic in 7.10..Can i know why is it so  bad..

---

### Post by odysseusjak on 2008-01-19
Have you tried disabling IPV6 in Firefox?  That is one of the very first things I do.  In the address bar, type

about:config

Now, right under the address bar there is another text bar called 'Filter' and your cursor should already be there and blinking.  Type

ipv6

IPV6 is enabled.  Double-click it to disable it.  You should notice a tremendous speed increase.

If you have already done this, then I'm at a loss.

---

### Post by Kilz on 2008-01-19
> **dayanandasaraswati said:**
> no it does not black out so badly. But still swiftweasel also doesnt run as good as it used to do in 7.04..In 7.04 **i used to stream flash movies in 15 tabs concurrently** and still the system will run like a horse..Now its really pathetic in 7.10..Can i know why is it so  bad..

This may be the issue. The amount of ram that a tab eats up is incredible, and streaming. With desktop effects, which is imho still in its infancy you are going to have issues.

---

### Post by dayanandasaraswati on 2008-01-19
Ya that worked a bit..It didnt solve the problem of RAM eating up fully but it atleast increased my speed of download. I have a max speed of 220KBps but i get only 100KBps using firefox..but in windows i get the full speed..Now my speed is resumed for downloads with firefox..Thankyou folks..

---

### Post by pstickar on 2008-02-09
Hi,

i also have this problem. 

And with 4GB ram i would not expect it to be a problem of memory. I notice that CPU activity goes up. Grey screen last two to three seconds here.

I do not need to visit a site full of pictures to get very slow response. For example, loading a swiss newspaper like [www.nzz.ch](www.nzz.ch) takes about 7 seconds (use to load in less than 1 s), and selecting the first piece of news to open in a different tab takes the same amount of time. 

Deselecting desktop effects had no influence. Nor deselecting ipv6. In my humble opinion is a problem with firefox and nothing else.

Two days ago, before the firefox upgrade, it worked really smooth. Does anybody know how can i get backwards with the upgrades?

TIA. 
cheers,
p.

---


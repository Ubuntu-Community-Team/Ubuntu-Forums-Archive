---
title: "ATI 9600XT, AMD64 and Beryl, once and for all"
date: 2007-04-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by rogeriovinhal on 2007-04-08
Hello, I am trying to install beryl in my AMD64 system, I have a 9600XT ATI radeon card, and I've been looking for the topics to find a way to do it, but they seem to tell different things from one to the other.

First, I saw a topic that someone said that it wasn't needed to use XGL in Edgy in order to make Beryl work, is that true? I have fglrx 8.33.6 and a self compiled 2.6.19.2 kernel up and running very well at the moment. Should I install XGL or not?

After installing, or not installing XGL, I should install beryl and do some specific configuration? What should I do?

Thanks for helping, and do you think a 9600 XT with 128 MB is enough to run the beryl desktop without flaws?

---

### Post by ffxr on 2007-04-08
beryl should run fine with the open source radeon driver... tho the CPU does the the 3d rendering, so bear that in mind if you see the CPU heaving a little more than expected.. 

In theory you should be able to get the GPU to do the rendering with the propiertary ATI flgrxr driver.., 

i could never get XGL setup correctly.. (with hindsight, my guess was that i had some remnants of AIGLX active in my 'XGL session' )

Edgy comes with AIGLX built in and its definately the easiet way to go, it worked flawlessly with my Radeon 9200SE ... and it doesnt really take much setting up, if i remember correctly... post fresh install all i had to do was add a couple of lines to my xorg.conf and apt-get install beryl..

just have a look around the community documentation; its probably a little more consistent compared to some of the conflicting advice you might have found on the forums..

[https://help.ubuntu.com/community/BerylOnEdgy?highlight=%28beryl%29](https://help.ubuntu.com/community/BerylOnEdgy?highlight=%28beryl%29)

---


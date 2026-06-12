---
title: "Stopmotion for 64-bit"
date: 2008-07-05
forum: x86 64-bit Users
---

### Post by secondstage on 2008-07-05
When I installed Ubuntu Studio 8.04 64-bit, I was glad to see a stop motion program, but it would work, and failed with a "Segmentation fault" error. This seems to be a 64-bit issue. I've tried to get other programs like Avidemux, and Kino. Does anyone know of a way to get Stopmotion running, or know of a program that can do stop motion animation(and do it it well/good)?

--secondstage

---

### Post by LutefiskJoe on 2008-07-28
I'm afraid the only workaround at present seems to be a 32bit system installed specifically to run stopmotion. I'd certainly appreciate a 64bit version, but I'm a complete newb and can't really concieve of sorting that one out. 

There is a program called [Stop Motion Pro]("www.stopmotionpro.com") which may work in WINE?

---

### Post by gremm on 2008-08-12
I also get a just the initial window and the program goes away in 64bit. However, starting via valgrind works and reports some memory leaks... probably this will be a first step.

---

### Post by Yellow Pasque on 2008-08-12
I've built a .deb package from the latest source and it appears to work on my system. I'm not quite sure how to distribute it though. I think I need to set up an ftp server for all the .deb's I've been building.

---

### Post by TheguywholikesLINUX on 2008-10-14
could you upload it as an attachment to the thread, i am having the same problem.

---


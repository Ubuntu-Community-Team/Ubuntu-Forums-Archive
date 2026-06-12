---
title: "is it possbile to compile 32bit sources to 64bit?"
date: 2006-09-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by sha_man on 2006-09-30
hello,

as in the titile: is it possbile to compile 32bit sources to  (amd) 64bit, make a .deb and install the package? Does the program become 64bit *native* then? 
If so, could anyone tell me how to do it? :D 
Let's say, for ex., the [VLC Sources]("http://www.videolan.org/vlc/download-sources.html").
How could i compile it to use amd64, then make a .deb, and install?
That would be very helpful!

Or: can i simply install most 32bit .deb packages manually for amd64 using "dpkg --force-architecture", would t work with VLC?

---

### Post by angkor on 2006-09-30
> **sha_man said:**
> as in the titile: is it possbile to compile 32bit sources 

Is there such a thing as 32bit source? I always thought that you could compile any source for a specific architecture. Maybe some programs are only tested on 32bit but I think you should just give it a try.

---

### Post by Kilz on 2006-09-30
> **sha_man said:**
> hello,

as in the titile: is it possbile to compile 32bit sources to  (amd) 64bit, make a .deb and install the package? Does the program become 64bit *native* then? 
If so, could anyone tell me how to do it? :D 
Let's say, for ex., the [VLC Sources]("http://www.videolan.org/vlc/download-sources.html").
How could i compile it to use amd64, then make a .deb, and install?
That would be very helpful!

Or: can i simply install most 32bit .deb packages manually for amd64 using "dpkg --force-architecture", would t work with VLC?


As said above source can be compiled to work on any platform. [Here is a link that gives the basics of compiling.]("http://www.monkeyblog.org/ubuntu/installing/#source")

---


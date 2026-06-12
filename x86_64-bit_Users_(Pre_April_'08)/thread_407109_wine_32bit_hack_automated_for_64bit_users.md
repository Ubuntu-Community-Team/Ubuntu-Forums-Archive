---
title: "wine 32bit hack automated for 64bit users?"
date: 2007-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by NullHead on 2007-04-11
Has anyone wondered if there is a way to automate the wine hack [http://wiki.winehq.org/UbuntuAMD64]("http://wiki.winehq.org/UbuntuAMD64")
to automatically install with the hack and from the repository?
Is it possible?

---

### Post by Kilz on 2007-04-11
> **NullHead said:**
> Has anyone wondered if there is a way to automate the wine hack [http://wiki.winehq.org/UbuntuAMD64]("http://wiki.winehq.org/UbuntuAMD64")
to automatically install with the hack and from the repository?
Is it possible?

It sure is possible, in fact I have had a script that dose it for a long time. :D Look in my signature.

---

### Post by NullHead on 2007-04-12
Thanks ... but I don't seem to understand your script ... Does it install "A" wine .deb or can you use syanptic or apt to get and install wine ...that is what I'm after. 
Can I use this script in 7.04??

---

### Post by kuja on 2007-04-12
> **NullHead said:**
> Does it install "A" wine .deb yup
> **NullHead said:**
>  or can you use syanptic or apt to get and install wine nope
> **NullHead said:**
> Can I use this script in 7.04??Sure can.

---

### Post by NullHead on 2007-04-12
well that's great and all but I'm looking for something that will allow me to use the wine repository ...

---

### Post by Kilz on 2007-04-12
> **NullHead said:**
> well that's great and all but I'm looking for something that will allow me to use the wine repository ...

First off, It dose download the 32bit .deb file from the wine repository. Shocking how you missed that, you do know how to read what a script does right?  My howto/script is much more detailed than the wine site and has fixes for problems that happen with Ubuntu. That you are here asking for a script, may indicate that you dont understand something. That when someone writes one to help people. People without a clue should get a clue or remain silent.

Second if you are following the so called "hack" on the wine site, be ready for problems. Third if you require a script for

```
cd ~/Desktop 
sudo dpkg --force-architecture -i wine_*_i386.deb
```

Feel free to write one that does that. You should have lots of people flocking for it. But be prepared to give them lots of help, because they will be exstremly clueless if they need a script for those simple commands.

Matthew 15:14 "Let them alone: they be blind leaders of the blind. And if the blind lead the blind, both shall fall into the ditch. "

---


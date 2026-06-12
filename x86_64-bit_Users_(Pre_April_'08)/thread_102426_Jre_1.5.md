---
title: "Jre 1.5?"
date: 2005-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Laen on 2005-12-12
Hi. I'm trying to install Jre 1.5, but I can only find the 1.4 version in the apt repositories. Installed 1.5 manually, but it doesn't seem to include a firefox plugin.
I looked around the forums and everyone's saying install j2re1.5, and that's simply not there for me. Yes, I've added the extra reps. Is it that there's no 1.5 yet for amd64 or am I just missing something?
Really frustrating.

---

### Post by RAOF on 2005-12-12
I don't think there's a 1.5 JRE in the repos.  And I don't think there can be (at least in official repos - the licencing terms on the Sun stuff aparently says that you can't also distribute non-Sun java).  And Sun hasn't released a browser plugin for x86_64.  Apart from helping the blackdown guys or hacking on the gnu classpath, I don't think you'll get any Java 1.5 browser joy, on x86_64, at least.

---

### Post by manicka on 2005-12-12
[http://doc.gwos.org/index.php/PLF](http://doc.gwos.org/index.php/PLF)

---

### Post by Imexius on 2005-12-12
Ok so just go sudo gedit /etc/apt/sources.list

add this to your list

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

Save then go into the terminal and type: sudo apt-get install j2sdk1.5

---

### Post by manicka on 2005-12-12
[QUOTE=Imexius]Ok so just go sudo gedit /etc/apt/sources.list

add this to your list

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

Save then go into the terminal and type: sudo apt-get install j2sdk1.5[/QUOTE]

sudo apt-get update
sudo apt-get install  sun-j2re1.5

That is for  the i386 packages. For other Archs follow the directions at PLF to build your own package and install it.

---

### Post by Laen on 2005-12-13
Thanks for the suggestions.

So sad when you have to be restricted or when things become a bit rougher just because you're using a 64-bit platform. Can't wait for the damn thing to become more popular. :D

---

### Post by atoponce on 2005-12-13
[quote=Laen]Can't wait for the damn thing to become more popular. :D[/quote]

It definitely is getting more popular, no doubt.  I order 55 Ubuntu CDs from Shipit every release, and hand them out at the University I attend, and the request for 64-bit is growing.  It surprised me actually, at first.  My next laptop purchase will be 64-bit for sure.

---

### Post by JuanC on 2005-12-13
You can use JRE 1.5 for Amd64 in Konqueror without problems.

There is no Java 1.5 Amd64 plugin for Firefox , I talk about the official Sun JRE.

The official reason form SUN is that there is no 64-bits Mozilla Browser , these guys should read all news.

---


---
title: "java releases a working 64 bit plugin."
date: 2009-02-02
forum: x86 64-bit Users
---

### Post by ethoxyethaan on 2009-02-02
both the icetea plugin and the Previous builds of java 6 update 12 just diden't do the job for me, but since yesterday they added a new build that works Very smooth, 

for those who want to give it a try i wrote a small howto [here](http://tldr.me/blog/2009/02/03/java-6-update-12-for-linux-amd64-howto/).

i think the Icetea developers did a great job trying to make the 64 bit plugin possible, but at the same time i'm happy that i wont have to screw around anymore to get java applets to work.

---

### Post by portis on 2009-02-03
when will it enter into the repo?

> **ethoxyethaan said:**
> both the icetea plugin and the Previous builds of java 6 update 12 just diden't do the job for me, but since yesterday they added a new build that works Very smooth, 

for those who want to give it a try i wrote a small howto [here](http://tldr.me/blog/2009/02/03/java-6-update-12-for-linux-amd64-howto/).

i think the Icetea developers did a great job trying to make the 64 bit plugin possible, but at the same time i'm happy that i wont have to screw around anymore to get java applets to work.

---

### Post by ethoxyethaan on 2009-02-03
Well if i may compare this situation with the release of the 64 bit flash plugin it will with the release of 9.04, or they will just include it with the next Java update.

---

### Post by Thelasko on 2009-02-03
So, this means it's out of beta?

---

### Post by ethoxyethaan on 2009-02-03
well according to here:
[http://java.sun.com/javase/6/webnotes/6u12.html](http://java.sun.com/javase/6/webnotes/6u12.html)
and here:
[http://java.sun.com/javase/6/webnotes/ReleaseNotes.html](http://java.sun.com/javase/6/webnotes/ReleaseNotes.html)

it says "current release", but on the mainpage it 6B11 is still featured and not the 6B12

[http://java.com/en/](http://java.com/en/)

---

### Post by bunnyhugh on 2009-02-03
> **ethoxyethaan said:**
> both the icetea plugin and the Previous builds of java 6 update 12 just diden't do the job for me, but since yesterday they added a new build that works Very smooth, 

for those who want to give it a try i wrote a small howto [here](http://tldr.me/blog/2009/02/03/java-6-update-12-for-linux-amd64-howto/).

i think the Icetea developers did a great job trying to make the 64 bit plugin possible, but at the same time i'm happy that i wont have to screw around anymore to get java applets to work.

Thanks for the heads up and the howto it has worked for me.

Bun

---

### Post by jespdj on 2009-02-03
I'm looking at the [Sun Java download page](http://java.sun.com/javase/downloads/index.jsp) now and it says Java 6 update 12 - it's out!

Finally a 64-bit Java plug-in!! \\:D/

> **ethoxyethaan said:**
> it says "current release", but on the mainpage it 6B11 is still featured and not the 6B12
[http://java.com/en/](http://java.com/en/)
It has happened before that that page lags behind on the version.

---

### Post by gila_monster on 2009-02-03
Does anyone know if the Sun Java works with Opera 64-bit? There have been problems in the past.

---

### Post by jespdj on 2009-02-04
I don't know if Opera works with Sun Java, but what I do know is that the browser plug-in is for Firefox; Opera can use Java directly, it doesn't need a plug-in.

---

### Post by ethoxyethaan on 2009-02-04
Why use Proprietary opera in the first place when you have the free firefox.

---

### Post by howefield on 2009-02-04
> for those who want to give it a try i wrote a small howto here.

Many thanks, works a charm.

> **ethoxyethaan said:**
> Why use Proprietary opera...

Why ever not ?

---

### Post by zika on 2009-02-04
> **ethoxyethaan said:**
> Why use Proprietary opera in the first place when you have the free firefox.
if You've installed freedom properly You wouldn't have asked such a question. sudo apt-get reinstall freedom ... ;) or just reconfigure ... :lol:

---

### Post by CJ56 on 2009-02-04
Many thanks ethoxyethaan -

Seems to work very nicely - :)

---

### Post by ethoxyethaan on 2009-02-04
> **zika said:**
> if You've installed freedom properly You wouldn't have asked such a question. sudo apt-get reinstall freedom ... ;) or just reconfigure ... :lol:

True true, But knowing that using Firefox supports mozilla labs and Ubuntu I could not help to point out the availability of the alternatives that benefit the community.

On the other hand there is a chance of de gustibus (et non est disputandum, But we won't know that unless `gila_monster` replies.

Also: Does anyone who updates the Java Packets for the apt respo's, because the current java lister there is 6.10 and lagging behind 2 versions,

unless there is a reason behind not updating it.

:KS

---

### Post by gila_monster on 2009-02-04
> **ethoxyethaan said:**
> On the other hand there is a chance of de gustibus (et non est disputandum, But we won't know that unless `gila_monster` replies.

Mainly just interested in the performance. I actually like Firefox quite a bit, have used it for years. But some sites render better in Opera than Firefox.

gm

---

### Post by ethoxyethaan on 2009-02-05
> **gila_monster said:**
> Mainly just interested in the performance. I actually like Firefox quite a bit, have used it for years. But some sites render better in Opera than Firefox.

gm

firefox only functions slow in gnome for me, When i use another window manager it Scrolls faster / renders everything more smoothly.

(Currently using xubuntu for that reason).

---

### Post by Thelasko on 2009-02-05
> **ethoxyethaan said:**
> firefox only functions slow in gnome for me, When i use another window manager it Scrolls faster / renders everything more smoothly.

(Currently using xubuntu for that reason).

Are you sure this isn't due to desktop-effects?

---

### Post by Steeperton on 2009-02-05
> **ethoxyethaan said:**
> for those who want to give it a try i wrote a small howto [here](http://tldr.me/blog/2009/02/03/java-6-update-12-for-linux-amd64-howto/).

Thanks for that, works a treat!

---

### Post by novafluxx on 2009-02-07
Thank you! It works! AWESOME!! THANK YOU!!!

Out of curiosity, is there a way to "uninstall" this or undo the installation of the bin and the plugin?

---

### Post by ethoxyethaan on 2009-02-18
yes there is you just remove that directory:

sudo rm -rdf /opt/NAME_OF_DIRECTORY/

and remove the plugin the same way

sudo rm /path/to/plugin/

the paths depend where the plugin is installed / the java binaries.

---


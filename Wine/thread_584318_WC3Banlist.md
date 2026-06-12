---
title: "WC3Banlist"
date: 2007-10-20
forum: Wine
---

### Post by pvangarde on 2007-10-20
There is a thread by this exact name already. It was closed because no one answered. I don't know how to reopen it. Warcraft 3 is a popular game in linux because it runs in linux beautifully and I'd like to know if it is possible to get wc3banlist running under wine. 

First, has anyone had any success with this?

Second, is it even possible? WC3Banlist uses a DirectX API hook and wine doesn't emulate DirectX well enough to my understanding, so the game runs in direct3d mode (someone verify this?).

---

### Post by Jugix on 2007-11-06
I have tried to get this program to work on my ubuntu box but with no success. It installs correctly (AFAIK) but it does not find any NICs. Google does not give any answers so I think it is impossible to use wc3banlist on linux.

---

### Post by cogadh on 2007-11-06
Direct3D *is* DirectX, well, a component of it at least. I don't think that has anything to do with WC3Banlist not working, DX and Direct3D both work quite well in Wine right now and they really have nothing to do with the functionality of WC3Banlist anyway. 

More likely it doesn't work because of the app's reliance on WinPcap, which requires driver capablilities not present and not installable in Wine (you can't install Windows drivers in Wine).

BTW -  Only mods or administrators can close or re-open threads.

---

### Post by EtrnlApocaplypse on 2007-11-06
> **pvangarde said:**
>  wine doesn't emulate DirectX well enough to my understanding, so the game runs in direct3d mode (someone verify this?).

Well actually the game works okay in direct3d mode which is the default unless you add the -opengl modifier to the launch command (or change the default in the registry key).

The game does run much better with opengl though because directx implementation isn't perfect so I recommend using it.

---

### Post by janfsd on 2008-01-09
Well someone tried to do a java banlist program, but it's stalled however if you know some java maybe you can help to develop it. More info at: [https://sourceforge.net/projects/jwc3banlist/](https://sourceforge.net/projects/jwc3banlist/)

There was another one in python but not so developed: [https://sourceforge.net/projects/wc3helper/](https://sourceforge.net/projects/wc3helper/)

---

### Post by jkman on 2008-04-24
I was actually on the small team to develop JWC3Banlist for a bit...till school and work and other things got in the way.  From what I understand the project is being worked on again.  I'll most likely jump back in the development if some of my other projects fall through.  They would most likely welcome any help.

---

### Post by janfsd on 2008-04-25
> **jkman said:**
> I was actually on the small team to develop JWC3Banlist for a bit...till school and work and other things got in the way.  From what I understand the project is being worked on again.  I'll most likely jump back in the development if some of my other projects fall through.  They would most likely welcome any help.
Thanks for the tip, just checked the svn, and they are working on it again, great news!

---

### Post by pfanne on 2008-08-13
was anyone able to get the latest alpha running in linux?

---

### Post by PandaGoat on 2008-08-13
I understand that you seek a banlist, but wc3banlist does other things like pings and auto refreshing.  I have been working on such a program in c using pcap called snoopy: [snoopy.tuxfamily.org]("snoopy.tuxfamily.org").  There is no banlist yet, but I plan to implement one; I just need to figure out using public banlists and having a private one.  

Currently (for hosts) it can get pings and location, auto refresh slots, and custom kick through use of tcpkill.  Theres only one person working on it, so give me some slack if you have problems!

---

### Post by antragon on 2008-08-14
Hey,
I'm one of the developers of jwc3banlist...

To use it with ubuntu you have to install:

* jpcap
* libpcap
* java jdk 1.6
* jwc3banlist


You have to run it as root.

Greetings,
Antragon

---

### Post by BlahMan_of.Doom on 2008-08-15
Hmm. Is it possible to install Listchecker (pickup.listchecker, LC, PLC are all different names for it) in wine? Like, is there a WinPCAP alternative?

---

### Post by Manu311 on 2008-08-23
It is possible to run ListChecker in Wine, without big problems.
Sometimes it changes the port (on my machine) but restarting List-Checker solves this problem everytime.
You don't need WinPcap anymore for running ListChecker (only for a few options, which I don't need :)).

---

### Post by Troll_the_Great on 2008-09-03
> **antragon said:**
> Hey,
I'm one of the developers of jwc3banlist...

To use it with ubuntu you have to install:

* jpcap
* libpcap
* java jdk 1.6
* jwc3banlist


You have to run it as root.

Greetings,
Antragon

OK, I downloaded the archive, I've extracted it...but that's it... There is no configuring file, no "make&make install", no nothing.I have 2 files, jpcap.dll, libjpcap.jnilib and a folder jwc3banlist.jar.Now what?

---

### Post by Troll_the_Great on 2008-09-04
Anyone?

---

### Post by Troll_the_Great on 2008-09-05
Bump!

---

### Post by chuche17 on 2008-09-08
How did you get listchecker to work under wine?

---

### Post by Troll_the_Great on 2008-09-10
Bump!

---

### Post by janfsd on 2008-09-13
> **Troll_the_Great said:**
> OK, I downloaded the archive, I've extracted it...but that's it... There is no configuring file, no "make&make install", no nothing.I have 2 files, jpcap.dll, libjpcap.jnilib and a folder jwc3banlist.jar.Now what?

I used to build it like this (it was long time ago, it might have changed):
```
javac JWC3Banlist.java
```

And to run it: (you need to run as root)
```
sudo java -cp ./lib/hsqldb.jar:. JWC3Banlist
```
The last command should give you information if any library is missing. Hope this works...

---

### Post by benzi on 2008-10-28
i downloaded the tar file from source forge and i have 2 files inside the archive, a .jar file which is the java program and a libjpcap.so file. 

I tried putting the .so file in /usr/lib/jvm/java-6-sun-1.6.0.07/jre/lib/amd64 folder and tried to run the .jar from the desktop but it tells me jpcap could not load.

i tried putting the .jar and .so files inside the same folder on the desktop and then run the .jar but still the same thing happened, could not load jpcap.

I then went to [http://netresearch.ics.uci.edu/kfujii/jpcap/doc/download.html]("http://netresearch.ics.uci.edu/kfujii/jpcap/doc/download.html") to download the jpcap.deb file but my package manager complains that it is a i386 package. I'm running Ubuntu 64 bits. 

Any ideas on how to get this banlist to run?

---

### Post by dignan on 2009-01-07
Hello,

I'm the lead developer on Bancraft (originally named JWC3Banlist).

Troll_the_great, make and make install are for makefiles, typically used with C/C++.  This is a Java application, so the equivalent is ant.  I am currently working on packaging Bancraft for Ubuntu, so fear not there will be a simple way to install this program.

---


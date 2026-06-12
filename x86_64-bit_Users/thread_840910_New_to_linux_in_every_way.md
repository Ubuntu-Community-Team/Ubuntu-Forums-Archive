---
title: "New to linux in every way"
date: 2008-06-25
forum: x86 64-bit Users
---

### Post by Mcchub on 2008-06-25
i was bored the other night and found ubuntu so i thought what the hell and installed it. 

now i have never even thought about messing with linux before, But this user interface seemed nice and it really is i just have a couple questions.

I am trying to install things like flash and java but i keep getting error's saying "Couldn't display "/home/god/Desktop/jre-6u6-linux-x64.bin"."

and the other question is is there a way to run .exe files at all.  I would love any help anyone would give me 

thanky you in advance
McChub

---

### Post by niyonk on 2008-06-25
For the exe files you can use wine ;) (not 100% compatible tho)
I don't know exactly anything about the java errors you are getting, stick around someone will surely help :-D

---

### Post by Mcchub on 2008-06-25
hot damn thanks for the quick reply

---

### Post by Sef on 2008-06-25
To install Flash on 64-bit, read [Kliz's tutorial]("http://ubuntuforums.org/showthread.php?t=772490").

To install Java on 64-bit, read '[Java on 64-Bit Systems]("http://ubuntuforums.org/showthread.php?t=774956")'.  (The second paragraph tells how to intall it.)

---

### Post by steveneddy on 2008-06-25
.exe files are for Windows.

This is Linux.

Flash and Java are in the repos.

```

sudo aptitude install flashplugin-nonfree

```

Installs Flash. For Java open up Synaptic

System --> Administration --> Synaptic Package Manager

and search for icedtea. It's a stable java platform for Linux that works well with 64 bit Ubuntu.

You may try [this link]("http://ubuntuforums.org/showthread.php?t=765428") and scroll down to [COLOR="Blue"]**Step 3**[/COLOR].

[This is a good link]("http://ubuntuguide.org/wiki/Ubuntu:Hardy") for you also.

Most of this information is at the top of the 64 bit section where you posted this thread. Search and read to get a good understanding of where you are now in Linux Land.

Good Luck, we're all counting on you.

---

### Post by Mcchub on 2008-06-25
got flash working

thanks a bunch

---

### Post by pixel :-) on 2008-06-25
for .exe

sudo apt-get install wine

it works ,or it doesn't work for a particular .exe.Expect them to fail.Always try to run a native alternative.

---

### Post by steveneddy on 2008-06-26
> **pixel :-) said:**
> for .exe

sudo apt-get install wine

it works ,or it doesn't work for a particular .exe.Expect them to fail.Always try to run a native alternative.

I would try a native alternative before installing an app made for Windows, although I do have windows apps installed on my Linux box, only because I need them for business or school and there was not a well supported Linux alternative.

I personally don't like using Windows apps on my Linux machine, but I will say that the new Wind1.0 is mighty impressive.

---

### Post by Payteer on 2008-08-06
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I would check out this thread, it is really good compared to all other guides

---


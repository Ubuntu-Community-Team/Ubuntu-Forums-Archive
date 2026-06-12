---
title: "RosettaStone?  Recent experiences please."
date: 2013-02-09
forum: Wine
---

### Post by 1clue on 2013-02-09
Hi,

My wife wants Rosetta Stone. I've converted her laptop from Vista to Ubuntu and don't particularly want to switch it back.

I searched on the forum and found that almost all Rosetta Stone discussions are talking about using it from wine, so I'm posting here.  I also searched in YouTube and it seems that the examples given are older versions of Rosetta Stone.

I would like to hear from people who have good, solid experiences with Rosetta, on any platform and also of course on Ubuntu.  She also has a Samsung Galaxy S3 phone, so will probably be using that helper app too.

The current laptop, I have huge trouble getting a microphone to work for very long at all.  Given the trouble that seems to be prevalent getting the microphone to work through Wine, I'm seriously concerned about my chances of getting already flaky microphone behavior through to Wine.

Thanks.

---

### Post by Mark Phelps on 2013-02-10
Sorry, but your experiences trying to use current Rosetta Stone version are likely to fail...

As to the SGS3, you will also have SERIOUS problems trying to connect that through Ubuntu.  I have one and can only connect it through MS Windows -- where the special drivers from Samsung are installed.  In Ubuntu, you have to use MTP, and while I've read that works in 13.04, I'm not foolish enough to run an ALPHA version of Ubuntu just to access my phone.

---

### Post by 1clue on 2013-02-11
> **Mark Phelps said:**
> Sorry, but your experiences trying to use current Rosetta Stone version are likely to fail...

As to the SGS3, you will also have SERIOUS problems trying to connect that through Ubuntu.  I have one and can only connect it through MS Windows -- where the special drivers from Samsung are installed.  In Ubuntu, you have to use MTP, and while I've read that works in 13.04, I'm not foolish enough to run an ALPHA version of Ubuntu just to access my phone.

Ya, the SGS3 access is a PITA.  I've been using Kies Air to do it, it's not anything like a mounted filesystem but it gets me by.

So what Rosetta Stone works?  Has anyone tried the recent one with Crossover Office?  What's the best approach?

I'd hate to have to buy a Windows laptop just to get Rosetta Stone.

---

### Post by SaintDanBert on 2013-12-29
The web site reports that "Rosetta Stone v4x" is a **Bronze** application.
They describe bronze as:
[list]
[*]installs and runs
[*]many but not all of the application features work as expected
[*]save early and save often because of run-time troubles
[*]oh, and CodeWeavers cannot or will not help if you have troubles
[/list]
I'm going to try to install RS v4x of French modules 1-5 over the next week.  I'll report back what happens to me.

By the way, all that I read says that the v3x editions mostly work. The web site gives them a **Gold** rating.

**Crossover** is the commercial edition of Wine supplied by *Code Weavers*.

Bonne Année
~~~ 0;-Dan

---

### Post by 1clue on 2013-12-29
It's a little late for me, being almost a year ago that this thread was started.

My wife is now using a newer Windows laptop with her English version on it, I'm using a Mac with the Spanish version on it, and all the Linux boxes are using 13.10.  And I haven't even bothered with the SGS3 and Rosetta.

I researched the wine approach before starting the thread, and I've owned Crossover in the past.  I'd do it again, should something indispensable come up.

---

### Post by Idahed on 2014-01-23
Hi All,

After a bit of experimentation, I have been able to successfully run Rosetta Stone on my LinuxMint machine (i5 CPU, 8GB RAM, 64 bit).  I might add that I've set up this machine with ONLY LinuxMint 16 Petra;  no Windows installed.  Here's the process:
1.  Install Oracle's Virtual Box.  Allocate at least 25 GB.
2.  Using Oracle Virtual Box, create a Windows 7 virtual machine.  Again, allocate at least 25 GB.  This assumes you have a Win7 disc to install Windows, btw.
3.  Install Google Chrome browser for Windows.  Just go out to Google and download the .exe file for Windows Google Chrome and not the Gdeb for Linux.  Remember, when you run a virtual machine, it's just like you're running Windows 7.
4.  Once you have your virtual machine running, it'll look just like Windows 7.  
5.  Go to your Linux Sound Settings and select ALSA for your sound engine.  This will allow the microphone to work in Rosetta Stone.
6.  Go to RosettaStone.com, sign in, and begin your lesson.  The microphone test should pass now.
7.  Enjoy!  Disfrute! Amusez-vous! Buon Divertimento!  &#12362;&#27005;&#12375;&#12415;&#12367;&#12384;&#12373;&#12356;&#65281;

I hope this works for you.  I was so disgusted with Windows 8, I converted all my PCs to Linux and so far, have been darned glad I did.  Rosetta Stone was the last thing I had a problem converting and now it's solved (for me, at least)  and I hope for you, too.

---

### Post by 1clue on 2014-01-24
That's a Windows install.  It requires a license and everything.  I have virtual machines going, that's not the point.

---

### Post by Mark Phelps on 2014-01-24
> ... no Windows installed. This contradicts your later statement that you're running Windows in VirtualBox.

This thread is about running Rosetta Stone in Wine; not about running it in Windows.

---


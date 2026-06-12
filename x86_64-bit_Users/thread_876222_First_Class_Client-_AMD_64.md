---
title: "First Class Client- AMD 64"
date: 2008-07-31
forum: x86 64-bit Users
---

### Post by Andrew B. on 2008-07-31
I'm very new to Ubuntu and not Linux literate.  Ubuntu "just worked" and is great.  I'm running Ubuntu Hardy Heron 64 bit version on an AMD 64 system.  

I'm trying now to install First Class Client, and have read several posts and other internet advice which give instructions for AMD 64 that I've tried to understand/implement but which I can't make work.  I've tried all the different instructions, but am hampered by not really understanding them.  

I've got an icon for First Class Client in my Applications>Internet menu.  

I've installed the debian package from the First Class website, and that created the icon, but when I click on that the Ubuntu equivalent of the eggtimer appears and then nothing happens.  I also downloaded the beta version 9 of First Class for Linux Debian.

There are complex instructions for a 32 bit library that I tried to install but which gave lots of error messages that I don't understand.

I've tried to uninstall all the first class stuff (so I can start again) but the Add-Remove Packages doesn't recognise that First Class exists -- even though it appears in the Applications>Internet menu.

Please, please can anyone help me with some really clear instructions?  I'm quite happy to completely uninstall Ubuntu and start again with a fresh version if that's the problem.  

I'm getting a bit down, tell you the truth.  It's hard to adapt to Ubuntu after at least 10 years of Windows, and I really want it to work but all this Terminal stuff is really, really hard.

:(

---

### Post by gsmanners on 2008-07-31
Just from a glance it looks like FirstClass is closed-source, so you'll probably need to switch to 32-bit.

---

### Post by Jokimoto on 2008-07-31
Don't get too down on it, mate. I'm about as clueless as they come in regards to working thru the Terminal, or *how* exactly any of what I've managed to get working actually works. Still, I wouldn't go back to windows if you paid me, except for Battlefield 2 which I can't do without. :)
I guess the best advice I've been given is to read man pages, starting by typing "man man" into the Terminal. There's a man page for nearly every command, and even though it's painstakingly boring to read I usually get a little bit of knowledge out of it anyway. 

One thing that may help is the byzanz applet. Search thru Synaptic for "byzanz", and it will allow you (or someone helping you if they've got it) to record your desktop as an animated .gif
For me, it's much easier to *see* what someone did than read it, sometimes. Hope it helps.

---

### Post by Cappy on 2008-07-31
No one can help you if you don't post links (to the download, tutorials, etc.) or the error messages.

---

### Post by Andrew B. on 2008-08-01
> **gsmanners said:**
> Just from a glance it looks like FirstClass is closed-source, so you'll probably need to switch to 32-bit.
Thank you gsmanners, I was wondering whether that might be a way forward.  I've read lots on the forum on 32 vs 64 bit.  It sounds like I could have chosen to install Ubuntu 32 bit on my AMD Athlon 64-based PC and it would still work.  Put another way, would I need to buy a 32 bit CPU in order to have a 32 bit OS -- it seems not?  I don't do anything fancy (email, word processing, internet, music) so it sounds like I won't much benefit from 64 bit performance anyway.

So is a way forward to try to figure out how to un-install the whole of Ubuntu 64 and start again with Ubuntu 32 bit?  Installing Ubuntu 64 was really easy so I'm not fazed by that -- if it's a sensible way forward.

---

### Post by Andrew B. on 2008-08-01
> **Jokimoto said:**
> Don't get too down on it, mate. I'm about as clueless as they come in regards to working thru the Terminal, or *how* exactly any of what I've managed to get working actually works. Still, I wouldn't go back to windows if you paid me, except for Battlefield 2 which I can't do without. :)
I guess the best advice I've been given is to read man pages, starting by typing "man man" into the Terminal. There's a man page for nearly every command, and even though it's painstakingly boring to read I usually get a little bit of knowledge out of it anyway. 

One thing that may help is the byzanz applet. Search thru Synaptic for "byzanz", and it will allow you (or someone helping you if they've got it) to record your desktop as an animated .gif
For me, it's much easier to *see* what someone did than read it, sometimes. Hope it helps.
Jokimoto -- thank you: you cheered me up enormously.  I do feel such an idiot but I am trying to remember that I grew up with MS DOS (I'm old enough to have used the original twin-5.25 inch floppy drive IBM PC), Windows 1.0, Windows 3.1, Windows 98, and Windows XP -- that's nearly two decades of accumulated experience.  Switching to Ubuntu has been (with the exception of First Class) a very positive experience.  I was just tired yesterday!

---

### Post by Andrew B. on 2008-08-01
> **Cappy said:**
> No one can help you if you don't post links (to the download, tutorials, etc.) or the error messages.
Cappy, I've learnt something here.  I tried lots of things but I didn't keep a trail of what I'd tried (and didn't understand a lot of what I'd done) and so when it came to asking for help I knew I was ill-prepared.  I'm probably going to try again from scratch with Ubuntu 32 bit and this time I will keep an audit trail.  I know forum users find it frustrating when people ask for help vaguely -- and I know I did it.  Sorry.

---

### Post by Breepee on 2008-08-01
> **Andrew B. said:**
> Thank you gsmanners, I was wondering whether that might be a way forward.  I've read lots on the forum on 32 vs 64 bit.  It sounds like I could have chosen to install Ubuntu 32 bit on my AMD Athlon 64-based PC and it would still work.  Put another way, would I need to buy a 32 bit CPU in order to have a 32 bit OS -- it seems not?  I don't do anything fancy (email, word processing, internet, music) so it sounds like I won't much benefit from 64 bit performance anyway.

You can install a 32bit OS on your AMD64 without problems. If you do not need 64bit specifically (which appears so), then by all means, do. You'll have this whole class of problems less to deal with of you do.

Please let us know if that helped solve your problem btw (if you decide to do it).

---

### Post by Andrew B. on 2008-08-01
> **Breepee said:**
> You can install a 32bit OS on your AMD64 without problems. If you do not need 64bit specifically (which appears so), then by all means, do. You'll have this whole class of problems less to deal with of you do.

Please let us know if that helped solve your problem btw (if you decide to do it).
Thank you -- I have downloaded Ubuntu 32 bit and will see if I can make FirstClass work on it in the coming days.  Thanks everyone for your help; it makes a massive difference not to feel alone.

---

### Post by Jokimoto on 2008-08-02
> **Andrew B. said:**
> Jokimoto -- thank you: you cheered me up enormously.  I do feel such an idiot but I am trying to remember that I grew up with MS DOS (I'm old enough to have used the original twin-5.25 inch floppy drive IBM PC), Windows 1.0, Windows 3.1, Windows 98, and Windows XP -- that's nearly two decades of accumulated experience.  Switching to Ubuntu has been (with the exception of First Class) a very positive experience.  I was just tired yesterday!

You're welcome, mate. I'll surely need the same one day :)

---

### Post by Yellow Pasque on 2008-08-02
](*,) We don't need a separate 32-bit environment to run 32-bit code.

Use getlibs to obtain the libraries you need.
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

In this case, you need:
```
sudo apt-get install ia32-libs
sudo getlibs -p libqt3-mt libjpeg62 libartsc0 libaudio2 libpng12-0
sudo dpkg -i --force-architecture fcc-8.315-2-Linux-i686
```

The software installs to /opt/firstclass and creates an Application Launcher under the 'Internet' menu

Edit: I attached the thumbnail for proof, no chroots or other installs were needed

---

### Post by Yellow Pasque on 2008-08-02
Actually, the linux version is old, buggy, and doesn't manage memory well. Just get the Windows version and run it through WINE.

---

### Post by Yellow Pasque on 2008-08-02
```
dan@harvest:/opt/firstclass$ ./fcc
SARegisterProtocolApp(nntp,/usr/bin/konqueror)
SARegisterProtocolApp(http,/usr/bin/konqueror)
SARegisterProtocolApp(https,/usr/bin/konqueror)
SARegisterProtocolApp(ftp,/usr/bin/konqueror)
SARegisterProtocolApp(mailto,fcc)
FirstClass Client 8.315-2
Qt Toolkit Version 3.3.8b
Word Size=32 Big Endian=FALSE
Error: Attempt to free invalid pointer (0xF65DD008).
         * Stack frame looks damaged.  Possible buffer overflow.
         * Stack frame looks damaged.  Possible buffer overflow.
fcc: Received signal 2 (aborting)...
fcc: Received signal 2 (aborting)...
       Traceback is: code at FFFFE405  [Invalid code address]
       Traceback is: code at FFFFE405  [Invalid code address]
         * Stack frame looks damaged.  Possible buffer overflow.
         * Stack frame looks damaged.  Possible buffer overflow.
Abort (dumping core, please wait) ...
Aborted

```

---

### Post by Andrew B. on 2008-08-03
I can't make it work in 32-bit Ubuntu either.  By chance, I have a second, brand new computer.  I installed 32-bit Ubuntu Hardy on it (that worked perfectly).  I then followed the instructions at: [https://help.ubuntu.com/community/FirstClass](https://help.ubuntu.com/community/FirstClass)
I followed the Terminal instructions which are:
wget -c [http://www3.firstclass.com/ClientDownloads/FC83ClientDownloadFiles/fcc-8.315-2-Linux-i686.deb](http://www3.firstclass.com/ClientDownloads/FC83ClientDownloadFiles/fcc-8.315-2-Linux-i686.deb)
sudo dpkg -i fcc-8.315-2-Linux-i686.deb
sudo ln -s /opt/firstclass/fcc /usr/bin/fcc
I cut and paste each line in turn into Terminal, and for the first two commands, things happened: the first one downloaded a 6MB file and the second prompted me for my password and things appeared on the screen.  The third one didn't seem to do anything but didn't give an error message.

After that, the option to start First Class Client appeared on my Applications>Internet menu, and I clicked on it.   The timer appears for a while, and a square appears in the bottom panel for First Class Client, but after a few seconds it disappears and I don't get the login screen.

I have done absolutely nothing else.  So I might be missing a step?

Then, some time later, I noticed that there was an icon in the top right prompting me to install some "updates".  This I did.  Then First Class worked.

So I am delighted!  

If I knew what I'd done I could help improve the page on First Class installation on the Community Docs.  Does anyone know what that installer was doing?

---

### Post by Andrew B. on 2008-08-03
> **Temüjin said:**
> ](*,) We don't need a separate 32-bit environment to run 32-bit code.

Use getlibs to obtain the libraries you need.
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

In this case, you need:
```
sudo apt-get install ia32-libs
sudo getlibs -p libqt3-mt libjpeg62 libartsc0 libaudio2 libpng12-0
sudo dpkg -i --force-architecture fcc-8.315-2-Linux-i686
```

The software installs to /opt/firstclass and creates an Application Launcher under the 'Internet' menu

Edit: I attached the thumbnail for proof, no chroots or other installs were needed
Temujin, I did try these instructions in 64 bit, because there are posts in the forums about doing it.  It obviously worked when you did it, so I must be missing something unrelated to the 64/32 thing.  I wish I knew what!

You put the "banging your head against the wall" smiley?  It might be worth adding to the Community Documentation for installing first class [https://help.ubuntu.com/community/FirstClass](https://help.ubuntu.com/community/FirstClass) the additional steps for 64 bit Ubuntu to download the 32 bit libraries?  

Many people new to Ubuntu are likely to want to get their emails as one of the first things they set up, and having good documentation for it would help.  I'm hoping, one day, to be able to help with things like that, but my technical knowledge is nothing like good enough yet!

---

### Post by Andrew B. on 2008-08-03
> **Temüjin said:**
> ```
dan@harvest:/opt/firstclass$ ./fcc
SARegisterProtocolApp(nntp,/usr/bin/konqueror)
SARegisterProtocolApp(http,/usr/bin/konqueror)
SARegisterProtocolApp(https,/usr/bin/konqueror)
SARegisterProtocolApp(ftp,/usr/bin/konqueror)
SARegisterProtocolApp(mailto,fcc)
FirstClass Client 8.315-2
Qt Toolkit Version 3.3.8b
Word Size=32 Big Endian=FALSE
Error: Attempt to free invalid pointer (0xF65DD008).
         * Stack frame looks damaged.  Possible buffer overflow.
         * Stack frame looks damaged.  Possible buffer overflow.
fcc: Received signal 2 (aborting)...
fcc: Received signal 2 (aborting)...
       Traceback is: code at FFFFE405  [Invalid code address]
       Traceback is: code at FFFFE405  [Invalid code address]
         * Stack frame looks damaged.  Possible buffer overflow.
         * Stack frame looks damaged.  Possible buffer overflow.
Abort (dumping core, please wait) ...
Aborted

```
This is lost on me, I'm afraid.  Is this a set of instructions for something related to First Class Client, please?

---

### Post by Andrew B. on 2008-08-03
> **Breepee said:**
> You can install a 32bit OS on your AMD64 without problems. If you do not need 64bit specifically (which appears so), then by all means, do. You'll have this whole class of problems less to deal with of you do.

Please let us know if that helped solve your problem btw (if you decide to do it).
It does now work.  Thank you, everyone, for all of your help -- and moral support, which was more important.

---


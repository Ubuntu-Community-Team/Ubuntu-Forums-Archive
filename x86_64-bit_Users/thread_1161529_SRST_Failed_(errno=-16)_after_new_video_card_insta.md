---
title: "SRST Failed (errno=-16) after new video card install"
date: 2009-05-16
forum: x86 64-bit Users
---

### Post by yedidyah on 2009-05-16
Recently I removed my nVidia 7600gt graphics card and replaced it with a nVidia 9800gt.

Before Kubuntu 9.04 starts during non-gui boot up the system is really slow starting up (which it was NOT before the graphics card swap) then does things similar to the following with various different number values:

ata 5 1.656017 SRST Failed (errno=-16)
ata 5 12.920013 SRST Failed (errno=-16)
ata 5 22.932013 SRST Failed (errno=-16)
ata 5 57.976013 SRST Failed (errno=-16)

Then finally starts.

I couldn't seem to find anything specifically on google

Thanks for your response.

---

### Post by pastalavista on 2009-05-16
I think you need to reconfigure the xorg.
```
sudo dpkg -a reconfigure xserver-xorg
```

and then restart..
at least that's what I would do first

---

### Post by yedidyah on 2009-05-18
Okay I ran

sudo dpkg -a reconfigure xserver-xorg

I wasn't sure if it really ran or not as here is the results from the terminal:

dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

So I rebooted and the

ata 5 errno=-16 (with the other variable) is still coming up.

If it helps keep in mind my motherboard advertisement at the very beginning is very slow during boot sequence since new graphics card install.


Also one other thing of note when I first installed Jaunty everything went well except at this same screen I have been getting the following all along (before and after graphics card installation):

ata 1 softreset failed (device not ready)


I have had an _occasional_ clicking coming from my hard drive that reminds me of a hard drive that crashed on me a couple of years ago. But everything other than the boot up seems to be running okay as this has been going on approximately a couple of months.

---

### Post by pastalavista on 2009-05-18
Sorry, I got my commands mixed up. I'm pretty new at this too. The command is supposed to be
```
sudo dpkg-reconfigure xserver-xorg
```. 

There is also a program called envyng that can install Nvidia (and ATI) drivers. Install envyng: ```
sudo apt-get install envyng
``` and then, to run it, type ```
envyng -t
```. It will search for the correct driver for your video card. If it doesn't recommend a driver specifically for your card, though don't install anything. Sorry again about the mistake. Hope the real code works.

---


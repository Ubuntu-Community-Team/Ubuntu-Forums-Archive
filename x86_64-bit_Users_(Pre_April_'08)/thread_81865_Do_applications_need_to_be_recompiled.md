---
title: "Do applications need to be recompiled?"
date: 2005-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Leigh on 2005-10-25
Fairly naive question, but I'm new to all this....

I'm building an AMD 64-based PC that will run 64-bit Breezy but am wondering about applications that may be downloaded from the repositories. Are there specific 64-bit apps available or do the 32-bit ones have to be recompiled. Also, is it possible to run 32-bit apps on 64-bit Breezy?

---

### Post by jon_gunnar on 2005-10-25
[QUOTE=Leigh]Fairly naive question, but I'm new to all this....

I'm building an AMD 64-based PC that will run 64-bit Breezy but am wondering about applications that may be downloaded from the repositories. Are there specific 64-bit apps available or do the 32-bit ones have to be recompiled. Also, is it possible to run 32-bit apps on 64-bit Breezy?[/QUOTE]

If you install the AMD64 version of Ubuntu the repositories will be set to amd64 automatic. So any download you do by apt-get or Synaptic will be compiled for amd64.

As for the 32 bit question, it is a little more difficult. It is possible but have a look at this thread for a start. It gives some info. Hope it will help you.
[http://ubuntuforums.org/showthread.php?t=75011](http://ubuntuforums.org/showthread.php?t=75011)

---

### Post by Leigh on 2005-10-25
Thanks for the quick reply.

---

### Post by wmcbrine on 2005-10-26
The 64-bit kernel will run either 64-bit or 32-bit apps. However, the apps need to be linked to libraries of the same kind. AMD64 Ubuntu includes a full set of 64-bit libraries, but only a partial set of 32-bit ones.

The other issue is the package system. You can't directly install an x86 deb in an AMD64 system; that's the main reason for using chroot, AFAICT. Otherwise, you could just put whatever missing libraries you needed into /usr/lib32 and be good to go. You can still do that, in many cases, with programs you compile yourself, instead of chrooting.

---

### Post by Leigh on 2005-10-26
This leads me to two further questions, then.

I assume from your reply, wmcbrine, that 32-bit apps don't come with the necessary libraries to run, as Windows apps do, I think. Is this correct?

Secondly, what does *chroot* allow one to do? I've seen it mentioned elsewhere but understood it just changed the root directory for a process.

---

### Post by wmcbrine on 2005-10-26
Apps in Linux aren't typically distributed with the libraries (= DLLs) included, no. Instead, if using a package system like .deb, the needed libraries are marked as dependencies. Then, when you go to install an application via, say, Synaptic, it will check the database of installed packages, and if additional libraries are needed, it will mark those packages to be installed along with the application package. This system avoids a lot of duplicative downloads and library version conflicts. It has sometimes caused a few problems of its own, but they've largely been overcome.

Your understanding of chroot is correct. But one of the things that allows you to do, is to essentially install a complete 32-bit system within a 64-bit system (since the kernel will work for either). That way, you can use apt-get and Synaptic, just like in the "host" distro, but to retrieve 32-bit apps and libraries.

---

### Post by Leigh on 2005-10-26
Is it worth running a 64-bit version of Ubuntu then, if the 64-bits apps aren't mature enough? Reading through the forums, it looks to my "neophyte eyes" that there aren't enough 64-bit apps equivalent to their 32-bit counterparts so everyone *chroot*s to get them going. It seems that if you can run a complete 32-bit system within the 64-bit version and go to the trouble of doing so, why bother with the latter.

I understand that a 64-bit OS will perform better on a 64-bit processor, but ultimately, it's the applications that people use, not the OS.

---

### Post by rplantz on 2005-10-26
[QUOTE=Leigh]Is it worth running a 64-bit version of Ubuntu then, if the 64-bits apps aren't mature enough? Reading through the forums, it looks to my "neophyte eyes" that there aren't enough 64-bit apps equivalent to their 32-bit counterparts so everyone *chroot*s to get them going. It seems that if you can run a complete 32-bit system within the 64-bit version and go to the trouble of doing so, why bother with the latter.

I understand that a 64-bit OS will perform better on a 64-bit processor, but ultimately, it's the applications that people use, not the OS.[/QUOTE]

I think you answered your own question. It depends on the applications you use.

I'm using 64-bit for several reasons. One is that I wanted to learn about the amd64 architecture. I have a bunch of 32-bit programs I designed for a book I wrote, and I wanted to learn how to use them in a 64-bit environment.

Another reason is that I sorta like having the newest technology. For example, I drive a Prius.

I'm retired, so I'm not under pressure to accomplish anything. When I was working, I tended to take a more conservative approach. I needed to get the job done. Now I have more time to do what I like, which is to play with this stuff.

I am often asked what is the best computer to buy. (I was a computer science professor.) My most common answer is Macintosh. (I still turn to my Mac for several things.) Frankly, I would be very hesitant to recommend a Linux box to someone unless they are pretty good at using a computer. And I have quite a few good friends for whom Windows is by far the best choice.

So, it all depends on what you want to do, and how you want to do it.

Bob

---

### Post by wmcbrine on 2005-10-27
32-bit chroot is used only for a handful of apps. Nobody has to post about the 64-bit apps that just work, which is most of them.

---

### Post by zekolas on 2005-10-30
THe apps that people have trouble with in all 64 bit systems(including windows) is flash, macromedia has not released a 64 bit compatable flash player. In linux you can use gplflash what will work with some flash sites. Sun also has not released a java plugin for 64 bit systems, however you can use blackroot java that works pretty good.

Some of the multimedia codecs do not work in a 64 bit envornment so you might have a hard time watching WMV files. 

So if you can live without a flash plugin, java plugin and windows codecs I reccomend ubuntu 64.

---

### Post by Leigh on 2005-10-30
Aha! I think you answered what I was origianlly trying to ask, but didn't know how.  I was wondering what the state of 64-bit applications was.  Being new to linux I think I was getting confused with the discussion in these forums with *chroot* and trying to get 32-bits app running in 64-bit Ubuntu. The impression I got was that there were very few 64-bit apps and people were trying to get the 32-bit versions to  run under a 64-bit OS. If the only problem is Flash, then personally, I can do without it.

---


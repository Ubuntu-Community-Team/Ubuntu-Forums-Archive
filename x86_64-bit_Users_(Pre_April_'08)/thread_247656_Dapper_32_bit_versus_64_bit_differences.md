---
title: "Dapper 32 bit versus 64 bit differences"
date: 2006-08-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by j0eb0b on 2006-08-30
I am happily running a 32 bit version of Ubuntu 6.0.6 on AMD K7 hardware.  i am assembling a new AMD64 FX 55 build with more contemporary (although not cutting edge) hardware. I'm really not a gamer but don't want to exclude the possibility.  Reading the various posts, Ubuntu Dapper 64 seems to work ok but lacks drivers and porting to various common environments (mostly multi media and Java). I firmly believe that Ubuntu/linux is the future but need things like USB camera and scanner support and video  today. So my questions are:

Do I install Dapper 64?
Do I install Dapper 32?
Do I install Windows Xp Pro and dual boot (or use VMware) with either Dapper 32 or 64?


I want to leave MS entirely but am not presently smart enough to figure out how to get there.  Are there resources out there to help me (I have various linux reference manuals and "dummie" books)?  Maybe this belongs in the newbie section but I post it here becasue i really want to try 64 bit if I can without crippling my machine in doing so.  

Thanks,
Joe

---

### Post by jimboberella on 2006-08-31
Install 32bit and use Automatix and save yourself some ](*,) 
The 64bit version is good but as you noted has some small issues that will be eventually be resolved.

Mind you I installed the 64bit version, used Automatix and am very happy but I can't tell the difference between 64 and 32 in anything I use the PC for.

---

### Post by Kilz on 2006-08-31
> **j0eb0b said:**
> I am happily running a 32 bit version of Ubuntu 6.0.6 on AMD K7 hardware.  i am assembling a new AMD64 FX 55 build with more contemporary (although not cutting edge) hardware. I'm really not a gamer but don't want to exclude the possibility.  Reading the various posts, Ubuntu Dapper 64 seems to work ok but lacks drivers and porting to various common environments (mostly multi media and Java). I firmly believe that Ubuntu/linux is the future but need things like USB camera and scanner support and video  today. So my questions are:

Do I install Dapper 64?
Do I install Dapper 32?
Do I install Windows Xp Pro and dual boot (or use VMware) with either Dapper 32 or 64?


I want to leave MS entirely but am not presently smart enough to figure out how to get there.  Are there resources out there to help me (I have various linux reference manuals and "dummie" books)?  Maybe this belongs in the newbie section but I post it here becasue i really want to try 64 bit if I can without crippling my machine in doing so.  

Thanks,
Joe

Give 64bit a shot, if you fail its easy to install 32bit later. The only problems you might have would be if you do development. If you do there is a chroot script that will set up a 32bit chroot. 
Other than that most things work. The only multimedia codecs I know of that give trouble are wmv and wma, there is a howto to install a 32bit mplayer for them in the sticky. If the java you are refering to is the browser plugin, take a look in my signature.
Of course you could go the easy rout, and install a 32bit os. But it wouldnt make the best use of the hardware you just paid for. At least give 64bit a try. I would also install Windows if you are not used to Linux, there is a learning curve. This will also give you time to work out the small problems that will pop up no matter what version of Ubuntu you install. That way you can boot into windows if you need to do something. Later if you find you dont use it you can delete it.

---

### Post by don_pucci on 2006-08-31
I am in the same situation as Joe.  I have some new 64bit hardware and decided to install 64bit ver. of 6.06.  My biggest issue is the ntfs writer support and the fact that flash 9 doesnt work (not just a 64bit problem though).

I decided to install vmware and run xp on it...however installing vmware workstation 5.5 on it has been proving quite a challenge.

I am not considering a dual boot system seeing as I have a second drive that is ntfs.

> **jimboberella said:**
> Install 32bit and use Automatix and save yourself some ](*,) 
The 64bit version is good but as you noted has some small issues that will be eventually be resolved.

Mind you I installed the 64bit version, used Automatix and am very happy but I can't tell the difference between 64 and 32 in anything I use the PC for.

---

### Post by John.Michael.Kane on 2006-08-31
Kilz might be time to add a 32bit vs 64bit to the sticky? it could include things like the diffrences in the repo's,and architecture. 

It's just a thought that might help those trying to make the jump.

---

### Post by Kilz on 2006-08-31
> **SD-Plissken said:**
> Kilz might be time to add a 32bit vs 64bit to the sticky? it could include things like the diffrences in the repo's,and architecture. 

It's just a thought that might help those trying to make the jump.

It might, but most people seem to ignore the sticky's in the forums. But at least there would be something to counteract the fud from 32bit users.

---

### Post by kuja on 2006-08-31
> **don_pucci said:**
> I am in the same situation as Joe.  I have some new 64bit hardware and decided to install 64bit ver. of 6.06.  My biggest issue is the ntfs writer support and the fact that flash 9 doesnt work (not just a 64bit problem though).

I decided to install vmware and run xp on it...however installing vmware workstation 5.5 on it has been proving quite a challenge.

I am not considering a dual boot system seeing as I have a second drive that is ntfs.

Hmm, I don't know about vmware workstation as I haven't used it, but I've found vmware server dead easy to use.

---

### Post by don_pucci on 2006-09-02
no point using server if i am only running one virtual machine...

> **kuja said:**
> Hmm, I don't know about vmware workstation as I haven't used it, but I've found vmware server dead easy to use.

---

### Post by Kilz on 2006-09-02
> **don_pucci said:**
> no point using server if i am only running one virtual machine...


The server is free, thats the main reason to use it.

---

### Post by McMarley on 2006-09-04
64 bit is worth more than gold man!!
just wanted to point out that asking which is better in the 64bit section of the forum is kinda pointless because obviously here we will al tell you that 64bit is better.

---

### Post by Kilz on 2006-09-04
> **McMarley said:**
> 64 bit is worth more than gold man!!
just wanted to point out that asking which is better in the 64bit section of the forum is kinda pointless because obviously here we will al tell you that 64bit is better.

Just as asking in the Beginners section will result in people telling you to run 32bit. But they are beginners after all. :-D

---

### Post by lynx.jc on 2007-11-05
[http://www.desktoplinux.com/news/NS8745257437.html](http://www.desktoplinux.com/news/NS8745257437.html) 

we really cant tell if it's better or not, it depends on "what you want to do with it" ... hehe

I'm also a newbie and all that so maybe i don't know what the hell im saying (as some would think) but still i think that these compatibility issues with 64 are meaningless compare to how it was back when linux was under development... we can remember the issues with mac also but now everything has change and the development of improved OS and apps can give us the chance to move on ...

---

### Post by rsambuca on 2007-11-05
> **lynx.jc said:**
> [http://www.desktoplinux.com/news/NS8745257437.html](http://www.desktoplinux.com/news/NS8745257437.html) 

we really cant tell if it's better or not, it depends on "what you want to do with it" ... hehe

I'm also a newbie and all that so maybe i don't know what the hell im saying (as some would think) but still i think that these compatibility issues with 64 are meaningless compare to how it was back when linux was under development... we can remember the issues with mac also but now everything has change and the development of improved OS and apps can give us the chance to move on ...

What in the world does that link have to do with this thread?  And did you notice this thread is over a year old?

---


---
title: "64 bits uses more memory?"
date: 2008-12-04
forum: x86 64-bit Users
---

### Post by vipseixas on 2008-12-04
I read that 64 bits systems use more memory than 32 bits ones, because of the pointers size. Is that for real? Anyone knows how much is this?

I recently discovered that my Dell Vostro with AMD64 X2 processor only accepts up to 2GB of memory, which it already has. What a shame! Why they sell a 64 bits system with this limit???

Anyway, I am concerned about memory because I run some memory intensive programs (a.k.a. Eclipse) and every byte is making a difference.

[]s!

Vinicius

---

### Post by wfp on 2008-12-04
It uses a little more on my system than did the 32-bit. The difference did not have any issues with performance. I have 2Gigs of ram. I do photo editing with digikam, and have firefox going in the background, and listening to music on banshee, and so far i have never had to go into swap, and my ram hardly never exceeds 60%.

---

### Post by Jive Turkey on 2008-12-04
The point of x64 bit is to support the addressing of more than 4GB of memory and to run data through the CPU in bigger chunks, you might enjoy better performance with 64-bit due to the latter.

---

### Post by insane_alien on 2008-12-05
> **vipseixas said:**
> I read that 64 bits systems use more memory than 32 bits ones, because of the pointers size. Is that for real? Anyone knows how much is this?

yep, the most it'll ever take up is twice the amount that a 32-bit system would take. typically the increase is small only a few percent as not all data is pointers.

> 
I recently discovered that my Dell Vostro with AMD64 X2 processor only accepts up to 2GB of memory, which it already has. What a shame! Why they sell a 64 bits system with this limit???

it probably just means that you can't fit more than a single 2GB memory module into the motherboard. its a physical space limit rather than an electronic addressing issue.

> 
Anyway, I am concerned about memory because I run some memory intensive programs (a.k.a. Eclipse) and every byte is making a difference.

[]s!

Vinicius

you'll probably still be fine.

---

### Post by vipseixas on 2008-12-05
> **wfp said:**
> It uses a little more on my system than did the 32-bit. The difference did not have any issues with performance. I have 2Gigs of ram. I do photo editing with digikam, and have firefox going in the background, and listening to music on banshee, and so far i have never had to go into swap, and my ram hardly never exceeds 60%.

The problem is that I really use a huge amount of swap, look:

```

vseixas@vseixas-laptop:~$ ps -eo %mem,vsz,rss,comm --sort=-rss | head -11
%MEM    VSZ   RSS COMMAND
16.9 1655244 327324 java
13.4 972284 259400 firefox
13.4 917320 258504 java
13.3 884724 258024 java
 7.3 298748 141792 Xorg
 7.3 298748 141792 Xorg
 5.8 887784 111824 pidgin
 2.6 655072 50212 amarokapp
 2.4 624680 47824 thunderbird-bin
 1.8 462804 34984 nautilus
vseixas@vseixas-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1881       1867         13          0          1        101
-/+ buffers/cache:       1764        117
Swap:         2047       1151        896

```

The Java process are Eclipse, Tomcat & SQL Developer, at that order. And sometimes I have to run the Oracle server too...

I know that I can't get hid of swap usage, but if I can save some memory by using the 32 bits OS probably the performance gain for using less swap would be greater than the performace loss with the 32 bits addressing... That's what I am trying to find out. 

I will install Ubuntu 32 bits in another partition, compare the memory usage with the 64 bits install and I will let you know the results ;)

---

### Post by vipseixas on 2008-12-05
> **insane_alien said:**
> yep, the most it'll ever take up is twice the amount that a 32-bit system would take. typically the increase is small only a few percent as not all data is pointers.

I read an article that said that it can be between 5% and 10% more... If it is that much it will make a difference for me, since I have almost 3GB of memory usage (physical+swap, see my previous post).

> **insane_alien said:**
> it probably just means that you can't fit more than a single 2GB memory module into the motherboard. its a physical space limit rather than an electronic addressing issue.


It has 2 slots that support 1GB modules each (that's what the f* manual says). I think it is very strange that limit of 1GB, but I never tried to put a 2GB module there...

---

### Post by AndersAA on 2008-12-05
[http://code.google.com/p/compcache/](http://code.google.com/p/compcache/)

---

### Post by insane_alien on 2008-12-05
> **vipseixas said:**
> It has 2 slots that support 1GB modules each (that's what the f* manual says). I think it is very strange that limit of 1GB, but I never tried to put a 2GB module there...

its not as strange as you think, it depends on the northbridge of the motherboard IIRC.  some can only handle 1gb modules. this doesn't preclude the system of being 64-bit though. i recommend you get a machine with more grunt if you need to run all these applications so often. it would be a wise investment.

---

### Post by vipseixas on 2008-12-09
> **AndersAA said:**
> [http://code.google.com/p/compcache/](http://code.google.com/p/compcache/)

Man... This is awesome! \\:D/

I configured the compcache with 1GB compressed swap and everything is smoother now. This 1GB is using less then 300MB of real ram and my real swap lowered to 0.2GB.

I will still test the difference between 32bit and 64bit memory usage, but now I will wait till I buy my new HD :)

Thank you all!

---

### Post by AndersAA on 2008-12-09
If you get to the point where you use swap at all, configure it to use more than 1gb memory.  The overhead in my experience is very small, hell it's EXTREMELY small compared to using swap :)

---

### Post by battyice on 2008-12-10
I notice that my machine uses more memory with the 64bit version, especially when encoding video.  The performance is excellent and since my PC has 8gb of ram the increased memory usage hasn't been an issue.

---

### Post by Arup on 2008-12-11
x64 is for systems with 4GB or more memory, otherwise its useless to install x64. The advantage is that the 4GB then gets used properly and efficiently.

---

### Post by tribaal on 2008-12-11
I found that changing the swappiness value of the kernel greatly imprves performance in eclipse (and big java apps in general) with regards to swap.

Maybe you should try setting your swappiness to something lower than the default 60 (it's a percentage).

I use vm.swappiness=10

(just paste the following at the end of your /etc/sysctl.conf and reboot)
```
#Swappiness:
vm.swappiness=10

```

You can read extensive documentation on swappiness on the net, for example the link in my sig about linux memory usage.

Hope this helps!

- Trib'

---

### Post by stchman on 2008-12-11
> **vipseixas said:**
> I read that 64 bits systems use more memory than 32 bits ones, because of the pointers size. Is that for real? Anyone knows how much is this?

I recently discovered that my Dell Vostro with AMD64 X2 processor only accepts up to 2GB of memory, which it already has. What a shame! Why they sell a 64 bits system with this limit???

Anyway, I am concerned about memory because I run some memory intensive programs (a.k.a. Eclipse) and every byte is making a difference.

[]s!

Vinicius

Yes, I find that the 64 bit version uses approximately 40% more RAM.  Yes the pointers a lot bigger if the program was indeed coded for 64 bit OS.  That is OK, because you can have (usually) a lot more memory.

On your PC see if you can install 4GB RAM.  It could be that when that PC was made the largest memory modules were 1GB.  Maybe there is a BIOS flash for your DELL Vostro BIOS.  I agree that giving a 64 bit enabled machine a 2GB limit is ridiculous.

---

### Post by vipseixas on 2008-12-12
> **stchman said:**
> Yes, I find that the 64 bit version uses approximately 40% more RAM.  Yes the pointers a lot bigger if the program was indeed coded for 64 bit OS.  That is OK, because you can have (usually) a lot more memory.


Unfortunately you are right... I installed Intrepid 32bits yesterday on another partition and the memory usage is much less then the 64bits. Look at the memory usage with the same programs there were running when I first posted:

```

vseixas@vs-note:~$ free
             total       used       free     shared    buffers     cached
Mem:          1895       1815         80          0          5        264
-/+ buffers/cache:       1545        350
Swap:         2047        104       1943

```

2.8GB before and 1.6GB now (not counting the cache), it barely scratches the swap. And I am actually running a postgresql server now that I was not running before.

I am thinking that might be a memory leak in some 64bits libs, that's too much difference.

> 
On your PC see if you can install 4GB RAM.  It could be that when that PC was made the largest memory modules were 1GB.  Maybe there is a BIOS flash for your DELL Vostro BIOS.  I agree that giving a 64 bit enabled machine a 2GB limit is ridiculous.


My notebook is not more than 6 months old... I blame myself for no seeing that it was limited before :'( I will stick with 32bits anyway...

[]s!

Vinicius

---

### Post by vipseixas on 2008-12-12
> **tribaal said:**
> I found that changing the swappiness value of the kernel greatly imprves performance in eclipse (and big java apps in general) with regards to swap.

Maybe you should try setting your swappiness to something lower than the default 60 (it's a percentage).

I use vm.swappiness=10

(just paste the following at the end of your /etc/sysctl.conf and reboot)
```
#Swappiness:
vm.swappiness=10

```

You can read extensive documentation on swappiness on the net, for example the link in my sig about linux memory usage.

Hope this helps!

- Trib'

I actually tried swappiness 40 and then 10... But there is no much gain when you have 1.8GB of physical mem and a 2.8GB usage need... IMHO, swappiness will make a difference when you have memory left to trade between swap and buffers/cache.

[]s!

Vinicius

---

### Post by vipseixas on 2008-12-12
> **battyice said:**
> I notice that my machine uses more memory with the 64bit version, especially when encoding video.  The performance is excellent and since my PC has 8gb of ram the increased memory usage hasn't been an issue.

8GB??? I am daydreaming with this :D Maybe next year...

---

### Post by RicktheBrick on 2008-12-13
My computer which is running ubuntu 64 bit OS, has 4Gbytes of memory(2 2Gbyte sticks).  But when I go to system monitor the computer is telling me there is only 3.2Gbytes of memory. Am I losing .8Gbytes of memory?

---

### Post by cocokiwi on 2008-12-14
> **vipseixas said:**
> I read that 64 bits systems use more memory than 32 bits ones, because of the pointers size. Is that for real? Anyone knows how much is this?

I recently discovered that my Dell Vostro with AMD64 X2 processor only accepts up to 2GB of memory, which it already has. What a shame! Why they sell a 64 bits system with this limit???

Anyway, I am concerned about memory because I run some memory intensive programs (a.k.a. Eclipse) and every byte is making a difference.

[]s!

Vinicius
DOWNLOAD the latest BIOS!

ALL motherboards before this fix had a problem with memory. This was a problem with those whom wanted to use more than 3 gig which was XP 32 bit limit! 64bit versions had the same problem!
MS came out with a fix and soon after the BIOS's got the fix! I have had no more problems with 4 gig which I run! So if you have not updated your BIOS since you got the computer I would do so!:lolflag:

Regards and all the best: MERRY XMAS:popcorn:

Dennis):P

---

### Post by jheaton5 on 2008-12-14
> **cocokiwi said:**
> DOWNLOAD the latest BIOS!

ALL motherboards before this fix had a problem with memory. This was a problem with those whom wanted to use more than 3 gig which was XP 32 bit limit! 64bit versions had the same problem!
MS came out with a fix and soon after the BIOS's got the fix! I have had no more problems with 4 gig which I run! So if you have not updated your BIOS since you got the computer I would do so!:lolflag:

Regards and all the best: MERRY XMAS:popcorn:

Dennis):P

Will this fix allow 4gb to be installed when the product specs say the max is only 2gb?

---

### Post by Chame_Wizard on 2008-12-14
It doesn't really use allot of memory(i have only 1 GB).:guitar:

---

### Post by kris1351 on 2008-12-24
I am running a Vostro 1510, before I had 2GB on the 32bit system and never got into the swap. I have less running currently on a fresh load with 4GB of ram on the 64bit version and I am constantly swapping with nothing but Thunderbird and Firefox running.

---

### Post by tomdkat on 2008-12-24
> **kris1351 said:**
> I am running a Vostro 1510, before I had 2GB on the 32bit system and never got into the swap. I have less running currently on a fresh load with 4GB of ram on the 64bit version and I am constantly swapping with nothing but Thunderbird and Firefox running.Believe me, if you're running Thunderbird and Firefox you've got *a lot more* running than you would think:

X
Desktop environment (GNOME, KDE, whatever)
If GNOME, GNOME subsystem components

and so on...

How much swap does your system use on a fresh boot?  Maybe after a fresh boot you could open a terminal window and enter this command:

$ free

and post the output here.

EDIT:  Also, Thunderbird can use a TON of memory if you've got a LOT of main in your mail folder(s).  

Peace...

---

### Post by AndersAA on 2008-12-24
> **tomdkat said:**
> Believe me, if you're running Thunderbird and Firefox you've got *a lot more* running than you would think:

X
Desktop environment (GNOME, KDE, whatever)
If GNOME, GNOME subsystem components


I got xfce, all the gnome autostart stuff, pidgin, gnome-do, thunderbird, liferea, firefox beta, several daemons, a text editor and 2 custom python daemons up and running and I'm using 1gb on a 64bit system.

If your swapping with 2 applications up, check free -m / top / xrestop and find out whats leaking memory.

---


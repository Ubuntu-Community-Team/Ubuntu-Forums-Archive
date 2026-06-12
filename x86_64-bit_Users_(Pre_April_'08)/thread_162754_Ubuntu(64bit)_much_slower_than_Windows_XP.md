---
title: "Ubuntu(64bit) much slower than Windows XP"
date: 2006-04-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by spako on 2006-04-19
i've been using ubuntu for a number of weeks now but most times find it gets painfully slow compared to my dual boot windows xp. i've got the 64 bit version installed and was wondering whether it could be that; will a switch to 32bit speed up ubuntu? if so is there a big performance difference between kubuntu and ubuntu?

a good example of exactly how _much_ slower it is that windows xp is Eclipse. sometimes i have to wait while a document is being saved, a relativly simple task. i also avoid running a lot of applications similtaniously because of this.

(i've just posted this in the beginners forum when i realised it is probably more relavent to this forum, can a mod remove one of these please)

---

### Post by george.aprozeanu on 2006-04-19
I think your example is not necesarly relevant, because Eclipse runs on top of Java. Moreover, in ubuntu, Java depends by default on GIJ, which is a GPL implementation of Sun's virtual machine. There is a serious difference in performance between GIJ as Sun's VM. You can try that out by installing JDK from [http://java.sun.com](http://java.sun.com)

I've had both 64bit and 32bit versions of 5.10, 6.04 and XP and XP x64 and what i can tell you of the top is that there is little difference between them. However, I've decided to stick to 32 bit dapper, as there is far better support for applications there, and you can find significantly more applications that run in 32bit environments.

Java, especially, is traditionally a 32bit beast, with timid attempts, especially on the GIJ part to port to 64bits.

---

### Post by spako on 2006-04-19
i have the JDK/SDK (not sure which) from java.sun.com installed. i've noticed the slowness in other things too but will try note if its only when eclipse is running.

i've also noticed the 32bit is supported much more so think i will be making the switch. my next choice is kubuntu or ubuntu? besides differences in speed (which are probably negligible after the difference you stated between 32 and 64 bit), are programs supported in ubuntu?

i will re-post here if i notice a big difference when i install 32 bit.

thanks for the info

---

### Post by FluffyElmo on 2006-04-22
How much RAM do you have? I find 64bit generally faster, but applications use more memory than when running on 32bit. Eclipse in particular likes lots of RAM to play with. 

If you do have enough memory, try increasing the amount of memory you give Eclipse when starting, it may solve you problems with that application at least.

---

### Post by spako on 2006-04-22
Recently spoke to a more experianced linux friend and my problem is RAM as I only have 512mb... I know eclipse have about a 300MB footprint in the RAM so should be able to run in smoothly if it dosen't use swp space (i'm assuming a few things here).

i'd like to solve the speed, how would i start eclipse with more RAM?

---

### Post by spako on 2006-04-22
I didn't find a RAM parameter for the eclipse executable so I suppose its a java thing to set the RAM? or is it a setting in ubuntu?

i've changed the process priority to -10 so i think that might help. also checked and my eclipse is running with a +/- 410MB footprint.

if you have any techniques to let me make sure that a minimum amount is always run off the RAM pls do tell!

thanks!

---

### Post by ronacc on 2006-04-22
I dont know about eclipse but I can tell you that on my amd64 box internet explorer (ie4linux + wine) loads pages and renders them  noticeaby FASTER than running natively under windowsXP (sp2) on the same box. I find this strange but I can attest that its true. and with a gig of ddr and an fx5200 nvidia card XP isnt starved for resources .

---

### Post by warp99 on 2006-04-24
I installed amd64 using reiserFS (notail and noatime enabled) and my 3400 loads about 50% faster than XP. Under dual boot XP would thrash on the hard driver hitting the swap file, even with a gig of ram. I can run a virtual XP session FASTER in VMPlayer then with XP stand alone.

Set up correctly ubuntu destroys XP in speed. My 5 year old daughter even notices the difference. :cool:

---

### Post by Grinning Fool on 2006-05-02
I had this problem as well, it was not memory -- even though you have the Sun JVM installed, Eclipse is hard-wired to use gij-4.1 .  Unfortunately, Eclipse is essentially unusable under that JVM (IME). 

To correct, launch eclipse as follows: 
eclipse -vm /usr/lib/j2sdk1.5-sun/bin/java 

(Update path above depending on which version of the JVM you have installed) 

That should take care of your performance issues.

---

### Post by george.aprozeanu on 2006-05-04
When using the default eclipse (packaged in ubuntu) you can use /etc/eclipse/java_home to tell eclipse where to scan for a JDK.

You can also set the ram size occupied by eclipse in eclipse.ini. For the ubuntu eclipse, you can use /usr/share/eclipse/eclipse.ini

---

### Post by spako on 2006-05-04
thanks for the tips on speeding up eclipse. i use a version of eclipse from the eclipse site. didn't know it was bundled. think this will make for a better working experiance.

am soon to get another gig of ram so hopefully that will help to. there is another app that is very slow, krusader, but i've heard that it isn't totally stable and it is built for kde. will see how the ram helps this though.

---

### Post by panurge77 on 2006-05-20
[QUOTE=warp99]I installed amd64 using reiserFS (notail and noatime enabled) and my 3400 loads about 50% faster than XP. Under dual boot XP would thrash on the hard driver hitting the swap file, even with a gig of ram. I can run a virtual XP session FASTER in VMPlayer then with XP stand alone.

Set up correctly ubuntu destroys XP in speed. My 5 year old daughter even notices the difference. :cool:[/QUOTE]

I'd be glad to know how did you "Set up correctly ubuntu" :-k 
My ubuntu is still 5 times slower than xp in booting up. And I have tried prelink, preload and disabling unused services from kernel...  That did a very little difference. Is reiserfs a big deal in this?

---

### Post by warp99 on 2006-05-22
[QUOTE=panurge77]I'd be glad to know how did you "Set up correctly ubuntu" :-k 
My ubuntu is still 5 times slower than xp in booting up. And I have tried prelink, preload and disabling unused services from kernel...  That did a very little difference. Is reiserfs a big deal in this?[/QUOTE]

ReiserFS with notail and noatime enabled makes a HUGH speed difference over ext3, especially with smaller files. According to this Wiki ReiserFS small file performance, files under 4K, is faster by a factor of 10-15.

[http://en.wikipedia.org/wiki/ReiserFS#Performance]("http://en.wikipedia.org/wiki/ReiserFS#Performance") 

When you say slower in booting your saying from turning on the machine until a useable desktop, correct? You have to remember that XP only loads a minimum of components in kernel space. XP is trying to get to the desktop ASAP so you "think" it's running faster, but once you start running in user space XP just gets loaded down.

The biggest speed difference is during the loading of applications and processing instructions. Applications load and execute at least 50% faster, except for maybe OpenOffice. By the way I'm using Kubuntu, but that shouldn't matter since only the desktop is different.:cool:

---

### Post by skippy81 on 2006-05-22
I think linux could beat the XP boot, if it wasnt for all the useless kernel modules getting loaded.  I would really like to know how to pull the things out.  

For example I have tsdev module loaded, which appears to be for touchscreens.  I dont have a touchscreen.  I can pull out the module with modprobe -r, but It just comes back at next boot up.

---

### Post by warp99 on 2006-05-22
[QUOTE=skippy81]I think linux could beat the XP boot, if it wasnt for all the useless kernel modules getting loaded.  I would really like to know how to pull the things out.  

For example I have tsdev module loaded, which appears to be for touchscreens.  I dont have a touchscreen.  I can pull out the module with modprobe -r, but It just comes back at next boot up.[/QUOTE]

Well, you can recompile the kernel without certain modules. It's not that differcult and the instructions are somewhere in the wiki. :cool:

---

### Post by warp99 on 2006-05-22
Found it!!! 8) 

[https://wiki.ubuntu.com/KernelCompileHowto?highlight=%28kernel%29%7C%28compile%29]("https://wiki.ubuntu.com/KernelCompileHowto?highlight=%28kernel%29%7C%28compile%29")

---

### Post by Ribs on 2006-05-24
Recompile your kernel? No need for such hard work... just blacklist the modules you don't want, then they will never load, regardless of what hardware you have...

This has the major advantage of still being able to use offical kernels, which will have security updates, and the changes will stay in affect throughout kernel upgrades.

See here:
[http://ubuntuforums.org/showthread.php?t=166624](http://ubuntuforums.org/showthread.php?t=166624)

---

### Post by Kuprin on 2006-05-27
Grinning Fool - where did you get your Eclipse install, that it's hard-wired to use gij? Mine runs using Sun without any trouble, all I did was pull it from the Eclipse site. Is there a package in one of our repositories for Eclipse, which is hardwired for gij, or am I seeing funny Sun symbols in the backs of my eyes and it's just running gij with no problems?

---

### Post by Grinning Fool on 2006-05-31
When you do a "ps -A", you see "java" and not "gij"?   I got mine from Synaptic, which'd probably explain the difference.  It wasn't a big deal, as I was able to switch it over to the Sun JVM (with a bit of perseverance), once I realized how badly gij was doing.

---

### Post by george.aprozeanu on 2006-05-31
It depends what Java package you are using in ubuntu. Eclipse depends by default on gij, but if you install blackdown j2se, and then try to remove gij it will work, because eclipse can also depend on that package.

However, both are 1.4.2's and I usually need 5.0, so custom eclipse + custom sdk is the way to achieve this.

---

### Post by jkroto on 2006-12-07
> **ronacc said:**
> I dont know about eclipse but I can tell you that on my amd64 box internet explorer (ie4linux + wine) loads pages and renders them  noticeaby FASTER than running natively under windowsXP (sp2) on the same box. I find this strange but I can attest that its true. and with a gig of ddr and an fx5200 nvidia card XP isnt starved for resources .

How did you get ie4linux + wine to work in 64-bit?

EDIT: nevermind, got it working, if you still want to know how I wrote it up [here](http://www.ubuntuforums.org/showthread.php?p=1860514#post1860514).

---


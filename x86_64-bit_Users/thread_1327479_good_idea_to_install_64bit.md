---
title: "good idea to install 64bit?"
date: 2009-11-15
forum: x86 64-bit Users
---

### Post by mr clark25 on 2009-11-15
i was wondering if it would be a good idea to install 64bit Ubuntu. how hard would it be? does it require a totally new install? or is there a simpler way? i beleive i am running 32bit on a core2 duo E4300. would i notice much of a performance boost? if it does require a totaly new install, could i copy my /home/ directory to another partition and then paste it back to have all of my old files,settings, and programs back?

just wondering if using 64bit would be a good idea, and i might be using 64bit already... how do you check this?

---

### Post by garvinrick4 on 2009-11-15
Type "sysinfo" without qoutes at command line.

Is one way.  If tells you to download do-it, nice to have around.

---

### Post by oldos2er on 2009-11-15
The installation process is the same whether you're installing 32- or 64-bit. You'd need to do a new install.

 To see if your current kernel is 64-bit, run **uname -a** in a terminal. You should see something like this: 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64 GNU/Linux. Note the bit at the end, x86_64.

---

### Post by sanderj on 2009-11-15
> **mr clark25 said:**
> i was wondering if it would be a good idea to install 64bit Ubuntu. how hard would it be? does it require a totally new install? or is there a simpler way? i beleive i am running 32bit on a core2 duo E4300. would i notice much of a performance boost? if it does require a totaly new install, could i copy my /home/ directory to another partition and then paste it back to have all of my old files,settings, and programs back?

just wondering if using 64bit would be a good idea, and i might be using 64bit already... how do you check this?

64-bit is useful if you have more than 3GB RAM on a 64-bit capable platform. Run the python script on [http://ubuntuforums.org/showpost.php?p=8284040&postcount=11](http://ubuntuforums.org/showpost.php?p=8284040&postcount=11) to get all information you need.

However, it seems even that advantage is gone with Ubuntu 9.10; the 32-bit Ubuntu seems to be able to access more than 3 GB using the PAE kernel.

Apart from that, 64-bit has a coolness factor. And yes, by saving /home to a separate partition, you can do a fresh 64-bit install.

HTH

---

### Post by lemming465 on 2009-11-15
In general 64-bit increases performance and decreases compatibility.  If you have lots of memory and are running intensive workloads such as scientific, database, multimedia encoding or virtual guest OS's then you should strongly prefer 64-bit. You may see speeds ups of 15-30% for a variety of arcane reasons (access to more CPU registers, shallower page tables, direct access to high memory, more aggressive use of modern instructions, ...).

Most (but not all) free/open source code is 64-bit clean at this point.  However, a lot of binary 3rd-party proprietary stuff is not.  Running things like multimedia playback, flash video, adobe reader, etc. will get harder.  If you don't want to put time into troubleshooting such issues, stick with 32-bit.

---

### Post by PGHammer on 2009-11-15
> **sanderj said:**
> 64-bit is useful if you have more than 3GB RAM on a 64-bit capable platform. Run the python script on [http://ubuntuforums.org/showpost.php?p=8284040&postcount=11](http://ubuntuforums.org/showpost.php?p=8284040&postcount=11) to get all information you need.

However, it seems even that advantage is gone with Ubuntu 9.10; the 32-bit Ubuntu seems to be able to access more than 3 GB using the PAE kernel.

Apart from that, 64-bit has a coolness factor. And yes, by saving /home to a separate partition, you can do a fresh 64-bit install.

HTH

I find 64-bit useful if you have a 64-bit-capable platform *regardless* of whether you have 4 GB of RAM or not, and even whether you run FOSS or not.  Starting with the much-maligned Vista 64-bit (and later going back to even XP64), I did some usability tests comparing 32-bit and 64-bit versions of the same operating system.

The issues with 64-bit, regardless of operating system and even regardless of system memory, fall into three categories - hardware/driver support, application support, and browser plug-in/add-in support.  Once you get past those hurdles, 64-bit makes sense for stability reasons over 32-bit, even (in fact, especially) if you have between 1 and 3 GB of RAM.

---

### Post by mr clark25 on 2009-11-15
ok, thanks. i am running 32bit, and plan to install 64bit soon. i am a little worried because the file name is "ubuntu-9.10-desktop-amd64" i have an Intel CPU... or will it still work? i just wanted to double check because i dont want to mess up my system...

---

### Post by Nburnes on 2009-11-15
> **mr clark25 said:**
> ok, thanks. i am running 32bit, and plan to install 64bit soon. i am a little worried because the file name is "ubuntu-9.10-desktop-amd64" i have an Intel CPU... or will it still work? i just wanted to double check because i dont want to mess up my system...

AMD or Intel, it doesn't matter. It is just what they chose to name the iso.

---

### Post by mr clark25 on 2009-11-16
how do you install it without burning it to a disk? i don't really want to waste a cd...

i know that there is a way in windows, but is there a way in ubuntu? i tried opening the .exe file with wine, but it didn't work...

---

### Post by jocko on 2009-11-16
> **mr clark25 said:**
> how do you install it without burning it to a disk? i don't really want to waste a cd...

i know that there is a way in windows, but is there a way in ubuntu? i tried opening the .exe file with wine, but it didn't work...
If you have a USb memory, you can make a bootable usb from the image. System-->Administration-->Create a bootable USB device.

---

### Post by lemming465 on 2009-11-16
The reason it's often called "AMD64" is because back in the 1999-2003 period intel was pushing "itanium" as its 64-bit solution.  Unfortunately, those CPU chips were large, late, thermally hot, and ran 32-bit x86 code in emulation exceedingly sluggishly.  AMD designed 64-bit extensions to x86, and shipped it first.  Intel adopted a compatible set shortly thereafter.  Most (but not all) recent x86 chips support the 64-bit extensions.

---

### Post by blueridgedog on 2009-11-16
> **mr clark25 said:**
> ok, thanks. i am running 32bit, and plan to install 64bit soon. i am a little worried because the file name is "ubuntu-9.10-desktop-amd64" i have an Intel CPU... or will it still work? i just wanted to double check because i dont want to mess up my system...

I did a clean install of 64 bit 9.10, from a working 32 bit 8.10.  Flash was the only issue and I was able to get it working with the alpha flash player from Adobe (instruction in this forum).  I had one issue with a 32 bit library that I needed for Floola.  All other software works as good or better under 64 bit and installed with ease.

---

### Post by 3Miro on 2009-11-16
If you have a working 32-bit system and don't run very CPU intensive jobs, you have no reason to switch.

If you are making a clean install anyway, might as well go for 64-bit. 32-bit flash works clean and there is a 64-bit copy that you can install relatively painlessly. In general 32-bit software works under 64-bit Linux without any problems. The only possible issue are some drivers, check with the liveCD for possible problems.

---

### Post by mr clark25 on 2009-11-17
i have decided to stay with 32bit for 2 reasons: 1.it would take 7 hours to transfer all of my files to another system.(25GB at 10mb/s) the installation doesnt have the option to install to the partition that already has ubuntu on it. 2.im not doing to many CPU-intensive tasks.(other than an online game called Runescape, which still doesnt take that much) runescape runs just fine in 32bit.

so i will stay with 32bit.

all of this isnt going to waste ,though. i will be building a core i7 setup soon that i will put 64bit on after i get done overclocking. (off topic: is overclocking worth it? i have heard that you dont get much more performance in ubuntu... i will make a thread in general help if i cant find any others like what i will post)

thanks for all the help.

---


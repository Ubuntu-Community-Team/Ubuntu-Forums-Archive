---
title: "Will Photoshop be able to acces &gt;4GB ram?"
date: 2008-11-16
forum: x86 64-bit Users
---

### Post by rust001 on 2008-11-16
If I install 64 bit ubuntu on my laptop and run photoshop CS3 through wine, will photoshop be able to take advantage of all the ram?

Basically I've quite wanted to move over to fully using linux for a while, but the performance hit of running ps through wine has always put me off. However, I've just realised that my laptop can support a 64 bit operating system and I'm curious to know if the performance drop of wine would be balanced out by access to the full 4GB of ram.

At the moment I only have 2GB of ram, but the plan would be upgrade to 4 - at which point my 32 bit vista would see about 3 or 3.5GB - and then run 64 bit linux.

Is there any logic to that?

Cheers,
James

---

### Post by cariboo on 2008-11-16
If you use Photoshop to make a living, stick with Windows, maybe upgrade to a 64bit version. If Photoshop isn't that important, then give it a try in Wine running on the 64bit version of Ubuntu.

Jim

---

### Post by tuxxy on 2008-11-16
You will be able to access 4 GB+ of RAM running 64-bit Ubuntu and also will see noticeable performance increases in video/photo editing using 64-bit

---

### Post by psusi on 2008-11-16
No, since photoshop will still be only 32 bit.  You could use the 64 bit build of GIMP though instead.

---

### Post by Rodney9 on 2008-11-16
I use Gimp 2.6.1 in Ubuntu 8.10 64Bit with 8Gb ram and it is very very quick.

---

### Post by Jive Turkey on 2008-11-16
I could be wrong but I don't think wine can run PS.  I have a winXP virtual machine with PS installed though and that works, but I only have 1.5GB of ram reserved for the VM, It works ok but if I needed PS for heavy lifting I would dual-boot.  If you have more than 4GB ram you could try having a VM with >4GB

---

### Post by TheSamurai on 2008-11-17
if you're currently using photoshop in 32 bit xp it's only using about ~2gb as is. you need to edit the boot.ini file to include a switch to allow use of the ram by applications.

[http://www.microsoft.com/whdc/system/platform/server/PAE/PAEmem.mspx](http://www.microsoft.com/whdc/system/platform/server/PAE/PAEmem.mspx)

as for 64 bit linux, i'm not sure. it takes a bit of work to even get it to run within wine. i keep windows on another harddrive and boot to that when i require heavy editing, otherwise i'll just use gimp for the basics.

*edit
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584)

---

### Post by felker2 on 2008-11-17
Based on the info on [http://www.adobe.com/products/photoshop/photoshop/faq/?promoid=DRHXB](http://www.adobe.com/products/photoshop/photoshop/faq/?promoid=DRHXB) on Photoshop **CS4**:

> Does Photoshop CS4 support native 64-bit processing?
Photoshop CS4 for Microsoft® Windows Vista® runs 64-bit native.

Will previous versions of Photoshop receive an update for 64-bit native support?
No, 64-bit native support will not be available for previous versions of Photoshop.


I would say photoshop **CS3** is a 32-bit application and running it on a 64-bit OS (Linux or Windows) will **not **give 64-bit advantages like using 4+ GB memory


HTH

---

### Post by TheSamurai on 2008-11-17
> **felker2 said:**
> Based on the info on [http://www.adobe.com/products/photoshop/photoshop/faq/?promoid=DRHXB](http://www.adobe.com/products/photoshop/photoshop/faq/?promoid=DRHXB) on Photoshop **CS4**:




I would say photoshop **CS3** is a 32-bit application and running it on a 64-bit OS (Linux or Windows) will **not **give 64-bit advantages like using 4+ GB memory


HTH

i don't think the OP is concerned about 4+... just using the ~3.5 that comes with using 32 bit systems. wine can only utilize 32 bit apps anyhow so 4+ isn't going to happen as it sits now.

---

### Post by felker2 on 2008-11-17
> **TheSamurai said:**
> i don't think the OP is concerned about 4+... 

Well, the OP's subject is "Will Photoshop be able to acces >4GB ram?".

---

### Post by TheSamurai on 2008-11-20
> **felker2 said:**
> Well, the OP's subject is "Will Photoshop be able to acces >4GB ram?".

very true! i was basing that statement on his post. :)

---

### Post by C. Wizard on 2008-11-20
Photo Shop runs very well in CrossOver, which, in turn, is built on WINE.

---

### Post by dv-design on 2008-11-21
Im new to Ubuntu and thus linux, but i think the answer is kind of...

CS3 is not 64-bit, so you will not see better performance with it being in a 64bit environment. If i recall from a post i vaguely recall on adobes site, it will be able to use more then 3gb's but not all for one process.

What you will see a difference in, is that your system will better utilize the memory and the OS should run faster on 64bit. In turn this should run CS3 faster.

To compare it, lets say your system was 3gb on a 32bit os, and you ran CS3...some of that 3gb would have to be used by the system and other functions. Even if you had more ram physically installed the max ram available to everything would only be 3gb's total.

Now lets say that same OS is 64bit and you have more then 3gb's of actual ram, hypotheticlly 4gb's lets say. Now your OS can utilize all 4gb's properly, meaning more ram availible to other non os process's even if those apps are 32bit. So the available ram to CS3 will be upto but not exceeding 3gb's for each process.

This is my understanding from what i have learned, read, and heard others say...that doesnt mean its right, but i hope it helps.

**From what ive read though running CS3 in Linux using some kind of emulator (not sure if this is the right term) like Wine will get the job done for small jobs, but will not cut it for proffessional use.**

---

### Post by jespdj on 2008-11-21
As far as I know, Photoshop **CS3** does not install on WINE. CS2 does, but not CS3.

---


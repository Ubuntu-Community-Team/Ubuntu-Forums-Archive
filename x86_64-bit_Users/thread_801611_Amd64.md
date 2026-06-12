---
title: "Amd64"
date: 2008-05-20
forum: x86 64-bit Users
---

### Post by Exsecrabilus on 2008-05-20
On my HP Pavilion dv5000 laptop, there is a tag that reads:

> AMD Turion64: Mobile Technology

This means I am capable of running 64-bit Ubuntu.

But I only have 1 GB of RAM, and I read somewhere Ubuntu amd64 was for people who have 4+ GB of RAM.

So here are my questions:

1) Since I only have 1 GB of RAM, will it make a difference in speed and performance?

2) If your computer isn't capable of 64-bit, what will happen? I am kinda confused here. Will your computer just crash or something when you try to install it?

---

### Post by Sef on 2008-05-20
> 1) Since I only have 1 GB of RAM, will it make a difference in speed and performance?

2) If your computer isn't capable of 64-bit, what will happen? I am kinda confused here. Will your computer just crash or something when you try to install it?

1) If you do a lot of graphic intensive applications (movie editing, and gaming for example) it will make a difference.  Otherwise not much. The 4 gb

2) If you don't have a 64-bit computer, it will just not install.

3) Update: > But I only have 1 GB of RAM, and I read somewhere Ubuntu amd64 was for people who have 4+ GB of RAM.

32-bit systems can only read about 3.7 gb of ram.  64-bit systems can read up to [16.8 tetrabytes]("http://en.wikipedia.org/wiki/64-bit").

---

### Post by saratchandra on 2008-05-21
Don't worry, I have only 768 mb of RAM and never experianced any performance problems.

---

### Post by Exsecrabilus on 2008-05-21
> **saratchandra said:**
> Don't worry, I have only 768 mb of RAM and never experianced any performance problems.
You run Ubuntu 8.04 LTS Hardy Heron 64-bit version?

---

### Post by saratchandra on 2008-05-21
> **Exsecrabilus said:**
> You run Ubuntu 8.04 LTS Hardy Heron 64-bit version?

Yes and I've never had any problems.

---

### Post by Kilz on 2008-05-21
> **saratchandra said:**
> Yes and I've never had any problems.

The ability to use more ram is a nice feature, but at 1 gb the 64bit version of Ubuntu will work just fine. You will also have the ability to make full use of that hardware. Applications like encoders and 3d modeling programs like Blender will show up to a 30% performance boost, but ymmv.

---

### Post by p_o_x on 2008-05-21
I'm running 64 bit 8.04 no problems.

AMD turion 64, 2GB ram. dv6000 though...

8.04 screams on my machine :D

---

### Post by Mortosa on 2008-05-21
I have ran 64bit unbuntu in VM before with only 768mb of ram allocated to it. 

I had found out that if you use vmware program and enable a certain feature in your bios then it will allow 64bit VMs.

---

### Post by markbuntu on 2008-05-23
I have 3GB ram and am running 64but Ubuntu and my system monitor rarely 1GB of memory used and never uses the swap partition. I am wondering if it was a waste of money to buy all that ram.

You probably have and on board video driver and that uses probably 256m of your ram max but that should not be a problem.

The only problems you will run into are if you have ALL the desktop visual effects enabled and are spinning the cube with compiz while streaming an internet radio station and watching youtube videos in firefox and burning a cd. Then things might run a little slow.

---

### Post by Exsecrabilus on 2008-05-24
> **Mortosa said:**
> I have ran 64bit unbuntu in VM before with only 768mb of ram allocated to it. 

I had found out that if you use vmware program and enable a certain feature in your bios then it will allow 64bit VMs.
Explain. What is VMs?

---

### Post by jespdj on 2008-05-24
> **Exsecrabilus said:**
> Explain. What is VMs?
Virtual Machine. You can use software like VirtualBox or VMWare to run an operating system in a virtual machine. See the [virtualization forum]("http://ubuntuforums.org/forumdisplay.php?f=308").

---

### Post by pixel :-) on 2008-05-24
1G is ok,i have 1.5G.Just make sure that you will install swap, so that you can survive the peak times,or a crazy proses.In 64 bits theirs a slite overhead with memory, because the adresses are longer, but this is negligible.Give it a try dude :guitar:

---

### Post by OmegaBLK on 2008-05-24
> **Sef said:**
> 
32-bit systems can only read about 3.7 gb of ram.  64-bit systems can read up to [16.8 tetrabytes]("http://en.wikipedia.org/wiki/64-bit").

Actually if you use the HIGHMEM kernel, a 32-bit Linux system can use up to 64GB of RAM if the processor supports PAE.  Each process is limited to under 4GB though.  Same with most versions of Windows (except XP w/SP2, not sure about SP3 or 32-bit Vista; check the second link at the bottom of my post for more info); they do not have this limitation if using PAE also.  

[http://kerneltrap.org/node/2450](http://kerneltrap.org/node/2450)
[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---


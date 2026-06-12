---
title: "Can I load 8GB of ram for Feisty 64bit version?"
date: 2007-07-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by funrider on 2007-07-15
I know this is sound crazy but Ram is kinda cheap nowadays. I would like to run multiple VM on my system so actually I can fully use them. Does anyone know if 64bit version of Fiesty support 8GB of ram or more out of the box? Thanks in advance!

---

### Post by stmiller on 2007-07-15
The 64bit Linux kernel can support up to 64GB of memory, I believe. So yes.

---

### Post by koshcu on 2007-07-15
Yeah it works great. I have 8GB of ram on this box using dual opterons and 64bit kubuntu is working great.

---

### Post by funrider on 2007-07-15
thanks koshcu and stmiller! Hey koshcu, how is the performance of 8GB ram and would you like to share your configuration with me please?

---

### Post by avik on 2007-07-15
> **stmiller said:**
> The 64bit Linux kernel can support up to 64GB of memory, I believe. So yes.

Actually, it supports 2^64 bits of memory.  So take 4GB in bytes (2^32, the amount supported by a 32bit system), square it, and you have the amount of RAM supported by a 64bit kernel.  That's 16 exabytes of RAM, or 17179869184GB.  You won't be hitting that limit soon!

---

### Post by stmiller on 2007-07-16
^Yeow! That's crazy. Well perhaps 64bit CPUs will be stable and the norm for a long time then. That would be great.

---

### Post by jespdj on 2007-07-16
> **avik said:**
> Actually, it supports 2^64 bits of memory.  So take 4GB in bytes (2^32, the amount supported by a 32bit system), square it, and you have the amount of RAM supported by a 64bit kernel.  That's 16 exabytes of RAM, or 17179869184GB.  You won't be hitting that limit soon!

A 64-bit processor can *in principle* support 2^64 **bytes** (not bits) of memory, but the current processors that support AMD64 or EM64T (Intel's version of AMD's 64-bit extensions) support an address space of "only" 2^48 bytes. This is still 256 TB (262,144 GB), which will be more than enough for the forseeable future.

64-bit Windows XP supports up to 128 GB, 64-bit Windows Server 2003 up to 1 TB (1,024 GB) RAM.

For more info see [x86-64 (Wikipedia)](http://en.wikipedia.org/wiki/X86-64).

---

### Post by misfitpierce on 2007-07-16
Also it isnt even necessary to have 8 gig of ram atm in my opinion. But it does not hurt to be prepared for future unless you running like 40 streaming movies and 100 editing programs at once on like 8 monitors... but w/e :) lol

---

### Post by koshcu on 2007-07-16
I am using a Tyan S2915 board

[http://tyan.com/product_board_detail.aspx?pid=163](http://tyan.com/product_board_detail.aspx?pid=163)

I have 8 1GB ram modules in it and dual 2218 opterons. I also have dual 8800GTS cards in it and an audigy 2 ZS sound card in it. Everything works flawlessly under linux. I can't think of any performance issues I have had with it. I did use envy to install the nvidia drivers for my cards since the default ubuntu does not support them yet but that was easy.

I really like this nforce professional design that the board uses. Go look at the wiring diagram for the board and see how the board is laid out, it has very nice IO.

---

### Post by avik on 2007-07-17
> **jespdj said:**
> A 64-bit processor can *in principle* support 2^64 **bytes** (not bits) of memory, but the current processors that support AMD64 or EM64T (Intel's version of AMD's 64-bit extensions) support an address space of "only" 2^48 bytes. This is still 256 TB (262,144 GB), which will be more than enough for the forseeable future.

Whoops.  I did mean bytes.

And yes, that is the theoretical amount supported, but no implementation of 32bit will be able to access more than 4GB.

Thanks for the corrections.  I should get more RAM just to justify my running 64bit Ubuntu!  :)

---

### Post by jespdj on 2007-07-17
> **misfitpierce said:**
> Also it isnt even necessary to have 8 gig of ram atm in my opinion. But it does not hurt to be prepared for future unless you running like 40 streaming movies and 100 editing programs at once on like 8 monitors... but w/e :) lol
It depends on what you do with your computer. If you're just using it as a desktop computer to surf on Internet and use e-mail then you don't need a lot of memory ofcourse.

If you want to run multiple operating systems at the same time, for example with VMWare or Virtual Box, then you need a lot of memory, and I can imagine that you would want more than 4 GB and a multi-core processor.

---

### Post by avik on 2007-07-18
> **jespdj said:**
> It depends on what you do with your computer. If you're just using it as a desktop computer to surf on Internet and use e-mail then you don't need a lot of memory ofcourse.

You need it for bragging rights!  :)  Not to mention Firefox's memory issues...

---

### Post by jaffamuffin on 2007-07-18
> **misfitpierce said:**
> Also it isnt even necessary to have 8 gig of ram atm in my opinion. But it does not hurt to be prepared for future unless you running like 40 streaming movies and 100 editing programs at once on like 8 monitors... but w/e :) lol

The OP intends to run virtualisations. That's only 4 2 GB machines, or 8 1 GB machines, or 16 512Meg machines, or .... See?

---

### Post by wangrui on 2008-02-29
Hi,

I don't know whether it's the right place to ask this question. But I really want to know whether a 32bit ubuntu can support 8GB memory. I really need a lot of memory to process text data. And I'm planning to purse a 8GB machine.  But I don't want to abandon the old 32-bit system which I used a lot of time to setup. And I don't really know if every tools under ubuntu has a 64-bit version (Actually I only need JVM which has no problem, but I hope all other useful commands can still be able to run)

I know it sound stupid because somebody said 32bit can only support 4GB memory. But when I in unversity I learned from book that 386 chipset can support up to 64TB memory. The address can only be 32 bit but there is also a segment selector which can extend it many times. And all of the servers in the company has 16GB memory. Once I found a empty server with 14GB memory left and try to run a java program, but the JVM can only use 1.6GB memory which is not enough. So I tried to install a 64 bit JVM to the server but failed. Which means the server has 16GB memory but install a 32bit RedHat. And I also I remember I installed 32bit JVM to serveral other servers which also has 16GB memory. And of course 90% of the memory of these server are in use.

So I really hope someone has experience to confirm whether a 32 bit ubuntu can support 8GB or not. Thanks in advance!

---

### Post by Kilz on 2008-02-29
> **wangrui said:**
> Hi,
**So I really hope someone has experience to confirm whether a 32 bit ubuntu can support 8GB or not. Thanks in advance!**

The standard 32bit Ubuntu desktop install can not see that much ram.

---

### Post by wangrui on 2008-02-29
Hi Kilz,

Thank you for the quick reply. Actually I found some article talking about this:

[http://kerneltrap.org/node/2450?page=1](http://kerneltrap.org/node/2450?page=1)

If I remember correctly. 386 CPU can support 64T memory. But 32 bit Linux can only support 64GB memory. And each application can only use 4GB memory. Actually I don't mind to split my program into several 32 bit processes to be able to use all memory. But I don't think 64 bit ubuntu is a workable solution. The problem is, the latest Intel P35 chipset can only support 8GB memory. If I bought 8GB memory and use 64 bit ubuntu, I can only handle the same data size as 32 bit ubuntu 4GB memory. The reason is because I use memory to store a large quantity of tiny data structures. Large text data will be put onto hard disk, but in memory most of them are pointers.  If upgraded to 64 bit, all 32bit pointer will become 64bit, and the program will need twice the memory. If I bought 4GB extra but can't process more data, why should I bother?

I wish there is a 40bit operating system, which will maximum the data handling ability. But so sad there isn't. Maybe we can only stick to 32bit but use 16 separate process to process data. And change to 64bit until the motherboard can handle more than 64GB.

I think I will make a survey and find some patch to enable 32 bit ubuntu using 8GB memory.

Thanks everybody for the information anyway.

---

### Post by Kilz on 2008-02-29
> **wangrui said:**
> Hi Kilz,

Thank you for the quick reply. Actually I found some article talking about this:

[http://kerneltrap.org/node/2450?page=1](http://kerneltrap.org/node/2450?page=1)

If I remember correctly. 386 CPU can support 64T memory. But 32 bit Linux can only support 64GB memory. And each application can only use 4GB memory. Actually I don't mind to split my program into several 32 bit processes to be able to use all memory. But I don't think 64 bit ubuntu is a workable solution. The problem is, the latest Intel P35 chipset can only support 8GB memory. If I bought 8GB memory and use 64 bit ubuntu, I can only handle the same data size as 32 bit ubuntu 4GB memory. The reason is because I use memory to store a large quantity of tiny data structures. Large text data will be put onto hard disk, but in memory most of them are pointers.  If upgraded to 64 bit, all 32bit pointer will become 64bit, and the program will need twice the memory. If I bought 4GB extra but can't process more data, why should I bother?

I wish there is a 40bit operating system, which will maximum the data handling ability. But so sad there isn't. Maybe we can only stick to 32bit but use 16 separate process to process data. And change to 64bit until the motherboard can handle more than 64GB.

I think I will make a survey and find some patch to enable 32 bit ubuntu using 8GB memory.

Thanks everybody for the information anyway.

To my knowledge, you would need to recompile a kernel with pae to access over 4 gb. If upgraded to 64 bit, you might consider running a 32bit application on a 64bit install. This would make the processor run in 32bit mode and should have the advantage of seeing the 8gb or ram and 32bit pointer should be 32bit. Though I seem to remember that the idea of 64bit using twice as much ram has been proven false on more than one occasion.

---

### Post by wangrui on 2008-02-29
Hi Kilz
Thanks very much for the information. If 64-bit ubuntu can run 32-bit programs. Then I will definitely move to 64bit. 

About the memory issue, in fact only pointer size is doubled in 64bit. If the program don't has too much pointers. For example, if you allocate all memory at once and managed them yourself. There won't be any difference. But if all data is small, in my case, the average length of the data which a pointer carrying is even less then 8 bytes. And another example is to build a char tree in memory, which the pointer size is 8 bytes but the data is only 2 bytes. Then the application will use almost twice as much memory if moved to 64 bits.

For normal users, which their application cached a lot of large sequence data, will not see much difference between 32 bit and 64 bit. But for us, we are doing research works and the algorithms have already been optimized many time, which unfortunately makes most of our code don't put large sequence data in memory but use a lot of pointers. Such pointer upgrade will make the assumption fail, and may need us to work out new algorithms to replace old one to maximum the performance.

---

### Post by Kilz on 2008-02-29
> **wangrui said:**
> Hi Kilz
Thanks very much for the information. If 64-bit ubuntu can run 32-bit programs. Then I will definitely move to 64bit. 

About the memory issue, in fact only pointer size is doubled in 64bit. If the program don't has too much pointers. For example, if you allocate all memory at once and managed them yourself. There won't be any difference. But if all data is small, in my case, the average length of the data which a pointer carrying is even less then 8 bytes. And another example is to build a char tree in memory, which the pointer size is 8 bytes but the data is only 2 bytes. Then the application will use almost twice as much memory if moved to 64 bits.

For normal users, which their application cached a lot of large sequence data, will not see much difference between 32 bit and 64 bit. But for us, we are doing research works and the algorithms have already been optimized many time, which unfortunately makes most of our code don't put large sequence data in memory but use a lot of pointers. Such pointer upgrade will make the assumption fail, and may need us to work out new algorithms to replace old one to maximum the performance.

64bit ubuntu can run 32bit applications. Its not a completely automatic install. But its not that hard. [The getlibs post should help you]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs"). 
If you already have the 32bit version installed I do recommend installing the 64bit version to a separate partition if you have room. That way you can test everything and work out any small problems while still being able to boot into 32bit to get work done. Then when its all working as you want it you can remove the 32bit partition to reclaim hard drive room if you want to. If you run into a major issue and for some reason the 64bit version isnt working for you, you can delete it and go back to the fully working 32bit install.

---

### Post by wangrui on 2008-02-29
> **Kilz said:**
> 64bit ubuntu can run 32bit applications. Its not a completely automatic install. But its not that hard. [The getlibs post should help you]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs"). 
If you already have the 32bit version installed I do recommend installing the 64bit version to a separate partition if you have room. That way you can test everything and work out any small problems while still being able to boot into 32bit to get work done. Then when its all working as you want it you can remove the 32bit partition to reclaim hard drive room if you want to. If you run into a major issue and for some reason the 64bit version isnt working for you, you can delete it and go back to the fully working 32bit install.

Thanks very much Kilz. You are really so kind. It's not a problem for me. I have a lot of hard disks, and that's what I exactly do when I moved from windows to ubuntu.  I kept the windows hard disk for several months and format it after found it completely useless. And this time it's even easier for me. I installed the root partition on an external usb flash disk (mounted readonly). I just need to unplug the usb disk and install the 64 bit ubuntu into the first partition of my newly purchased hard disk (which I reserved as a backup image of the flash disk). 

Life is really amazing in ubuntu, can't wait to try it.

---

### Post by funrider on 2008-02-29
i am the OP and am so surprised to see this post popped up again. i have been running the 8GB box for couple months so far. life is good and i never run out of ram. i can run a lamp and a windoze 64 bit at the same time. just managed to install zsnes 32 bit on my box for some entertainment. the only issue i had is firefox + flash which keep freezing all the time.

also, i installed a 32 bit ubuntu on a VM as well just in case thing doesnt work well on the 64 bit install.

good luck

---

### Post by _Phineas_ on 2008-03-01
Yep Ubuntu 64 bit supports up to 64gb. They make mobos that support up to 32gb , we will not be using 64gb anytime soon lol

---

### Post by zl2k on 2008-03-05
> **koshcu said:**
> Yeah it works great. I have 8GB of ram on this box using dual opterons and 64bit kubuntu is working great.

Can you provide more detail if any extra configuration you did? I have 4GB and tested on debian 7.10 i386 desktop, 64bit server and i386 server, all can only see 3GB.

---

### Post by jespdj on 2008-03-05
> **zl2k said:**
> Can you provide more detail if any extra configuration you did? I have 4GB and tested on debian 7.10 i386 desktop, 64bit server and i386 server, all can only see 3GB.
You might have some devices (I/O interfaces or your video card) that are taking up some address space. Are you using a video card that takes part of the main memory of your computer, or does your video card have its own dedicated video memory?

You could have a look around in the BIOS setup of your computer if there's something like a "memory remap" setting, to map the addresses of I/O interfaces to another place, which makes the extra RAM visible to the OS. (If the video card is using part of the memory, then you can't use that memory for running software and the memory remap setting is not going to help).

---

### Post by utUtu on 2008-03-05
> **funrider said:**
> I know this is sound crazy but Ram is kinda cheap nowadays. I would like to run multiple VM on my system so actually I can fully use them. Does anyone know if 64bit version of Fiesty support 8GB of ram or more out of the box? Thanks in advance!

As posted here, it can support much more than 8GB.  The question you have to find out is does your hardware supports it?  Some MOBO has issues supporting 8GB though they have slots for it.  

:guitar:

---


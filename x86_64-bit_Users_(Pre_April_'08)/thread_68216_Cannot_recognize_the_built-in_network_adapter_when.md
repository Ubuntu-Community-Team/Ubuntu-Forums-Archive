---
title: "Cannot recognize the built-in network adapter when installing Ubuntu AMD64/EM64T"
date: 2005-09-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by gaobo on 2005-09-22
My computer:

Motherboard: ASUS K8U-X
CPU: AMD Sempron 2500+
Video Card: Ra 9550

I want to know what is the proper driver for the built-in network adapter for my computer, where to download it and how to install it.

Any idea will be highly appreciated.

---

### Post by DancingSun on 2005-09-22
You should probably check the ASUS website for driver downloads.  Usually, there will be a README file in the download that contains some installation instructions.

---

### Post by gaobo on 2005-09-22
Thank you for your support. However I don't think I am a bad searcher but after conducting many searches via Internet I failed to find anything significant. Would you be pleased to help me out? Thanks in advance.

Daniel

---

### Post by mlomker on 2005-09-22
Post the output of **lspci** (from a terminal prompt).  It should give you the chipset for the adapter.

---

### Post by DancingSun on 2005-09-23
Ok, I went to ASUS's website and found the following link:

[http://support.asus.com/download/download_item_nn.aspx?model=K8U-X&product=1&f_name=&type=&SLanguage=en-us#](http://support.asus.com/download/download_item_nn.aspx?model=K8U-X&product=1&f_name=&type=&SLanguage=en-us#)

Click on the "Drivers" tab. Scroll down until you see "Linux".  Look for the driver that has this line: 
```
ULi M5263 10/100M Ethernet Controller Driver for fedora2(kernel 2.6.5-358). ULi M5263 10/100M Ethernet Controller Driver for kernel
```

It really wasn't that hard to find.  I just went to [www.ASUS.com](www.ASUS.com), then went to the North America website, clicked on support, then on downloads, then selected motherboards as product type, then selected socket 754, and then K8U-X as the model.  Clicked on search, then it took me to that page.

The hard part will probably be compiling the driver into the kernel...which I don't have experience on, so I'll leave that to our fellow forumers.

---

### Post by gaobo on 2005-09-23
[QUOTE=DancingSun]Ok, I went to ASUS's website and found the following link:

[http://support.asus.com/download/download_item_nn.aspx?model=K8U-X&product=1&f_name=&type=&SLanguage=en-us#](http://support.asus.com/download/download_item_nn.aspx?model=K8U-X&product=1&f_name=&type=&SLanguage=en-us#)

Click on the "Drivers" tab. Scroll down until you see "Linux".  Look for the driver that has this line: 
```
ULi M5263 10/100M Ethernet Controller Driver for fedora2(kernel 2.6.5-358). ULi M5263 10/100M Ethernet Controller Driver for kernel
```

It really wasn't that hard to find.  I just went to [www.ASUS.com](www.ASUS.com), then went to the North America website, clicked on support, then on downloads, then selected motherboards as product type, then selected socket 754, and then K8U-X as the model.  Clicked on search, then it took me to that page.

The hard part will probably be compiling the driver into the kernel...which I don't have experience on, so I'll leave that to our fellow forumers.[/QUOTE]

Oh, you really helped me a lot! I have downloaded the driver from the link below under your help:

[http://dlsvr01.asus.com/pub/ASUS/mb/sock754/K8U-X/LAN.zip](http://dlsvr01.asus.com/pub/ASUS/mb/sock754/K8U-X/LAN.zip)

Now I found two folders within the ZIP package, one is 2.6.8 and the other is fedora. How to compile this into the kernel? Any assistance will be appreciated.

Thanks a lot for taking me here!

Daniel

---

### Post by DancingSun on 2005-09-23
I think there's a README file that should tell you some basic instructions.  Read that, and ask questions about the procedures which you aren't sure of here.

But I guess the first question is which folder's content should you use?  Fedora2 or 2.6.8?

I'd guess it would be 2.6.8...

Update: I just downloaded the file myself, if you read the README file under the Fedora2 folder, you'll see that it's for kernel 2.6.5...so I guess the newer one is better?

---

### Post by mlomker on 2005-09-23
> I'd guess it would be 2.6.8...


Hoary uses the 2.6.10 kernel and Breezy is on 2.6.12.  In other words, those are not going to work for you.

What is the output of:

```

ifconfig
lsmod | grep tulip
dmesg | grep eth0

```

You need to figure out if it is loading and not working or just not loading.

---

### Post by DancingSun on 2005-09-23
Just did a quick search on the web and found that some distributions like Gentoo 2005 have the drivers installed already, but people still had problem making it work:

[http://www.linuxquestions.org/questions/showthread.php?threadid=357563](http://www.linuxquestions.org/questions/showthread.php?threadid=357563)

So yes, follow mlomker's instructions first.  We need to determine whether you actually have the drivers installed or not.

---

### Post by gaobo on 2005-09-23
[QUOTE=mlomker]Hoary uses the 2.6.10 kernel and Breezy is on 2.6.12.  In other words, those are not going to work for you.

What is the output of:

```

ifconfig
lsmod | grep tulip
dmesg | grep eth0

```

You need to figure out if it is loading and not working or just not loading.[/QUOTE]

I don't know whether the driver designed for the lower version of kernel can be usable for higher version of kernel or not. I don't know whether the driver designed for Fedora can be usable for Ubuntu or not, either.

Will anybody explain this to me? Thanks in advance.

Daniel

---

### Post by mlomker on 2005-09-23
> Will anybody explain this to me? Thanks in advance.


Daniel, I'm getting frustrated because you aren't letting me help you and yet you continue to ask for help.  Care to reply to any of the questions that I've posed?

Older driver **do not** work with newer kernels.  Ubuntu comes with a driver for that card and it's called **tulip**.

---

### Post by shinsplints on 2005-09-29
sorry to revive a week old thread but it looks like there's a fair amount of confusion out there regarding this issue:

your board uses the m5263 chipset for ethernet.  The driver for this chipset was supposed to be integrated into the linux kernel somewhere around 2.6.11 but never worked correctly.  They (the higher powers above) are currently seperating the driver content from the main tulip.c file (where it originally resided) and moving it to its own file (called uli526x.c I believe).  Apparently a patch from the -mm tree is supposed to fix it - tulip-fixes-for-uli5261.patch.  However, this patch was never merged into the main kernel tree.  Unless you know exactly what you are doing, I'd be careful about using this.

ASUS provides its own driver, as you discovered on their webpage, but this driver only works for Fedora or kernel 2.6.8, which Ubuntu does not use.

Your options are limited.  There is no easy way to get your network working with ubuntu 5.04.  Any fix will at least require you to compile your own kernel.  So you can use kernel 2.6.8 and merge in the driver from ASUS's website if you wish, or you can use a new kernel and apply the tulip-fixes-for-uli5261 patch.

I don't believe that kernel 2.6.12 fixed the m5263.  At the moment I'm not sure about 2.6.13, but I faintly recall seeing something in the changelogs about 2.6.14.  So, at the very least, you should be able to use a stock kernel once 2.6.14 is released.  Even this will require you to compile your own kernel, but it won't require you to modify the source in any way.

I have the same chipset and I've been playing around with this on and off since mid-July with no success.  For a temporary fix I just threw in a pci-lan card.  If that's not an option then I'm afraid you'll have to wait.

This isn't an Ubuntu specific problem, it's a Linux kernel issue.

Good luck

---

### Post by mlomker on 2005-09-29
> 
I have the same chipset and I've been playing around with this on and off since mid-July with no success. 

Thanks for the info.  That is good to know in case I run across other people with this problem.

---

### Post by shinsplints on 2005-09-29
quick update after some research:

uli526x is not in 2.6.13

but is in 2.6.14rc so it will be in 2.6.14, hopefully working properly.  Right now I'm guessing it won't be included in Breezy Badger, so you'll be on your own to compile a custom kernel.

---

### Post by bonnei on 2006-03-21
[QUOTE=shinsplints]quick update after some research:

uli526x is not in 2.6.13

but is in 2.6.14rc so it will be in 2.6.14, hopefully working properly.  Right now I'm guessing it won't be included in Breezy Badger, so you'll be on your own to compile a custom kernel.[/QUOTE]
Could it work properly in 2.6.15?I'm downing Ubuntu 6.04 (Dapper Drake) Flight 5,hope it will work.

---


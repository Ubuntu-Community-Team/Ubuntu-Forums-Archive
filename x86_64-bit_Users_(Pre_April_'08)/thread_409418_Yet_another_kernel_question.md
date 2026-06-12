---
title: "Yet another kernel question"
date: 2007-04-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by rivera151 on 2007-04-14
Hi.  After trial and error and help from these forums, I got my ATI video chipset working; thanks to all of you who helped.

Now that I have that working, I'm still trying to get my wireless LAN working.  I read on this [post]("http://ubuntuforums.org/showthread.php?t=197102") (on the **Troubleshooting** section) that the latest 64-bit kernels do not allow the wireless to work.  He posts some links to kernels that should work with the procedure he outlines in his post.

My question has to do with the kernel compiling.  I'm still a little rough on the kernel and modules, so I ask a lot of questions about this.

To install the ATI driver, I had to compile both the kernel and module ( I think?).  Now it works, but the previous post says I need to use another kernel to get my wireless working.  So how should I proceed?

Method A.  Uninstall fglrx driver-->Restore xorg.conf-->reboot-->Acquire kernel image that supports my WiFi-->compile kernel image-->install kernel image-->reboot-->Install wireless-->Reinstall fglrx

Method B.  Acquire kernel image that supports my WiFi-->compile kernel image-->install kernel image-->Recompile fglrx kernel module-->reboot

Any suggestions are welcome.:D

---

### Post by ffxr on 2007-04-14
what chipset does your wireless card use?

*EDIT oh i see from your other thread Broadcom 4318; i know nothing about them, except that they seem to cause a lot of problems. ** just looked at that link ; your not doing nothing to your kernel that will upset your graphics drivers....

fire away...

---

### Post by ffxr on 2007-04-14
sorry im misunderstanding you terribly.. before you go looking to compile a new kernel, just to get that broadcam nic to work, keep looking around for a native linux driver that you might be able use... (one mightnt exist but make sure youve done a good load of hunting around)

or just get a new, more linux compatitble wireless card.. (i only buy ones with a ralink chipset)

if you do decide to compile a new kernel.. you will compile and make it then reboot & the new kernel will appear in your GRUB menu, you select it, boot back into ubuntu, then yes, you would have to reinstall the ATI drivers again..

hope that helps..

ps. when you installed the ATI driver, you just compiled a kernel module (driver) for your kernel...you didnt recompile your kernel (unless you did something completely nuts, that i havent considered)

*pps read that howto AGAIN.. what kernel are you using? in terminal type: 

```

uname -r

```

---

### Post by nbound on 2007-04-14
Run it under ndiswrapper if possible, much much easier :p

---

### Post by bugler on 2007-04-14
> **nbound said:**
> Run it under ndiswrapper if possible, much much easier :p 

Yep I Second that.

Just got my troublesome hp laptop dv6000 with bcm4311 wifi working under edgy and feisty with ndiswrapper.  Ndiswrapper uses the windows 64bit driver for your card.  If I can find the how-to I used, I will edit this post.  ndiswrapper under heavy development and runs at 54g.  In feisty ndiswrapper comes in the repo's.  It's just as easy to compile it and what not.

let us know how you make out.

Bugler

---

### Post by rivera151 on 2007-04-15
> **bugler said:**
> Yep I Second that.

Just got my troublesome hp laptop dv6000 with bcm4311 wifi working under edgy and feisty with ndiswrapper.  Ndiswrapper uses the windows 64bit driver for your card.  If I can find the how-to I used, I will edit this post.  ndiswrapper under heavy development and runs at 54g.  In feisty ndiswrapper comes in the repo's.  It's just as easy to compile it and what not.

let us know how you make out.

Bugler

Thanks for the quick replies, guys.

This is the post I used to try and set up ndiswrapper.

[http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102")

The author of the post, compwiz, did a pretty good job of writing a thorough tutorial.  I used it on my 32-bit install and got my internal wifi working.

However, after finishing the tutorial, compwiz has a troubleshooting section.  In it, he writes the following:

> 
If you are using 64bit Edgy Eft and the 2.6.17-10-generic, make sure you are NOT using the 2.6.17-10-generic kernel as it doesn't work (after running the script, you will be warned if there is a problem). If you need help finding a different kernel, check [here.]("http://ubuntuforums.org/showpost.php?p=1705658&postcount=668")


bugler: you are saying that I can use my current kernel for ndiswrapper?  If so, am I misinterpreting compwiz's statement?

ffxr: My "uname -r" output is "2.6.17-11-generic".  Also, it just seems I'm misunderstanding the compilation step a little; this is good, cause it means I'm not doing something "completely nuts" :biggrin: And then again, if it comes to it, I'll get another wifi card, but I'd love to just use the internal.  As long as there is people like you guys in here, I know it's only a matter of time before I get it to work.:guitar:

Now I found this guide

[http://compwiz18.blackhole.cx/linux/bcm4318/howto.htm](http://compwiz18.blackhole.cx/linux/bcm4318/howto.htm)

I'm gonna try that today and see if it works.  I'll post my result here.

---

### Post by ffxr on 2007-04-15
yeah that guide looks like nice and straightforward, that other one you were looking at was melting my head trying to understand it.. you'll just need to reinstall the ATI drivers once your booting into your new kernel. & good luck.

p.s if them prepackaged kernels dont work for you, you can always go ahead and compile your own, or you could consider Feisty as this new version of ubuntu may 'magically' sort out all your problems.

---

### Post by rivera151 on 2007-04-15
Well, I uninstalled my fglrx driver, found an ndiswrapper-compatible kernel, installed it, and got ndiswrapper working.

This is the problem I'm having now is posted on this page:
[http://ubuntuforums.org/showthread.php?t=197102&page=131](http://ubuntuforums.org/showthread.php?t=197102&page=131)

I found the code I need to modify on the fglrx module source files, and did so.  I need to put them in a deb package, but I don't know how to package into a deb.  :(

---


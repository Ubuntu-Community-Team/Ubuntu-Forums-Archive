---
title: "Help installing Canon LIDE30 USB scanner"
date: 2007-07-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rizlaw on 2007-07-09
I'm running Ubuntu 7.04 - AMD64 and would like to scan my CD cover art using my Canon Lide30 USB scanner. So far, every time I plug the scanner in and start Xsane, it looks like it sees a scanner, but I can't scan anything. I find Xsane somewhat confusing, so I'm not sure if there is a place where I can set a parameter to get it to work with my scanner.

The Xsane website states that this scanner is "completely" supported, but I remember reading a post back when 7.04 Feisty was released that this scanner, which had worked in 6.10 Edgy, stopped working in Feisty due to some bug introduced in Feisty. I can't find that thread again.

Does anyone have the Canon Lide30 working in Ubuntu 7.04 AMD64, and if so, can you help me get it working in my system?

---

### Post by rmfought on 2007-07-09
I'm not sure how much different it is, but I am successfully using the LIDE60 on my Ubuntu 7.04 - AMD64 system with Xsane.

Perhaps you can elaborate on your problem - what exactly is happening in Xsane?

---

### Post by Rizlaw on 2007-07-10
> **rmfought said:**
> I'm not sure how much different it is, but I am successfully using the LIDE60 on my Ubuntu 7.04 - AMD64 system with Xsane.

Perhaps you can elaborate on your problem - what exactly is happening in Xsane?

First, when I plug the scanner into any USB2.0 port nothing happens, even though Ubuntu is set to start SANE when a scanner is plugged in.

When the scanner is plugged in and I manually start Sane, two windows pop up, if I click on "SCAN," the progress bar shows "Receiving RGB data" but it takes about 15 seconds before the bar shows any orange bars. Finally, the scan completes and a get another window filled with solid black. In all that time the scanner doesn't even turn on!

The info tab says:

Vendor: Canon
Model:  N1240/Lide30
Type: USB Flatbed Scanner
Device: 005
Loaded backend: plustek:libusb:001
Sane: 1.0.18

I did a little more digging to find the post about this problem. I found it. There is definitely a bug in the sane backend on Feisty (7.04) you can find all the info about it at: [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488)  and here: [https://answers.launchpad.net/ubuntu/+question/7700](https://answers.launchpad.net/ubuntu/+question/7700)
This is a very long thread with a lot of unhappy people. From the posts I read, it looks like the problem is being ignored by Ubuntu and will not be corrected for Feisty. I guess one way to handle this is to install  and hook up the scanner in Edgy Eft (where it is supposed to work). I installed Ubuntu 6.10 [64 bit] in a VMware 6 Virtual Machine and the Canon Lide30 works perfectly.

---

### Post by ryanlutz on 2007-07-23
I had this same problem, until today. I use xsane, but I was seeing the same results. I came across a post that hinted that if I started xsane (or sane) as root, it might work. I tried and it did work after telling me that I was doing something very wrong, illegal and I will blow up my computer. :) This post helped me get it fixed so that a normal user could do it: [ http://ubuntuforums.org/showthread.php?t=400142]("http://ubuntuforums.org/showthread.php?t=400142"). I love the Ubuntu forums!

I am using 32 bit on Feisty, but I hope this can solve the problem for you as well.

---

### Post by crjackson on 2007-07-23
I have the LIDE20 with problems.  xsane sees the scanner, and activates it when I press the scan or preview button, however the result is a black page.  I don't think it's turning on the led lights inside or something.

I'll try the suggestion in the link and see what happens...

---

### Post by John Jason Jordan on 2007-07-23
> **Rizlaw said:**
> I'm running Ubuntu 7.04 - AMD64 and would like to scan my CD cover art using my Canon Lide30 USB scanner. So far, every time I plug the scanner in and start Xsane, it looks like it sees a scanner, but I can't scan anything. I find Xsane somewhat confusing, so I'm not sure if there is a place where I can set a parameter to get it to work with my scanner.

The Xsane website states that this scanner is "completely" supported, but I remember reading a post back when 7.04 Feisty was released that this scanner, which had worked in 6.10 Edgy, stopped working in Feisty due to some bug introduced in Feisty. I can't find that thread again.

Does anyone have the Canon Lide30 working in Ubuntu 7.04 AMD64, and if so, can you help me get it working in my system?

Yep. I have it working, but with problems. First, here is the thread where the problems are discussed:

[http://ubuntuforums.org/showthread.php?p=2952741&highlight=USB+scanner+broke+feisty#post2952741](http://ubuntuforums.org/showthread.php?p=2952741&highlight=USB+scanner+broke+feisty#post2952741)

The problem is the USB suspend feature that was added to the kernel before Feisty came out. However, I found two fixes.

The simplest is to install scanbuttond. (It's in Synaptic.) You have to run it from the command line before starting xsane or kooka. Then your scanner will work. My problem with this is that I can't figure out how to stop scanbuttond, and it sends my CPU to the max. The only way I know how to stop it is to use System > Administration > System Monitor and kill it.

The only alternative I have found is to boot to a Knoppix 5.0 live CD and scan from it. You have to use a 5.0 CD, because Knoppix 5.1 uses the same newer kernel and has the same problem. Once the 5.0 CD has booted you can click on the penguin, then open a root terminal, which allows you to mount your existing drives. You have to mount something under Knoppix, else you won't have anyplace to save the scan files.

---

### Post by Rizlaw on 2007-07-23
> **ryanlutz said:**
> I had this same problem, until today. I use xsane, but I was seeing the same results. I came across a post that hinted that if I started xsane (or sane) as root, it might work. I tried and it did work after telling me that I was doing something very wrong, illegal and I will blow up my computer. :) This post helped me get it fixed so that a normal user could do it: [ http://ubuntuforums.org/showthread.php?t=400142]("http://ubuntuforums.org/showthread.php?t=400142"). I love the Ubuntu forums!

I am using 32 bit on Feisty, but I hope this can solve the problem for you as well.

Thanks for the suggestion, but, for the time being, I decided to sidestep the Ubuntu 7.04 scanner problem. I set up a VMware Workstation 6 virtual machine with Windows XP Pro. I added the scanner software and now I can scan from the Windows VM Guest running in my Ubuntu AMD64 Host.

For anyone reading this, I also tried Ubuntu 7.10 Tribe 3 as a VM, and they still haven't fixed this particular problem with the Canon Lide30 USB scanner. I hope they get it fixed by the October 2007 release date of 7.10.

---

### Post by ryanlutz on 2007-07-23
> **John Jason Jordan said:**
> 
The problem is the USB suspend feature that was added to the kernel before Feisty came out. However, I found two fixes.

The simplest is to install scanbuttond. (It's in Synaptic.) You have to run it from the command line before starting xsane or kooka. Then your scanner will work. My problem with this is that I can't figure out how to stop scanbuttond, and it sends my CPU to the max. The only way I know how to stop it is to use System > Administration > System Monitor and kill it.


Yep. That happened to me 1 hour later. My scanner went to sleep and the problem returned. I installed scanbuttond and it worked again. As far as stopping it. It looks like it is supposed to be run as a daemon, set to start on boot. If that takes 100% CPU on your box, this is not desirable. I found that you can add a  "-f" option to it so it will run in the foreground. Then push ctrl-C to stop it. It is a workaround, but it should work.

> **Rizlaw said:**
> Thanks for the suggestion, but, for the time being, I decided to sidestep the Ubuntu 7.04 scanner problem. I set up a VMware Workstation 6 virtual machine with Windows XP Pro. I added the scanner software and now I can scan from the Windows VM Guest running in my Ubuntu AMD64 Host.

For anyone reading this, I also tried Ubuntu 7.10 Tribe 3 as a VM, and they still haven't fixed this particular problem with the Canon Lide30 USB scanner. I hope they get it fixed by the October 2007 release date of 7.10.

If that is working for you, I say stick with it. Last thing you want to do is break it even more. According to the post that John linked to, the scanner problem is supposed to be fixed in the next release. Here's hoping it is.

---


---
title: "does ubuntu 64 suported on Intel® Core™2 Quad Processor Q9550?"
date: 2008-11-23
forum: x86 64-bit Users
---

### Post by asvestomix on 2008-11-23
Hi i am new here i will run ubuntu for first time..My cpu is Intel® Core™2 Quad Processor Q9550 and it suport x64 but when i tryed to run the ubuntu Ubuntu 8.10 (64 bit version) from virtualbox it says itsays my cpu dont support it.. Is there something wrong or this is working only with amd and not intel 64

---

### Post by hypert on 2008-11-23
Try this install ubuntu on a CD and install it that way without virtual box and see what happens That is the way i had to install ubuntu 8.10

---

### Post by asvestomix on 2008-11-23
oh thnx it works i am writing from obuntu right now...
The question now is that.. Is it possible to make dual boot my disk and have both vista and obuntu?

---

### Post by jespdj on 2008-11-23
If you run VirtualBox on a 32-bit host operating system (for example, 32-bit Windows or Ubuntu), then you cannot run 64-bit guest operating systems. Your host operating system must be 64-bit to be able to run 64-bit guest operating systems in VirtualBox.

64-bit Ubuntu should run normally on an Intel Core 2 Quad Q9550. Why don't you just boot from the live CD and see if it works?
> **asvestomix said:**
> The question now is that.. Is it possible to make dual boot my disk and have both vista and obuntu?
Yes, that's possible.

---

### Post by asvestomix on 2008-11-23
> **jespdj said:**
> If you run VirtualBox on a 32-bit host operating system (for example, 32-bit Windows or Ubuntu), then you cannot run 64-bit guest operating systems. Your host operating system must be 64-bit to be able to run 64-bit guest operating systems in VirtualBox.

64-bit Ubuntu should run normally on an Intel Core 2 Quad Q9550. Why don't you just boot from the live CD and see if it works?

Yes, that's possible.

yes i i am writing right now from ubuntu live cd ..
i had vista 64 with virtual box 64 version .. dont know why it didnt suport it..

---

### Post by asvestomix on 2008-11-23
Is possible to run commercial games like crysiss or unreal on ubuntu and if it is can you give a link or a guide tha telling how to do it?

---

### Post by ecsa0014 on 2008-11-26
I actually have Ubuntu 8.10 64-bit installed as a Virtualbox guest under Vista Ultimate X64 and have no problems. My CPU is also a Core 2 Quad Q9550. Do you have the latest version of Virtualbox (2.06, I think)? Make sure the VT-x/AMD-V box is checked under your virtual machine settings. Also go into your Bios and make sure virtualization is enabled.

---

### Post by PatrickVogeli on 2008-11-26
virtualbox doesn't currently support 64 bits guest operating sistems. Install the 32 bits and you'll be fine.

---

### Post by martino2k8 on 2008-11-26
> **PatrickVogeli said:**
> virtualbox doesn't currently support 64 bits guest operating sistems. Install the 32 bits and you'll be fine.
Actually it does.

> VirtualBox 2.0.0 (released 2008-09-04)

This version is a major update. The following major new features were added:

    * 64 bits guest support (64 bits host only) 

---

### Post by nzadLithium on 2008-11-26
I'm not sure whether you can run crysis or unreal. They would have to be run through wine or cedega or something, check out [www.winehq.org](www.winehq.org) have a look in their 'appdb' for those two games, people will have reported how well they run in wine.

I found the entries for crysis and unreal for you
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107) Crysis
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3733](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3733)  Unreal

---

### Post by Hyper Tails on 2008-12-04
Did you try the 32-bit version?

if not go download the 32-bit one

it'll be worth it ;)

---

### Post by graysky on 2008-12-04
I have the Xeon version of your CPU (X3360) and both Ubuntu 8.10 amd64 and Debian/Lenny amd64 run just fine on it.

[img]http://triton.imageshack.us/Himg78/scaled.php?server=78&filename=titax0.gif&xsize=578&ysize=480[/img]

Mind you, [Ubuntu cannot manage the CPU scaling (speedstep)](http://ubuntuforums.org/showthread.php?t=1001265); Debian/Lenny does it just fine.

---

### Post by asvestomix on 2009-06-02
sorry guys it was very simple i just should enamble some settings so it can run 64bit op systems

---


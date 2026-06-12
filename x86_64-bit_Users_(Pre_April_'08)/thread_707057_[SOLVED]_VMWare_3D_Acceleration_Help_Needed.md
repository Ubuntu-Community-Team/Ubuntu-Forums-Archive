---
title: "[SOLVED] VMWare 3D Acceleration Help Needed"
date: 2008-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by scrop on 2008-02-25
I've been following the instructions in the manual for enabling acceleration. I've added this to the vmx file of a non-running vm.

mks.enable3d = "TRUE"
svga.vramSize = "67108864"
vmmouse.present = "FALSE"

when I start the vm, vmware immediately flips that mks.enable3d setting back to FALSE.
 I can't find any error in the logs or information about this. Can someone please help?

Latest Gutsy in use
Latest NVIDIA driver in use (desktop is accelerated, no trouble here)
GeForce 8600 GT

---

### Post by Kilz on 2008-02-25
> **scrop said:**
> I've been following the instructions in the manual for enabling acceleration. I've added this to the vmx file of a non-running vm.

mks.enable3d = "TRUE"
svga.vramSize = "67108864"
vmmouse.present = "FALSE"

when I start the vm, vmware immediately flips that mks.enable3d setting back to FALSE.
 I can't find any error in the logs or information about this. Can someone please help?

Latest Gutsy in use
Latest NVIDIA driver in use (desktop is accelerated, no trouble here)
GeForce 8600 GT

Do you have vmware tools installed in the vm?

---

### Post by scrop on 2008-02-25
Yes. VMWare tools is installed

It seems like this is one of the very first things to happen when VMWare loads, before the guest OS even starts

---

### Post by fjgaude on 2008-02-25
What manual did you get these instructions from?

Exactly what is the file name you added the 3D item?

It is my understanding that real 3D-video acceleration is not possible in present versions of VMware, but they are working on it in later versions.

The SVGA virtual driver that is presently in the Tools is good enough for everything but games.

---

### Post by eToIPiIsMinus1 on 2008-02-25
I'm seeing this same behavior.

The instructions are in the VMware Workstation User's Manual for version 6.0 starting on page 323.

---

### Post by eToIPiIsMinus1 on 2008-02-25
I made a bit of progress by quitting VMware completely, then editing the file as described. When powering on the VM it complained about have multiple monitors and experimental 3D mode only supports 1. I had "Use host settings for montiors" checked. I clicked the other radio button to select 1 montior. Powering on again produced a message that it failed to creat an OpenGL context. Still not working but a bit less mysterious.

---

### Post by fjgaude on 2008-02-25
Gosh, I had no idea we were talking about the non-free Workstation. Sorry, I was thinking Player or Server.

---

### Post by scrop on 2008-02-28
The VMWare forums have been having some issues for a few days. Users can't login w/o being taken to the registration screen in an endless loop. I even called them and they had the same issue on their end.

Anyway, after experimentation, I found that VMWare will silently disable 3d support if you don't specify this parameter correctly.

svga.vramSize = "67108864"

If this works out to be anything other than the exact size of the memory your graphics card has then w/o warning or errors being logged you just get reverted to no 3d.

How about a round of applause for that user experience?

---


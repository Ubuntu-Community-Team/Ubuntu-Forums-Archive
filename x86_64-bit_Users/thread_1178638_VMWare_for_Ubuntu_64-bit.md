---
title: "VMWare for Ubuntu 64-bit?"
date: 2009-06-04
forum: x86 64-bit Users
---

### Post by punkduck02 on 2009-06-04
VMWare for Ubuntu x86 64-bit.  I have tried multiple times to install VMWare, I have searched the internet and found some information, but can't get it to work.  The problem is it can't configure correctly, is there a 64 bit VMWare app out there or is there a fix for this so I can get it to configure correctly for me?

---

### Post by pbrane on 2009-06-04
[http://www.vmware.com/download/server/]("http://www.vmware.com/download/server/") will allow you download the 64-bit version of vmware server. I have used it and it works fine on Jaunty 64-bit.

---

### Post by rlogan on 2009-06-05
I have VMWare Server 2.x working on Jaunty 64bit just fine now after some little issues. My main issue was that kvm was running and stopping the VM's from running.

TO install it just download the tar file and use the installer with it, when it says that there is no version for your kernal. Allow the installer to compile it for your kernal and follow the prompts.

Good luck

Richard

---

### Post by dabl on 2009-06-05
VMWare Player works great on my 64-bit Kubuntu system.  Here's the How-To:

[http://kubuntuforums.net/forums/index.php?topic=3095339.0](http://kubuntuforums.net/forums/index.php?topic=3095339.0)


and here's a screenshot:

[http://www.kubuntuforums.net/index.php?ind=gallery&op=foto_show&ida=249](http://www.kubuntuforums.net/index.php?ind=gallery&op=foto_show&ida=249)

---

### Post by diamondnular on 2009-06-05
> **punkduck02 said:**
> VMWare for Ubuntu x86 64-bit.  I have tried multiple times to install VMWare, I have searched the internet and found some information, but can't get it to work.  The problem is it can't configure correctly, is there a 64 bit VMWare app out there or is there a fix for this so I can get it to configure correctly for me?

I have VMWare running just fine here as well. Maybe you have the 32-bit version?

D.

---

### Post by ProbablyX on 2009-06-06
Why not try VirtualBox? [www.virtualbox.org](www.virtualbox.org), works like a charm for me :)

---

### Post by Liv3dN8as on 2009-06-06
> **ProbablyX said:**
> Why not try VirtualBox? [www.virtualbox.org](www.virtualbox.org), works like a charm for me :)

Right on! VirtualBox is way better. I followed [this]("http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu") guide for setting it up. The only thing I changed was the intrepid to jaunty on the second command example. Works Perfect!

---


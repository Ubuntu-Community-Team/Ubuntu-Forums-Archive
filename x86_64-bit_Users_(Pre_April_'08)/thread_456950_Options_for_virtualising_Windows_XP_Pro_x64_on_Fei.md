---
title: "Options for virtualising Windows XP Pro x64 on Feisty"
date: 2007-05-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by jharrop on 2007-05-28
Hi 

I'm looking into my options for virtualizing the 64 bit  version of Win XP Pro on Ubuntu 7.04.

This is just for my personal workstation (Dell Precision Workstation 490), so i'd like for it not to crash regularly (or at all), but its not as if its running a bank.

Here's what i've found out so far.  Comments and corrections welcome please.

1.  VMWare Server

[LIST]
[*]performance issues on 7.04 as noted by Pressureman - see [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/113532](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/113532), so i'd have to install a 2.6.18 kernel (which is ok, but then KVM won't work)
[*]VMWare is 32 bit.  It seems less than ideal to be running a 64 bit OS inside a 32 bit program on a 64 bit OS, but does it have adverse performance implications?
[/LIST]

2.  Xen

[LIST]
[*]Need to be running Xen 3.04 or later 
[*]Need Intel VT or AMD-V hardware support (which i have)
[*]But there is nothing to make it easy to make Feisty into dom0 - unless [http://packages.debian.org/unstable/admin/xen-linux-system-2.6.20-1-xen-amd64](http://packages.debian.org/unstable/admin/xen-linux-system-2.6.20-1-xen-amd64) just works?
[/LIST]

3.  KVM

[LIST]
[*]Supported in Feisty, but ...
[*]64-bit windows doesn't work at present: [http://kvm.qumranet.com/kvmwiki/FAQ#head-c3a08e5599921c18f9727e6e335257a582ade86a](http://kvm.qumranet.com/kvmwiki/FAQ#head-c3a08e5599921c18f9727e6e335257a582ade86a)
[/LIST]

Is this a fair summary?

thanks

Jason

---

### Post by Twintop on 2007-05-29
> **jharrop said:**
> 
1.  VMWare Server

[LIST]
[*]performance issues on 7.04 as noted by Pressureman - see [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/113532](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/113532), so i'd have to install a 2.6.18 kernel (which is ok, but then KVM won't work)
[*]VMWare is 32 bit.  It seems less than ideal to be running a 64 bit OS inside a 32 bit program on a 64 bit OS, but does it have adverse performance implications?
[/LIST]

Correct me if I'm wrong, but I don't think you can emulate a 64 bit OS inside of a 32 bit host. I tried this on my laptop under VMWare-Player on Windows and it wouldn't let me. Are you running the 64 bit version of Feisty? If so, then WinXP Pro x64 will run under VMWare-Player no problem because the version in the repositories is 64-bit (I have it running on my desktop machine right now).

---

### Post by Kilz on 2007-05-29
> **Twintop said:**
> Correct me if I'm wrong, but I don't think you can emulate a 64 bit OS inside of a 32 bit host. I tried this on my laptop under VMWare-Player on Windows and it wouldn't let me. Are you running the 64 bit version of Feisty? If so, then WinXP Pro x64 will run under VMWare-Player no problem because the version in the repositories is 64-bit (I have it running on my desktop machine right now).

No you cant emulate a 64bit host in a 32bit os on 32bit hardware. But the vmware application itself is 32bit, even on a 64bit Ubuntu install, and you can run 64bit vm's in it.

> **jharrop said:**
> Hi 

I'm looking into my options for virtualizing the 64 bit  version of Win XP Pro on Ubuntu 7.04.

This is just for my personal workstation (Dell Precision Workstation 490), so i'd like for it not to crash regularly (or at all), but its not as if its running a bank.

Here's what i've found out so far.  Comments and corrections welcome please.
It looks about right. But, just a question, what are you planing on running n a vm?

---

### Post by jharrop on 2007-05-29
> But, just a question, what are you planing on running n a vm?

I'm planning to run Office 2007 and VSTO in the VM.  Especially since the so-called "Office button" doesn't display properly in Tight VNC (at least as i've got it configured).

Why 64 bit Windows, rather than 32 bit?  Just because that's what came with the PC.

And yes, I am running the 64 bit version of Ubuntu :)

cheers,

Jason

---


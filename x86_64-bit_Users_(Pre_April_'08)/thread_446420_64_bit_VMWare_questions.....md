---
title: "64 bit VMWare questions...."
date: 2007-05-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by DJiNN on 2007-05-16
I've  a few questions & if someone more knowledgeable than i out there could answer them, or point me in the right direction, it would be much appreciated.

If i'm using the 64bit version of Xubuntu (Which "Rocks" big time BTW!) and i install the 64 bit version of VMWare Player or Server, will i be able to run a Win2k (32 Bit) virtual OS?  I have a need to run Win2k (Preferably under Linux) and although i can run it in VirtualBox, it's only 32 bit & i have to then use the 32 bit version of Xubuntu..... :(

Also, how easy/straightforward is it to get the virtual OS's setup in VMWare? VirtualBox is pretty straightforward, although there are a few things (Apart from the 64 bit issue) that i don't like about it. Doesn't do USB very well, and also have no access to Native Fat32/Ext3 etc partitions.... Does VMWare allow this?

Thanks for taking the time to read this, and hope someone can reply with a few answers. :)

DJiNN

---

### Post by RawMustard on 2007-05-17
> **DJiNN said:**
> I've  a few questions & if someone more knowledgeable than i out there could answer them, or point me in the right direction, it would be much appreciated.


No probs!

> 
If i'm using the 64bit version of Xubuntu (Which "Rocks" big time BTW!) and i install the 64 bit version of VMWare Player or Server, will i be able to run a Win2k (32 Bit) virtual OS?  I have a need to run Win2k (Preferably under Linux) and although i can run it in VirtualBox, it's only 32 bit & i have to then use the 32 bit version of Xubuntu..... :(


You can run 32bit or 64bit OS's in vmware on your 64bit Xubuntu, no problems.

> 
Also, how easy/straightforward is it to get the virtual OS's setup in VMWare? VirtualBox is pretty straightforward, although there are a few things (Apart from the 64 bit issue) that i don't like about it. Doesn't do USB very well, and also have no access to Native Fat32/Ext3 etc partitions.... Does VMWare allow this?


I'm not expet on using vmware and didn't find it too hard to install XP, Win2003 Server, and Ubuntu Gutsy.  It's pretty straight forward :)

---

### Post by DJiNN on 2007-05-17
Hey, thanks for the quick reply RawMustard..... & thankfully, all your answers where exactly what i i was hoping to hear. :)  I tried XP on VirtualBox, but had to use a 32bit OS to do it, and apart from anything else i really noticed the performance hit over having used the 64 bit Xubuntu, which is really fast!!

So i'm just installing Xubuntu again (64 bit of course) then i'm going to give VM a go..... wish me luck!! :D

Thanks again......

DJiNN

---

### Post by dfreer on 2007-05-17
I think you have to have VT support in your kernel/processor in order to run a 32-bit OS from a 64-bit OS, but I could be wrong.

---

### Post by DJiNN on 2007-05-18
> **dfreer said:**
> I think you have to have VT support in your kernel/processor in order to run a 32-bit OS from a 64-bit OS, but I could be wrong.

I think i have that enabled, but i'm not 100% sure. I've since tried VMWare server anyway, and although it's very good, and runs W2k etc really well, it's nothing like running it on a dedicated machine, and as i'm using it for Music mainly i need a bit more speed than i'm getting from VMWare.... :(

So it's back to dual-booting for me. It was fun trying it out though. :)

DJiNN

---

### Post by joe0joe on 2007-06-07
Hi DJiNN,

How is your test drive of VMWare on 64-bit Xbuntu?

I have a Athlon64 PC at home and want try somethings similar. Can you give an update? Thanks!

Joe

---

### Post by dfreer on 2007-06-07
> **DJiNN said:**
> I think i have that enabled, but i'm not 100% sure. I've since tried VMWare server anyway, and although it's very good, and runs W2k etc really well, it's nothing like running it on a dedicated machine, and as i'm using it for Music mainly i need a bit more speed than i'm getting from VMWare.... :(

So it's back to dual-booting for me. It was fun trying it out though. :)

DJiNN

Did you have the virtual machine located on a seperate hard drive from your main OS? this generally helps with the speed issue, as most users have enough RAM nowindays the bottleneck generally occurs with hard drive I/O.

EDIT: it is fun though, I'm not running VMWare simply because I don't have an extra hard drive to put in my laptop, and don't have another machine powerful enough to run the server.

---

### Post by pentax on 2007-06-08
I installed VMware server from the repos about a week ago. I'm very happy with it, Photoshop CS2  under XP really runs great.
But how do I know if I have the 64bit version of VMware? The version  of VMware that I am running is 1.0.3 build-44356

---

### Post by dfreer on 2007-06-08
If you are running 64-bit ubuntu you'll have the 64-bit version of vmware :)

if you don't know if you are running the 64-bit version of ubuntu, then you are most running x86.

you can check with this command:
```
uname -m
```
If it doesn't say x86_64, you are running a 32-bit OS.

---

### Post by tgm4883 on 2007-06-08
> **dfreer said:**
> I think you have to have VT support in your kernel/processor in order to run a 32-bit OS from a 64-bit OS, but I could be wrong.

To jump into this thread late, you are wrong. 

On a side not, Virtualbox now runs on AMD64, currently only 32 bit guest OS's, but 64 bit guests are planned

---

### Post by dfreer on 2007-06-08
> **tgm4883 said:**
> To jump into this thread late, you are wrong. 

On a side not, Virtualbox now runs on AMD64, currently only 32 bit guest OS's, but 64 bit guests are planned

Perhaps you could explain WHY, so that others might learn?

---

### Post by tgm4883 on 2007-06-08
> **dfreer said:**
> Perhaps you could explain WHY, so that others might learn?

Explaining why you don't need VT to run a 32 bit OS as a VM of a 64 bit host is like explaining why I can't type on my speakers.  

Because VT or Virtualization Technology (also known as IVT (Intel) or AMD-V (AMD)) has almost nothing to do with 64 bit or 32 bit Host or Guest OS's.

Simply put, Wikipedia (talking about both x86 virtualizations made by intel and AMD)
> Either will allow a virtual machine hypervisor to run an unmodified guest operating system without incurring significant emulation performance penalties.

---

### Post by dfreer on 2007-06-09
Granted, I was wrong about needing VT to run a 32-bit host. I even said I probably was when I made the comment.

> **tgm4883 said:**
> Explaining why you don't need VT to run a 32 bit OS as a VM of a 64 bit host is like explaining why I can't type on my speakers.  

Because VT or Virtualization Technology (also known as IVT (Intel) or AMD-V (AMD)) has almost nothing to do with 64 bit or 32 bit Host or Guest OS's.

Oh, because Virtualization Technology doesn't have anything to do with running a **virtual** machine.

> **tgm4883 said:**
> 
Simply put, Wikipedia (talking about both x86 virtualizations made by intel and AMD)
> Either will allow a virtual machine hypervisor to run an unmodified guest operating system without incurring significant emulation performance penalties.

From same article:
> # VMware — on Intel processors, VMware Workstation 5.5 **requires Intel VT to execute 64-bit guests.**[8] For 32-bit guests, use of VT is possible but not enabled by default because for normal workloads it's slower

[http://www.vmware.com/company/news/releases/ws55_beta.html](http://www.vmware.com/company/news/releases/ws55_beta.html)

> 64-bit Guest Support for AMD64 Technology Systems and Intel EM64T Systems with VT Support

Although I was wrong, I wasn't that far off. It is nothing like "trying to explain why you can't type on your speakers". More like trying to explain that although VT isn't required to run 32-bit guests, it is required to run 64-bit guests (according to vmware), and it certainly helps when running multiple virtual machines.

In other words, you are simply an ***-hole. Try not to be one next time.

---

### Post by tgm4883 on 2007-06-09
> **dfreer said:**
> Granted, I was wrong about needing VT to run a 32-bit host. I even said I probably was when I made the comment.


You were wrong, you said you probably were.  I was just agreeing with you.  Would a smile face at the end of that made you feel all warm and cozy inside?

> 
Oh, because Virtualization Technology doesn't have anything to do with running a **virtual** machine.


Hmm, forgot I left that sentence in there.  Originally I had planned to write a lot about why, but then instead just quoted from the wikipedia.  I'm half right though, as you don't **need** it to run virtual machines (although it does help in running virtual machines it isn't required).  If you're going to get hot about the word virtual, explain how virtual reality relates to virtual machines.

> 
From same article:


[http://www.vmware.com/company/news/releases/ws55_beta.html](http://www.vmware.com/company/news/releases/ws55_beta.html)



Although I was wrong, I wasn't that far off. It is nothing like "trying to explain why you can't type on your speakers". More like trying to explain that although VT isn't required to run 32-bit guests, it is required to run 64-bit guests (according to vmware), and it certainly helps when running multiple virtual machines.


Hmm, seems I am in the wrong here, as I forgot the OP asked about VMware Workstation 5.5.  Although since the OP asked about running a 32-bit guest OS on a 64-bit host, I guess i'm right.  And the argument stands about not being able to type on your speakers.  Speakers are not used for typing, just like VT is not used to run a guest OS's.  VT being a requirement for 64-bit guest OS's is simply a software requirement to balance the performance hit.  (see below)

I could theorize as to why it is a requirement to run a 64-bit guest OS.  Most likely due to the huge performance penalty that one gets while running a 64-bit guest OS.  You can run a 64-bit guest OS on a 32-bit host too, but most programs don't allow it as it would be so slow that it would be unusable.

> In other words, you are simply an ***-hole. Try not to be one next time.

Sticks and stones mate.  Have a nice day :)

---


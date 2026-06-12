---
title: "VirtualBox Windows 2003 Server"
date: 2008-08-25
forum: x86 64-bit Users
---

### Post by ColinuxB on 2008-08-25
I'm trying to run Windows 2003 server 64 bit on my Ubuntu Hardy 64 bit version. However, I'm getting the following
"Attempting to load an x64 bit operating system, however this CPU is not compatible with x64 bit mode"

I have a Core 2 Duo.

Done the usual Google on this and a search in this forum.

Any ideas?

---

### Post by mellowd on 2008-08-25
Not sure if virtualbox emulates an x64 cpu. Have you checked and which version are you using?

---

### Post by ColinuxB on 2008-08-25
Yes, I've RTFM.

It seems it does support 64 bit. I'm using pretty much the latest version, downloaded it off the repositories an hour or so ago. This is on a brand new build of Ubuntu, also just downloaded and updated.

---

### Post by roelpeeters on 2008-08-25
What you are looking for is that your guest (Windows 2003) runs on 64 bit. It seems like you already have the host operating system running on 64 bit.
As per the following link, 64-bit guest operating systems are currently not supported by VirtualBox. 

[http://forums.virtualbox.org/viewtopic.php?t=3941](http://forums.virtualbox.org/viewtopic.php?t=3941)

You might want to check out VMWare ([http://www.vmware.com/support/ws55/doc/intro_supguest_ws.html](http://www.vmware.com/support/ws55/doc/intro_supguest_ws.html))

Roel

---

### Post by ColinuxB on 2008-08-25
I think you'll find that the thread is quite dated and more recently refers to a 64 bit guest on a 32 bit host.

That's not what I'm doing - this is a case of a 64 bit guest on a 64 bit host.

As per page 12 of the VirtualBox manual Windows 2003 Server (64 bit) IS supported by VirtualBox since version 1.5

I'm using a version > 2

---

### Post by Kilz on 2008-08-25
> **ColinuxB said:**
> I think you'll find that the thread is quite dated and more recently refers to a 64 bit guest on a 32 bit host.

That's not what I'm doing - this is a case of a 64 bit guest on a 64 bit host.

As per page 12 of the VirtualBox manual Windows 2003 Server (64 bit) IS supported by VirtualBox since version 1.5

I'm using a version > 2

The 64bit support is for Hosts. That means the computer operating system that you are running VirtualBox on. VirtualBox does not support 64bit Guest operating systems. Page 12 of the manual, only lists 64bit under section 1.3.1, the Host section.
In the guest section it says.

[INDENT]While VirtualBox is designed to provide a generic virtualization environment for **x86 systems**, our focus is to optimize the product’s performance for a select list of guest systems. [/INDENT]

Notice where it says x86 and not x86_64? That says that it is x86 or 32bit compatible for Guests.

If you want to run 64bit Guests, use vmware.

---

### Post by ColinuxB on 2008-08-29
I hate to push the point.

However, the manual I have states under Guest operating systems:

"Windows 2000 / XP / Server 2003 / Vista All versions/editions and service packs are fully supported. Guest Additions are available."

I also have a colleague at work who claims to be running exactly this setup.

I currently use VMWare under WindowsXP to host Windows 2003 server (64 bit). Previous experience is that Virtual Box is lighter & faster, but of course if it can't do the job then VMWare it will have to be.

Regards

---

### Post by Kilz on 2008-08-30
> **ColinuxB said:**
> I hate to push the point.

However, the manual I have states under Guest operating systems:

"Windows 2000 / XP / Server 2003 / Vista All versions/editions and service packs are fully supported. Guest Additions are available."

I also have a colleague at work who claims to be running exactly this setup.

I currently use VMWare under WindowsXP to host Windows 2003 server (64 bit). Previous experience is that Virtual Box is lighter & faster, but of course if it can't do the job then VMWare it will have to be.

Regards

You are reading out of context. [The manual]("http://virtualbox.org/download/1.6.4/UserManual.pdf") clearly says in the header above that that it runs x86 systems, not x86_64 systems. It cant be done, wont work, isnt designed for 64bit guests, cant handle 64bit guests, needs to be added, wont install 64bit guests, 64bit guests are not a feature, 64bit guests are not an option, and you cant run 64bit guests.

I and others have told you it isnt possible, if you choose to selectivly read the manual to think you might possibly. You are only fooling yourself. 
INSTALL VMWARE AND BE DONE WITH IT.

---

### Post by ColinuxB on 2008-08-31
Ooer, getting a bit tetchy are we? Still, there's no need to shout. ;-)

In my defence might I point out that the term x86 in my book originates from the 8086 processor which was (at best) a 16 bit processor. Therefore referring to x86 architecture as the manual does, doesn't imply the number of bits the architecture uses. This doesn't mean selectively reading the manual, it means not understanding the manual's intent. Whether or not the manual has been worded in a coherent and unambivalent way is another discussion.

Thanks for your help - I've done as you suggested and installed VMWare and it runs Windows 2003 (64) a lot better than under XP 32 bit. In fact the difference between Windows Server under VMWare and Windows Server on bare metal is barely discernable.

---

### Post by mysidia on 2008-09-12
The vendor site claims 64-bit guest support.

[http://www.virtualbox.org/wiki/Changelog]("http://www.virtualbox.org/wiki/Changelog")

VirtualBox 2.0.0 (released 2008-09-04)
...
* 64 bits guest support (64 bits host only)

---

### Post by Thelasko on 2008-09-12
> **mysidia said:**
> The vendor site claims 64-bit guest support.

[http://www.virtualbox.org/wiki/Changelog]("http://www.virtualbox.org/wiki/Changelog")

VirtualBox 2.0.0 (released 2008-09-04)
...
* 64 bits guest support (64 bits host only)

At the time this thread was started, [VirtualBox 2.0.0 was not released yet.]("http://www.sun.com/aboutsun/pr/2008-09/sunflash.20080904.1.xml")  It's amazing what can happen in two weeks.

---


---
title: "Which Virtualization tool?"
date: 2007-04-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Necreia on 2007-04-24
I'm looking for a Virtualization tool for Feisty AMD64 (it's one of the very last things I need to be fully setup), but don't know what to pick.  I've tried to get VirtualBox to go, but ran into some execution issues that doesn't appear to be resolved yet (DID get it to install as per [this page]("http://ubuntuforums.org/showthread.php?t=417192&page=3").)  All I'd like to do really is have a guest instance of Windows XP until I no longer have any Windows applications I require.

What I'm looking for in detail is something that is just like either VMWare Workstation or VirtualBox.  I don't mind jumping through a few hoops to get it up and running.
- Free (or not very expensive)
- GUI-Driven
- Fairly good performance

I rather like using AMD64 version for it's benefits, but the virtualization issue is driving me bonkers... any suggestions?

---

### Post by Kilz on 2007-04-24
I recommend Vmware server. Its free as in beer and pretty easy to use.
Here are some links that may help you if you choose to use it.

[vmware server on amd64]("https://help.ubuntu.com/community/VMware/Server/AMD64?highlight=%28vmware%29")

[vmware server generic instructions for install]("https://help.ubuntu.com/community/VMware/Server?highlight=%28vmware%29")

---

### Post by Kingedgar on 2007-04-24
I have to second VMware Server. Excellent product and it works great.

---

### Post by Necreia on 2007-04-24
VMWare Server, hmmm.  I've looked at that, but it looked more like a multi-part system (need a server, and a client/console... start server then attach client).  I was looking for something more 'packaged' like VMWare Workstation (start it, run the one you want... and BAM your set).  Am I understanding VMWare Server right?  Also, can it do instance snapshots?

I'll read up a bit more on it.  Thanks!  Anything else?

---

### Post by dbqp on 2007-04-24
I too would recommend VM Ware Server. Don't let all the console/client talk disuade you as it really is seamless and there aren't any "hoops" to have to jump through to get yourself up and running in no time...well, until you have to go through the XP installation process...so bloated and slow!

I am not sure about snapshots. I know they do have a tool for this, but I am not sure if it is a freebie.

---

### Post by Necreia on 2007-04-24
Okay,  How's performance?  Has anyone compared it to either workstation or VirtualBox?  The server/client element that I'm worried about is a potential slam in performance more than steps in order to connect.

Edit: Also, looks like it does have snapshot / revert ability

---

### Post by dbqp on 2007-04-24
I am running it on an IBM T30 P4 1.8 with 1GB RAM. I have assigned it 256MB and the performance is great! After VM Tools are installed (install these only after the OS has been installed and is running) the vm acts as if it is its own machine! I originally had 512MB and did see a performance lag...

---

### Post by Holzster on 2007-04-24
One difference between VMWare Server & VMWare client you need to know - the client has sound support but the server does not.

so.......

---

### Post by Necreia on 2007-04-24
Sounds great then, I'll hook it up when I get home and see how it goes.

Just curious, can you assign processor time / cores to it?  I run a Core 2 Duo + 4 gigs ram, thinking about giving it 2 gigs RAM and one of the cores.  Is that possible?

---

### Post by dbqp on 2007-04-24
I have sound through VM Ware Server. I just added the device through the management console. All GUI.

---

### Post by Necreia on 2007-04-24
> **Holzster said:**
> One difference between VMWare Server & VMWare client you need to know - the client has sound support but the server does not.

so.......

Do you mean, if you run it FROM the server it has no sound, but if you run it from the client it does?**

**Edit: dbqp answered that already before I posted.

---

### Post by dbqp on 2007-04-24
See my reply on page one - I have sound using VM Ware Server.

I am not in front of my machine right now, but I do believe you can assign these different options (cores, etc)

Also, check the VM Ware site for pre-built appliances you can install in a matter of minutes that can be used right away! Cool coomunity and awesome appliances!

---

### Post by rmfought on 2007-04-24
VMWare server works pretty well, and yes it does have sound.  It is not necessary to install the management interface if you only need to use it on your local machine.  I've found that the USB connectivity is a little flaky (sometimes it works, sometimes it doesn't, and usually detected as USB 1.1) - but overall pretty solid and speedy with VMWare Tools installed.

I had to tweak a thing or two to get it to install on Feisty amd64, but it wasn't bad (see post by  michelemase at the following URL):

[VMWare Server and 2.6.20 kernel discussion]("http://www.vmware.com/community/thread.jspa?messageID=591626")

Rich

---

### Post by Bigsy on 2007-04-24
> **Necreia said:**
> Sounds great then, I'll hook it up when I get home and see how it goes.

Just curious, can you assign processor time / cores to it?  I run a Core 2 Duo + 4 gigs ram, thinking about giving it 2 gigs RAM and one of the cores.  Is that possible?
Yup you can do both.

I also have sound on server.

---

### Post by boogachamp on 2007-04-24
Hey guys,

I dual boot windows XP 64 with Kubuntu 64 at present.  Is there an easy way to use VMWare to with the installation of windows currently on my PC?

---

### Post by Necreia on 2007-04-24
I found this benchmark test: [LINK]("http://www.linux-gamers.net/smartsection.item.56/virtualbox-vs-qemu.html").

Because of that, I'm also going to grab QEMU.  I'll probably get both and compare on my own.  Should get better results out of just the server.

---

### Post by rmfought on 2007-04-24
> **boogachamp said:**
> Hey guys,

I dual boot windows XP 64 with Kubuntu 64 at present.  Is there an easy way to use VMWare to with the installation of windows currently on my PC?

You mean run the instance of XP you already have installed inside VMWare?  I don't think so.  You would have to install from scratch inside the Virtual Machine.  But once you get it set up the way you like it, you can take a snapshot of the VM and save it off.

---

### Post by Necreia on 2007-04-25
Using VMWare Server now (wasn't too much trouble to install) and it's GREAT!  I was pretty disappointed until I installed the tools, but now it's pretty awesome.

---

### Post by wvalters on 2007-04-25
> **rmfought said:**
> You mean run the instance of XP you already have installed inside VMWare?  I don't think so.  You would have to install from scratch inside the Virtual Machine.  But once you get it set up the way you like it, you can take a snapshot of the VM and save it off.

There is a tool to use a currently installed Windows instance and convert it to a [VMWare Image]("http://www.vmware.com/whatsnew/converter.html").  It is slow as hell though, and you will have to re-activate windows due to the major "hardware" change it will see.

Better off just re-installing

---

### Post by cemptor on 2007-04-25
I have an existing installation of Windows XP home with all the service packs applied, and office, antivirus, and a bunch of software installed, plus its an upgrade from Win 98. A conversion would save me time, if I can let it run unattended.

Do you mean it is slow to convert, or slow to run, once converted? The latter would def rule out conversion.

Does the conversion work fine for a 64 bit install of fiesty?

I only need windows to run MS Office and Yahoo messenger (for webcam messaging). Will I be better off trying out Wine? I heard it was not available or didn't work well for 64 bit Ubuntu.

Please advise this ignoramus.

---

### Post by BIGtrouble77 on 2007-04-25
I run win98 in vmware and the performance is very good.  I play Front Page Football 98, Ultima 6 Online and a few sports sims.  They all play nearly perfectly.  Vmware has an accelleration option that can, on occasion, make graphics run too fast.  Other than that everything works great.  win98 is MUCH faster than 2000 or XP.

---

### Post by Necreia on 2007-04-26
> **cemptor said:**
> I have an existing installation of Windows XP home with all the service packs applied, and office, antivirus, and a bunch of software installed, plus its an upgrade from Win 98. A conversion would save me time, if I can let it run unattended.

Do you mean it is slow to convert, or slow to run, once converted? The latter would def rule out conversion.

Does the conversion work fine for a 64 bit install of fiesty?

I only need windows to run MS Office and Yahoo messenger (for webcam messaging). Will I be better off trying out Wine? I heard it was not available or didn't work well for 64 bit Ubuntu.

Please advise this ignoramus.

I was going that route, but after research decided against it and just did fresh install.  The biggest issue I saw people having was driver issues, especially device-specific drivers.  With proper steps you run a good chance that it'll go smooth.

With slow, I'm almost positive he means slow to convert.

Keep in mind, my opinion isn't on actual use but on research and observance of other's experiences.

---

### Post by glantucan on 2007-04-26
Hi
Did anyone test qemu?
I use it at work the opposite way at work computers (running linux on a windows host) and I'm happy with it. Not very fast (computers at work are old) but makes it's job

Glantucan

EDIT: Ups! didn't check this: [VirtualBox vs. Qemu vs. VMware-player (updated)]("http://www.linux-gamers.net/smartsection.item.56/virtualbox-vs-qemu.html") But anyway. Iwould like to hear further opinions.

---

### Post by rmfought on 2007-04-27
> **wvalters said:**
> There is a tool to use a currently installed Windows instance and convert it to a [VMWare Image]("http://www.vmware.com/whatsnew/converter.html").  It is slow as hell though, and you will have to re-activate windows due to the major "hardware" change it will see.

Better off just re-installing

I stand corrected.  I agree it would be better off restarting from scratch, it would probably perform a lot better.

---


---
title: "VMware: Windows install won't let me use the partition"
date: 2007-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by OsakaWilson on 2007-06-01
Hi.
I'm installing Windows XP into VMware on Feisty 64bit. I gave it 20G, but when it starts to format onto it it stops and tells me that it can't install onto that partition.

Any ideas on what might be the problem?

---

### Post by Kilz on 2007-06-01
> **OsakaWilson said:**
> Hi.
I'm installing Windows XP into VMware on Feisty 64bit. I gave it 20G, but when it starts to format onto it it stops and tells me that it can't install onto that partition.

Any ideas on what might be the problem?

Did you allocate the drive space?

---

### Post by OsakaWilson on 2007-06-01
Within VMware, I told it to use 20G in the setup dialog. If there is anything else to do, then no, I haven't allocated the drive space. I have set up partitions when I install a new system, but I have never done that after the initial install of a system. Is that necessary to install Windows in VMware?

Sorry if I sound ignorant, but I am. :)

---

### Post by Kilz on 2007-06-01
> **OsakaWilson said:**
> Within VMware, I told it to use 20G in the setup dialog. If there is anything else to do, then no, I haven't allocated the drive space. I have set up partitions when I install a new system, but I have never done that after the initial install of a system. Is that necessary to install Windows in VMware?

Sorry if I sound ignorant, but I am. :)

I use VMware workstation during the setup of the vm in the drive setup, there is a box to check that allocates the drive. In other words it sets up the files that make up the full drive space. This is helpfull in that it speeds up the vm in its reading/writing to the drive.
Since I dont have any windows vm's currently its hard to remember if it was needed. The last one was a windows 2000 that I setup for Rhino 3D (sadly there is no linux version and v3 wont work under wine). But its worth a try, all it is is checking a box.

---

### Post by OsakaWilson on 2007-06-01
I'll give it a shot. Thanks.

---

### Post by OsakaWilson on 2007-06-01
I went through the process of creating a new virtual machine and there is a checkbox entitled "Allocate Space Now" which I did check, so in answer to your first question, yes I did allocate the disk space.

---

### Post by OsakaWilson on 2007-06-01
Well. On the new virtual machine I set up, I did two things differently. One, changed the settings to work with two processors instead of one, which is what I had it set for before. The second thing I did was select NAT instead of Binary Bridge (?). I don't know which thing made it work, but it is now in installing Windows. 

So far, so good.

---

### Post by OsakaWilson on 2007-06-02
Windows in now running within Ubuntu with VMware. Thanks for your help.

---


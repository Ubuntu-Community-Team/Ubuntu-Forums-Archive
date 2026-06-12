---
title: "8gb RAM"
date: 2009-03-30
forum: x86 64-bit Users
---

### Post by nperry on 2009-03-30
Hey Guys,


Just a quick question - Just ordered a new mobo, cpu and 8gb RAM, Im currently running 32bit with 2gb of ram, Will I have to do a clean install to 64bit or is there anyway i can do it without? As i take it 32bit only address 2gb per process and as i do alot of virtual machine work I need this ammount of ram 3gb for a Virtual Box.

Thanks

---

### Post by jbrevik on 2009-03-30
Well you will need to install OS anyways if your replacing the mobo. The current installation is specific for your hardware.

---

### Post by nperry on 2009-03-30
> **jbrevik said:**
> Well you will need to install OS anyways if your replacing the mobo. The current installation is specific for your hardware.

Thanks, Thought I would of needed to, was just checking if anything else can be done!!

---

### Post by skymera on 2009-03-30
It would be easiest to do a fresh install.

Whack on 64BIT Ubuntu 9.04 :)

---

### Post by fjgaude on 2009-03-30
> **jbrevik said:**
> Well you will need to install OS anyways if your replacing the mobo. The current installation is specific for your hardware.

That's not true! Ubuntu Linux knows at bootup what hardware is there... I used the same drives with the OS and changed out MBs without issue.

You do have to go through a new install from 32 to 64-bit.

---

### Post by sanderj on 2009-03-30
> **fjgaude said:**
> That's not true! Ubuntu Linux knows at bootup what hardware is there... I used the same drives with the OS and changed out MBs without issue.

Exactly

> **fjgaude said:**
> 
You do have to go through a new install from 32 to 64-bit.
Correct

---

### Post by jespdj on 2009-03-30
> **jbrevik said:**
> Well you will need to install OS anyways if your replacing the mobo. The current installation is specific for your hardware.
That's true for Windows, but not for Ubuntu! :)

---

### Post by sebastianabate on 2009-03-30
> **sanderj said:**
> 
You do have to go through a new install from 32 to 64-bit.

Yes, you need a new install, but you can backup your /etc and /home/your_user, reinstall, restore the directories (checking the permissions), and voila!!!! your new 64 bit system whith the same configuration and preferences as your old 32 bit system. As always YMMV.

PD: You may also need to backup other places, like /var/lib/samba, or /var/lib/mysql/data, or any other place where your applications or deamons keeps their data.

PD2: Sorry for my english, I hope you can understend.

---

### Post by kevmitch on 2009-03-30
I would recommend a new install, but it would not be strictly necessary. 

You can run a 64-bit kernel with a 32-bit system. You just need to install the amd64 version of your kernel. Then you would have the 64-bit address space even if your userland is only 32-bit. I can imagine this would lead to a few surprises here and there, but it should mostly work. 

On second thought looking at the archives, it doesn't appear that Ubuntu supports this simply because they don't have an amd64 kernel in the i386 repositories. Debian however does have this. In theory you could grab the Debian kernel, but I think that would lead to even more unexpected surprises.

---


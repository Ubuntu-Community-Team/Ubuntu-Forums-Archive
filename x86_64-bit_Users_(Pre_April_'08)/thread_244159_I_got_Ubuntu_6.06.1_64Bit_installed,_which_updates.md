---
title: "I got Ubuntu 6.06.1 64Bit installed, which updates first."
date: 2006-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ausus on 2006-08-26
Hi All,

I got my  mobile working to do updates.
I installed Ubuntu version 6.01.1

I have updated four files:
libkvb53
xserver-xorg-core
libmagickq
libwrmf0.2-7
These came from synaptic update manager.
Are these file still in folder or do they get deleted when they get installed.
I would like to copy them and save them and if possible re-use them when I do a complete install again.
Help will be appriciated.

Then I would like to update my generic AMD64 processor file.
But I dont know which file to select.
My CPU is a AMD 64 +3800 dual core cpu.

Regards

---

### Post by mogelhead on 2006-08-27
Downloaded packages are stored in /var/cache/apt/archives/

I don't understand this: > Then I would like to update my generic AMD64 processor file.
But I dont know which file to select.
My CPU is a AMD 64 +3800 dual core cpu.

Can you explain further?

Do you have two different computers running ubuntu?

---

### Post by cocteau on 2006-08-27
apt stores the files it downloads temporarely in /var/cache/apt/archives. Try and see if it is in there. If you haven't installed the packages you can download them with apt by doing:

sudo apt-get -d install [package]

That will download but not unpack or install anything.

If you want .deb files you've already installed I don't a better way than browse to the repos and download them directly.

---

### Post by Ausus on 2006-08-27
Hi mogelhead,

Tnx for the reply.

With the processor I went from "generic" to Linux-image-2.6.16-26-amd64-k8.
What i'm trying to say from default cpu support to actual.

regards

---


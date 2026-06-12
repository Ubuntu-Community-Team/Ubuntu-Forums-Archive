---
title: "Fresh Install to latest version"
date: 2008-08-04
forum: x86 64-bit Users
---

### Post by jason1234 on 2008-08-04
Hello, I am a first time Ubuntu user with a fresh install as of tonight with 8.04.

Part of the install was FF beta

After reading everything I can find on the forums I cannot get flashplayer to work. 

Is this not possible on Ubuntu for AMD64 with FF beta?

None of the threads dealing with this were able to actually make flashplayer work for me.

---

### Post by xen-uno on 2008-08-04
FF is no longer beta and is actually at 3.0.1. If you installed Ub tonite, perhaps the 8.04.1 update hasn't been applied yet. I don't remember having to do anything special to get Flash working.

---

### Post by jason1234 on 2008-08-04
I installed from a Ubuntu 7.* cd and ran the updater to the new distribution tonight. The update manager does not show FF as available for anything other than beta 5.  Is this just a FF beta problem possibly?

How can I update to FF 3 non beta to fix this? I am not a Linux savvy person.

---

### Post by xen-uno on 2008-08-04
I would suggest a clean install with 8.04. It just works better than an on-line upgrade ... because I did it that way too initially off 7.10, and had unimpressive results. I like the Alternate disk over the Live disk, but you do need some Ubuntu savvy and/or dual boot so you can get online to ask questions.

---

### Post by kahlil88 on 2008-08-04
I believe Ubuntu comes with [Gnash]("http://www.gnashdev.org/") installed because Adobe's flash player is non-free. However, you can easily install it with **sudo apt-get install flashplugin-nonfree**

---

### Post by jason1234 on 2008-08-04
[I]:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree[/I]

This is what happens when I try to install the nonfree plugin.


xen-uno I would have liked to install directly to Ubuntu 8 but the only thing I had was the CD for version 7. I was on dual boot with xp and thats where the problem started. Something destroyed the MBR and I lost access to all my partitions included my Ubuntu partition. I had Ubuntu 7 working fine prior to today with all plugins for FF etc.


Just to clarify I installed this system a few days ago with Ubuntu 7 but had not updated it because I was busy with other things. When everything broke today I reinstalled Ubuntu and updated to version 8.

---

### Post by xen-uno on 2008-08-04
I must have installed that non-free plugin too. So you can't login to Windows either now? Not following the state of your system ATM. You need to DL and burn (ImgBurn excels) an 8.04 iso it appears.

edit: OK on system state ... look into burning a SuperGrub disk. Your windows partitions are probably OK, just that menu.lst is screwed up and doesn't know where Win is installed.

---

### Post by kahlil88 on 2008-08-04
I forgot to mention you might need to enable some extra repositories - I think Adobe's Flash plugin is part of Universe or something.

---

### Post by jason1234 on 2008-08-04
The state of my system is that I am online posting from the Ubuntu install mentioned in my first post. I am not interested in recovering my windows partions, infact they have already been removed when I reinstalled Ubuntu from CD. Everything important is backed up and I don't really require windows for anything anyways at this point.

I am sure I am probably missing something here with this flash stuff but I likely don't know enough to know what it is heh.

---


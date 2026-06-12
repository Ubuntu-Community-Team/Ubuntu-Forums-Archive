---
title: "Nvidia in openSuSE 11"
date: 2008-04-22
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Down8ve on 2008-04-22
Anyone know of a fool-proof way to install the Nvidia drivers in the new beta?  The usual ways, auto and manual, don't work as they did.

Perhaps we should wait until after the 25th?

---

### Post by quickshade on 2008-04-22
You have to recompile the driver and edit in some stuff. I'm happy without the fancy desktop effects for now and don't feel like spending time on this, but heres the how to: [http://lists.opensuse.org/opensuse-kde/2008-03/msg00119.html](http://lists.opensuse.org/opensuse-kde/2008-03/msg00119.html)

---

### Post by Down8ve on 2008-04-22
Saw that post earlier and tried it, with the correct name of the 32-bit driver.  No luck, so may as well wait for them to release the Suse-ified version.

---

### Post by bluefightingcat on 2008-06-04
Can't you download the NVIDIA-driver from the NVIDIA website? I used it in both Kubuntu and Arch and it seems to work fine. 

BFC

---

### Post by Growbag on 2008-06-04
Yes, Nvidia just released an updated driver.

Just download the newest one from their site and compile as normal, no messing about required.

---

### Post by RS3York on 2008-06-14
The Nvidia repository is now available.
If you check the Community Repositories in YaST you'll find it.

Open: YaST
Select: Software Repositories
Click: Add
Select: Community Repositories
Select: Nvidia Repository
Next, Finish

When it's finished you can open the Software Management module.  "Package" menu -> "All Packages" ->"Update if newer version available".

It should then download the Nvidia driver & kernel module for you.

---


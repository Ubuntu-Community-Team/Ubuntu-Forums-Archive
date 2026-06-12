---
title: "Edgy Update Manager Screwiness"
date: 2007-01-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-01-24
A few days ago I upgraded my Dapper amd64 to Edgy amd64. Today I ran Update Manager. I noticed a nice new touch -- you don't need the root password just to launch it; only when you go to install the updates. 

However, it list two under a separator line titled "Distribution Upgrades" -- libggi and mplayer. These two were unchecked and I could not check them for the upgrade. There were a total of 33 upgrades and I installed all of them. Afterwards these two remained uninstalled and in the Update Manager window they are grayed out.

What does this mean?

---

### Post by Arasfang on 2007-01-25
I had this problem in a previous installation of ubuntu.

What I did as I recall is that I ran sudo apt-get upgrade + a switch to ignore dependencies. Dont remember the switch though >.<

What it means I have no idea of. But the apps I forced upgrade on worked without a problem even though I ignored the deps.

/Mattias

---

### Post by mannih2001 on 2007-02-09
Bump.

John, where you able to upgrade those grayed-out items?

---

### Post by John Jason Jordan on 2007-02-09
> **mannih2001 said:**
> Bump.
John, where you able to upgrade those grayed-out items?
Yes, they upgraded fine when I used Synaptic instead of Update Manager. However, just last night I got bit again, and this time they won't upgrade with Synaptic. This time there are three things grayed out:

linux-headers-generic
   from version 2.6.17-10 to 2.6.17-11
linux-image-generic
   from version 2.6.17-10 to 2.6.17-11
linux-restricted-modules-generic
   from version 2.6.17-10 to 2.6.17-11

There were a total of eight items when I ran Update Manager last night. One was nvidia-glx and the others were all upgrades from version 2.6.17-10 to 2.6.17-11. The other version upgrades worked; the above three were grayed out and could not be selected. They appear as upgradeable in Synaptic, but when I try to mark them to upgrade Synaptic pops up an error message:

Depends: linux-restricted-modules-2.6.17-11-generic but it is not going to be installed

I don't understand what these things are even, let alone how to fix it. :confused:

---

### Post by mannih2001 on 2007-02-09
Thanks for the reply, John.

> **John Jason Jordan said:**
> ...However, just last night I got bit again, and this time they won't upgrade with Synaptic....

This is exactly the same sort of weird behavior that I observed before searching the forums and then posting here. 

Meanwhile, things have been sorted out and it seems that all we have to do is wait. This thread is the relevant one: [http://ubuntuforums.org/showthread.php?t=356408](http://ubuntuforums.org/showthread.php?t=356408)

---


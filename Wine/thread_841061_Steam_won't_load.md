---
title: "Steam won't load"
date: 2008-06-26
forum: Wine
---

### Post by Dpaulson on 2008-06-26
I installed steam today, started it up, and it keeps shutting down as it starts up. It starts with the usual "connecting steam account" and the main window will open for a split second before closing. no idea what to do, I've uninstalled and reinstalled several times but to no avail.

---

### Post by Frak on 2008-06-26
What is the output?

---

### Post by Dpaulson on 2008-06-26
you mean after I type "wine Steam.exe" into the terminal? sorry im pretty new to linux.

---

### Post by Frak on 2008-06-26
> **Dpaulson said:**
> you mean after I type "wine Steam.exe" into the terminal? sorry im pretty new to linux.
Yes

---

### Post by Dpaulson on 2008-06-26
It wouldnt let me post it in a reply, its in the attachment

---

### Post by Dpaulson on 2008-06-26
any help?

---

### Post by Bradl3yJ on 2008-07-30
I am expiriencing the same issue here. 

Using Wine-1.0

Hardy 8.04 x86_64, Linux Kernel 2.6.24-19-generic, latest official nvidia drivers installed using EnvyNG.

It worked fine when i first installed it (using Wine-Doors). I have since tried uninstalling and reinstalling, with no luck. My output looks very similar to yours there. I am not sure if i had installed steam before or after installing the latest nvidia using EnvyNG, so that could be related.

I can get to the login screen. I can login, but once it comes time to open the steam ad that pops up and show the main steam screen with the tabs, it flashes for a second then crashes.

EDIT: I uninstalled the latest nvidia drivers using envy, rebooted, confirmed system was using "nv" drivers in xorg.conf, and the problem persists, so most likely isnt a driver problem, but I am not sure what might have changed since it was working.

---

### Post by Bradl3yJ on 2008-07-30
Ok, I was able to solve my problem. I followed the instructions on this page to download the latest version of wine (the version in the ubuntu repository is not the latest).

I updated to the latest version of Wine by adding the official wine repo to my sources using the command the wine website gives me:

[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

Once i did this, I upgraded wine via Synaptic and steam now launches fine. Not sure what caused the problems before as it *was* working.

---


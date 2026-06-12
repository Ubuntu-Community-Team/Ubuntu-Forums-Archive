---
title: "reinstall kde stuff without a reinstall of OS"
date: 2006-02-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by ubuntubrian on 2006-02-28
I'm running Breezy and have installed a bunch of KDE apps and desktop so I can switch from time to time and the apps are sometimes nicer than the Gnome versions, i.e. Juk over Rythym Box. I posted about Juk crashing after I installed more themes with Synaptic. Amarok, kgpg, xmms also crash and themes won't change in KDE. I thought of wiping all the KDE stuff and then just reinstalling the desktop and see if that works. It probably won't because some package was installed/removed during my adding themes that is making these apps crap out. 
Any suggestions as to how to proceed?
Muchas gracias!
PS-Gnome is as happy as a clam.

---

### Post by Sutekh on 2006-02-28
Ok so how did you install these KDE apps?  With Synaptic?  Did you install them one by one, or did you install the KDE desktop?

If you used Synaptic, you can access the history of your installed packages.  You can use that to find what you installed before/when things went wrong, and completely remove them.

---

### Post by ubuntubrian on 2006-02-28
I did use synaptic so i will give that a shot! Thanks

---

### Post by ubuntubrian on 2006-02-28
I removed all of the installed packages from the last 2 days. I thought that maybe it was all of the ruby bits installed as dependencies but no! It turned out that the gtk and gtk2-engines"theme" were choking things up. I was surprised and I sure did like my new gnome look but now I'm back to where I was (which is better than where I just left!)

---


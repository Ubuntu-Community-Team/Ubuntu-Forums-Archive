---
title: "Skype on 64 bit: Runs, but nothing to see in KDE"
date: 2006-12-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by derhannes on 2006-12-10
Hello,

when I run skype, there is no error message, and "ps ax" tells me it is running. But I don't get the skype window.

This happens with both the skype I installed with the *.deb (and start with "linux32 skype") and the one in the statically linked .tar.bz2.

The straces of both versions are attached, but I don't have the knowledge to interpret them. Maybe one of you can?

(I have no idea if these problems are connected, but my KDE fails to show PSI and kdenetwork in the panel (kicker). Just in case this is relevant.)


Thanks in advance,

Hannes

---

### Post by derhannes on 2006-12-11
It is solved - sort of. I reinstalled using the Kubuntu AMD64 Desktop Image, and now my problems are gone. Skype comes up, Psi rests in the panel.
Kubuntu seems to be different from installing "kubuntu-desktop" which I did before, starting with Ubuntu.

I noticed that the part of the panel, Psi resides in is called "System Tray" and one is able to select which icons are visible, and which are not. This could have been the solution for my Psi problem. But I doubt that the Skype issue depends on this, too.

Anyway, call it "solved".


Hannes

---


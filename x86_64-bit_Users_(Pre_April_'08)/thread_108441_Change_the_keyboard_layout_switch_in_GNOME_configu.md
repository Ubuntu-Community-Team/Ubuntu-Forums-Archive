---
title: "Change the keyboard layout switch in GNOME configuration"
date: 2005-12-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by xenophon on 2005-12-26
Hi, and season's greetings from Athens.

Here's the problem that applies to users with multiple keyboard layouts (Greek and US, in my case) - I'm trying to modify the keyboard toggle to include the "Alt-Space" key combination, which has been the establish way to switch keyboards on Macs localized for Greece.

The "Alt-space" combination, however, is not available in GNOME configuration {gconf} editor. KDE has a "Keyboard shortcuts" application which allows one to specify this, but I wouldn't want to switch desktop environments on this reason alone!

I suspect that one has to modify some system-wide xkb resources, but I haven't been able to figure out which.

Any help would be appreciated!

Xen

iBook G4 14" Breezy 5.10 / MacOS X dual boot

---

### Post by anil_robo on 2005-12-26
Why not make a launcher for language selector and put it on panel? It's easy to use if you select the languages from the drop-down menu! Just set the command of launcher to **gksudo gnome-language-selector**

---


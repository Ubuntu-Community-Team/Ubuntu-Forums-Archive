---
title: "Ubuntu Guide for amd64?"
date: 2007-08-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by volksolwagen57 on 2007-08-24
Isn't there  a useful guide like the one on ubuntuguide.org for amd64?

---

### Post by Jouke74 on 2007-08-24
What you need guidance with? Many of the "32 bit" guide will probably work for the "64 bit" as well, with some exceptions that have been mentioned here already many times : 64 bit Flash, codecs, adding 32 bit libraries etc. 

I have made a guide for my own Ubuntu install(s) including Compiz, Awn, XGL (+ATI + FGLRX), Fonts adjustment and wireless set-up (Simply kept notes during the last install.) The problem is that, it is not general.

---

### Post by volksolwagen57 on 2007-08-24
I've been trying for the longest time already to get Compiz Fusion working. I also want to get AWN and Frostwire working. Thanks for the quick response. Share the knowledge!

---

### Post by volksolwagen57 on 2007-08-24
furthermore, in the past, when i had 32 bit, the only way i could install awn reliably was with buildin it from svn. is there a way to do this in 64?

---

### Post by Jouke74 on 2007-08-24
Yes by building it using SVN :)  From my guide:

**Avant window navigator:**
- Composite must be up and running!! (Compiz / XGL / AIXGL)

> sudo apt-get install subversion automake1.9 build-essential			

> sudo apt-get install libgtk2.0-dev libwnck-dev libwnck-common libgconf2-dev libglib2.0-	dev libgnome2-dev libgnome-desktop-2 libgnome-desktop-dev libdbus-glib-1-dev gnome-	common libxcomposite-dev libxdamage-dev		

(dependencies)

> svn checkout [http://avant-window-navigator.googlecode.com/svn/trunk/](http://avant-window-navigator.googlecode.com/svn/trunk/) avant-window-	navigator

> cd avant-window-navigator

> ./autogen.sh

> make

> sudo make install

!!! Don't erase the install dir because only from here a "sudo make uninstall" can remove the program!

After install there should an icon to run the navigator under "Accessories". Also it is possible to remove the "window switcher" from Gnome now from the top panel. Move the Trash around and adjust the lower bar in such way that everything is on the top Gnome bar. The down part can then be used for Avant to select the active windows. To make Avant autostart at log-in. Add the avant-window-navigator to the "Sessions".

---

### Post by Jouke74 on 2007-08-24
Seeing your other posts I think your composite fails to work.... First figure that part out.
What is your hardware? Especially, which video card are you using?

---

### Post by tgm4883 on 2007-08-24
you can get AWN from the repos

Check here  [http://ubuntuforums.org/showthread.php?t=385981&highlight=awn](http://ubuntuforums.org/showthread.php?t=385981&highlight=awn)

And this is the guide I followed for compiz fusion, but I used trevino's repos to do it (it has since been updated)

[http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion](http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion)

I believe you can use trevino's repos and his guide is still available at compiz.org

---

### Post by volksolwagen57 on 2007-08-27
one of my greatest reservations for installing compiz is that i don't want any unnecessary files floating around in obscure directories. i found a backup program thanks to automatix2. and jouke74, i have my hardware now in my signature slot...

---

### Post by volksolwagen57 on 2007-08-27
by composite, do you mean the desktop effects that are included with the distribution (i.e. wobbly windows and desktop cube)? let me get this straight- desktop effects needs to be running with both check boxes checked for the installation to go smoothly? this would save me a lot of hassle... and label me an idiot after trying three or four times.

---

### Post by volksolwagen57 on 2007-08-27
i tired to get the desktop effects working and for some reason only the wobbly windows effect works. when i try to enable the workspaces on a cube effect nothing happens aside from my workspace switcher app in the panel goes from four spaces to one space. what happened? did compiz-core get broken? can a re-install of these components in synaptic fix the problem?

---

### Post by volksolwagen57 on 2007-08-27
I would like to thank everyone who made it possible for me to run Compiz Fusion successfully. Thanks a million and one.

---

### Post by Jouke74 on 2007-08-28
Reading your last post makes me think you already fixed it, but:

The cube effect is a bit buggy still in the "Feisty Compiz" when it comes to desktop switching. As long as you use the shortcut keys it will be fine, however it might do this when you use the Gnome desktop switcher. You need at least 4 viewports configured on 1 desktop (that's what's the problem as most people think they need 4 desktops). See the "Compiz" website documentation on how to fix this (and some other great tricks).

---


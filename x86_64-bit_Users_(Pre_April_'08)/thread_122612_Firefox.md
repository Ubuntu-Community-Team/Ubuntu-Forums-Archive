---
title: "Firefox"
date: 2006-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by thepocketdrummer on 2006-01-28
How do you get firefox to work?

I downloaded the file. Extracted it... now what?

---

### Post by towsonu2003 on 2006-01-28
first, back up your profile from the previous firefox usage:
in terminal (see below) type ```
cp -r ~/.mozilla ~/.mozilla.backup.107
```

assuming that you extracted it to
/home/yourusername/Desktop/firefox
open up a terminal
which is alt+f2 & type gnome-terminal
and ```
cd /home/yourusername/Desktop/firefox
firefox
```
you can add a launcher to your desktop. right click on desktop and choose create launcher. 
Name: Firefox
Command: /home/yourusername/Desktop/firefox/firefox
OK

---

### Post by thepocketdrummer on 2006-01-29
I'm using Kubuntu though. :???:

---

### Post by towsonu2003 on 2006-01-29
[QUOTE=thepocketdrummer]I'm using Kubuntu though. :???:[/QUOTE]
ayay I didn't check where the post was (ie Kubuntu). substitute gnome-terminal with xterm. Hopefully, xterm is there by default. (or you can apt-get it, or find what kde uses as the terminal emulator for x). the rest should be the same, except that the launcher process may be different. I'd still try right clicking on the desktop and poke arund a little bit to get a firefox icon to te desktop.  

**important**I just assumed you read the wiki. please make sure you installed (apt-get) > libstdc++5 before you launch firefox.

---

### Post by thepocketdrummer on 2006-01-29
I've noticed it seems much easier to do things in Ubuntu that it does in Kubuntu, maybe I should switch.

But I really like that taskbar :cry:

---

### Post by towsonu2003 on 2006-01-29
you can just ```
sudo apt-get install ubuntu-desktop
``` and you'll have both. then you can use the tools of gnome (or gnome itself) whenever you'd like.

---

### Post by thepocketdrummer on 2006-01-29
How much space does that require, and how do I see how much space I have?

---

### Post by Ptero-4 on 2006-01-29
Type konsole in the run box (konsole is KDE's equivalent of gnome-terminal) and then type df -h in the konsole window, it will show you how much space (in Kb, mb or GB depending on the disk capacity) you have in each partition and drive out of the total for each.

---

### Post by towsonu2003 on 2006-01-29
[QUOTE=thepocketdrummer]How much space does that require, and how do I see how much space I have?[/QUOTE]
ubuntu-desktop is a metapackage which downloads and install a bunch of other packages. I don't know how much space it needs. to check your own hd usage: ```
df -h
``` which will show space in Megabytes. 

To check how much it will download / install, you might try the frton end of apt-get in kubuntu (may be adept or kynaptic, no clue)??

---

### Post by thepocketdrummer on 2006-01-29
Ok, I did a quick search for gnome-desktop and it said about 2.1Mb does that sound about right?

Oh, and how do you go between the desktops once the other is installed?

---

### Post by towsonu2003 on 2006-01-30
[QUOTE=thepocketdrummer]Ok, I did a quick search for gnome-desktop and it said about 2.1Mb does that sound about right?
[/QUOTE]
no. I really don't know the size, but I'm pretty sure it is more than 50MB.

in *synaptic*, you search for ubuntu-desktop, choose to install, accept to install a  list of other package, hit "apply" and it asks you "this will download this much, and will install this much of megabytes, do you accept?"... ? but sorry, no clue how adept works... I would try to install it, but dial up is so slow......

the metapackage ("ubuntu-desktop") will install a bunch of packages (a long list of packages). here is the list of those packages: [http://packages.ubuntu.com/breezy/base/ubuntu-desktop](http://packages.ubuntu.com/breezy/base/ubuntu-desktop) 
it will also install packages that those packages (listed in that link) dependent on.

once you sudo apt-get install ubuntu-desktop, log out from kde (log out, not shut down), choose gnome from the "session" menu in the log in screen, and log in. it will give you an option to make gnome your default desktop, which is up to you. to get back to kde/kubuntu, log out, choose kde and log in.

---

### Post by thepocketdrummer on 2006-01-31
OK, I installed ubuntu-desktop. I have the old version of firefox and I tried following the instructions to get 1.5, but it doesn't seem to work. When I start firefox, it opens the error report window. It doesn't open firefox 1.5.

How do I fix this?

Also, I tried one way that it said to do it (which put the files in /opt and now I can't delete them. How can I delete those files?)

---

### Post by towsonu2003 on 2006-01-31
[QUOTE=thepocketdrummer]OK, I installed ubuntu-desktop. I have the old version of firefox and I tried following the instructions to get 1.5, but it doesn't seem to work. When I start firefox, it opens the error report window. [/QUOTE]
start firefox from a terminal (firefox) and copy paste the error output here, may be we can make sense of it?. but before that, make sure you installed **libstdc++5** first. it's apt-gettable.

---


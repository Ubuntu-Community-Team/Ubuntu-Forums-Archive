---
title: "Broadcom Card in SuSe"
date: 2007-08-16
forum: openSUSE and SUSE Linux Enterprise
---

### Post by polygone on 2007-08-16
I followed this tutorial, in the past, and got my wireless card working in Ubuntu.

[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

I liked Ubuntu, but decided to go with 10.2 Suse. It was my first love and I love the way it's set up.  I tried using the lspci command, but bash wasn't having it.  Does anyone know of a tutorial for this card, only geared towards a Suse 10.2 KDE user?

---

### Post by RedDwarf on 2007-08-17
[http://en.opensuse.org/SDB:Broadcom_(BCM4306)_WLAN_Installation_under_SUSE](http://en.opensuse.org/SDB:Broadcom_(BCM4306)_WLAN_Installation_under_SUSE)

openSUSE 10.2 installs lspci (no related to bash) in /sbin, and /sbin isn't in the PATH of non root users. Anyway in your tutorial lspci is only used to verify that you have a  broadcom chipset, no something that you really need.

---

### Post by igknighted on 2007-08-17
> **RedDwarf said:**
> [http://en.opensuse.org/SDB:Broadcom_(BCM4306)_WLAN_Installation_under_SUSE](http://en.opensuse.org/SDB:Broadcom_(BCM4306)_WLAN_Installation_under_SUSE)

openSUSE 10.2 installs lspci (no related to bash) in /sbin, and /sbin isn't in the PATH of non root users. Anyway in your tutorial lspci is only used to verify that you have a  broadcom chipset, no something that you really need.

To clarify this, if you want to use the command lspci (or a host of other commands), you must have the root PATH.  To do this type "su -" and enter your password.  Be aware that until you type "exit" you will be root, so be careful.  This is different than simply typing "su" to become root, because "su" does not give you the PATH.

---

### Post by polygone on 2007-08-17
OK, I know for a fact that I do have this card.  I got the tutorial to work in Ubuntu.  Do you think the same course of actions will work in Suse? or is there another tutorial.

---

### Post by walkerk on 2007-08-17
> **polygone said:**
> OK, I know for a fact that I do have this card.  I got the tutorial to work in Ubuntu.  Do you think the same course of actions will work in Suse? or is there another tutorial.

this course would work in opensuse 10.2 because i've done it. instead of using lspci i believe you can use this instead:
```
lshw -C network
```

been awhile since i've used opensuse.

---

### Post by polygone on 2007-08-17
Hey man thanks.  I will give it a whirl, when I get to my other machine. :)

---

### Post by polygone on 2007-08-17
OK, I am running into some problems.  I downloaded ndiswrapper from Sourceforge and tried to install it.  It won't work.  I get this.

```
polygone@polygone:~/Documents/ndiswrapper> make distclean
make: *** No rule to make target `distclean'.  Stop.
polygone@polygone:~/Documents/ndiswrapper> ndiswrapper
bash: ndiswrapper: command not found
```

Another problem I'm having is that it says to update.  It says to run this.

```
sudo aptitude install linux-headers-2.6.18.2-34-default
```

That, of course, is what I got when I ran the uname -r.

Now, being on suse, I've gathered that I don't have aptitude.  Is there a way to do this through YaST, or is it already current?  I am pretty confident that, if I get ndiswrapper to work, it should be smooth sailing.

Any takers?

---

### Post by igknighted on 2007-08-18
> **polygone said:**
> OK, I am running into some problems.  I downloaded ndiswrapper from Sourceforge and tried to install it.  It won't work.  I get this.

```
polygone@polygone:~/Documents/ndiswrapper> make distclean
make: *** No rule to make target `distclean'.  Stop.
polygone@polygone:~/Documents/ndiswrapper> ndiswrapper
bash: ndiswrapper: command not found
```

Another problem I'm having is that it says to update.  It says to run this.

```
sudo aptitude install linux-headers-2.6.18.2-34-default
```

That, of course, is what I got when I ran the uname -r.

Now, being on suse, I've gathered that I don't have aptitude.  Is there a way to do this through YaST, or is it already current?  I am pretty confident that, if I get ndiswrapper to work, it should be smooth sailing.

Any takers?

zypper is the CLI command you want

---


---
title: "katapult + edgy?"
date: 2006-10-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by CyberAngel on 2006-10-28
I`ve upgraded my kubuntu dapper to kubuntu edgy and katapult is not working anymore!
Program opens normally but when I press "alt + space" to bring it up, it is not working :(

Anyone else tried katapult on edgy?

---

### Post by kuja on 2006-10-28
It works for me, try this:

```
sudo apt-get --purge remove katapult
```
```
sudo apt-get install katapult
```

If it removed any metapackages when you do the purge, be sure to reinstall them. (unless you don't want to)

---

### Post by CyberAngel on 2006-10-28
> **kuja said:**
> It works for me, try this:

```
sudo apt-get --purge remove katapult
```
```
sudo apt-get install katapult
```

If it removed any metapackages when you do the purge, be sure to reinstall them. (unless you don't want to)

Thank for the tip :)
It works for me too now :-D

---

### Post by Al_maverick on 2006-10-29
I also had to do this before it started working again.

```

sudo dpkg-reconfigure katapult

```

---

### Post by ssalazar on 2006-10-29
I tried to remove and install the katapult                   package, do the     dpkg-reconfigure, and                   It doesn't work.  Besides, I can't           install       the   kubuntu-desktop   package.

---

### Post by Al_maverick on 2006-10-29
> **ssalazar said:**
> I tried to remove and install the katapult                   package, do the     dpkg-reconfigure, and                   It doesn't work.  Besides, I can't           install       the   kubuntu-desktop   package.

What I did was remove katapult and kubuntu-desktop, then removed the configuration file at /usr/share/kubuntu-default-settings/kde-profile/default/share/config (I actually copied to katapultrc.original, just in case)
After that I installed kubuntu-desktop (which also installed katapult). 

Then I ran dpkg-reconfigure katapult

After that, I ran katapult and it worked flawlessly.

Sorry, I had gone through a couple of steps I hadnt said before ](*,)

---

### Post by esplinter on 2006-10-29
I tried to do everything explained in this thread and couldnt get katapult working...what a pain  :-|

---

### Post by kuja on 2006-10-29
Why can't you, ssalazar?

---

### Post by ssalazar on 2006-10-30
I tried the propose solution by A _maverick, but it hasn't worked to me, I can either install the kubuntu-desktop package:

seba@Shadow:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: digikam but it is not going to be installed
E: Broken packages


:confused:

---

### Post by Al_maverick on 2006-10-30
> **ssalazar said:**
> I tried the propose solution by A _maverick, but it hasn't worked to me, I can either install the kubuntu-desktop package:

seba@Shadow:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: digikam but it is not going to be installed
E: Broken packages


:confused:

Check your sources.list to make sure you dont have conflicting repositories there (ie. Edgy and Dapper repositories at the same time)

Try to install digikam manually, then go for kubuntu-desktop again. The same thing happened to me with Amarok and kubuntu-deesktop. I had to first install xine libs, then Amarok, and then kubuntu-desktop.

---

### Post by ssalazar on 2006-10-30
Sorry for the long post.
I have a lot of problems with edgy.

My sources.list
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe restricted multiverse



When I tried to install digikam:

seba@Shadow:~$ sudo apt-get install digikam
Reading package lists... Done
...
The following packages have unmet dependencies:
  digikam: Depends: libgphoto2-2-dev but it is not going to be installed
E: Broken packages




When I tried to install libgphoto2-2-dev:

seba@Shadow:~$ sudo apt-get install libgphoto2-2-dev
Reading package lists... Done
...
The following packages have unmet dependencies:
  libgphoto2-2-dev: Depends: libgphoto2-2 (= 2.2.1-2ubuntu4) but 2.2.1.1.trunk-svn-r9026-0raof1 is to be installed
E: Broken packages

Katapult still doesn't work :(

:confused:

---

### Post by kuja on 2006-10-30
When was the last time you did an apt-get update? Which mirror are you using?

---

### Post by MasterHead on 2006-10-31
i have a fresh install and it doesnt work for either... 
qhen i run in console katapult it says : 

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


not sure what it means.. obviusly something's wrong but no idea what it may be.. ¿?

i have also done all the steps said in this post, removing reinstalling reconfiguring taking out the original condif, etxc.. :)

---

### Post by kuja on 2006-10-31
> **MasterHead said:**
> i have a fresh install and it doesnt work for either... 
qhen i run in console katapult it says : 

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


not sure what it means.. obviusly something's wrong but no idea what it may be.. ¿?

i have also done all the steps said in this post, removing reinstalling reconfiguring taking out the original condif, etxc.. :)
XError bad device means nothing. It's simply because by default it adds a stylus, and eraser, and maybe one other thing to the xorg.conf file. If you don't have them, it will show you that message when you start anything graphical. 

I know you've already tried much of the stuff in this thread, but try this in a konsole:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get --purge remove katapult
sudo apt-get install katapult

```

---

### Post by ssalazar on 2006-10-31
I update daily, I could install the package kubuntu-desktop, installing the dapper packages of digikam. But still I cann't use katapult.

---

### Post by kuja on 2006-11-01
ssalazar, I think I was having trouble with the us.archive.ubuntu.com mirror at one point or another, try changing it in the sources.list file to archive.ubuntu.com and doing an update, then trying to install again. (This is what I did, anyway).

---

### Post by MasterHead on 2006-11-01
thanks a lot, yesterday before going to sleep i restarted s but not with Ctr-Alt-Bck but wit kmd stop, kdm start and it startted working perfect, was just a problem of restarting completly the s system.. :) so the guide here worked out for me.. Thanks a lot ;)

---

### Post by ssalazar on 2006-11-01
I change the mirror (to cl), but katapult doesn't work, Thank for all, that tried to help me.
I have a lot of problem with Edgy and my amd64, I tried to solve anothers.

---

### Post by xardas on 2007-01-01
So I've installed Katapult on Ubuntu. I'm using fluxbox as my desktop. When I start katapult by typing "katapult" in console it gives errors of "permission denied creating directories" but when I do the same with sudo katapult it starts fine but it picks up root user's settings. So what to do?

---


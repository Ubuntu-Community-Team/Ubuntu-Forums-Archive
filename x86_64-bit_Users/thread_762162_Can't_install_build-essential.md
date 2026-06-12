---
title: "Can't install build-essential"
date: 2008-04-21
forum: x86 64-bit Users
---

### Post by Thorjelly on 2008-04-21
```
dunder@dunder-laptop:~/Dev/test$ sudo apt-get install build-essential
[sudo] password for dunder:
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
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages
```

What's that mean?

Essentially, I am trying to follow [_this page of this SDL tutorial_]("http://www.supinfo-projects.com/en/2005/tile%5Fbased%5Fgame%5Fengine/1/") but during compile it can't even find stdio.h or stdlib.h, let alone SDL.h (despite libsdl1.2debian being installed), and I am hoping build-essentials would help. I am probably doing something terribly wrong but I am pretty new this whole business, let alone Linux in general.. can anyone help?

Thanks in advanced. Sorry if this is a poor choice of subforum.

---

### Post by Ziggy72 on 2008-04-21
I'm using Hardy x86 64-bit downloaded yesterday. Everything I've tried to install so far, including build-essential, has worked without any problems. Instead of using the command line install you've tried use synaptic and see if you have a better result.

---

### Post by Vadi on 2008-04-21
I'd say make sure that your system is completely up to date (system - administration - update manager) and try again.

---

### Post by soxs on 2008-04-22
Are you able to update your system via ```
sudo apt-get update && sudo apt-get dist-upgrade
```
Edit: I had this very same error when I tried to install build essentials. Finally, I came around that my root filessystem was broken -.-

To force an filessytemcheck on next boot: ```
sudo touch /forcefsck
``` or for instant action this hsould work aswell: ```
sudo shutdown -F -h
``` [do _NOT_ press _ESC_ next boot time, unless fsck gets stuck at some point for more than 3mins]

---

### Post by Thorjelly on 2008-04-22
My system is completely up to date. It is Gutsy, by the way. I tried using the Synaptic GUI instead and got the same error -- an unresolved dependency on gpp and libc6-dev which it won't install. I tried to install gpp and libc6-dev separately; gpp installed (although I could have sworn it already was installed... I've used it), but it doesn't change the error message. build-essential still cites gpp as an unresolvable dependency. Libc6-dev won't install citing libc6 as an unresolvable dependency, even though libc6 is already installed.

I have pretty much always been able to install things before; this error message is pretty new. I tried the fdisk thing, as SOXS suggested, and stared at a blank screen for 15 minutes on reboot. How do I check fdisk logs?

---

### Post by soxs on 2008-04-22
I do not knoe where fsck logs are stored and atm I am somwhat clueless where your problem lies. Another suggestion would be, to remove the damaged packages via synaptic and try reinstalling.
Another option would be to upgrade to hardy, which ran fine for me for a while now.

---

### Post by Thorjelly on 2008-04-23
Okay, I updated to Hardy, reinstalled my graphic driver and used my backed up xorg.conf to get the resolution to work correctly, installed build-essential, libsdl1.2-dev, and compiled the code. Everything seems to be working beautifully! Thanks a lot. :)

EDIT: Oddly, when I upgraded the system it said that some packages couldn't be installed and said that maybe some of the repositories were disabled, which I'm quite sure none of them were :/ I'm not sure what that was about. Some of the packages appeared to be the ones giving me trouble. But everything seems to work fine now, so I guess I won't worry about it.

---

### Post by soxs on 2008-04-23
Just in case: Remove the packages completly via synaptics that keep bothering you and reinstall them. It *should* work fine.

---

### Post by Vadi on 2008-04-23
Also, go to System - Administration - Software Sources and make sure that in the first tab everything is enabled except source code and the CD.

(I think that's what was the problem from the beginning. But oh well, the upgrade didn't hurt anyway)

---

### Post by Thorjelly on 2008-04-23
> **Vadi said:**
> Also, go to System - Administration - Software Sources and make sure that in the first tab everything is enabled except source code and the CD.

(I think that's what was the problem from the beginning. But oh well, the upgrade didn't hurt anyway)

Pretty sure it wasn't. All of my sources were enabled. I don't think it would report that message if it were just because a repository wasn't enabled, anyway; it would have probably said that the package is referred by something else, but an appropriate package but couldn't be found.

> **soxs said:**
> Just in case: Remove the packages completly via synaptics that keep bothering you and reinstall them. It *should* work fine.

Well, I am not getting any problems anymore, it was just a message popped up before it even began downloading anything. I don't think the problem is persisting, since several of the packages listed are up to date and are installing/uninstalling fine. Incidentally, I did try to uninstall and reinstall packages before I upgraded, but it didn't help. Basically I don't know what was going on, but everything seems to be fine now. *shrug* Well, thanks for the help. :)

---

### Post by soxs on 2008-04-23
Well, then plaese mark this thread as solved.
Good to know that hardy (more or less) "fixed" it

---

### Post by Vadi on 2008-04-23
You can do that right now, the option hasn't been restored.

---

### Post by soxs on 2008-04-24
Ops, sorry. I were not aware of that.

---


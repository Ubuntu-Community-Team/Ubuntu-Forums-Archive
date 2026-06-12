---
title: "Wine broken, and I cannot fix it"
date: 2020-01-24
forum: Wine
---

### Post by Paddy Landau on 2020-01-24
Today, out of the blue, my Wine installation suddenly broke. I've tried the solutions that I've found on this forum and on [AskUbuntu]("https://askubuntu.com/"), but to no avail.

My current situation is that Wine isn't installed at all, but I do have the Wine repository:
[http://dl.winehq.org/wine-builds/ubuntu/](http://dl.winehq.org/wine-builds/ubuntu/) bionic main

Here are the results when I try to install:
```
[COLOR=#a52a2a]sudo apt install --install-recommends winehq-stable wine-stable wine-stable-i386 wine-stable-amd64
[/COLOR]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 wine-stable-amd64 : Depends: libfaudio0 but it is not installable
 wine-stable-i386:i386 : Depends: libfaudio0:i386 but it is not installable
                         Recommends: libsane:i386 or
                                     libsane1:i386 but it is not going to be installed
                         Recommends: libsdl2-2.0-0:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```
I've been going round in circles trying to fix this, but I'm lost.

Please could you help?

---

### Post by webaake on 2020-01-24
This  might solve it:

[https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)

---

### Post by Paddy Landau on 2020-01-24
EDIT: I had missed the bit about FAudio, so now it's working!

Thank you for pointing me in that direction.

---

### Post by CelticWarrior on 2020-01-24
What exactly have you tried?

You should have been able to install the missing dependency before attempting to install wine.

---

### Post by CatKiller on 2020-01-24
> **Paddy Landau said:**
> Thanks, but I've already tried that (i've just done it again, to be sure). 

On that linked page:

> Beginning with Wine 4.5, the wine-devel and wine-staging packages require libfaudio0 as a dependency. Beginning with Wine 5.0.0, the wine-stable packages will also require it. FAudio packages can be downloaded from the OBS for Ubuntu 18.04. See [https://forum.winehq.org/viewtopic.php?f=8&t=32192](https://forum.winehq.org/viewtopic.php?f=8&t=32192) for details. (FAudio packages for Ubuntu 19.10 and later are in the distro's universe repository.)

---

### Post by webaake on 2020-01-24
He's using the Wine repo. He's living on the edge.... :):):P

---

### Post by Paddy Landau on 2020-01-24
Thank you, everyone. I didn't realise that I was living on the edge :)

It's all working now, and I have to blame my (lack of) reading skills for not being able to fix it the first few times around.

Though, I have no idea why it suddenly failed in the first place!

---

### Post by CelticWarrior on 2020-01-24
> **Paddy Landau said:**
> Though, I have no idea why it suddenly failed in the first place!

The reason is explained in the quoted part of post #5 ;)

---


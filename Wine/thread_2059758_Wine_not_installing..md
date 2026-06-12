---
title: "Wine not installing."
date: 2012-09-18
forum: Wine
---

### Post by JakeTheEmerican on 2012-09-18
I'm pretty new to Ubuntu, and I am trying to install wine using terminal, it keeps giving me an error. 

```
jake@jake-Inspiron-518:~$ sudo apt-get install wine1.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1~precise1~ppa3)
           Depends: wine1.4-i386 (= 1.4.1-0ubuntu1~precise1~ppa3)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Unable to correct problems, you have held broken packages.

```

Please help out in simple terms, thanks :)

---

### Post by midocelli on 2012-10-02
I'm having the same problem, minus the update part... 

did we really screw something up or are we just missing something?

---

### Post by offgridguy on 2012-10-02
I realize I am not much help, but I could not get wine to install either and eventually
gave up trying.

---

### Post by midocelli on 2012-10-02
I think I figured it out  :)

all I did was remove wine1.5 and when I tried to install 1.4 after that it worked.

hope that helps ^^

---

### Post by Pal Csanyi on 2012-10-08
> **midocelli said:**
> I think I figured it out  :)

all I did was remove wine1.5 and when I tried to install 1.4 after that it worked.

hope that helps ^^
I haven't installed any wine on my Ubuntu 12.04.1 LTS,
and I still can't to install wine.

I have attached a file.txt gzipped.
In it is the output of the shell when I try to install wine.

Regards, from Pal

---


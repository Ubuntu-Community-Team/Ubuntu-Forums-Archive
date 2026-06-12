---
title: "how do you install wine on ubuntu"
date: 2007-12-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by soratheultima on 2007-12-13
ok i got ubuntu on my pc now i wanna get wine of course it wont work
it says that it doesn't work because these packages aren't installed
these are the packages The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: ia32-libs (>= 1.6) but it is not installable
        Depends: lib32asound2 (> 1.0.14) but it is not installable
        Depends: libc6-i386 (>= 2.6-1) but it is not installable
and i tryed it with the package installer and it has non of those in there
can someone tell me how it works

---

### Post by markusf21 on 2007-12-13
sounds like you don't have all of the repos on. Run Synaptic and click on setting then repositories and check all the boxes under the 3 tabs. Then hit the refresh button.

---

### Post by utUtu on 2007-12-13
> **soratheultima said:**
> ok i got ubuntu on my pc now i wanna get wine of course it wont work
it says that it doesn't work because these packages aren't installed
these are the packages The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: ia32-libs (>= 1.6) but it is not installable
        Depends: lib32asound2 (> 1.0.14) but it is not installable
        Depends: libc6-i386 (>= 2.6-1) but it is not installable
and i tryed it with the package installer and it has non of those in there
can someone tell me how it works

Open a terminal and then execute this code

```

sudo aptitude install binfmt-support ia32-libs lib32asound2 libc6-i386 wine

```

---

### Post by soratheultima on 2007-12-13
they were already there i dont know why there not there

---

### Post by soratheultima on 2007-12-13
and now it does this 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No candidate version found for ia32-libs
No candidate version found for lib32asound2
No candidate version found for libc6-i386
The following packages are BROKEN:
  wine 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.0MB of archives. After unpacking 50.7MB will be used.
The following packages have unmet dependencies:
  wine: Depends: ia32-libs (>= 1.6) which is a virtual package.
        Depends: lib32asound2 (> 1.0.14) which is a virtual package.
        Depends: libc6-i386 (>= 2.6-1) which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

---

### Post by Kilz on 2007-12-13
> **soratheultima said:**
> and now it does this 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No candidate version found for ia32-libs
No candidate version found for lib32asound2
No candidate version found for libc6-i386
The following packages are BROKEN:
  wine 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.0MB of archives. After unpacking 50.7MB will be used.
The following packages have unmet dependencies:
  wine: Depends: ia32-libs (>= 1.6) which is a virtual package.
        Depends: lib32asound2 (> 1.0.14) which is a virtual package.
        Depends: libc6-i386 (>= 2.6-1) which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

please open a terminal and type in ```
arch
``` and hit enter. then tell us what the results are.

---

### Post by Mze on 2007-12-13
Code

> sudo apt-get install -f 

---

### Post by soratheultima on 2007-12-13
lol bash: arch: command not found

---

### Post by Kilz on 2007-12-13
> **soratheultima said:**
> lol bash: arch: command not found

How about ```
uname -a
```

---

### Post by soratheultima on 2007-12-13
ahh Linux zofo 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux 


im just a 13 year old boy who would like to do this lol 
its frustrating

---

### Post by Kilz on 2007-12-13
> **soratheultima said:**
> ahh Linux zofo 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux 


im just a 13 year old boy who would like to do this lol 
its frustrating

There is a little problem. You see, it shouldnt say zofo, it should give the ubuntu version of gutsy. Are you sure you have ubuntu installed?

---

### Post by soratheultima on 2007-12-13
well i dont know why it says that my dad messed with it and he said he didnt so i hope i didnt do anything to mess it up

---

### Post by utUtu on 2007-12-14
I think your problem is the universe repository is not enabled.  I don't use synaptic, but if you can opne synaptic, and then under repositories, enable the universe tab.  Or if you are ok with vim or nano, edit the /etc/apt/sources.list and uncomment the 4 lines that has universe  like below
----
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
---

Then save it, and then execute

sudo aptitude update
sudo aptitude install  << as in my previous post

---

### Post by utUtu on 2007-12-14
> **Kilz said:**
> There is a little problem. You see, it shouldnt say zofo, it should give the ubuntu version of gutsy. Are you sure you have ubuntu installed?

That's ok.  'zofo' is the host name

---

### Post by krabigail on 2007-12-22
> **markusf21 said:**
> sounds like you don't have all of the repos on. Run Synaptic and click on setting then repositories and check all the boxes under the 3 tabs. Then hit the refresh button.

I had the same problem (found this thread by googling the upset packages) and this solved all my problems. Even the one about my mother-in-law (sort of). Thanks!

---

### Post by Ehtetur on 2007-12-22
> **soratheultima said:**
> ok i got ubuntu on my pc now i wanna get wine of course it wont work
and i tryed it with the package installer and it has non of those in there
can someone tell me how it works

It sounds like your trying to install 32-bit wine on your x64_86 system...
You CAN do that, but you'll need to fill lots of lib32** dependencies. :evil:

Here are the instructions for installing wine on  64-bit versions Gutsy & Feisty:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Hope it helps.

---

### Post by Marantz on 2007-12-22
Automatix installed Wine just fine for me

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by Kilz on 2007-12-23
> **Marantz said:**
> Automatix installed Wine just fine for me

[http://www.getautomatix.com](http://www.getautomatix.com)

[According to a member of the Ubuntu Techinical Board]("http://mjg59.livejournal.com/77440.html")
Automatix messes over installs for a lot of people.
It can leve you with a broken , unusable system.

---


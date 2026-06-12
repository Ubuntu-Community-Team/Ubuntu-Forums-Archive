---
title: "Can't install gcc ?"
date: 2006-08-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by steven43126 on 2006-08-25
Help, i have just installed ubuntu 64bit. Trying to install a few extra pakages and i quite a few of them won't install because of dependancy problems. For instance i get the following error when trying to install gcc

```
The following packages have unmet dependencies.
  gcc: Depends: cpp (>= 4:4.0.1-3) but it is not going to be installed
       Depends: gcc-4.0 (>= 4.0.1-2) but it is not going to be installed
E: Broken packages
steven@x1:~$

```

---

### Post by cantormath on 2006-08-25
> **steven43126 said:**
> Help, i have just installed ubuntu 64bit. Trying to install a few extra pakages and i quite a few of them won't install because of dependancy problems. For instance i get the following error when trying to install gcc

```
The following packages have unmet dependencies.
  gcc: Depends: cpp (>= 4:4.0.1-3) but it is not going to be installed
       Depends: gcc-4.0 (>= 4.0.1-2) but it is not going to be installed
E: Broken packages
steven@x1:~$

```

you could install build-essential
if you want to read about it, look up build-essential in synaptic
to install, use synaptic or in termial
laptop:~$ sudo apt-get install build-essential
gcc is in there.

---

### Post by Fass on 2006-08-25
Do you have the universe and multiverse repos enabled?

---

### Post by Kilz on 2006-08-25
> **steven43126 said:**
> Help, i have just installed ubuntu 64bit. Trying to install a few extra pakages and i quite a few of them won't install because of dependancy problems. For instance i get the following error when trying to install gcc

```
The following packages have unmet dependencies.
  gcc: Depends: cpp (>= 4:4.0.1-3) but it is not going to be installed
       Depends: gcc-4.0 (>= 4.0.1-2) but it is not going to be installed
E: Broken packages
steven@x1:~$

```

The important part of the error to me is this "E: Broken packages" It tells us you have broken packages in your system. perhaps you got a bad download. I would clean out the download cashe and try installing again.

```
sudo apt-get clean
```

---

### Post by steven43126 on 2006-08-25
Okay i tried apt-get clean.

But build essential also gives the following errors?

The following packages have unmet dependencies.
  build-essential: Depends: libc6-dev but it is not going to be installedor
                            libc-dev
                   Depends: gcc (>= 4:4.0) but it is not going to be installed
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages


All the reposiories or uncommented in the sources list. A few applications or displaying this behaviour im guessing this is a problem with some base lib somewhere?

---

### Post by Kilz on 2006-08-25
> **steven43126 said:**
> Okay i tried apt-get clean.

But build essential also gives the following errors?

The following packages have unmet dependencies.
  build-essential: Depends: libc6-dev but it is not going to be installedor
                            libc-dev
                   Depends: gcc (>= 4:4.0) but it is not going to be installed
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages


All the reposiories or uncommented in the sources list. A few applications or displaying this behaviour im guessing this is a problem with some base lib somewhere?

Sounds like one is bad. This may help dpkg -C|--audit  check for broken package(s). The command would be.
sudo dpkg --audit

---

### Post by steven43126 on 2006-08-25
Thanks for the replys but seen as it was a fresh install, i just decided to 
reinstall, problem seems to have gone away and everythig working fine, so wether it was a bad download or a corrupt repository or something i don't know.
But thanks again for the help
Steve.

---


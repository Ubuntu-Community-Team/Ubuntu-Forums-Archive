---
title: "Open office on 64 Gutsy"
date: 2007-07-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by j_dog on 2007-07-06
There was a problem installing the updates thru the update mgr. So I removed office and now can not reinstall.

Any suggestions ?   

Thanks

---

### Post by stmiller on 2007-07-06
Have you tried these:

sudo apt-get autoremove

sudo apt-get autoclean

---

### Post by j_dog on 2007-07-06
> **stmiller said:**
> Have you tried these:

sudo apt-get autoremove

sudo apt-get autoclean


Yes...no luck.

---

### Post by kuja on 2007-07-06
Welcome to the wonderful and fun world of running an unstable unstable alpha version of an operating system j_dog.

---

### Post by j_dog on 2007-07-06
> **kuja said:**
> Welcome to the wonderful and fun world of running an unstable unstable alpha version of an operating system j_dog.


Well...........Feisty was running way to good for me, I thought I would screw things up a bit .  :lol:

Here is what I get.

john@john-desktop:~$ sudo apt-get install openoffice.org
[sudo] password for john:
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
  openoffice.org: Depends: openoffice.org-core (= 2.2.1-2ubuntu1) but it is not going to be installed
                  Depends: openoffice.org-writer but it is not going to be installed
                  Depends: openoffice.org-calc but it is not going to be installed
                  Depends: openoffice.org-impress but it is not going to be installed
                  Depends: openoffice.org-draw but it is not going to be installed
                  Depends: openoffice.org-math but it is not going to be installed
                  Depends: openoffice.org-base but it is not going to be installed
                  Depends: openoffice.org-filter-mobiledev but it is not going to be installed
                  Depends: openoffice.org-java-common (> 2.2.0-4) but it is not going to be installed
E: Broken packages
john@john-desktop:~$

---

### Post by chrisccoulson on 2007-07-06
Have you tried
```
sudo apt-get install -f
```

---

### Post by Cappy on 2007-07-07
> [B]or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.[/B]
Post in the gutsy forums instead ...

---

### Post by j_dog on 2007-07-07
Thanks for everyones help. I'm off to Gutsy.

---


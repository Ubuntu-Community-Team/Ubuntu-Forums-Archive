---
title: "libcairo2 - and trouble with updates"
date: 2008-05-06
forum: x86 64-bit Users
---

### Post by xigen on 2008-05-06
AMD64 / Hardy

My updates are getting ... stuck.

Here is the error message I get when I hit the update icon:

Extracting templates from packages: 100%
dpkg: parse error, in file `/var/lib/dpkg/status' near line 2034 package `libcairo2':
 `Replaces' field, invalid package name `libc!iro0.6.0': character `!' not allowed (only letters, digits and characters `-+._')

How would you suggest that I work through this?

All the best,

MW

---

### Post by Kilz on 2008-05-06
> **xigen said:**
> AMD64 / Hardy

My updates are getting ... stuck.

Here is the error message I get when I hit the update icon:

Extracting templates from packages: 100%
dpkg: parse error, in file `/var/lib/dpkg/status' near line 2034 package `libcairo2':
 `Replaces' field, invalid package name `libc!iro0.6.0': character `!' not allowed (only letters, digits and characters `-+._')

How would you suggest that I work through this?

All the best,

MW

You may have a corrupted package in the apt-cashe
```
sudo apt-get clean
```
will clean out the apt cashe. Then try again.

---

### Post by xigen on 2008-05-07
No luck ...  here is the message I get:

Extracting templates from packages: 100%

Any other suggestions?

... and as always -- thanks ...

---

### Post by xigen on 2008-05-07
apt-cache madison libcairo2
cat -tven /var/lib/dpkg/status | sed -e '1,2033d' | sed -e '30,$d'

... there was a "!" in the name cairo. Specifically, it read c!iro.  

I wonder if this is bad memory or an issue with the file.

In any case - I backed up the file and edited it with 
sudo gedit /var/lib/dpkg/status.

It works.

---

### Post by Kilz on 2008-05-07
> **xigen said:**
> apt-cache madison libcairo2
cat -tven /var/lib/dpkg/status | sed -e '1,2033d' | sed -e '30,$d'

... there was a "!" in the name cairo. Specifically, it read c!iro.  

I wonder if this is bad memory or an issue with the file.

In any case - I backed up the file and edited it with 
sudo gedit /var/lib/dpkg/status.

It works.

Did you report the bug on launchpad so it can be fixed? You do realize that hidden in the forums , the package maintainers will never see this.

---


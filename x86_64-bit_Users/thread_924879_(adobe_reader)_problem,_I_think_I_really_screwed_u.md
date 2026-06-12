---
title: "(adobe reader) problem, I think I really screwed up."
date: 2008-09-20
forum: x86 64-bit Users
---

### Post by melvnatic on 2008-09-20
I followed some guide on the internet to install adobe reader by doing some kind of sudo dpkg --force-architecture -i Adobe Reader command. Welll....it installed right, but I wanted to remove it...

I tried sudo rm -rfd /usr/local/Adobe, but in the end I just got rid of all the files out of /opt and out of /usr/local/share/applications...which I don't think I should have done (I was pretty sure they were all adobe files though)

Now when I try to install anything I get:
```
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  acroread-escript: Depends: acroread but it is not going to be installed
  acroread-plugins: Depends: acroread (= 8.1.2.su1-0.0medibuntu0.8.04.1) but it is not going to be installed
  mozilla-acroread: Depends: acroread (= 8.1.2.su1-0.0medibuntu0.8.04.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```
Doing sudo apt-get -f install I get:
```
Unpacking acroread (from .../acroread_8.1.2.su1-0.0medibuntu0.8.04.1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/acroread_8.1.2.su1-0.0medibuntu0.8.04.1_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/acroread', which is also in package adobereader-enu
Errors were encountered while processing:
 /var/cache/apt/archives/acroread_8.1.2.su1-0.0medibuntu0.8.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Yeah...update manager claims three broken packages...and:
```
E: /var/cache/apt/archives/acroread_8.1.2.su1-0.0medibuntu0.8.04.1_amd64.deb: trying to overwrite `/usr/bin/acroread', which is also in package adobereader-enu
```

And yeah, I can't find anywhere how to install adobe reader(that works) on a 64 bit system with the firefox plugins...Gah!

---

### Post by melvnatic on 2008-09-20
Resolved, removed broken packages.

---

### Post by wimmelis on 2008-10-27
Dear all, 

To those who would run into this message having the same problem (like I did), I will give what worked for me:

```
sudo dpkg -P --force-all adobereader-enu
```

and then to get the broken packages installed and working again, do:

```
sudo apt-get --fix-broken upgrade
```

Hope this helps someone one day :)


WM

---

### Post by VeeDubb on 2008-10-27
I'm glad you found a solution, but there is a better one.

You should NEVER try to uninstall anything with "sudo rm -rfd /usr/local/anything"

In fact, unless you are 100% sure what you are doing, you should ABSOLUTELY NEVER enter any command in a terminal which begins with "sudo rm -rfd"

That's a pretty good way to destroy your system.

Any program which is installed from a .deb can be uninstalled from synaptec package manager in the administration menu.

---

### Post by kedmond on 2009-03-07
Dude.  Thanks so much.  Nothing would remove acroread-enu.  Finally.

> **wimmelis said:**
> Dear all, 

To those who would run into this message having the same problem (like I did), I will give what worked for me:

```
sudo dpkg -P --force-all adobereader-enu
```

and then to get the broken packages installed and working again, do:

```
sudo apt-get --fix-broken upgrade
```

Hope this helps someone one day :)


WM

---


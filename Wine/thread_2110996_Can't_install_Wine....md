---
title: "Can't install Wine..."
date: 2013-01-31
forum: Wine
---

### Post by smitty4478 on 2013-01-31
Hi, every time I try to install Wine it won't let me it always says "Package dependencies cannot be resolved. This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time." Is it not compatible with 12.10 yet, or 64-bit? I really don't know what to do so your help will be appreciated! Thanks. :)

---

### Post by TOMBSTONEV2 on 2013-01-31
Try this:
```
sudo dpkg --configure -a
sudo apt-get install -f
```Then:
```
sudo apt-get update
```Finally:
```
sudo apt-get install wine
```

---

### Post by offgridguy on 2013-01-31
> **smitty4478 said:**
> Hi, every time I try to install Wine it won't let me it always says "Package dependencies cannot be resolved. This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time." Is it not compatible with 12.10 yet, or 64-bit? I really don't know what to do so your help will be appreciated! Thanks. :)
Installing wine is often a problem, example in this thread.

[http://ubuntuforums.org/showthread.php?t=2103649](http://ubuntuforums.org/showthread.php?t=2103649)
I myself was never able to get wine installed, after many hours of trying. Since i do have windows, i use windows to run windows apps.

---

### Post by TOMBSTONEV2 on 2013-01-31
Odd, wine installed easy as typing sudo apt-get install wine on my machine.

---

### Post by smitty4478 on 2013-01-31
> **TOMBSTONEV2 said:**
> Try this:
```
sudo dpkg --configure -a
sudo apt-get install -f
```Then:
```
sudo apt-get update
```Finally:
```
sudo apt-get install wine
```

This is what I got back:

```
@ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.5 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by Lightning Dragon on 2013-01-31
Hello,

Try going to the Software center and see if that works. You will need to add the ppa for it though. Please see this link;

[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

---

### Post by TOMBSTONEV2 on 2013-02-01
Try this:


```
sudo apt-get autoremove wine
sudo apt-get update
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get install wine
```

---


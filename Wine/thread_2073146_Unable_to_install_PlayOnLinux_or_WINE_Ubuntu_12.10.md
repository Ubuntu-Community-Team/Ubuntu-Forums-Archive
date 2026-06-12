---
title: "Unable to install PlayOnLinux or WINE Ubuntu 12.10"
date: 2012-10-19
forum: Wine
---

### Post by Vacarsu on 2012-10-19
I downloaded the WUBI installer for 12.10, ran it, then booted. The first thing I did was try to install PlayOnLinux and I get an error popup saying, "Package dependencies cannot be resolved." 

"The following packages have unmet dependencies:
playonlinux:"

The  same thing happens when I try to install WINE. I checked the software sources to see if I had to 'tick' anything, however the Other sources tab is completely empty. All the ubuntu sources are 'ticked' too.

I am currently running 64bit Quantal Quetzel. Any help would be greatly appreciated.

---

### Post by carl4926 on 2012-10-19
Wine installed fine for me
But I used Synaptic and checked the meta package for wine 1.4

---

### Post by Vacarsu on 2012-10-19
What did your sources list look like?

---

### Post by carl4926 on 2012-10-19
> **Vacarsu said:**
> What did your sources list look like?
It's Out of the Box, nothing added

---

### Post by Vacarsu on 2012-10-19
Synaptic package manager is saying Wine 1.4 is broken. I can't even download a lower version of wine because they all seem to be dependent on 1.4. Attempting to fix broken packages doesn't work either.

---

### Post by coastwatcher on 2012-10-19
On Xubuntu 12.04.1-amd64, trying to install wine through Synaptic gets the following, depending on which package I try to mark for installation:

wine1.4:
 Depends: wine1.4-amd64 but it is not going to be installed
 Depends: wine1.4-i386 (= 1.4-0ubuntu4.1)

wine1.4-amd64:
 Depends: wine1.4-common but it is not going to be installed

wine1.4-common:
 Depends: wine1.4 but it is not going to be installed

That looks like a cycle in the graph of dependencies.  Either that, or the dependency on wine1.4-i386 is wrong.  I'm not sure which.

If that wine-1.4-i386 dependency is correct, what repository do I need to add to get it to install on a 64-bit system?

---

### Post by Vacarsu on 2012-10-19
I fixed the problem by reinstalling WUBI using the 32bit ISO. Decided not to stick with 64bit with all the problem out of the box, wasn't looking good for the future.

---

### Post by karlstad on 2012-10-23
I'm having the same problem (on x64). Can't install because of unmet dependencies. Does this problem only occur in the 64 bit version of Ubuntu? Anyone know how to fix it without reinstalling Ubuntu?

---


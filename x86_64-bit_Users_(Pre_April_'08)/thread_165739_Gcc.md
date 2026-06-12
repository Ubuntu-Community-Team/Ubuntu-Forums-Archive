---
title: "Gcc?"
date: 2006-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Equinox2004 on 2006-04-25
I have used linux for a total of four days and from what I know I need to install gcc in order to compile things.  The problem is how do I install it?  I have (or thought I have) downloaded all the packages for it through Synaptic but when I go to Add Applications it isn't in there.  I am using a fresh install of Ubuntu 5.10 on an AMD64 system.

---

### Post by alamba on 2006-04-25
apt-get install gcc<version> or install from synaptic by searching for gcc. You won't find it in add applications on on the menu screen. When you compile a package it will automatically call gcc. If u're trying to compile a program u've written then gcc <programname.ext> should work in a terminal window.

A

---

### Post by Equinox2004 on 2006-04-25
In Synaptic i've downloaded every single package that has 'gcc' in it but when I go to compile WINE (following instructions off the website) it says the compiler cannot compile executables and aborts.

---

### Post by alamba on 2006-04-25
Sorry you've lost me there. Why would you compile wine when you can install it straight off from synaptic? 

A

---

### Post by Equinox2004 on 2006-04-25
I doesn't work off Synaptic, I go to run a program with it (sudo xwine setup.exe?) and it says to install Wine.  So I tried to compile Wine instead and it won't compile because gcc is not installed.

---

### Post by alamba on 2006-04-25
From what I know, xwine is just a GUI for wine. You still need to install the wine package (search synaptic for wine not xwine and install)

A

---


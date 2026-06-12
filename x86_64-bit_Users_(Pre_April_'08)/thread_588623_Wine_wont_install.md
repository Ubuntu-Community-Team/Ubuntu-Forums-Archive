---
title: "Wine wont install"
date: 2007-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by bollofinwe on 2007-10-23
When I try to install using 
```
 sudo apt-get install wine

```

I get:

```
The following packages have unmet dependencies.
  wine: Depends: ia32-libs (>= 1.6) but it is not going to be installed
        Depends: lib32asound2 (> 1.0.14) but it is not installable
        Depends: libc6-i386 (>= 2.6-1) but it is not installable
E: Broken packages

```

Please help me.

Bollo

---

### Post by ACLerok on 2007-10-23
What happens if you type:

apt-get install ia32-libs?

What happens if you search for wine and attempt to install it through synaptic?  Does it give a more verbose error message?

---

### Post by bollofinwe on 2007-10-23
apt-get install ia32-libs gives:

```
The following packages have unmet dependencies.
  ia32-libs: Depends: lib32gcc1 but it is not installable
             Depends: libc6-i386 (>= 2.3.6-2) but it is not installable
             Depends: lib32z1 but it is not installable
             Depends: lib32stdc++6 but it is not installable
             Depends: lib32asound2 but it is not installable
             Depends: lib32ncurses5 but it is not installable
E: Broken packages

```

and synaptic gives a similar error to the first. Jus a bit more detailed.

Thanks

---

### Post by bonestonne on 2007-10-23
i could be wrong, but i do believe that you're attempting to install 32bit Wine on a 64bit system....that will not work....installing 32bit on 64bit is still being experimented/developed.

---

### Post by Bokonon on 2007-10-23
Did you go through the install directions on the wine web site?  They will have you add a key and then update your repositories for the correct version.

My install went flawlessly following their directions on Edgy/Fiesty and now Gusty.

[URL="http://www.winehq.org/site/download-deb"]
Wine HQ Install Directions[/URL]

---

### Post by jellicoe on 2007-10-23
you need to add more repositories multiverse and universe

---

### Post by chrishere01 on 2007-10-23
[http://ubuntuforums.org/showthread.php?t=587652](http://ubuntuforums.org/showthread.php?t=587652)

---

### Post by Yellow Pasque on 2007-10-24
> **bonestonne said:**
> i could be wrong, but i do believe that you're attempting to install 32bit Wine on a 64bit system....that will not work....installing 32bit on 64bit is still being experimented/developed.

I though that the 32-bit files are needed for wine because it is running Win32 programs.

---


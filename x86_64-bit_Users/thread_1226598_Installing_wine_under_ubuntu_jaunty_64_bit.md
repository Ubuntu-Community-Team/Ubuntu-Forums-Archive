---
title: "Installing wine under ubuntu jaunty 64 bit"
date: 2009-07-29
forum: x86 64-bit Users
---

### Post by baby_wallert on 2009-07-29
Hi all,

I am trying to install wine under

```
cat /etc/issue
Ubuntu 9.04 \n \l

```

64 bit.
i followed [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) and get the following error:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: ia32-libs (>= 1.6) but it is not installable
        Depends: lib32asound2 (> 1.0.14) but it is not installable
        Depends: libc6-i386 (>= 2.6-1) but it is not installable
        Depends: lib32nss-mdns (>= 0.10-3) but it is not installable
        Recommends: ttf-liberation but it is not installable
        Recommends: winbind but it is not installable
        Recommends: ttf-mscorefonts-installer but it is not installable
E: Broken packages

```Please help me to install wine :)

Thanks in advance

---

### Post by 3Miro on 2009-07-29
That is odd, since it worked for me. What is your CPU?

---

### Post by baby_wallert on 2009-07-30
Hi,

finally I got it installed using aptitude instead of apt-get.

Greetz

---

### Post by wolfgar on 2009-07-31
Ultamatix / Version: 1.8.0-7

It works great for installing a lot of stuff.

Check it out here:  [http://ultamatix.com/](http://ultamatix.com/)

Download it from here:  [http://downloadue.info/repo/ultamatix-1.8.0-7_all.deb](http://downloadue.info/repo/ultamatix-1.8.0-7_all.deb)

Enjoy,

Wolfgar

---


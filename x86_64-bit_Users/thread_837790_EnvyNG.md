---
title: "EnvyNG"
date: 2008-06-22
forum: x86 64-bit Users
---

### Post by heinzbitte on 2008-06-22
My version of EnvyNG only has the 8-4 version of fglrx.  I've tried removing it and adding it again.  It still has this.

How can I update it or install fglrx a different way?

---

### Post by stchman on 2008-06-23
> **heinzbitte said:**
> My version of EnvyNG only has the 8-4 version of fglrx.  I've tried removing it and adding it again.  It still has this.

How can I update it or install fglrx a different way?

You should just install the following:

```
sudo apt-get install xorg-driver-fglrx
```

That is the restricted ATI driver.

---

### Post by markbuntu on 2008-06-23
If you want the newest 8.6 ATI driver you can get it here:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/)

Directions for installing it are here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Directions for tweaking it are here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

Envy has caused me nothing but problems with my ATI driver installs.

---

### Post by stchman on 2008-06-23
The fglrx drivers in Hardy's repos are the 7.1 ATI drivers.

They are solid and work well with Compiz.

---

### Post by soxs on 2008-06-25
Latest one (8.6) works like a charm for me (3870 RadeonHD)
Since 8.6, the installer has an upgraded api for installing the driver.
See: [http://ubuntuforums.org/showthread.php?t=840092](http://ubuntuforums.org/showthread.php?t=840092)

---


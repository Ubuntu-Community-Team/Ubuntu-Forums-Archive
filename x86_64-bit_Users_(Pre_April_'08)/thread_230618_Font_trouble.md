---
title: "Font trouble"
date: 2006-08-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by tomek.vz on 2006-08-06
Hello!

I tried to make linux versions of ePSXe and Zsnes to work on Ubuntu,and i have basically manually installed all the 32bit libs that they needed in /usr/lib32.ePSXe works,but Zsnes does not.Hovewer,that is not the problem.It loks like i have done something bad because i have problem with fonts in Firefox 32bit and OpenOffice.org.It looks like this:

[[IMG]http://img233.imageshack.us/img233/6397/screenshottl3.th.png[/IMG]](http://img233.imageshack.us/my.php?image=screenshottl3.png)

I think that i have to reinstall something...but what :confused:

---

### Post by flying_icarus on 2006-08-06
Apparently you're not the only one with this problem. :)

The details are on [https://launchpad.net/distros/ubuntu/+source/ia32-libs-gtk/+bug/55058](https://launchpad.net/distros/ubuntu/+source/ia32-libs-gtk/+bug/55058)

And the temporary fix is to install an earlier version of the broken library, like this:

```
sudo apt-get install ia32-libs-gtk=16
```

---

### Post by tomek.vz on 2006-08-06
Thanks :-) It works now :rolleyes:

EDIT: this is repaired in 16.2 :-)

---


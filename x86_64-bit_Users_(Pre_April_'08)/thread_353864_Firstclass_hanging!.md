---
title: "Firstclass hanging!"
date: 2007-02-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Norfolk 'n' Good on 2007-02-05
Hi,

I have downloaded '**fcc-8.090-1-Linux-i686.deb**', installed it via the package installer, but when I click on it's icon in the Applications menu it fails to load.

Any ideas would be greatly appreciated.

PS. Running Edgy 6.10 x64 on an AMD64.

---

### Post by cmost on 2007-02-05
Well, offhand I'd say you have a deb for the wrong architecture.  Did you get any errors when you tried installing this?  Did you use dpkg -i --force architecture?

---

### Post by ravenon on 2007-02-05
I installed it using dpkg -i --force-architecture
After installation, I ran /opt/firstclass/fcc in a terminal. Likely some library files will be missing and you can chase them down at packages.ubuntulinux.org
Make sure you get the i386 debs, unpack them and grab the lib files. They need to go in /usr/lib32

Also, make sure you have installed the ia32-libs from the dapper/edgy repositories.

---

### Post by Norfolk 'n' Good on 2007-02-06
Thanks for your replies chaps.

I'm a complete beginner at this Linux stuff, so I will need you to walk me through it a bit more please.

I downloaded '**fcc-8.315-2-Linux-i686.deb**', which I tried installing via the package manager; there is even an icon in my Applications folder.  I then tried reinstalling the package using your suggested command and this is all I got...

```

root@ubuntu64:~/Desktop# dpkg -i fcc-8.315-2-Linux-i686.deb --force-architecture
dpkg: error processing fcc-8.315-2-Linux-i686.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing --force-architecture (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 fcc-8.315-2-Linux-i686.deb
 --force-architecture

```

I also downloaded the i386 version and scoured it for the **lib** files you suggested, but again I was unsuccessful there too.  I need this working if I can because it's a massive part of my Open University course.

Thank you once again.

---

### Post by Norfolk 'n' Good on 2007-02-06
PS.. In response to cmost's post, there were no error messages about architecture when I installed these packages.

---

### Post by BIGtrouble77 on 2007-02-06
I think this is the correct syntax:
```
dpkg -i --force-architecture fcc-8.315-2-Linux-i686.deb
```

---

### Post by sam81 on 2007-04-16
firstclass hangs a lot on Linux anyway (I'm on i686), and I've found no other solution to make it work than rebooting...and crossing your fingers

---

### Post by ravenon on 2007-04-16
The version 8.315 gave me nothing but trouble on linux, including hanging when launching from an icon. I reverted to version 8.101 and most of the time it is fine. It does hang occasionally but you can kill it as a user process.
Another way to launch is Alt-F2 and then type /opt/firstclass/fcc. That way has never failed me.

---

### Post by Kilz on 2007-04-16
[Click Here for instructions]("http://tghc.org/32biton64bit.php") on how to get 32bit applications running on 64bit Ubuntu.

---


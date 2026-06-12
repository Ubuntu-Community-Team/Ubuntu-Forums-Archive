---
title: "Cyberpower UPS on Ubuntu Server 64 bit"
date: 2009-10-10
forum: x86 64-bit Users
---

### Post by southerngeek on 2009-10-10
I have a cyberpower 485VA UPS that I have previously had plugged in to my 32 bit Jaunty desktop system, and it was detected and monitored fine by the Gnome power manager. Now I have the same UPS plugged into a 64 bit Jaunty server, with no graphical enviroment. I have gotten everything else working with no problem, however I fiddled with NUT for 3 hrs this afternoon without success. I know that it works in gnome, and it also has the Linux PowerPanel software availible for it, but that is only for 32 bit platforms. Anyone got any suggestions? :confused:

---

### Post by tcrapper on 2009-10-28
You can get the linux powerpanel software to work by installing ia32-libs and then forcing the installation of the 32bit package.

```
sudo apt-get install ia32-libs
wget http://www.cyberpowersystems.com/software/powerpanel_1.1.2_i386.deb
sudo dpkg -i --force-architecture powerpanel_1.1.2_i386.deb

```

To use run pwrstat, which will show the help. You have to run it as root for it to work.

```
sudo pwrstat -status
```

---

### Post by southerngeek on 2009-10-30
ok thanks for your help I'll try it and see how it turns out :)

---

### Post by southerngeek on 2009-10-30
Update: I just looked on the Cyberpower website and they now have a 64bit version of the software

---


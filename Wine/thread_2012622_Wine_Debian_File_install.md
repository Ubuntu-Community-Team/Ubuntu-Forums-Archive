---
title: "Wine Debian File install"
date: 2012-06-29
forum: Wine
---

### Post by Joshua Parsons on 2012-06-29
Downloaded: [libwine-alsa-unstable_1.5.5-0.1_i386.deb]("http://dev.carbon-project.org/debian/wine-unstable/libwine-alsa-unstable_1.5.5-0.1_i386.deb")
 
Opened terminal and tried to install it and got this result...? Did it work
 
> 
joshua@joshua-c6535:~$ sudo dpkg -i cd Documents/libwine-alsa-unstable_1.5.5-0.1_i386.deb
dpkg: error processing cd (--install):
cannot access archive: No such file or directory
(Reading database ... 140555 files and directories currently installed.)
Preparing to replace linewine-alsa-unstable 1.5.5-0.1 (using .../libwine-alsa-unstable_1.5.5-0.1_i386.deb)...
Unpacking replacement libwine-alsa-unstable ...
dpkg: dependency problems prevent configuration of libwine-alsa-unstable:
libwine-alsa-unstable depends on libwine-unstable (= 1.5.5-0.1); however:
Package libwine-unstable is not installed.
dpkg: error processing libwine-alsa-unstable (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
cd
libwine-alsa-unstable
joshua@joshua-c6535:~$ 

---

### Post by afixane on 2012-06-29
> **Joshua Parsons said:**
> joshua@joshua-c6535:~$ sudo dpkg -i cd Documents/libwine-alsa-unstable_1.5.5-0.1_i386.debdpkg: error processing cd (--install):
cannot access archive: No such file or directory
(Reading database ... 140555 files and directories currently installed.)
Preparing to replace linewine-alsa-unstable 1.5.5-0.1 (using .../libwine-alsa-unstable_1.5.5-0.1_i386.deb)...
Unpacking replacement libwine-alsa-unstable ...
dpkg: dependency problems prevent configuration of libwine-alsa-unstable:
libwine-alsa-unstable depends on libwine-unstable (= 1.5.5-0.1); however:
Package libwine-unstable is not installed.
dpkg: error processing libwine-alsa-unstable (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
cd
libwine-alsa-unstable
joshua@joshua-c6535:~$

No need to use "cd", but use 
```
sudo dpkg -i ~/Documents/libwine-alsa-unstable_1.5.5-0.1_i386.deb
```

---

### Post by Joshua Parsons on 2012-06-29
Results
> 
[EMAIL="joshua@joshua-C6535:~$"]joshua@joshua-C6535:~$[/EMAIL] sudo dpkg -i ~/Documents/libwine-alsa-unstable_1.5.5-0.1_i386.deb
[sudo] password for joshua:
Sorry, try again.
[sudo] password for joshua: 
(Reading database ... 140555 files and directories currently installed.)
Preparing to replace libwine-alsa-unstable 1.5.5-0.1 
(using .../libwine-alsa-unstable_1.5.5-0.1_i386.deb) ...
Unpacking replacement libwine-alsa-unstable ...
dpkg: dependency problems prevent configuration of libwine-alsa-unstable:
 
libwine-alsa-unstable depends on libwine-unstable (= 1.5.5-0.1); however:
  
Package libwine-unstable is not installed.
dpkg: error processing libwine-alsa-unstable (--install):
 
dependency problems - leaving unconfigured
Errors were encountered while processing:
 
libwine-alsa-unstable

 
but, in the upper right a red circle with a minus sign comes up and says
 
> 
An error occured, please run package manager from the right-click menu or apt-get in a terminal to see what is wrong. There error message was: 'Error: BrokenCount > 0'. this usually means that your installed package have unmet dependencies.


---

### Post by afixane on 2012-06-29
The error message has same meaning. It's mean you've unmet dependency.

---

### Post by Joshua Parsons on 2012-06-29
Ok, so how can i get the met dependency? Like is there a different db file i need or would an older version work?
 
Like I got the deb file from here
 
[http://dev.carbon-project.org/debian/wine-unstable/](http://dev.carbon-project.org/debian/wine-unstable/)

---

### Post by afixane on 2012-06-29
Are you connected to internet? If yes, just type this

```
sudo apt-get install wine1.4
```

---

### Post by oldos2er on 2012-06-29
Installing packages meant for a different distro is not really a good idea unless you know exactly what you're doing. May I ask why you're not using wine from Ubuntu's repositories?

---

### Post by laopaishpe on 2012-12-13
same reason I'm here: 307 MB of crap dependencies, which is a bit much when you try to fit everything on a 4GB usb stick (yes, I could, I have 1.7G left, thanks2 LXDE, but y would I ?)

---


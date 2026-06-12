---
title: "Installing WINE from the software center"
date: 2011-10-24
forum: Wine
---

### Post by Mazate on 2011-10-24
I'm looking to install wine but I'm not seeing it in the software center.  I several add-on meta packages but not the application itself.  Am I missing something?  Do I have to just add the winehq repositories?

---

### Post by TeoBigusGeekus on 2011-10-24
Do you get any error messages with
```
sudo apt-get install wine
```
?

---

### Post by holycow131415 on 2011-10-24
install playonlinux. its wine with a front-end to it.

---

### Post by blackmail on 2011-10-24
Better yet visit [wine]("winehq.org") homepage and download it, it is always the newest version, mainly it should be 1.2 the stable one and 1.3 the beta one. Install 1.2 and you should be fine...

Please report back in case you need anything further or if this doesn't help your cause :)

---

### Post by Perfect Storm on 2011-10-24
Moved to wine section.

---

### Post by ubupirate on 2011-10-24
The best and easiest way to get Wine is from PPA:

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
```Then to install stable (1.2.3):

```
sudo apt-get install wine1.2
```or development (1.3.3x):

```
sudo apt-get install wine1.3
```And after Wine is installed simply configure it:

```
winecfg
```

---


---
title: "Installing wine(need help I n00b)"
date: 2008-05-23
forum: Wine
---

### Post by videoman1994 on 2008-05-23
OK I have absolutely no idea how to do it how to configure it or just how to install it or download it so please help. 

My brother installed ubuntu and now he went to colledge so know I am left to try nd install this stuff so please help. thanked ahead

---

### Post by stinger30au on 2008-05-23
piece of cake

if your using 8.04 this will help you

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by forrestcupp on 2008-05-23
just install the version from the official repos, and you should be alright for now.
```
sudo apt-get install wine
```
To configure it, type in a terminal
```
winecfg
```
Then you can either run a program from the terminal by changing to the appropriate directory and using the **wine** command
```
cd */correct/directory*
wine *programname.exe*
```
or you can set exe's to open with wine and just double click them in nautilus.

For future reference, there is a subforum here specifically for wine.

---


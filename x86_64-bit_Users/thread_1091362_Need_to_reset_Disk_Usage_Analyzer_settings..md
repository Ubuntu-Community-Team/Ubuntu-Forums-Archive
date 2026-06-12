---
title: "Need to reset Disk Usage Analyzer settings."
date: 2009-03-09
forum: x86 64-bit Users
---

### Post by mªrty on 2009-03-09
Hi, this isn't a 64bit problem, but I am running 8.10 x86_64. The last time I ran Disk Usage Analyzer, I changed some settings & now when I try to open it, it just disappears as soon as it appears in the taskbar.

I tried to add and remove via Synaptic, but I don't know the package name. Is there an easier way to reset it's settings to default?
Thanks

---

### Post by cariboo on 2009-03-09
The name of the application is baobab, if you don't know the name of an appliction in the menus, right-click and choose Edit Menus, select the applications and click the properties button. See screenshot.

To remove the application completely open a Applications-->Accessories-->Terminal and type:

```
sudo apt-get purge baobab
``` 

Jim

---

### Post by mªrty on 2009-03-12
```
martin@ubuntu64:~$ sudo apt-get purge baobab
[sudo] password for martin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package baobab is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
martin@ubuntu64:~$ sudo apt-get install baobab
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package baobab is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  gnome-utils
E: Package baobab has no installation candidate

```I tried reinstalling gnome-utils and I still get this when I try to run baobab:
```
martin@ubuntu64:~$ baobab
Segmentation fault
martin@ubuntu64:~$ 
```

---

### Post by mªrty on 2009-03-12
I finally solved the problem, here's how:

I had to run **gconf-editor**, then go to **apps/baobab/properties**, then double click on skip_scan_uri_list and remove the line that only had "**file:///**"

Voila!

---


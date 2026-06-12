---
title: "Problem facing while installing Gloobus on ubuntu 8.10 64 bit"
date: 2008-11-11
forum: x86 64-bit Users
---

### Post by cr01nk on 2008-11-11
Hi,

First of all i would like to thanks the creator for gloobus.

I have been trying to install Gloobus on my system as stated above , my system is 64 bits , but there seems to be some problem while using gloobus

I downloaded the latest version of Gloobus-Preview from Launchpad; extracted it; and run the command
sudo ./install.sh
then to test gloobus preview , which is now installed in my /usr/bin/ directory I type in the following command in my terminal
$gloobus-preview ~/Pictures/path/to/file.jpg
Now if every thing would have worked write my system should give me preview of it.
But instead it gives me an error saying
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
(process:15629): Gnome-CRITICAL **: gnome_program_module_register: assertion `module_info' failed

(process:15629): Gnome-CRITICAL **: gnome_program_preinit: assertion `argv != NULL' failed
/home/cr01nk/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/cr01nk/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/cr01nk/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
LOADING PLUGINS:
  /usr/share/gloobus/plugins-preview/iDefault.so
  /usr/share/gloobus/plugins-preview/iMp3.so
Error loading Plugin: libtag.so.1: cannot open shared object file: No such file or directory
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

then i thought that libtag.so.1 files is not present in my system i check it and it was there. so another case could be that gloobus could not see this file.... And thats where the problem start . I linked /usr/lib/libtag.so.1 with /usr/share/libtag.so.1 also with /usr/share/gloobus-preview/libtag.so.1 and with /usr/share/gloobus-preview/plugin-preview
using
$sudo ln -s /filetolink /pathtolink

But still there is same problem.
on using
$whereis libtag.so.1
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
libtag.so: /usr/lib/libtag.so /usr/lib/libtag.so.1 /usr/lib64/libtag.so /usr/lib64/libtag.so.1 /usr/share/libtag.so.1
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
I get the following.
Can anyone tell me where is the problem. How could i rectify it?

(I have taken care of all the related dependencies with Gloobus and i dont think there is some problem in that)
(I have also done $sudo getlibs /usr/bin/gloobus-preview)

---

### Post by cr01nk on 2008-11-11
Edit bz : Duplicate post, merged :)

---

### Post by cariboo on 2008-11-11
Have you checked with the developer? He may be able to help you solve your problem. His email address is on the Gloobus page.

Jim

---

### Post by Yellow Pasque on 2008-11-11
[http://linux.softpedia.com/progDownload/Gloobus-Download-38543.html](http://linux.softpedia.com/progDownload/Gloobus-Download-38543.html)
It's a 32-bit program, so it needs a 32-bit version of libtag.so.1 in /usr/lib32
I was able to get the above version working. After I installed, I:
```
sudo getlibs /usr/bin/gloobus-preview
sudo getlibs -l libtag.so.1
```

---

### Post by cr01nk on 2008-11-18
Thanks for reply.

I did tried what is suggested above ... and it didn't work

Anyway i m waiting for the developer of Gloobus to reply on this..
till them i m using old version of gloobus which is working fine.

---

### Post by badchoice on 2009-03-16
Did you solved the problem?

---


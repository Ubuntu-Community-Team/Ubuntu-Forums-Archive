---
title: "How to get Wine to see Win apps?"
date: 2008-03-18
forum: Wine
---

### Post by barney_xuf on 2008-03-18
After installing Wine 0.9.57, how do I install Win apps in/on it?
These are downloaded apps, no CD install media.

I've tried several things suggested in various forum posts, but nothing seems to work.  Winecfg shows Program Files and Windows directories, but nothing significant beneath them.

Program Files contians Common Files (empty) and Internet Explorer (iexplore.exe) directories, while Windows holds a mix of directories and files for a total of 17 objects.

Command line attempts have been equally frustrating.  If I try, "wine program.exe," Wine complains, "wine: could not load L"C:\\windows\\system32\\program.exe": Module not found
barney@gu3ggw:~$ err:advapi:service_control_dispatcher pipe connect failed."
If I use the command, "wine "C:\\Program Files\\Program Dir\program.exe," the error is returned, "wine: cannot find 'C:\Program Files\Program Dir\program.exe'."

All attempts to date have failed.  Wine menu shows only Notepad as a viable application.

Obviously I'm doing something wrong, but I've no idea what.

Oh, this is on a box with WinXP, XUbuntu, GUbuntu and KUbunto each installed on separate partitions of a 240GB HD.  I'm currently trying to install Wine on the GUbuntu (Gnome) distro.
And one of the apps I'm trying to run is Info Select, which is in the AppDB - yeah, I read it, but no soap ... before I can do anyting about libraries & graphics, I need to be able to find the app.

'Preciate any help anyone might be able to offer.

Make a good day...
                            ... barn

---

### Post by grazzt_85 on 2008-03-18
check the wine's site for supported apps.

You might consider using virtualbox for windows applications. With that you can run every application you want, because in fact you run the whole windows os, except games (direct3d is not supported)

[www.virtualbox.org](www.virtualbox.org)

---

### Post by Lord Illidan on 2008-03-18
Let's say you have setup.exe in a directory. For the sake of argument, let's say it is in your /home/gu3ggw/Downloads directory.

So.

```
cd ~/Downloads
wine setup.exe
```

EDIT : The shortcut for the installed application will probably appear in the Applications menu. If not, you can usually navigate to the wine directories and try to open them with wine manually.

---

### Post by barney_xuf on 2008-03-18
Lord Illidan,
Thanks, I finally figured out - about half an hour ago - that I had to have the setup files on the Ubuntu partition.  My understanding previous to that was that Wine would pick up the apps from the Windows partition.

Grazzt_85,
I've tried several times to compile the VirtualBox system over the last couple of days ... it never creates the vboxdev element ... errors that haven't scrolled of the screen indicate that Kernel configuration is invalid, include/linux/autoconf.h or include/config/auto.conf are missing.

They're both there, of course ... so there's prolly a version conflict, but I simply don't have enough knowledge to resolve it.  I suspect there were other errors in the kmk command or the make command, but they've scrolled out of the 500 line console limit.

What I was hoping to find - and thought Wine was - is something that will let me share data files 'twixt Linux & Win.  Alas, that seems not possible with what I've found to date <sigh />.

Make a good day ...
                           ... barn

---


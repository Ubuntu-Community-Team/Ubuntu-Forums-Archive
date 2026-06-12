---
title: "MONO 1.8 in ubuntu x64"
date: 2005-06-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by abiezerm on 2005-06-25
hi all

how can i install mono and monodevelop in my ubuntu x64??

thanks.

---

### Post by negatory on 2005-06-25
I've downloaded the installer from [http://www.mono-project.com/Downloads](http://www.mono-project.com/Downloads) and it installed ok!But when I try to run monodevelop I get:
```
Unhandled Exception: System.DllNotFoundException: libgnomeui-2.so.0
in (wrapper managed-to-native) Gnome.Modules:libgnomeui_module_info_get ()
in <0x0000a> Gnome.Modules:get_UI ()
in <0x0045a> MonoDevelop.SharpDevelopMain:Main (System.String[] args)
```
And similar  System.DllNotFoundException occur when I try to run mono applications.
Didn't get much effort to try and solve it....
Any thoughts on this are welcome.
Thanks
Pedro Carrico

---

### Post by Ryan FB on 2005-06-28
[QUOTE=negatory]I've downloaded the installer from [http://www.mono-project.com/Downloads](http://www.mono-project.com/Downloads) and it installed ok!But when I try to run monodevelop I get:
```
Unhandled Exception: System.DllNotFoundException: libgnomeui-2.so.0
in (wrapper managed-to-native) Gnome.Modules:libgnomeui_module_info_get ()
in <0x0000a> Gnome.Modules:get_UI ()
in <0x0045a> MonoDevelop.SharpDevelopMain:Main (System.String[] args)
```
And similar  System.DllNotFoundException occur when I try to run mono applications.
Didn't get much effort to try and solve it....
Any thoughts on this are welcome.
Thanks
Pedro Carrico[/QUOTE]
Try:```
sudo updatedb && locate libgnomeui-2.so.0
```If that gives you a path (like "/usr/local/lib") that libgnomeui is in, take that path and do:```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/path/where/the/library/is
```Then try to run monodevelop. Repeat the locate/export step for any more libraries it says it can't find.

---

### Post by Mr. Electric Wizard on 2005-06-29
So have you created any apps yet?
I am completely intruiged with this....
.Net developement on a linux box. \\:D/

---

### Post by negatory on 2005-06-29
@Ryan FB:
It didn't work!The error is the same...any other ideas?
Thanks for your thoughts!
Pedro Carrico

---

### Post by abiezerm on 2005-06-29
deam,  it looks like the mono has problems in the x64 platform.

only can wait. 

thanks all folks.

---

### Post by negatory on 2005-06-30
@abiezerm:
I'm not so sure of that...I think it is a configuration problem.But as I said before I haven't tought about it too much.I'm in the middle of exams and not at home most of the times.When this is all over I'll get to this problem and see what I can do to put mono working.
And by the way,have you googled it up about mono with x86_64?
Thanks
Pedro Carrico

---

### Post by bukagedi on 2005-07-29
Standard installation puts all MONO software in /usr/local/lib thus you must set environment variables:
       PATH, PKG_CONFIG_PATH, LD_LIBRARY_PATH
PATH and PKG_CONFIG_PATH may be set in /etc/X11/Xsession.d directory: I did new file "56gnome_develop_environment" in this directory and wrote my settings. This trick does not work with LD_LIBRARY_PATH: I had to write it at start of ~/.bashrc (look at my question).
Login into your system again after these settings.
Run ./configure scripts again and study output messages to find what is wrong on your system, if environment setting helps nothing.

Gediminas Bukauskas
[email]audriusb@homelan.lt[/email]

---

### Post by Mad Leguan on 2005-07-29
I used Mono in a bigger kind of exercise at university and so far it works well under linux ,too.
I didn't manage to get the installer to work right, but installing from sources gone right without any problems. So why don't try this?

---

### Post by bukagedi on 2005-07-29
I just installed MONO on AMD64, UBUNTU HOARY. Met some problems, but easy fixed them. Most of them required to install one or two DEVELOP packages. I think that your problem is related to: absence one of environment variable, bad sequence of installation or absence some libraries.

---

### Post by niC666 on 2006-01-13
I am getting the exact same libgnomeui-2.so.0 errors when trying to run monodevelop. I have installed it from the installer and from source and both times i come up with this. I have tried setting the variables mentioned in this thread, but nothing is working.

Did anyone manage to get around this problem? has anyone managed to get mono to work properly on hoary amd64?

any help is appreciated

---


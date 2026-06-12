---
title: "userconfig won't start on AMD64 LTSP"
date: 2006-09-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by floyd24 on 2006-09-05
Hi @all,

i admit I may have a special setup, but I experience the following strangeness when trying to add new users to my System.

First, what is my setup? I run ubuntu-server v6.06 inside a Xen VM with KDE-deskop and LTSP installed. I connect from a Thin Client via a PXES 1.0 Boot image over PXE Boot, logging onto the server via XDMCP.

I log in as normal user, then "KDE-Menu -> System Settings -> Users & Groups. Everything fine till here.

But when I change into Administrator's Mode, I get:

"The module Users & Groups could not be loaded."

When I try "kcmshell userconfig" as root from the console, the following error appears:

--
Xlib: connection to "<my client's ip here>:0.0" refused by server
Xlib: No protocol specified

kcmshell: cannot connect to X server <my client's ip here>:0.0
--

This is not bugging me much, since I'm quite familiar with using the console, but strange anyway.

Can anyone shed any light on this? May be something that should/could be fixed?

Another thing that doesn#t really wirk with my setup is my wireless Mouse (Cherry F-8900) which does almost single-click as a double click. This has almost driven me insane in the first place, urging me to switch back to a cable mouse until I find a solution.

Any Ideas appreciated. In any case Ubuntu is a very nice peace of work. I am working on migrating all my machines from Mandriva to Ubuntu at the moment. Thanks for it all @ the devs!

---

### Post by kuja on 2006-09-05
I don't know if it's 100% related, but I sometimes have issues getting things to switch to root... Try running "kdesu kcmshell userconfig" and see if things run any smoother then. Does it seem to give any trouble with any other things in system settings? Will it let you get to it through kcontrol or systemsettings?

---

### Post by floyd24 on 2006-09-06
It's the same problem when I issue the command via kdesu. The funny :-? thing is that I can use most of the System-Settings Apps, even switch to Administrators Mode in most of them. But it doesn't workw with the Users & Groups module, and yesterday i found out that the same problem occurs with the "Display" App from that panel.

---

### Post by kuja on 2006-09-06
Well, I've got no idea where to go with this one really. If I were you I'd head over to launchpad.net and file a bug report for it.

---


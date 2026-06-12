---
title: "win vncviewer grey no gui"
date: 2008-03-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Onbeperkt on 2008-03-20
Hello guys,

I searched all over the internet for this problem, but whithout luck.
i have vnc4server installed and when i connect with vncviewer on window i see no gui and have grey things.

my xstartup:

#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &


x-window-manager &
exec gnome-session

when is use the normal vncserver i can't even connect and also can't connect local. When i connect to local it says connection refused (111)
i dont know whats going on can anyone help me?

---

### Post by Onbeperkt on 2008-03-20
<solved>

sudo vi /etc/gdm/gdm.conf

Find XDMCP section and set enable to True
Enable=True

uncomment
# RemoteGreeter=/usr/lib/gdm/gdmlogin

thats all.
I think its strange to do these things. Normal users like me can't figure this out. I found it because a guy on internet wrote something about this.

---


---
title: "Invalid MIT-MAGIC-COOKIE-1 key"
date: 2007-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-01-20
Dapper AMD-64 laptop

Everything has always worked fine, but suddenly when I try to log in I just get dumped back to the login screen. 

I exited to a command line (Ctrl-Alt-F1) and typed "startx." This gave me:

```
xauth: Creating new authority file for /home/jjj/.serverauth.5382
xauth: Creating new authority file for /home/jjj/.Xauthority
xauth: Creating new authority file for /home/jjj/.Xauthority

Fatal server error
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again

Xlib: Connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
giving up
xinit: Unable to connect to X server
xinit: No such process (errno 3): Server error
```
I googled and evidently this is a common problem. However, most of the posts I found were from people on RPM based systems. And none of the suggestions I found have helped.

I am currently logged in as root by using the recovery boot option. Most everything is working, except half my programs are not listed in the Applications menu, and none of the tweaks I have made to the Gnome desktop are here. I could reconfigure this, but it would take days, plus I don't want to be running as root.

How can I get X running again as my usual account?

---

### Post by John Jason Jordan on 2007-01-20
I've spent over ten hours trying to fix this. I have a list of all the things I have tried, but it would be a couple pages long.

In working on this problem I realized that the last thing I did that might have caused this was to use Update Manager to update the kernel and nvidia-glx. Afterward I continued to use the computer for a day and a half or so before shutting down (it's a laptop). It was when I restarted it that the problem occurred. Note that I am using the nv driver, not the proprietary nVidia driver. At one time I did use the proprietary driver, and evidently Update Manager thinks it still needs to be updated. 

I could really use some suggestions here!

---


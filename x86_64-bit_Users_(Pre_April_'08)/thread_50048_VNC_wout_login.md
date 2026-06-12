---
title: "VNC w/out login?"
date: 2005-07-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by viniosity on 2005-07-18
I want to give remote access to by AMD64 to a friend of mine.  I gave him his own account on my box but it requires that he/me be logged in to the desktop in order to use VNC.  Is there any way around this?  Else, what are the chances of getting NX server to work with AMD64?

---

### Post by netrattler on 2005-07-18
freenx worked for me without any problems, then you could just have him download the nxclient from nomachine website.

Joe

---

### Post by viniosity on 2005-07-18
Can you please please please tell me how to get freenx on AMD64?  The last I heard packages were missing that let it work.  I have added these two lines to my /etc/apt/sources.list:

```

deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-backports main universe multiverse restricted
deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-extras main universe multiverse restricted

```

But there is still no package for freenx or nxserver. In fact doing an apt-cache search for freenx shows nothing.  So I've either got the wrong repo or I'm going about it the wrong way.  Either way I could sure use a hand.

---

### Post by filterban on 2005-07-19
Try requesting the package for either of these progs in the "amd64 packages" thread.  Tamir & co may just help you out.

---

### Post by Saru san on 2005-07-19
NX will give you a nicer connection if you can get it going, but you can always have him SSH in forwarding the appropriate port and start a VNC server from the shell. You'll need a full VNC server installed, not just Vino. Thankfully it's very easy.
Grab it here for your architecture and install.
```
http://packages.debian.org/stable/x11/tightvncserver
```
Have him ssh to your AMD64 box forwarding 5902 from his client then edit ~/.vnc/xstartup to read
```
#!/bin/sh
exec gnome-session
```
then run
```
$ vncserver :2
```
He can then open a vnc viewer on his local machine and connect to localhost:2
He can log out and leave that server running but it's better to kill it with
```
$ vncserver -kill :2
```

Google will give you much better info than I can here, but this is a start.

---

### Post by viniosity on 2005-07-19
When I try to start the vncserver I get this error:

```

Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the tightvncserver script.
Couldn't start Xtightvnc process.

```

Any idea?  I used apt-get install tightvncserver

---

### Post by netrattler on 2005-07-19
I just downloaded freenx from there website and compiled it, but they do have .deb packages for debian and ubuntu. But I haven't tried the deb packages from there site yet.

[http://freenx.berlios.de/download.php](http://freenx.berlios.de/download.php)

Joe

---

### Post by Saru san on 2005-07-19
[QUOTE=viniosity]When I try to start the vncserver I get this error:

```

Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the tightvncserver script.
Couldn't start Xtightvnc process.

```

Any idea?  I used apt-get install tightvncserver[/QUOTE]

Not sure, I didn't have it in my apt sources... mine are pretty conservative.
Try installing the version I used and see? Someone here should know more than I though.

---

### Post by viniosity on 2005-07-19
I downloaded the version you have from the link you provided but still have the same error.  Are you using AMD64?  I can't understand why my install is being so uncooperative.  

I also tried just the plain vncserver but that didn't work either.. no error but no response from the vncserver.  

Typing ps aux | grep vnc gives me no results..

---

### Post by Brandon Hoult on 2005-09-12
[QUOTE=viniosity]I downloaded the version you have from the link you provided but still have the same error.  Are you using AMD64?  I can't understand why my install is being so uncooperative.  

I also tried just the plain vncserver but that didn't work either.. no error but no response from the vncserver.  

Typing ps aux | grep vnc gives me no results..[/QUOTE]
 I am also using amd64 and have the same problem with the font path.  I have no problem with the Kubuntu version on an amd 64 running in 32 bit mode

---

### Post by Divan Santana on 2005-09-13
Mine doesn't work either! No matter what Ido, all VNC's I've tried! Still no luck on 5.04 and 5.10. Help??

---

### Post by kingkong on 2005-10-26
[QUOTE=Divan Santana]Mine doesn't work either! No matter what Ido, all VNC's I've tried! Still no luck on 5.04 and 5.10. Help??[/QUOTE]

Exact same problem here! vncserver or tightvnc don't work. Remote desktop seems to work fine. I tried changing the fontPath in vnc.conf to match the fontpath in xorg files but still the same error. I have AMD64.

---


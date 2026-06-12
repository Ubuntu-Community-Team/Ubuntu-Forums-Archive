---
title: "VNC Problems"
date: 2006-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by mwales on 2006-06-01
Does anybody have a working VNC server on DD x86_64.

The regular vncserver application has never worked for me, even on Hoary.  But when I used Hoary, I could use vnc4server instead, and it worked fine.

But my current Dapper install doesn't have a working VNC server.  vncserver is just as broken as it was on Hoary.  It acts like it starts, but you can never connect to it.  When you kill it, it never deletes the lock files.

But now I'm having a problem with vnc4server.  I normally start it, connect VNC viewer, and usually manually start kde (by calling startkde in the 1 open console).  But now, that console doesn't have any window decorations.  One time I was able to click in it, and type in it, but now I can't even do that.  The one time I did start KDE, I couldn't get any windows focus, and none of them had decorations.

I'm also thinking it may have something to do with the fact that I have XGL/Compiz stuff installed.  I don't actually use the XGL/Compiz stuff though.  It never worked right in KDE for me, and I like KDE more than gnome.  So I went back to using the regular Xorg X server and KDE.

If you do have VNC server working, do you have the XGL/Compiz stuff too.

---

### Post by Jason_25 on 2006-06-01
x11vnc works perfectly for me.  Even with XGL/compiz.

---

### Post by mwales on 2006-06-02
I added the x11vnc package, and tried it out.  It works good.  Thanks

---

### Post by mellowiz on 2006-06-05
[QUOTE=mwales]I added the x11vnc package, and tried it out.  It works good.  Thanks[/QUOTE]
Hi,
I've tried to install the package but the system couldn't find it.
Have you added anything to /etc/apt/sources.list ?

Thanks,
-mw

---

### Post by fragos on 2006-06-05
The Remote Desktop is a vnc which works after configuring it and the routes on both ends.  The only gotcha I found was that the someone at the remote system had to click an allow button for each connect establishment.

---

### Post by mwales on 2006-06-12
```
# deb file:/var/cache/apt-build/repository apt-build main
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted


deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src http://us.archive.ubuntu.com/ubuntu dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe


deb http://us.archive.ubuntu.com/ubuntu/ dapper multiverse universe main restricted
# deb http://wine.sourceforge.net/apt/ binary/

# deb http://orniere-du-globe.net/debian ./
# deb-src http://orniere-du-globe.net/debian ./

```

---

### Post by chshon on 2007-06-18
How can I change the resolution of x11vnc?
I still using defalt one, which has 800x600.
I want to change this. It is not easy to find.
Please help me.

---

### Post by incubus on 2007-06-19
chshon,

I haven't used VNC in a very long time, but I might be able to remember.  Do you have a file:
```

/etc/vnc.conf

```

What you can do is copy that file to your home directory as ".vncrc"
```

$ cp /etc/vnc.conf ~/.vncrc

```

And then edit it.  Basically, if my memory serves me, you'll have to edit the entry for geometry.

Alternatively, when you launch vncserver, you also have that option.  It might be something like this:
```

$ vncserver -geometry 1024x768

```

Make sure you check:
```

$ vncserver -h
$ man vncserver

```

incubus

---


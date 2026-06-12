---
title: "All browsers are crashing randomly (Mozilla, Konqueror), X.org conf issue?"
date: 2005-11-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by tijs on 2005-11-30
Hi,

I happily installed Kubuntu on my G4, and everything works fine, but I am experiencing very annoying crashes. first I thought it was just Firefox 1.0.7, which was also unstable on x86 architecture, so I tried the latest Mozilla package. But again there were random crashes. It usually happens after like four hours or more. Then I worked for a while with Konqueror, but it crashed too. It's driving me crazy!

So, I suspect this is a problem with my video card? In the G4 there is an nVidia card. The drivers have not been installed but then I don't need any 3D, I just use this computer for office work and I'm afraid of breaking Ubuntu when messing with nvidia drivers.

Could somebody please give some advice?

There is nothing about the crashes in the system log neither in a terminal. Though I used to have a message in the system log that "Gconf is not in use. Exiting", though I don't get that message anymore, yet I still experience the crashes.

(This forum didn't allow me to post my X.org log file.)

---

### Post by Entity on 2005-12-01
Did you compile these yourself or you installed these from Ubuntu's breezy repositories?

Do you get crashes using applications that are not web browsers? If not, it could be caused by a plug-in like flash, java, etc.

---

### Post by autocrosser on 2005-12-01
Agreed--sounds like a plug-in problem---I'd disable a plugin & test--then another plugin--etc-etc

---

### Post by tijs on 2005-12-02
Hmmm I thought I had no plugins installed, only an Mplayer plugin. I don't have any Flash in any case. Uhm, how can I see which plugins I have? Shall I just search in synaptic?

Oh, I just had another crash. Kontact crashed and with it also Mozilla. Mozilla just disappeared and for Kontact I had this crash notification. Konqueror, which was also open (I use it only as a file manager) is still around and didn't crash.

I thought in Gnome everything was alright again, but as I said I just experienced another crash. Nothing in the syslog, however.

I didn't compile anything, just installed from the repositories (multiverse, universe and backports are enabled)

Any hints welcome!

Thanks,

---

### Post by teaker1s on 2005-12-02
try booting a previous kernel in grub or better still look [here]("http://www.ubuntuforums.org/showthread.php?t=85917") and choose the best one for you

---

### Post by tijs on 2005-12-02
[QUOTE=teaker1s]try booting a previous kernel in grub or better still look [here]("http://www.ubuntuforums.org/showthread.php?t=85917") and choose the best one for you[/QUOTE]

Thanks, but that link says:

----------
Notes:

- This guide does not apply to the PPC or 64 bit version of Ubuntu.
----------

So anyway, I never upgraded any kernel on this G4 machine, I just stuck with whatever Kubuntu installed for me. Let's try to see if uninstalling the Mplayer plugin in Mozilla makes any difference (I just did that so cross fingers...)

---

### Post by Entity on 2005-12-02
[QUOTE=tijs]Uhm, how can I see which plugins I have? [/QUOTE]

type the following your firefox's address bar and press OK to get the plugin list :
```
about:plugins
```

---

### Post by Entity on 2005-12-02
damn smilies :p

---

### Post by tijs on 2005-12-02
OK thanks, this is what came up:

> Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes

So I suppose these are just default plugins that can't be the problem? Note that I uninstalled the Mplayer plugin.

No crashes yet this afternoon, let's hope it remains like that.

Oh, I can't start Firefox 1.0.7 anymore, it says there is a "segmentation fault". Firefox 1.5 works fine.

---

### Post by Entity on 2005-12-02
[QUOTE=tijs]OK thanks, this is what came up:



So I suppose these are just default plugins that can't be the problem? Note that I uninstalled the Mplayer plugin.

No crashes yet this afternoon, let's hope it remains like that.

Oh, I can't start Firefox 1.0.7 anymore, it says there is a "segmentation fault". Firefox 1.5 works fine.[/QUOTE]
Well, let's see, how it works from now, but fyi my mplayer plugin doesn't make my browser crash. Was that a clean install?

---

### Post by tijs on 2005-12-02
Oh well, Mozilla still crashes. No notification or anything, just gone. It does seem to happen when I have quite a few tabs open.

Next week I will try to work with Firefox 1.5 and see if that makes a difference (before it didn't)

Thanks for the suggestions.

I must say that I installed Ubuntu about three weeks ago. Initially I didn't have KDE working and the package manager was broken. I managed to install missing KDE packages and then all seemed fine. The only thing that still keeps happening is these browser crashes. The annoying thins is there is no notification whatsoever and nothing in the syslog. Is there a kind of Mozilla or Firefox log?
(note that there isn't a notification if you open the browser from the cli)

---

### Post by Entity on 2005-12-02
[QUOTE=tijs]Oh well, Mozilla still crashes. No notification or anything, just gone. It does seem to happen when I have quite a few tabs open.

Next week I will try to work with Firefox 1.5 and see if that makes a difference (before it didn't)

Thanks for the suggestions.

I must say that I installed Ubuntu about three weeks ago. Initially I didn't have KDE working and the package manager was broken. I managed to install missing KDE packages and then all seemed fine. The only thing that still keeps happening is these browser crashes. The annoying thins is there is no notification whatsoever and nothing in the syslog. Is there a kind of Mozilla or Firefox log?
(note that there isn't a notification if you open the browser from the cli)[/QUOTE]
Maybe you should simply proceed to a clean (k)ubuntu re-installation.

---


---
title: "So, what do *you* chroot?"
date: 2005-12-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by nwillis on 2005-12-15
Well, since upgrading to Breezy two weeks ago [I like to wait for the official CDs cause they're so purty], I've gone through the motions of setting up my chrooted apps, and it got me thinking: what do *you* chroot on your otherwise baad amd64 system.

Here is what I currently run in chroot:
[LIST]
[*]Adobe Acrobat Reader
[*]Azureus
[*]RealPlayer
[*]Helix-Player
[*]Synaptic (duh)
[*]OpenWengo
[*]Skype
[*]Firefox (for the plugin support)
[*]Tovid (because the available source didn't compile)
[*]Beagle, Tomboy, F-Spot and Muine (because Mono is currently in HogMemoryStealCPUandCrashImmediately mode on 64)
[*]Xine (for some codecs)
[*]WINE
[/LIST]

Some of these obviously I *could* try compiling from source, and I'm not 100% sure about Azureus.  Skype and Wengo I virtually never use; I installed them for an article I was writing.

Come to think of it, I never use F-Spot or Muine either.

Anyway, the floor is yours!  Post your chroot lists here; let's find out what the most popular choices are....

Nate
(if there's already a thread devoted to this, please excuse my poor searching skillz cause I didn't find it)

---

### Post by RAOF on 2005-12-15
I don't actually chroot **anything**.  Although, from that list I only run:
*) Beagle & Banshee as mono apps
*) Azureus
*) Wine
*) Firefox

A chroot has always seemed such a ugly solution to me ;)

---

### Post by BoyOfDestiny on 2005-12-15
synaptic (as you mentioned)
Zsnes (my cvs build)

That's it :)

---

### Post by nwillis on 2005-12-16
Ugly?  It uses apt and it blends in with the rest of the system; nothing ugly about that.

Seems like using *dpkg --force-** is ugly....

---

### Post by Suger on 2005-12-16
wine
opera
skype
acroread (the only one I could not manage to get running without a chroot, so the real culprit of the presence of the chroot on my system).

You should not need to chroot for azureus, but I'm not absolutely positive about that (personnally, I use rtorrent).

---

### Post by Casey on 2005-12-16
nothing

---

### Post by skylark on 2005-12-17
totem, wine, firefox

---

### Post by negatory on 2005-12-17
Why Skype or Azureus?I've downloaded the skype static binary and it works fine and Azureus as a 64bit port...
My list:
Last.fm player
acrobat reader
firefox (for the macromedia stuff)
nvu ->(can't seem to run it native mode)
And that's all...

---

### Post by Suger on 2005-12-17
In my case, I use opera in 32 bit modes for plugins, and I installed the shared-qt deb, so I already had all the libraries for skype in the chroot, so I said, why bother with the bloated static when I can go for the shared one in chroot ?

---

### Post by MighMoS on 2005-12-19
The only thing I use a chroot for is codecs for mplayer.  And once real gets implemented or even 64bit binaries, I'll prolly ditch it.  I don't chroot firefox for flash player, because most flash things are simply really annoying ads.

---

### Post by KLineD on 2005-12-19
[QUOTE=Suger]wine
opera
skype
acroread (the only one I could not manage to get running without a chroot, so the real culprit of the presence of the chroot on my system).

You should not need to chroot for azureus, but I'm not absolutely positive about that (personnally, I use rtorrent).[/QUOTE]

I'm sure you don't need chroot for Azureus, that's my torrent client and all I did was install Sun's Java.

---

### Post by nwillis on 2005-12-19
Unless if you've chrooted Firefox, and want it to launch Azureus from the browser when clicking on torrent links.

---

### Post by Ribs on 2005-12-21
No chroot set-up here.

I feel the longer term solution requires us to improve free, open, and well written software to allow everything to work well in 64-bit. Using closed source software within a 32-bit chroot is only encouraging the software developers not to change, and sends a clear message to them that they need not care. This is the wrong message for us to be sending out.

Whenever I can, I use 64-bit software, 32-bit at a push. If it doesn't work in my 64-bit installation, then tough, I don't use it, I find an alternative and stick to it, and the developers loose another customer/user.

---

### Post by nwillis on 2005-12-22
[QUOTE=Ribs]No chroot set-up here.

I feel the longer term solution requires us to improve free, open, and well written software to allow everything to work well in 64-bit. Using closed source software within a 32-bit chroot is only encouraging the software developers not to change, and sends a clear message to them that they need not care. This is the wrong message for us to be sending out.

Whenever I can, I use 64-bit software, 32-bit at a push. If it doesn't work in my 64-bit installation, then tough, I don't use it, I find an alternative and stick to it, and the developers loose another customer/user.[/QUOTE]


It sounds like you're confusing two unrelated issues here.  Just running a 32-bit app in a chroot has nothing to do with whether it is closed or open source.  And I think all of us prefer to run 64-bit binaries natively; you only run the 32-bit app in chroot when there's no equivalent (as you put it, "at a push").  Speaking of which, how are you using 32-bit "at a push" if -- a sentence later -- you say "tough, I don't use it" ....  That just doesn't add up.

---

### Post by Ribs on 2005-12-22
[QUOTE=nwillis]It sounds like you're confusing two unrelated issues here.  Just running a 32-bit app in a chroot has nothing to do with whether it is closed or open source.  And I think all of us prefer to run 64-bit binaries natively; you only run the 32-bit app in chroot when there's no equivalent (as you put it, "at a push").  Speaking of which, how are you using 32-bit "at a push" if -- a sentence later -- you say "tough, I don't use it" ....  That just doesn't add up.[/QUOTE]

Fair comment, I wasn't clear here. I use 32-bit applications when I have to, on my 64-bit installation, if they work. For example, Cedega or Wine. If they don't work in my 64-bit installation at all, or require a hell of a lot of work to get working (such a Flash), then I don't bother and try something else.

I still feel my point on free software is valid. Take flash for example. It's closed source, provided by one vendor, and if you don't like something about it, then tough, you have zero power to actually change anything within it. I either take it or leave it, there is no freedom there. This is exactly what I'm trying to get away from when I migrated away from Windows.

Free software gives us choice, and importantly in this case, portablility. With the exception of OpenOffice (but they are working on this), all the free software I run has a 64-bit version. And that's because it's free and open. Mozilla, for example, do not supply a 64-bit version of Firefox, but anyone is free to create one. This is the beauty of free open source software, and I feel it's something we should all support whenever possible.

---

### Post by Yagisan on 2005-12-22
I use wine because some apps even though they are opensource are windows only (can you say virtualdub), and doomsday (see my sig for details, its in community projects), as it isn't 64bit clean yet.

---

### Post by jon_gunnar on 2005-12-25
[QUOTE=nwillis]Well, since upgrading to Breezy two weeks ago [I like to wait for the official CDs cause they're so purty], I've gone through the motions of setting up my chrooted apps, and it got me thinking: what do *you* chroot on your otherwise baad amd64 system.
[/QUOTE]

Nothing. The only thing I miss a little is Adobe Acrobat. Flash I'm in fact very happy to have got rid of. 

Azureus                       Works like a charm
RealPlayer                    Hate it, never used it.
Synaptic                      Why would I?
Skype                          Static works ok,
Beagle, F-Spot              Works nice
Xine                            Only thing missing is the newest wmv format. and I           manage fine without it.

I really think chroot is a very "evil" thing :rolleyes:

---

### Post by nwillis on 2005-12-25
*Note to self: next time, invite people who want to say "nothing" to start a separate thread.*

....

---

### Post by Ribs on 2005-12-26
[QUOTE=nwillis]*Note to self: next time, invite people who want to say "nothing" to start a separate thread.*[/QUOTE]
Interesting. But now you've seen a viewpoint which you were not expecting. Ultimately you're more enlightened than you were before.

Okay, I'll shut up now.

---

### Post by nwillis on 2005-12-26
It's an irrelevant viewpoint.  What I'm interested in is what apps 64bit users are chrooting either because there is no 64bit equivalent or because the 64bit equivalent doesn't work.  For instance, we all know that proprietary apps like Flash have to be run in 32bits.

But a side effect of that dependancy is the Azureus one; most people find torrents through their web browser, consequently people who could otherwise use Azureus in their native 64bit setup have to install it in the 32bit chroot because of the frustration that comes with being unable to click on a .torrent link without it.  Azureus is free software; it doesn't directly depend on anything non-free or architecture-specific, but it's trapped by this unusual circumstance.  *That's* interesting.  It's the kind of thing that a distro out "in the wild" can reveal to you, that studying package dependancies in the lab can't.  Finding these quirks and fixing them is what makes an open source OS so much more flexible than the alternatives.

Alternatively, we all learn (sooner or later) that WINE doesn't build in 64bits.  But from reading the AMD64 forums, people are working on it constantly, and getting further than you might think.  Someday people will answer the question without WINE making an appearance at all.

Yeehaw.

---

### Post by poofyhairguy on 2005-12-27
I chroot not for my playstation emulator and to make i386 packages.

The 64 bit version of Ubuntu is so much faster to me (I am VERY picky about responsiveness) I can never go back. Thank goodness for chroot.

---

### Post by FedeXX on 2006-10-21
Firefox (and plugins), Wine, Skype.

I'd like to use a chrooted Mplayer too, but it seems working only for files located in my home directory (file not found for other locations), there's a way to fix it?

---

### Post by kuja on 2006-10-21
In your (not chroot) mount --bind /path/to/files /yourchroot/path/to/files. A chroot is essentially a jail, it can't see anything that you don't explicitly tell it to.

---


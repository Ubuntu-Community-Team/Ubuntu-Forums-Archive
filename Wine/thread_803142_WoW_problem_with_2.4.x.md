---
title: "WoW problem with 2.4.x"
date: 2008-05-22
forum: Wine
---

### Post by toupeiro on 2008-05-22
OK, I'm stumped on this one...

A conglomeration of things all transpired at once as far as patching is concerned.  Blizzard released a mini-patch for World of Warcraft, Ubuntu released some new xorg patches, wine 1.0.0 RC1 came out.  The net result is: I can no longer run WoW.  When I use the icon launcher, the game will start, but my mouse and keyboard will freeze completely, requiring me to hit the reset button on my computer.  When using Metacity, launching from a CLI (the same command syntax used in the launcher) I can sometimes alt-tab back to my desktop quick enough to gain GUI control of gnome, and I caught this in the terminal window:

X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  587
  Current serial number in output stream:  587




I have:

Reverted back to the old version of wine, completely recreating a .wine working directory

Reinstalled my video drivers and ensured they are the latest ones available from Nvidia

Tried running the game with Metacity and Compiz

Tried disabling any additional GTK themes I had.

Ran the blizzard repair tool against WoW.

Tried running in Win98 compatibility mode as opposed to WinXP

Tried running in opengl mode and D3D mode

Tried using a 3rd party tool like cedega.


I'm out of things to try.  It does seem like some other people have had a lot of heartache since the patch, but I've yet to find a solution that fixes my problem.  Anyone have any ideas?  your help is very much appreciated!

-T

---

### Post by toupeiro on 2008-05-22
Update: I can now put trying 2 previous kernels on the list of things that failed to fix the problem :(

---

### Post by toupeiro on 2008-05-23
*Hopeless Bump*

---

### Post by toupeiro on 2008-05-24
I resolved this:

For those wondering how, or that may be experiencing it themselves, I didn't pinpoint the exact cause of my problem, but definitely the exact location of it:  my Config.wtf file.

Wow is one of those few games that is completely portable.  The install I have is from when wow first came out, and thus the formatting of my Config.wtf has been structurally the same since its initall install on windows, being transferred to linux, upgraded with the expansion, patches etc etc..  

My only guess is that something in there is now invalid as of 2.4.x, so I just deleted the config.wtf file and let wow create a brand new one, then went through and reset the specifics like gxApi, sound buffering, and the resolution I play in (1600x1200)

I decided to do a diff on the new file and the old, and there is certainly a lot less garb in the new one, but the garb in the old one is stuff that previous versions of the game put in there, not that I added manually.  I will also add that doing this seems to have somewhat helped my FPS, so an extra added bonus there.

So this wasn't **actually** a wine problem, although wine was the thing snarling about it.  It might be worthwhile to file this back under gaming and leisure where I originally posted it.

I have a couple posts under wine AppDB which I will update as well.

-T.

---


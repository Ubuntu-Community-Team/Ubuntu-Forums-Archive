---
title: "Any RealPlayer 10 successes?"
date: 2005-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by youngster1 on 2005-10-19
RealPlayer seems to work fine on the 32-bit version of Breezy. However, all my attempts at installing it on the AMD64 version have been a disaster. When I try and lauch realplay I get the following error:

libXt.so: cannot open shared object file: No such file or directory

But the worst part is that I am no longer able to open a web browser. The only way to recover is to reload the OS.

Have any of you AMD64 users been able to successfully install RealPlayer 10 ?

---

### Post by Storyman on 2005-10-19
I've had the same problem.

---

### Post by youngster1 on 2005-10-19
Poster gsring is also having this problem. So now there are three of us, at least.

I might also mention that I followed the ReaLPlayer installation procedure documented in the Breezy Help.

---

### Post by grsing on 2005-10-19
I followed the same procedure, to no avail.  Not going to touch it again anytime soon.

---

### Post by tufkal on 2005-10-22
[QUOTE=youngster1]RealPlayer seems to work fine on the 32-bit version of Breezy. However, all my attempts at installing it on the AMD64 version have been a disaster. When I try and lauch realplay I get the following error:

libXt.so: cannot open shared object file: No such file or directory

But the worst part is that I am no longer able to open a web browser. The only way to recover is to reload the OS.

Have any of you AMD64 users been able to successfully install RealPlayer 10 ?[/QUOTE]

You do not need to reload your OS.   

Check in /usr/lib/mozilla/plugins and /usr/lib/mozilla-firefox/plugins for the nphelix files.  Get rid of them.  Firefox panics trying to load those files cause they are staticly linked to 32bit code.  That is why you get the LibXt and LibXext errors.

I havent found a solution yet, but will let you know when I do.

---

### Post by autonomy on 2005-10-26
I guess I'm on the 32-bit version, and I get this message, "./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory". Does anyone have a remedy?

---

### Post by RAOF on 2005-10-26
For that, certainly.  It's complaining about a missing library "libstdc++", version 5.  You just need to install it.  Either search in synaptic for "libstdc++" and select "libstdc++5", or from a terminal run "sudo apt-get install libstdc++5"

And in general, with those sorts of error messages, you can try searching in Synaptic.  If it says "... error while loading shared libraries: libfoo.so.x: cannot open...", you'd try searching for "libfoo" in Synaptic and seeing if 'libfoo' version 'x' is installed.

---

### Post by autonomy on 2005-10-26
[FONT=monospace]Thanks[/FONT]

---

### Post by mjreged on 2005-10-29
Tha't not true in case of 64bit machines because i did install all the missing libs with synaptic and realplayer is still complaing about not being able to find them when clearly synaptec has them as installed

---

### Post by RAOF on 2005-10-30
[QUOTE=mjreged]Tha't not true in case of 64bit machines because i did install all the missing libs with synaptic and realplayer is still complaing about not being able to find them when clearly synaptec has them as installed[/QUOTE]
Ah, ok.  realplayer would be a 32bit binary then, yes?  I think that installing "ia32-libs" will include the 32bit version of libstdc++5.  At least, it includes a file "libstdc++.so.5.0.7", or something similar.

---

### Post by sanyoko on 2005-11-09
my problem is after installed realplayer 10.
 it autoclosed when open vcd files from cdrom.

---

### Post by tux61 on 2005-11-09
I can use Realplayer 10 and also the plugin in firefox (for the plugin you need to install a 32 bits version of firefox).
To use reaplayer alone :
Create a little script called /usr/bin/realplay32 for example :
```

#!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0/
export PANGO_RC_FILE=/etc/pango32/pangorc
realplay

```

Create a file /etc/pango32/pangorc
```

[Pango]
ModuleFiles=/etc/pango32/pango.modules
[PangoX]
AliasFiles=/etc/pango/pangox.aliases

```

---


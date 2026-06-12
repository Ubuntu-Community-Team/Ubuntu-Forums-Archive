---
title: "Timidity++ Windows Synthesizer (TWSYNTH)"
date: 2014-07-12
forum: Wine
---

### Post by stu-klaum.tiernan on 2014-07-12
Hi. I need to run a program under Wine 1.7.17 on Linux Mint 14 Nadia MATE Edition 64-bit. Its called Timidity++ Windows Synthesizer (TWSYNTH). It and Wine haven't been playing nice and its really been grinding my gears. :mad:

I downloaded the installer for TWSYNTH at:
[http://en.sourceforge.jp/frs/redir.php?m=iij&f=%2Ftwsynth%2F36408%2FTiMidity-CVS081206_setup_ENG.exe](http://en.sourceforge.jp/frs/redir.php?m=iij&f=%2Ftwsynth%2F36408%2FTiMidity-CVS081206_setup_ENG.exe) (direct link) and ran it under Wine using the Terminal.

[IMG]http://www.mediafire.com/convkey/99c6/34w546s3wo1nd4tfg.jpg[/IMG]

Then the Terminal spit this out:
```
fixme:shell:SHAutoComplete stub
```
This appeared when I went on to the next step in the installer:

[IMG]http://www.mediafire.com/convkey/8f97/twfh5juw550httffg.jpg[/IMG]

Ignoring this, I venture forth to the next step.

[IMG]http://www.mediafire.com/convkey/7a2a/hn0yze4w8ajs689fg.jpg[/IMG]

While it is installing, the Terminal gives me this:
```
err:rundll32:wWinMain Unable to load L"syssetup.dll"
```
I ignored this, since it wasn't a showstopper. The installer took about 15 seconds to copy and register everything. Once it was done, it went to the next screen automagically.

[IMG]http://www.mediafire.com/convkey/de3a/d4lo8z980182omyfg.jpg[/IMG] 

In doing so, the Terminal yells at me.
```
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
```
When I clicked the Finish button, the installer exited and a wild and very stylish TWSYNTH Player appeared!

Then the Terminal gives me get the same error as before.
```
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
```
I ignored it, because once again, it wasn't a showstopper.

I got hit with a huge wave of nostalgia listening to a Windows 3.1 classic:

[IMG]http://www.mediafire.com/convkey/af97/b4959y708avg999fg.jpg[/IMG]

I could listen to this MIDI perfectly! High quality sound and NO LATENCY!

The MIDI I was listening to (CANYON.MID)
[http://download1491.mediafire.com/eq3dd8l8gsog/rm0cmx4imnr3d91/CANYON.MID](http://download1491.mediafire.com/eq3dd8l8gsog/rm0cmx4imnr3d91/CANYON.MID) (direct link)

This is all fine and good, but I want to be able to listen to my MIDIs with [COLOR=#ff0000]V[/COLOR][COLOR=#ffa500]I[/COLOR][COLOR=#ffff00]S[/COLOR][COLOR=#00ff00]U[/COLOR][COLOR=#0000ff]A[/COLOR][COLOR=#ee82ee]L[/COLOR][COLOR=#ff0000]I[/COLOR][COLOR=#ffa500]Z[/COLOR][COLOR=#ffff00]A[/COLOR][COLOR=#00ff00]T[/COLOR][COLOR=#0000ff]I[/COLOR][COLOR=#ee82ee]O[/COLOR][COLOR=#ff0000]N[/COLOR]&#8203;!

The TWSYNTH Player has a tracer, but it constantly bogs my computer down and lags behind.

[IMG]http://www.mediafire.com/convkey/72b2/473h9gn8bmlz2a7fg.jpg[/IMG]

Oh, and I might not be able to enlighten you visually on every step I take because of the "Eight-pictures-in-one-post-because-we-think-you're-gonna-be-like-the-rest-of-the-jerks-on-the-internet-and-spam-and-try-to-slow-down-other-people's-computers" limit. Sorry!

The problem with the trace[SIZE=2]r is[/SIZE] why I need TWSYNTH up and running so I can use TWSYNTH with other MIDI playing programs like MIDITrail, Synthesia, and TMIDI.

For now I want to use TMIDI.
You can read all about TMIDI here:
[http://www.grandgent.com/tom/projects/tmidi/](http://www.grandgent.com/tom/projects/tmidi/)

To open TWSYNTH, I must navigate to and open a .exe called "twsyng.exe". This created an icon in the system tray ([IMG]http://www.mediafire.com/convkey/f54a/aj42uz2r1dzq62mfg.jpg[/IMG]) which I can clicked on and it gave me a set of options.

---

### Post by stu-klaum.tiernan on 2014-07-12
Sorry! that kind of cut off, didn't it? A token expired or whatever. Continuing on,

To open TWSYNTH, I had to open an exe file called "twsyng.exe" in the terminal. This created an icon in the system tray ([IMG]http://www.mediafire.com/convkey/f54a/aj42uz2r1dzq62mfg.jpg[/IMG]) and a lecture from the Terminal:
```
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
```
I ignored it. Most of the stuff that Wine outputs is junk and doesn't need to be fixed.

When I clicked on the system tray icon created by TWSYNTH, a menu appeared.

I clicked on "Start synthesizer"

---

### Post by stu-klaum.tiernan on 2014-07-13
Somebody delete this post, there is an entire forum dedicated to WINE.

---


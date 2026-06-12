---
title: "Firefox 1.0.7 buggy?"
date: 2005-12-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by OOpabloOO on 2005-12-16
Hi all,
I'm new to this forum, now I'm glad to be here :)

I'm using firefox 1.0.7-0ubuntu20 from the Breezy rep. Every now and then, it gets 100% CPU usage and then crashes. (not in a particular web page)

If I launch it from a terminal, it prints the following error:

```

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 24280075 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


```

Also, sometimes, if I'm using ATI fireglrx module for 3D Acceleration, the user interface of gnome hangs totally and only the panel seems to work. The only thing to do is restarting the gnome session.
If I don't use 3D acceleration firefox just hangs but at least it doesn't crash the whole GUI.

I've upgraded from Hoary to Breezy, but in Hoary I've never exeperienced this behaviour.

Is this a bug?

---

### Post by Taino on 2005-12-16
[QUOTE=OOpabloOO]I've upgraded from Hoary to Breezy, but in Hoary I've never exeperienced this behaviour.[/QUOTE]

I dont know what your system stats are Cpu, Ram, Linux Swap, Linux Partition sizes.. etc.. But i can tell you Breezy is more resource intensive than Hoary was and it'll use more Cpu and more Ram so i suggest making some minor adjustments to your setup.

Ive had this happen before also, 2 firefox crashes and 3 firefox stall outs (while loading), but i was pushing my system intensely, and it also didnt happen with Hoary for me just Breezy.

What solved it for me was increasing the Linux Swap, if your pushing your system like i was you may be running out of Ram, so you might want to try adjusting that.

---

### Post by OOpabloOO on 2005-12-16
No, it's not a problem of swap
I have 1GB of RAM and 512MB of swap space.
While firefox is taking 100% of CPU (before it crashes) I've monitored the RAM and the swap used, and there's still a lot of free space. The swap isn't used at all
Maybe there's a setting into firefox that indicates the maximum memory available?

---

### Post by OOpabloOO on 2005-12-17
Probably I've solved.
I guess this issue is due to the proprietary ATI fglrx driver. Even if I've uninstalled them, they've overwritten some lib, like libGL and similar. I've replaced those libraries with the original ones and now everything seems to be stable.
I suppose that ATI's driver have a buggy memory management and they don't allow the swap between video card memory (just 128MB) and system memory  (that in fact, remains unused during the crash).

Another amazing story about proprietary drivers.... :(

See ya

---

### Post by OOpabloOO on 2005-12-19
Damn! I've not solved!!
Today firefox crashed again!!!!
I cannot reproduce this bug, I've haven't understood yet when it happens.
It seems that it takes down even metacity, because after the crash, no window borders appear
Someone else have the same experience?

---

### Post by Ribs on 2005-12-21
Purely a stab in the dark here. But it *feels* like the display drivers, as you've already noted.

Breezy uses a fairly heavly patched beta of the X.org server, this may be the cause of your problems.

I know it sounds silly, but can you try using the vesa driver for a while? See if that helps...

---

### Post by nick4mony on 2005-12-22
I've also had a lot of problems with Firefox 1.0.7.  Just note though, that I'm running an older Intel processor, not an AMD: the processor is a Pentium MMX, vendor_id: GenuineIntel, cpu family: 5, model: 4, model name: Pentium MMX, stepping: 3, cpu MHz: 200.482

Firefox was working OK before, and it worked OK on Fedora Core, but I've not tested there in recent times.

Memory is 128MB, and I run XFCE, not Gnome.  I'm also running Warty, for everything below except point 4, which is WinXtraPain SP 2 running on a Pentium 4/HT (much younger machine).

Symptoms include:
  1. My bookmarks menu disappearing on me except for the first two entries (Bookmark this page & Manage bookmarks)
  2. The URL in the address bar does not change as you navigate around the site, or for redirections (example redirect - [http://mail.chronopia.net/](http://mail.chronopia.net/) )
  3. The title-bar on the window does not change as you click different
  4. On Winxp, version 1.0.6 hangs when you attempt an auto update (presumably to install 1.0.7)
  5. On a link, right-click -> Open Link in new tab does not do anything at all.
  6. Setting preferences - browser does not behave according to what you set (eg unclick Hide tab bar when only one open - still hidden).

Sometimes, trashing the ~/.mozilla directory helps, but it's not long before problems reappear.

We all love Firefox (yes, even the Windows Geek (boss)) but these problems are freaking me out to some degree).

---

### Post by Ribs on 2005-12-22
Are either of you running any extensions? I had problems with Firefox this morning (it wouldn't even start properly), and tracked it down to an extension mis-behaving...

---

### Post by estel on 2005-12-22
My Firefox crashes a couple of times a day, sometimes randomly but often on pages where is discovers it needs some sort of multimedia plugin. The Windows just... immediately vanishes for no apparent reason.

And atm, no extensions.

---

### Post by OOpabloOO on 2005-12-22
[QUOTE=Ribs]Purely a stab in the dark here. But it *feels* like the display drivers, as you've already noted.

Breezy uses a fairly heavly patched beta of the X.org server, this may be the cause of your problems.

I know it sounds silly, but can you try using the vesa driver for a while? See if that helps...[/QUOTE]

Right now, I'm not using fglrx driver. I turned back to ati drivers. I'll try to use vesa instead, just to see what happens, but I guess the problem is more serious:

[https://bugzilla.mozilla.org/show_bug.cgi?id=310917](https://bugzilla.mozilla.org/show_bug.cgi?id=310917)

---

### Post by estel on 2005-12-22
Yes, I thought that it was an upstream bug (this error has been mentioned in the past)

[http://lists.debian.org/debian-user/2005/11/msg00147.html](http://lists.debian.org/debian-user/2005/11/msg00147.html)

---

### Post by nick4mony on 2005-12-22
[QUOTE=Ribs]Are either of you running any extensions? I had problems with Firefox this morning (it wouldn't even start properly), and tracked it down to an extension mis-behaving...[/QUOTE]

I cautiously answer "no, I'm not running extensions", but I'm willing to make doubly sure.

What do I check?
  --OR--
do I do
```

#apt-get --purge remove mozilla-firefox
#apt-get install mozilla-firefox
```????

---

### Post by Ribs on 2005-12-24
[QUOTE=nick4mony]I cautiously answer "no, I'm not running extensions", but I'm willing to make doubly sure.

What do I check?
  --OR--
do I do
```

#apt-get --purge remove mozilla-firefox
#apt-get install mozilla-firefox
```????[/QUOTE]

Goto the tools menu, then 'Extensions'. The only thing listed there should be a language pack.

Also, try running firefox in 'safe' mode, to rule out issues with plugins etc. To do this, run 'firefox -safe-mode'.

---

### Post by nick4mony on 2005-12-28
[QUOTE=Ribs]Goto the tools menu, then 'Extensions'. The only thing listed there should be a language pack.

Also, try running firefox in 'safe' mode, to rule out issues with plugins etc. To do this, run 'firefox -safe-mode'.[/QUOTE]

OK, done both.

When I listed the extensions, NOTHING came up.  Not even a language pack.

When I ran safe mode, it made no difference (still the same stupid things).  This is the output to console:
```
nick@willis:~ $ firefox -safe-mode
Error: No running window found
auto selected locale: en-US
*** loading the extensions datasource
*** nsExtensionManager::start - (safe mode) failure, catching exception so finalize window can close

```

Comments, anyone?

---

### Post by Ribs on 2005-12-28
Hi,

The lack of a language pack is probably normal if you're using US English, as I'm using GB English, a language pack was installed for me by Ubuntu.

With your actual problem... Well, I've run out of ideas about that :confused:

---

### Post by dlrider on 2006-01-04
Well, I'm fairly convinced that changing to the 686 kernel made the difference on my Thinkpad T23.  I would get the hangs when the fan would turn on after some period of use.  Yes, Firefox 1.07 running but that is what I currently spend most of my time doing.  Running Hoary too.

Anyway, I haven't seen a hang since switching ~2 weeks ago, and the fan cycles on/off all the while I am running multiple Firefox windows.  Only had to reinstall ndiswrapper.

D.

Crap, I just realized this thread is for AMD 64!  Sorry.  I'll leave it here just in case... well, I don't know... for someone like me who can't read =(

---


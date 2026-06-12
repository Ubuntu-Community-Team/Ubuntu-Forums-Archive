---
title: "Unable to play any Sound, Video or Flash"
date: 2008-07-05
forum: x86 64-bit Users
---

### Post by netsurfau on 2008-07-05
I'm running Gutsy on an AMD 64bit AM 6000+ with:
Gigabyte m/board using a nVidia chipset & onboard sound
nVidia 8600 GTS Super video card with 512Mb 
4Gb RAM

I cannot get any sound, video or flash files to play by any app.

Not sure how long sound & video files have been unplayable as I've been
concentrating on getting flash working.

I actually found the sound issue when, my install of T/Bird kept locking-up
straight after d/loading email.  It turned out to be my custom .wav file was
the cause.  I tried playing the .wav file by itself & Totem lock-up solid &
had to "Force Quit" (FQ) to close.

This happening, prompted me to try other audio formats & then, files with 
the different video formats I have.  Everyone of the would lock-up Totem
requiring a FQ to close it.

By going through Synaptic, I checked what plug-ins & codecs were installed
and added a few extra (in addition to the one's installed by default) that
I thought may help, but to now avail.

Additionally, I have tried every suggested fix to get flash working but, 
again, no luck there either.  I gave up on Hardy after about 6-8 weeks and
now wondering if going back to ver. 6.06 LTS might help.

I'm now at a complete loss as to how to resolve these issues. I don't
want to even contemplate going back to windoze but, I need a working system
that doesn't give me problems like I've been experiencing for the last 5-6 months.

---

### Post by netsurfau on 2008-07-05
Bump

---

### Post by Sealbhach on 2008-07-05
What model computer have you got?

Does the sound work when you test it in System/Preferences/Sound ?

Have you tried any of the tests here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I don't know much but there's a step-by-step diagnostic in that thread which could help you pinpoint what the trouble is.


.

---

### Post by Artemis3 on 2008-07-05
I had flash working just by installing the usual ubuntu-restricted-extras package.

Your sound issue sounds intriguing, maybe you should try lspci -v in a terminal and paste your audio results, for example i have:

```
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 81f6
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fe020000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping
```

Usually when ubuntu loads it plays a sound, also when the user logs after entering password it plays another sound. Does that sound work? Also check System -> Preferences -> Sound (test buttons).

---

### Post by netsurfau on 2008-07-05
PC was built for me by a local retailer.

Testing sound with Sys/Prefs/Sound resulted in locking-up the utility & I had to FQ to close it.

The link [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) was a ripper.
Now have sound back - Thanks.

Checked video files.
.wmv played fine.  Streaming from [http://www.smh.com.au](http://www.smh.com.au) still wont work.

Like (it seems) a number of people, I still can't get F**king flash to work,
and have tried every fix that's been listed in this forum.  Might try ripping
out all flash files and start from scratch - again.

---

### Post by netsurfau on 2008-07-06
After last flash re-install, now able to view .flv files but no other flash.
YouTube and other pages with embedded flash still wanting Flash Plug-in.

Really getting sick of this.

---

### Post by Sealbhach on 2008-07-06
Did you see the Flash troubleshooting section on this page here?

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

[QUOTE= reassuringlyoffensive]
--TROUBLESHOOTING--


ADOBE FLASH


On occasion, installing the Adobe Flash plugin and/or watching online Flash streams successfully isn't as simple as it might ordinarily be. If you have tried installing it already and are having issues, read on. First of all, please disable any ad-blocking Firefox extensions you have installed, such as Adblock Plus, as they can sometimes interfere with the Flash content you actually want to see. If you are still having issues after disabling the extension(s), you should now completely purge Adobe Flash from your system, along with any other packages which may be interfering with it, reinstall only Adobe Flash, restart Firefox and then test Flash performance again. Will both 32-bit and 64-bit users copy and paste this command into the terminal:

sudo apt-get purge flashplugin-nonfree gnash gnash-common libflash-mozplugin libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree

Still no joy? I would suggest following the instructions below for your particular Ubuntu version and architecture. I would also suggest that Hardy Heron users install version 10 of Flash, despite the fact it's beta, as it has full support for PulseAudio and performance improvements.[/QUOTE]



.

---

### Post by netsurfau on 2008-07-07
I "bit the bullet" again today and re-upgraded to Hardy.

Seems to have helped in resolving a couple of issues but, flash still giving a bit of grief.  Another member called "Soxs" has given easily followed instructions that should resolve Flash in another thread I started.  Will follow those & (fingers crossed) I should be right.

Thanks for the help

---


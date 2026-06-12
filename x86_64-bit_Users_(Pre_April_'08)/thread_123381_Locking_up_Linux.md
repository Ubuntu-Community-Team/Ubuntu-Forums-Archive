---
title: "Locking up Linux"
date: 2006-01-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-01-29
Ubuntu-64 Breezy on Compaq R3240 laptop.

At least once a week I lock up my Ubuntu-64 Breezy laptop and have to hit the power button to get out. Mouse is dead, keyboard dead, no screen activity. It happens at random, but never all by itself. In other words, I do something and it's suddenly locked up. It might be inserting a graphic into an OO.o Writer document, opening a web site in Firefox, playing an mp3 with xmms -- I can't find any common thread. But I never come back to the computer and discover it locked up while I was gone. It always happens when I do something. Just now it happened when I had Kfind open searching for files. It had found two and was still searching. I selected one of them and right-clicked to see the properties. Bang! Dead in the water.

I should also add that I have no beta software on this computer. Everything is officially released or I don't install it (except for OO.o 1.93, but that is actually the most stable program on this computer). Nevertheless, apps lock up all the time. A couple times a week I have to shell to a command line and do "top" to kill something.

Is this common? Is it Linux? Or flaky apps? Or maybe both? Like Linux should do a better job of keeping a flaky app from locking up the OS?

Looking for stability. Getting tired of having to restart all the time. :(

---

### Post by moephan on 2006-01-29
Perhpas your are encountering the issue with powernowd? Check out this thread and see if it might be related your problems.
[http://ubuntuforums.org/showthread.php?t=76288&highlight=hang+powernowd](http://ubuntuforums.org/showthread.php?t=76288&highlight=hang+powernowd)

Good luck.

Cheers, Rick

---

### Post by RAOF on 2006-01-29
That's a bit weird.  Could it be flaky memory?  You can run a memtest from the grub boot menu - maybe you should try.

I'm running Dapper64, and that's full of all sorts of beta software - that never hardlocks, and when I was running Breezy64 the only way I could get it to do that was by trying to eject my firewire iPod (& that's been fixed now ;))

In short, you shouldn't be having these problems.  It **may** be some sort of hardware fault, or maybe the kernel hates one of your hardware devices.  You could also try checking out the system log (I think it's under Applications -> System?) and seeing if there are any error messages in there.

---

### Post by John Jason Jordan on 2006-01-29
[QUOTE=RAOF]That's a bit weird.  Could it be flaky memory?  You can run a memtest from the grub boot menu - maybe you should try.

I'm running Dapper64, and that's full of all sorts of beta software - that never hardlocks, and when I was running Breezy64 the only way I could get it to do that was by trying to eject my firewire iPod (& that's been fixed now ;))

In short, you shouldn't be having these problems.  It **may** be some sort of hardware fault, or maybe the kernel hates one of your hardware devices.  You could also try checking out the system log (I think it's under Applications -> System?) and seeing if there are any error messages in there.[/QUOTE]

I doubt it's memory. This computer is only 6 months old and the problems started mostly after installing Ubuntu. Admittedly I didn't spend much time in other distros, but they never locked up.

I'll look at the system log later. Right now I am trying to recover. I had a long homework document open in OO.o writer at the time it locked up. No problem -- OO.o Writer recovered it, not that it was even necessary, as I save often. But when I opened it up the font was some serif system font, not the special linguistics font I need for this document. I selected the whole document and opened the fonts drop-down list and guess what? My linguistics font is no longer installed. In other words, OO.o substituted something else because it couldn't find the font used in the document.

Now I can't remember where the fonts are installed. There are so many folders on a Linux machine and none of them are named with human names, like "here is where your damn fonts are."

So I clicked on System > Help, only to be reminded that Help will not load. All I get is "Yelp quit unexpectedly." Considering that it always quits, it is no longer really unexpected, now is it? I clicked on the button to send a report to the developers a long time ago, but even though I always do all upgrades, Yelp still won't run. I also uninstalled and reinstalled it via Synaptic.

Luckily I have copies of the fonts on this Windows machine. But I guess now I have to go off and google for help on where the fonts are.

Every time it locks up something annoying like this happens. That's why I'm pretty sure it's software incompatibilities, not hardware.

Grrrr.

---

### Post by RAOF on 2006-01-30
That problem could be due to all the hardcrashes starting to drive your filesystem nuts.  Could be time for a fsck.  I **think** you can go to fonts:// in nautilus, or something similar, to get at your fonts.

---

### Post by John Jason Jordan on 2006-01-30
[QUOTE=RAOF]That problem could be due to all the hardcrashes starting to drive your filesystem nuts.  Could be time for a fsck.  I **think** you can go to fonts:// in nautilus, or something similar, to get at your fonts.[/QUOTE]

Actually, after I calmed down I suddenly realized I knew the name of the font and could just do a search. And when Kfind located the files, I remembered where they were supposed to be, because that's where they were. So then I closed down OO.o and restarted it. Still no fonts. Shut down the computer and restarted it, then restarted OO.o -- fonts back again. So evidently the problem was in OO.o, and is resolved. That is, until something screws up again. 

OO.o never crashes, but it has other flaky moments, and this is a typical example.

Thanks for the suggestions.

---

### Post by Jason_25 on 2006-01-30
I second the recommendation that the problem could be powernowd.

Remove the package and see if the lockups stop.

---

### Post by John Jason Jordan on 2006-01-30
[QUOTE=Jason_25]I second the recommendation that the problem could be powernowd.

Remove the package and see if the lockups stop.[/QUOTE]
What does powernowd do? If it extends battery life I might be better off putting up with the lockups. This laptop sucks the battery down like a fat kid with a milkshake.

---

### Post by moephan on 2006-01-30
My understanding is that powernowd does, in fact, work with cpu frequency monitor, etc... to adjust power consumption. 

You might want to consider removing it and seeing if the hanging stops. You could always add it back in again if it wasn't causing the problem or if you can't with the battery life.

Cheers, Rick

---


---
title: "Weird video output"
date: 2006-02-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by gabrielpm on 2006-02-05
Hi!
I have a Powerbook G4 Titanium.
I installed 5.10 from a DVD with video=ofonly because otherwise I would get garbage on screen (blots of purple and random lines... much like an assembler demo, really).

After I've completed install the system boots, I see the initial checklist (everything is OK except the time synchronisation) but the Ubuntu logo isn't looking right... there are red pixels all over the logo and it looks sort of inverted.

After the boot I get the same strange color blobs that slowly fade away and I'm left with a blank screen, I hear some drums and I can get more drums if I hit enter. (It seems it booted properly but there's an X error).

Using Linux video=ofonly doesn't change this behavior.

Ctrl+Alt+F1 stops the purple blobs but then I'm left with a black screen with a slight flicker at the bottom...

My questions are:

1) How do I do to boot in text only mode?
2) Does anyone know how I can fix this video problem?
3) What's the best resolution for a 15" Powerbook and how can I set it? (1280x768 in OS X)

Any ideas? Thanks a lot!

---

### Post by koni2005 on 2006-02-06
Finally someone with exactly my problem - I posted stuff in other threads here - hopefully not already bugging people.

The weird thing is however - that had ubuntu and kubuntu 5.10 installed scince October 05 and it worked perfectly without the slightest problem. Then, one day I rebooted kubuntu and suddenly there was this weird behavior. I rebooted several times and suddenly it booted up without the "display crash".

For the installation process - I also tried a fresh install with video=ofonly - wich works well - but again, after rebooting I end up with a black screen and the ubuntu logo color palette is totally weird - red, yellow, etc. - looks like the color palette has a standard colors that are used by default if no graphics driver is running - like "EGA" graphics on old PCs.

By the way - when installing in video=ofonly - the background is red and the letters are blue. When installing normally (or in expert mode - which still seems to work until the installation process reboots) - and the display does not crash - the background is blue and the letters are red.

Does anyone have an idea what's wrong here?

---

### Post by koni2005 on 2006-02-07
Just a wild guess: Could it be that the OS X Tiger update from 10.4.3 to 10.4.4 has also changed the ATI graphics drivers and maybe installed some kind of firmware patch on the graphics card itself (in my case an ATI Radeon 9000 Mobility with 64MB), so that it does not work correctly with the xorg drivers anymore?

I don't know if this is complete nonsense - but would really like to get ubuntu up and running again, as it did work perfectly until 2 weeks ago...

---

### Post by koni2005 on 2006-02-08
Are we really the only ones with this problem?

Well, I tried rebooting again - and at the second try it worked!
Of course the next try wasn't succesfull anymore - and I ended up with those weird artifacts again.

But now I know exactly were the display crashes: If it does not crash, there is a message saying something like:

radeonfb: Invalid ROM signature 0 should be 0xaa55

although the numbers are different, I guess...

does this ring a bell with someone?

---

### Post by ben@powermac on 2006-03-12
I have the same prob, but not only when starting up. The color is all messed up, and the only way I can temporarily fix it is by logging out and back in, changing the resolution reverting it back to normal.

I am on a dual 500mhz g4 with ATI Radeon 32mb.

---

### Post by jdp on 2006-03-12
[QUOTE=koni2005]But now I know exactly were the display crashes: If it does not crash, there is a message saying something like:

radeonfb: Invalid ROM signature 0 should be 0xaa55[/QUOTE]


It seems alot of ATI-based Macs get that.  I know I see it on my iMac G3s, and ISTR it on my Beige G3MT with it's ATI PCI video card.

---

### Post by shreeswifty on 2007-08-15
i have the same problem on my G4, just started happening. 
Has anyone found a fix for this?

i re-installed OSX just for kicks and it works fine.

infuriating

---


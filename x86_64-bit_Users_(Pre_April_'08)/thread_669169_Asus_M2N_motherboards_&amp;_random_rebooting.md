---
title: "Asus M2N motherboards &amp; random rebooting"
date: 2008-01-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by otchie1 on 2008-01-16
I have an Asus M2N-SLi deluxe with an AMD 3800+ and in common with many thousands of other Ubuntu users I have stability issues. 
My reboot goes like I pulled the power lead out. Bang, system down. Reboots automatically and it's back in 20 seconds or so. Happens several times a day (or not at all).

In the hunt for the cause of my random reboots (and odd GUI lockups) I have,

junked dhcpcd and Network Manager in favour of dhclient
Killed all screensavers
Checked, rechecked and checked again for temperature problems (nothing ever gets hotter that 59 degs)
Removed my wifi board
Removed my EIDE/SATA expansion board
Disconnected CD & DVD drives
Dumped the Ubuntu restricted drivers for NVidia originals
Moved from Firefox to Galeon and thence to Opera
Tried noapic, nolapic & apm=off as boot parameters (acip = off kills my USB)
Run memtest for hours with no faults
Moved my RAM to other slots
Junked my 2nd VGA & associated SLi stuff (twin 7600GS)
Pulled unused bluez utilities out
Run it with the sides off and fans blowing at it

NONE of the above solved it.

The onboard MCP55 SATA hasn't worked properly since Edgy. In fact, this board has become more unstable as Ubuntu progresses up the alphabet.

So, IMHO, my instability issues on this hardware are caused by Ubuntu. Backwards compatibility has been lost.

Has anyone else got issues with this SPECIFIC motherboard? People with just random lock ups can add their names to the list in other topics....just ASUS M2N-SLi please.

I can hardly believe it....stability issues under Linux...that was a Win95 problem for pity's sake.

---

### Post by OoooMatron on 2008-01-16
I have the M2NS-NVM. I don't know how close it is but I guess it must be from the same family (mine is an nvidia chipset I think). 

I had stability issues with my board and Corsair ram, which I replaced with another brand and everything has been just fine. (note that it returned no errors in memtest either).

Another problem with random rebooting is commonly (but people don't realise) linked to an under powered system from a low Watt power supply or too many devices in the PC draining the power.

Could be one of these two issues.

I don't have any issues with Gutsy at all now with this setup.

---

### Post by otchie1 on 2008-01-16
I feel I may be apologising to Ubuntu shortly.

I had a matched pair of 2 1GB DDR sticks from Buffalo but during a recent box-build-fest had to scavenge bits for testing. What's gone back in is two odd  albeit 'matching' 1GB sticks.

I've ripped one out so I'm back down to 1GB but I'm crash free since doing it.

Hopefully that'll be the end of that but shouldn't good memory management include error catching at OS level? Maybe it's not so easy as that......

---

### Post by OoooMatron on 2008-01-17
Yeah, seems to mirror my experience.

I bought the matching corsair because it was so cheap but it just caused a lot of frustration. I didn't actually test in Windows to see if it crashed.

I ended up swapping my 2x1gb for 2x512mb and buying another stick of 1gb that was a different brand. No problems at all now! Running a 3gb machine without a hitch.

---

### Post by otchie1 on 2008-01-18
Crash free now so it's as confirmed as it's going to get.

Also did a fair bit of reading around and it seems as though all AM2 based motherboards are 'twitchy' about their RAM especially when more than one stick is fitted.

As so many of the 'Gutsy crashes' threads involve AMD 64bit boxes I guess a lot of people are discovering the same thing.

Anyway, Ubuntu, I am sorry I doubted you and I'm glad that you're back to your stable self. :)

Just a by the way, read in several places that often the mobo gets the memory voltage wrong and that it is best to set it manually to whatever the memory manufacturer states. Some even suggest stick another .1V or so on top for better stability.

---

### Post by drs305 on 2008-01-18
otchie1, I have the same motherboard and cpu. I'm running 4GB of kingston ram and have never had a problem. Until you found the solution, I would have suspected, as did another poster, that the problem was with the power supply...

Glad you were able to solve the problem.

---

### Post by otchie1 on 2008-01-18
If it wasn't a Hiper Modular 580W job so would I. Thing could probably jump start my land rover.:guitar:

Matched 2G of approved Kingston (KVR800D2N5K2/2G) ordered for a paltry £35 delivered.

Was gong to risk OCZ or Geil but I'll let some else have that compatibility experience.

---

### Post by drs305 on 2008-01-18
... and it looks like it can power your guitar as well!

---

### Post by Mr.Auer on 2008-01-19
I have Asus M2N with AMD X2 64 5000+ cpu, 2 gb ram, mobos chipset is NVidia nForce 430 MCP, integrated HD Audio by Azalia, graphics Winfast NVidia 8600 GT. This is a brand new machine, no SLI. I just installed 64-bit Gutsy, and have been running tests for 2 days since (lots of programs doing heavy stuff all the time, both cores maxed, mem at 80% and swap at 10 for two days straight, gamig as well with Quake Wars). I have no problems at all, no instability issues and no crashes. 

Only issue ive had was that I get no splash screen on bootup, and ive disabled splash for that reason (this is a known and confirmed bug in Gutsy). Otherwise fine and stable..

Do you have the Nvidia chipset on the motherboard as well? If so, it would seem the difference is the SLI...Im running repository Nvidia drivers myself, and they seem to work fine. Compiz Fusion running as well.

I also had all default services running for the first day, and yesterday I disabled all that I didnt need (like bluetooth, bluetooth printing, apport bug reporting etc). Still fine..

Edit: lol, didnt read all of posts and didnt realize it was solved :) Good thing!

---


---
title: "64-bit LiveCD won't boot on AMD processor, hangs at powernowd"
date: 2008-10-30
forum: x86 64-bit Users
---

### Post by deruberhanyok on 2008-10-30
We had a short thread going about this in the testing forum. Here's the basic version:

64-bit LiveCD won't boot. Loads most of the way and then activity stops, eventually displaying the text screen showing modules loading. It seems to have stopped at "powernowd" and won't go any further.

The only common equipment we found so far was that we're all using AMD processors. I found that 8.04 64-bit does the same thing. I'd previously run it on a Core 2 Duo system and didn't have any problems.

Is anyone else having this issue?

([bug report here]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/267198"))

---

### Post by randiroo76073 on 2008-10-30
I'm running a AMD 64x2 5600, 4gb pc6400 ram and have had no problems at all with 7.10, 8.04, 8.10 so I can't help out at all.  I think I had to reboot 8.04 1 time from live cause it hung, but then it booted right up.

---

### Post by phlembob on 2008-10-30
Verify your CD the exact same CD you used before without problem.  During downloads I have heard several people with problems installing in these forums because of bad download of live CDs. I use AMD processors without problems.
:guitar:

---

### Post by dnns on 2008-10-31
I must confirm this problem. I've tried downloading the LiveCD .iso from 2 separate locations and burned them to 3 different CD's, all of which resulted in the same error when trying to boot. I can't even check if the CD has errors because my pc hangs. 

My Pc's got an AMD 5600+ X2 processor.

---

### Post by deruberhanyok on 2008-10-31
randi - thanks for the info. I started messing with a few BIOS settings and may have found a fix.

phlem - definitely the same 8.04 CD I used before.

dnns - Can you go into your system's BIOS and disable Cool N Quiet, and let us know if you can then boot the LiveCD? I turned it off and can boot the disc now, so I'm guessing the conflict is somewhere between Cool N Quiet and powernowd.

---

### Post by vijinho on 2008-10-31
i had the same issue just now.  disabling cool'n'quiet worked for me.

---

### Post by khmr33 on 2008-10-31
Check your BIOS for overclocking options.

Ubuntu uses Powernow to control the frequency and voltage of the CPU.

Your BIOS overclocking settings for Multiplier (frequency) and voltage must both be set to [AUTO] or Powernow can't assume control of them.

If Powernow fails to load because of this Ubuntu can't finish booting.

I made this mistake for weeks after having built a new machine with an AMD X2 Black Edition. I had the BIOS overclocking from 2.6 to 3.1 GHz since you could get that for free without changing the voltage.

It was only out of blind luck that I even figured out my motherboard had [AUTO] options for these settings since the list of multipliers was longer than the window frame and [AUTO] was at the top of the list off screen.

Hey, first post ever was an answer, not a question!

---

### Post by waffen on 2008-10-31
Are you try to burn the ISO Image in a lower velocity??

---

### Post by khmr33 on 2008-10-31
You should always burn any disc as slow as possible, but it's not likely the problem.
When I was dealing with this, I burned 32 and 64 bit versions of 8.04 ubuntu and kubuntu. None of them ever worked alternate or live it didn't matter. Once I fixed the BIOS, I installed without issue the first time.

---

### Post by fedora on 2008-11-01
i have the same problem in my AMD phenom quadcore 9750 however i've stopped the cool n quiet option in my bios

---

### Post by khmr33 on 2008-11-01
That is weird, I'm pretty sure I still have cool n quiet enabled. I don't think I had that cause problems...

---

### Post by deruberhanyok on 2008-11-01
khmr - well, while I have a black edition processor that allowed me to change the multiplier, others in the old thread we had did not. I'll have to double check my settings but I'm pretty sure everything is on auto (first thing I usually do when I'm having a problem is reset clock speeds/voltages to defaults).

I wonder, though, if it would pertain to any setting being specified and not on auto... Hmm. I'll mess with the BIOS a little and then post back here.

---

### Post by deruberhanyok on 2008-11-01
Well I had the settings on auto but for some reason it was keeping the multiplier higher than default. I had to switch the top level OC setting back to manual, change the multiplier setting to auto and then switch the main OC setting to auto.

With everything forced to auto the system will boot with cool n quiet enabled. So I guess the question now is:

For anyone experiencing this problem, have you changed any CPU settings in the BIOS?

---

### Post by khmr33 on 2008-11-01
Even on my Black Edition the default is the multiplier that equals 2.6GHz. Now on Auto with Ubuntu running on my machine the default at rest speed is 1GHz. It won't hit 2.6GHz unless I'm doing something.

That was one of the first things I did when I had a problem. I dialed back the multiplier to the default, but that's still a multiplier that locks the CPU to a certain speed and the BIOS needs to allow the OS to throttle the clock speed and voltage in real time.

What kind of motherboards are we talking about?

I have the ASUS M3A-78 EMH HDMI with ATI780g...

---

### Post by deruberhanyok on 2008-11-01
The old thread is here:

[http://ubuntuforums.org/showthread.php?t=925193](http://ubuntuforums.org/showthread.php?t=925193)

Of the other two that posted specs, one had an AMD 770 chipset board and another was an nForce 4 board. I'm using an Asus M3A79-T Deluxe, 790FX chipset.

I'll add this information to the bug report and see where it goes from there.

If anyone has other findings to report that either confirm this information or disprove it please post it here.

---

### Post by mirca_sp on 2008-11-01
Well, I downloaded the LiveCD 8.10 64bit iso, checked md5 and burned at low speed the CD. I´ve got 2 CD/DVD devices: ide and sata. When I first tried to boot by the sata one, it hapenned the same ´bug´. However, with the same cd i tried to boot by the ide one and it loaded without any problems. I didn´t make bios change.
I have a AMD X2 5200@2.7GHz on M2N-SLI/4GB RAM Corsair

---

### Post by deruberhanyok on 2008-11-01
I've updated the bug report on launchpad with the information posted so far.

---

### Post by shane2peru on 2008-12-24
I have the same problem, but mine is intermittent.  Sometimes even on my Ibex installation I still have this problem.  I simply shut it off and reboot and it seems to do fine after that.  I also noticed this on the liveCD and thought it was a problem with the CD, but now I have re-tried it and learned that sometimes it causes a hang, and sometimes it doesn't on my box.  I"m using a Toshiba Satellite Laptop, AMD 64 Turion x2.

Shane

---

### Post by mredding on 2009-02-22
The Live CD ran okay for me, but after installing and trying to boot the installed OS it wouldn't get past "Starting powernowd..." at all. HP Pavillion dv7-1245dx with AMD Turion X2 Dual Core Mobile RM-72 processor. The BIOS doesn't seem to have any multiplier or cool 'n' quiet options. Unsure if this is 100% related.

EDIT: Intrepid 8.10, BTW. Should have mentioned that.

EDITx2: Kernel update, and the problem seems to have gone away.

---

### Post by shadowhacker on 2009-02-25
> **shane2peru said:**
> I have the same problem, but mine is intermittent.  Sometimes even on my Ibex installation I still have this problem.  I simply shut it off and reboot and it seems to do fine after that.  I also noticed this on the liveCD and thought it was a problem with the CD, but now I have re-tried it and learned that sometimes it causes a hang, and sometimes it doesn't on my box.  I"m using a Toshiba Satellite Laptop, AMD 64 Turion x2.

Shane

I have the exact same problem. It happens once in a blue moon, usually after installing something. It's not very irritating, as a quick reboot fixes it for me as well. I also have the Turion x2.

To the person having problems with one CD/DVD drive and not another, the problem IS the Disc. Always burn operating systems with Disc-at-Once, not Track-at-once. I don't know why, but like 50% of optical drives I've encountered hate booting from Track-at-once discs.

---


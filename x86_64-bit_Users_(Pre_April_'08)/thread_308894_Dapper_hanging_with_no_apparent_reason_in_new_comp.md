---
title: "Dapper hanging with no apparent reason in new computer"
date: 2006-11-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by tszanon on 2006-11-28
Hi,

I installed Dapper 6.06.1 in my new computer:
Athlon64 X2 3800+ (stepping F2)
Mobo Gigabyte GA-M55SLI-S4
DDR2-800 Corsair 1GB (Single-channel)
XFX GeForce 7600GT
2 HDD Sata Seagate 160GB in Soft-RAID0

The computer works fine, but then, after not being used for some time, it hangs. I find out it has hung when I get back, turn on the monitor and it doesn't come back to life (it turns on, but no signal received, or the screensaver image).

As far as I remember, it's running only aMule (from repositories) before it hangs. Nothing unusual has been done, since I'm still checking how the system behaves in this hardware. No overclocking (well, MemTest tells me that the cpu clock is 2010 MHz and the memory clock is 402MHz, but I double checked the BIOS settings and everything is ok. The P.O.S.T. says that the "FSB" is 200MHz, as expected).

I've already tested the memory module, and it seems to be ok. Checked the HDDs, and both also seem to be ok. I have also ran aMule overnight and it was fine, no hanging at all.

Can anyone give me a suggestion on what else should be checked? I really don't have a clue on what is making the computer hang. I'll really appreciate it.

---

### Post by d.j.schroeder on 2006-11-28
I have a nearly identical problem.  No clue what it is.

Only difference is that my desktop usually reappears, it just won't respond to anything.

---

### Post by tszanon on 2006-11-28
I'm going to run aMule overnight again (I'm going to sleep, it's 12:15 AM here).

One thing I forgot to mention is that when it hangs, the memory Activity LEDs are on (they're not blinking, they are continuously on).

I just remembered that, when turning the computer on, it just didn't do anything. I had to reset it in order to make it work. It has happened twice and, in this case, the memory activity leds were on, too.

If I find anything out, I surely will post my findings here. In the meantime, if anyone here has any crazy idea on how to fix this (that doesn't include burning down the house or something like that :mrgreen: ), please share it with us.

---

### Post by Harry_Callahan on 2006-11-29
Hello,

In the last 3 days I'm having the same problem. The first two times I was using aMule and Azureus, I then found both of them shut down, the second day I has using only aMule, same thing, I found it shut down. This morning I heard my HD grinding and had a black screen, slowly the desktop began to come back. I found an error on the kernel log, "out of swap memory"(only in the log of the first time). My desktop' responds after this happens. I've been using 6.10 for over a month and never had this problem. Does anyone remember if this happened after any update?

---

### Post by tszanon on 2006-11-29
I'm back. :) 

This morning, I woke up and noticed that the computer was fine. Nothing unusual. I turned it off and went to work.

I'll keep my eyes wide open. Up to now, I haven't found anything that could be causing problems.

@Harry_Callahan: In my case, I haven't found anything in the logs. Everything is normal.

---

### Post by tszanon on 2006-11-29
Back again...

When trying to start the computer, it didn't start. Everything seemed ok, but the P.O.S.T. didn't run. No video signal. After turning the computer off and on again, things were ok.

So, I believe it is a motherboard issue. I'm going to check it out.

---

### Post by tszanon on 2006-11-29
I did some research and a lot of people say that it's an AM2 issue concerning PC6400 memory modules. Something about voltages, memory timings and so on.

Possible causes that I listed from various sources:
- memory voltage being used is below the voltage level the memory needs;
- most AM2 socket motherboards have problems with DDR2-800 memory modules;
- problems concerning Cool n Quiet technology;
- one person said that his problem was one of those video cards that are produced overclocked. He replaced his card with an non-overclocked one and the problem never occured again. Anyway, this seems to be an isolated case.

As I already told you, since my board won't boot at first when I power on the computer, and the strange behavior in the memory activity LEDs, I'd say that those memory issues make sense to me. Maybe the memory voltage/clock/timings are my problem, since these 3 settings are all related (higher voltage means higher clock and better timings).

In order to be safe, I'd suggest decreasing memory clock and increasing timings before attempting to increase memory voltage, avoiding damage to the module.

I haven't tested anything yet - I'm waiting for the problem to occur once again. If anyone here tests the above suggestions, please report what you find out, ok?

Thanks to you all, hope you can solve this problem!

---

### Post by d.j.schroeder on 2006-11-29
I seem to have a similar problem as what you're describing, but with an older Intel machine.  Could be a totally separate thing I guess but my problem is clearly not AMD socket AM2 related.

---

### Post by RAOF on 2006-11-29
Another fine culprit is your nVidia card.  Have you installed the proprietry drivers (the **nvidia-glx** package)?  If not, you might want to try:
1) install the **nvidia-glx** package
2) Run, from a terminal **sudo nvidia-xconfig** - this updates your configuration (/etc/X11/xorg.conf) to use the new driver
3) Restart your GUI.  Log off, then either press Ctrl-Alt-Backspace or (better), switch to a terminal (using Ctrl-F1 or Ctrl-F2, or, ... -F4), login, and run **sudo /etc/init.d/gdm restart**.

---

### Post by tszanon on 2006-11-30
> **RAOF said:**
> 2) Run, from a terminal **sudo nvidia-xconfig** - this updates your configuration (/etc/X11/xorg.conf) to use the new driver

nvidia-xconfig? I used **nvidia-glx-config enable**, as written in the UbuntuGuide. I'm not at home now, so I can't check if there's any difference between them. :( 

Anyway, yes, I installed the nvidia drivers. Doom3 tells me the video card works :D 
*******************
Yesterday the computer hung again. I changed the memory speed down to 667 MHz. It worked fine all night, but hung again this morning. This problem is starting to really annoy me...:mad: 

I did some more research and found someone saying that the problem may be the 24pin motherboard power connector. He suggested that the extra 4pin should not be used. I think that the only problem in doing it would be some more load on the other wires, but I'm not qualified to say such thing. I think I'm gonna try doing this...

---

### Post by tszanon on 2006-12-01
Anyone tried any of these possible solutions? Yesterday I unplugged those extra 4pins of the motherboard power connector. Up to now, the computer was fine. Let's see if it freezes again...

---

### Post by bloose on 2006-12-01
I had the same problem.  It turned out to be a corrupted screensaver that would hang the video card when it tried to display it.  I turned off the screen saver about 4 months ago and it hasn't happened since.

The easiest way to test if that is the problem is to go into System>Preferences>Screensaver and see if the computer hangs when the screensaver is displayed.  It the computer hangs you can ctrl+alt+F1 to go to the text window and kill the screensaver process.  Then ctrl+alt+F7 to get back and see if the screen is unhung.

Hope that helps

---

### Post by tszanon on 2006-12-01
> **bloose said:**
> (...) It turned out to be a corrupted screensaver that would hang the video card when it tried to display it.(..)

go into System>Preferences>Screensaver and see if the computer hangs when the screensaver is displayed.  It the computer hangs you can ctrl+alt+F1 to go to the text window and kill the screensaver process.  Then ctrl+alt+F7 to get back and see if the screen is unhung.

I'm going to try it for sure, but I don't think that's my case. When the computer hangs, nothing works, not even CTRL-ALT-Fx :( 

Update on my situation: After I arrived home, I turned the computer on and the machine is still fine (about 1 hour ago). It seems that that post about the extra 4pins is correct. But it's too early to say that the problem is solved.

Thanks!

**Edit:** I tried to watch all screensavers. Some of them couldn't be previewed, but none of them froze the computer.

---

### Post by tszanon on 2006-12-06
This morning, I noticed it was frozen again. Maybe the chipset is getting too hot?:sad:

---

### Post by d.j.schroeder on 2006-12-10
I finally figured out what correlates to my problem.  Every time my ISP changes my IP address the machine hangs up.  I have no idea why, but that's when it happens.

Any ideas?

---

### Post by tszanon on 2006-12-10
> **d.j.schroeder said:**
> I finally figured out what correlates to my problem.  Every time my ISP changes my IP address the machine hangs up.  I have no idea why, but that's when it happens.

Wow, THAT'S weird.

My ADSL modem is configured as a router, so, when the ISP changes my IP address, the computers in the LAN don't notice that it has happened. Only the modem is affected.
Anyway, this really doesn't make any sense. At least, not to me.:???: :-k

---

### Post by d.j.schroeder on 2006-12-10
It doesn't make sense to me either, but that's what's happening.  My computer is attached directly to the DSL modem and is aware of the actual IP address.  Maybe the solution is to get a router?

---

### Post by tszanon on 2006-12-10
> **d.j.schroeder said:**
> Maybe the solution is to get a router?

Hmmm...well...I wouldn't tell you to do so, because:
1. I don't know if it's going to work;
2. A router isn't free :mrgreen: 

If you could borrow a router to test this solution, it would be great.
I don't have any ideas on how to help you, so, if you can't do some tests, buying one seems to be the only thing to do.

Maybe you could wait a few days to see if someone else has a suggestion before spending some money.

---

### Post by d.j.schroeder on 2006-12-11
This is probably even a crazier solution but I've been wanting to try it anyway, maybe it will help this problem (it did it again today, IP change and lockup).

I have an old PC and a bunch of cheap network cards lying around, I was thinking of using it to make a Smoothwall box and using that and a switch as a router.  We'll see if I can find the time.  Otherwise I don't mind throwing a few bucks at a router to see if it helps.

---

### Post by tszanon on 2006-12-12
> **d.j.schroeder said:**
> This is probably even a crazier solution but I've been wanting to try it anyway, maybe it will help this problem (it did it again today, IP change and lockup).

I have an old PC and a bunch of cheap network cards lying around, I was thinking of using it to make a Smoothwall box and using that and a switch as a router.  We'll see if I can find the time.  Otherwise I don't mind throwing a few bucks at a router to see if it helps.
That's probably going to be a little time consuming, but if it works (and I believe it will), it will be worth the effort. Good luck!

---

### Post by d.j.schroeder on 2006-12-13
Well, the Smoothwall box is up and running with the Ubuntu machine behind it.  Everything is working fine at the moment.  Now I just wait and see I guess.  Hopefully, now that the address will never change from the perspective of the Ubuntu machine everything will stay working fine.

---

### Post by tszanon on 2006-12-14
> **d.j.schroeder said:**
> Well, the Smoothwall box is up and running with the Ubuntu machine behind it.  Everything is working fine at the moment.  Now I just wait and see I guess.  Hopefully, now that the address will never change from the perspective of the Ubuntu machine everything will stay working fine.

That's great. Please come back in a few days and tell us if it has really worked.

---

### Post by Cynical on 2006-12-14
Your problem could be power supply related. I just had this same problem, fortunately this is the first time. I know for a fact that my power supply is a weak generic brand one that I'm planning to replace soon. I don't really see any other reason because all of the other components in my computer are new. (I also get warning messages about my video card not receiving sufficient power in windows, in linux I sometimes get a message saying that my power connector may not be plugged in)

---

### Post by tszanon on 2006-12-15
> **Cynical said:**
> Your problem could be power supply related. I just had this same problem, fortunately this is the first time. I know for a fact that my power supply is a weak generic brand one that I'm planning to replace soon. I don't really see any other reason because all of the other components in my computer are new. (I also get warning messages about my video card not receiving sufficient power in windows, in linux I sometimes get a message saying that my power connector may not be plugged in)

Though I doubt that my problem is PSU-related, I don't exclude the possibility.
I have an Enermax Liberty 400W, which I believe is enough for the system, but with few spare watts available. My full system consists of:
Athlon64 X2 3800+
1GB DDR2-800 Corsair (single module)
Sony DVD-writer DRU-820A (IDE ATA)
XFX GeForce 7600GT (PCI-E x16)
1x FDD
2x HDD Seagate 160GB SATA 3Gbps 7200RPM (RAID0 for Ubuntu)
1x HDD Seagate 80GB SATA 1.5Gbps 7200RPM (Gaming Windows)
2x 8cm cooler
1x 12cm cooler

Together, these items require some more than 300W.

If the system rebooted instead of hanging, I'd bet it would be a problem with the PSU. But it never reboots, it just freezes.

I have another problem, in which the computer refuses to boot when I turn it on. Gigabyte says to update BIOS in order to solve the problem. I'm going to do it today; maybe the new BIOS corrects this problem too.

---

### Post by d.j.schroeder on 2006-12-19
One week and a couple of IP changes later, no lockup.  Looks like the router fixed it.

---

### Post by tszanon on 2006-12-20
> **d.j.schroeder said:**
> One week and a couple of IP changes later, no lockup.  Looks like the router fixed it.

Great! I'm glad to know that your problem is solved.
But I still would like to know why your computer hangs when the ISP changes your IP address...

---

### Post by d.j.schroeder on 2006-12-24
It's been changed by the ISP at least twice now.  Still running...

---

### Post by tszanon on 2006-12-24
> **d.j.schroeder said:**
> It's been changed by the ISP at least twice now.  Still running...

As I said before, my computer had another problem that kept it from running the P.O.S.T.
I found out that the Reset cable (the cable that connects the motherboard to the reset button) was defective.

The computer stopped hanging sometime ago, but I don't know why. Maybe the problem still exists, but for some weird reason it has not hung again for a while. Maybe the cause for both problems was the Reset cable.

I don't know why it started hanging, nor why it has stopped hanging. And, again, it's good to know that your workaround works :)

---


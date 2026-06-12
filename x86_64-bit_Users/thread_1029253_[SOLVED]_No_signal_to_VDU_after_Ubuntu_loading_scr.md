---
title: "[SOLVED] No signal to VDU after Ubuntu loading screen"
date: 2009-01-03
forum: x86 64-bit Users
---

### Post by ucof on 2009-01-03
Hi there all.

New to Ubuntu and Linux in general, so even if you say "copy x to here and edit"; I will have no idea what commands to type :)

Pc spec is as follows:
AMD Athlon 64 3500+ Processor
Gigabyte GA-K8NF-9 (rev 1.0) Motherboard
ATI Radeon X800 GTO PCI-e Video Card
3gb DDR 400 RAM
HDTV via S-video.
Dual boot with XP Pro.

I downloaded the latest Ubuntu x64 CD .iso and burnt it to disk to install. Popped it in the CD tray, booted from CD.... blank screen. Also tried in safe graphics mode, same problem.
Then downloaded the alternate X64 install CD, burnt to disk, booted from CD, at least I now have Ubuntu installed.

However,the problem is that after the "Ubuntu Loading" screen with the orange bar, at the point where it looks like it should go to the desktop, my VDU changes to the "No Signal" message and will stay like that until the TV turns itself off due to no signal. I tried changing the input to the TV from "S-video to composite" to "D-Sub"but problem remains.

I can press "Ctrl"+"Alt"+"F1" and the TV will click back on and display the command prompt.

I have searched both on here and on Google for an answer, and there seem  to be a few people reporting problems similar to mine, but not exactly the same. I have tried adding commands like "vga=794" etc, but the Grub boot loader doesn't seem to remember them when I try to boot. No one on the threads I read seem to have fixed the problems.

I have tried:

Going to recovery mode, then accessing Shell as root and editing xorg.conf to change the driver used; have used "vesa","radeon" and "flgrx" but still nothing is displayed on the screen. I have been able to wait for the HDD light to stop flashing,then entered my username and password and I hear the Ubuntu startup sound, but still nothing is shown on the screen.

Uninstalling compiz and compiz-core



Can anyone help me out please?
Thanks in advance.

---

### Post by ucof on 2009-01-03
Ok..so..I got a spare monitor and hooked that up expecting to see the exact same thing.

However, it correctly displays the desktop as it should.

So this leads me to believe that the problem lies in the signal that is being sent to the TV is unable to be understood by it.

How do I change the resolution of the desktop to one that is understandable by the TV?

---

### Post by ucof on 2009-01-03
Right,so...

Turns out that Ubuntu didn't like the S-video output on my card.

Both the D-sub and DVI output are recognised and I now have a pictureon my TV...

However, Imnow just getting a white screen and cursor. No desktop or anything :(

---

### Post by ucof on 2009-01-03
OK, so now, Im getting to the desktop.. and Ubuntu is just crashing. Not even Ctrl+Alt+F1 works

Everytime  :(

---

### Post by ucof on 2009-01-03
No longer crashing after I edited the xorg.conf file.

Just doing the last few tweaks.

---

### Post by cariboo on 2009-01-03
It seems you solved the problem yourself. Could you please mark this thread solved, by going to the top of the page and selecting Thread Tolls-->Solved.

Jim

---

### Post by ucof on 2009-01-03
Done.

However, Ubuntu is now being more annoying than I could have ever expected.

Going to give it one more try then I'm going back to XP.

---


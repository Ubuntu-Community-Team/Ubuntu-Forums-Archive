---
title: "problem with starting x"
date: 2006-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dr. Z2A on 2006-04-27
I just installed Ubuntu on my mac yesterday. I had X up and running just fine, but when I shut down the computer for the first time since I put Ubuntu on it this morning and turned it back on later, X didn't start correctly.  I booted from a floppy and set gdm to not start at boot, and then did a startx when I was logged in from command line and I had the same problem.  The mouse appears and I can move it around, but the screen is sort of like black with white marks scattered on it on the top 1/3 and on the bottom 2/3 its like a mixture of blue and red thatched.  I can't kill X from there so I have to press the power button to turn it off to get rid of it, although I may just not be putting in the right key combo to kill X.  Can anyone help me with this?

---

### Post by Monster_user on 2006-04-27
There are a couple things to try.

Press Ctrl-Option-F2 to switch to a command line, and type dmesg.

Alternatively, use ' vi /var/log/dmesg', and 'vi /var/log/Xorg.0.log' to view the log files.

Put the mount path in front '/var/log', but after 'vi', if you want to check them from a Live CD.

'vi /media/hda2/var/log/Xorg.0.log'

Post the results.

---

### Post by Dr. Z2A on 2006-04-27
[QUOTE=Monster_user]There are a couple things to try.

Press Ctrl-Option-F2 to switch to a command line, and type dmesg.

Alternatively, use ' vi /var/log/dmesg', and 'vi /var/log/Xorg.0.log' to view the log files.

Put the mount path in front '/var/log', but after 'vi', if you want to check them from a Live CD.

'vi /media/hda2/var/log/Xorg.0.log'

Post the results.[/QUOTE]
ok I did that and got the log files.  You can read the dmesg one at [http://www.dr-z2a.biz/logz/dmesg](http://www.dr-z2a.biz/logz/dmesg) and you can read the Xorg.0.log at [http://www.dr-z2a.biz/logz/Xorg.0.log](http://www.dr-z2a.biz/logz/Xorg.0.log)

---

### Post by Dr. Z2A on 2006-04-28
oh I also just remembered, my video card is overclocked, could that be the source of the problem?

---

### Post by Monster_user on 2006-04-30
I'm only seeing one error (EE) in your Xorg log, and none from dmesg. The one in the Xorg log, is a common error, and should not be causing this problem.

That is a common problem with unstable overclocks. It can cause glitches with X.

Try downclocking it.


Here is the reported clock setting, and the Error from Xorg.  It says it is Clocked to,...

200 SCLK (Which I assume is the Core chip)
102 MCLK (Which I assume is the Memory clock)

> (WW) RADEON(0): Video BIOS not detected, using default clock settings!
(WW) RADEON(0): Failed to probe xtal value ! Using default 27Mhz
(WW) RADEON(0): Unsupported SCLK source setting 7, can't probe SCLK value !
(II) RADEON(0): Probed PLL values: xtal: 27.000000 Mhz, sclk: 200.000000 Mhz, mclk: 102.807693 Mhz
(EE) RADEON(0): MergedFB does not work with Option UseFBDev, MergedFB mode is disabled

MergedFB mode is disabled. That does not sound like a critical error. Unless MergedFB mode is required for your Mac. I don't use my Mac very often, and it is an old PowerMac G4 350 tower..

---


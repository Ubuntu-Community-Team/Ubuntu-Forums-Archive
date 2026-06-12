---
title: "Alt+SysRq+REISUB"
date: 2008-11-20
forum: x86 64-bit Users
---

### Post by xigen on 2008-11-20
{[Solved]} My system keeps locking up / freezing.
AMD 64, 2 gig ram, ATI 3200

I am rebooting about once every 3 hrs - it's ridiculous.

After reading a post on life hacker I decided to try Alt+SysRq+REISUB    ...  ctrl+alt+del does nothing, nor does alt+f2

I thought nothing happened and I hit the reset button on the physical box.

When my system came back ... it makes the normal sounds of Ubuntu booting - however, I have a blank screen.

Just for kicks I put in my usr/pswd and it made all of the sounds of the start of my normal user session.

How would you suggest I get my display back?

Cheers,

MW

---

### Post by xigen on 2008-11-21
I tried to restart the X server (Ctrl+Alt+Backspace) or switch to a tty (Ctrl+Alt+F[1-6})  ....   no luck.  My screen at boot is still blank.

---

### Post by xigen on 2008-11-24
Solved!

My ATI Radeon 3200 Graphics Card was causing my system to crash.    This was not simple to diagnose.

Here is the summary:
Lockups/crashes begin - I looked at all logs
cat /var/log/syslog | grep error
cat /var/log/messages
dmesg
cat /var/log/Xorg.0.log
cat /var/log/messages | grep kernel
cat /var/log/messages | grep panic
cat /var/log/messages | grep sys
cat /proc/meminfo 
cat /proc/cpuinfo

I did my best to check/monitor the temperature.  The CPU temp was fine.  I found no simple way to check the GPU temperature.

I then did my best to see if this was related in any way to software.  I tried Ubuntu Studio, Ubuntu 8.10 and Knoppix.  My system would consistently freeze.

This indicated a hardware issue.

I tested the memory (memtest) - and all appeared fine.

After months of continuous problems I changed the graphics card to an nvidia card. (GeForce 9500 GT)

I am no expert on graphics drivers for Ubuntu - however, geez! this really made it difficult for me to use my system. 

My system is now working perfectly. 

... and speaking of working ...
It is time for me to move past this and get some work done.

Cheers,

MW

---

### Post by cjazz on 2008-11-25
Congratulations. Sounds like you had to do some serious detective work.

---

### Post by YaroMan86 on 2008-11-29
This seems to be a problem with Intrepid in which REISUB doesn't even work anymore.

This is the ONLY way to safely bring Linux down when all else fails. It's a borderline dealbreaker that there seems to be some bug in Compiz causing X to freeze completel and the magic sysrq keys don't work anymore.

---

### Post by ushimitsudoki on 2008-12-02
Ha! REISUB is the only way I CAN shut down most of the time. Ever since I upgraded to Intrepid, something is hanging on shutdown and I need the magic keys to shutdown/reboot.

Running compiz or not hasn't impacted me in this area.

---

### Post by prostar on 2008-12-05
Just to add that I am having the lockup/no REISUB issue too.  I am using an Acer Travelmate 8100 with an ATI mobility Radeon X700.  I'm too afraid to update my AMD 64 workstation...  I have a love/hate with upgrading.

---

### Post by lavinog on 2008-12-05
I had the same problem after installing intrepid.
I have an ATI 3200 also
Once I updated the ATI driver with the 8-11 (non-Beta) fglrx driver...the crashing stopped.
I think the problem is related to the restricted driver that ships with intrepid is a Beta of the 8-11 fglrx driver. This was required because intrepid was released before 8-11 was and 8-11 is the only version that supports the new Xserver.

---


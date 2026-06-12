---
title: "karmic koala &amp; amd 64 4000+"
date: 2009-11-16
forum: x86 64-bit Users
---

### Post by jeditalian on 2009-11-16
cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 55
model name    : AMD Athlon(tm) 64 Processor 4000+
stepping    : 2
cpu MHz        : 1000.000
cache size    : 1024 KB
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up rep_good pni lahf_lm
bogomips    : 2009.21
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

note that it lists my cpu MHZ as 1000. i was wondering why ubuntu was being so sluggish when my processor is supposed to be at least 2.4 ghz.
is there something i should do, like install some kind of support for amd 64 cpus in ubuntu?
i think i am going to go play with my onboard oc utility, because i havent overclocked my cpu since 2006.  and back then i changed it all back to stock, and windows recognizes my 2.4 ghz or 2.6 whatever i have i dont remember but i will go check it out and get back to you.
in the meantime, i hope somebody has an answer.

---

### Post by jeditalian on 2009-11-16
ok, just upped my freq. from 200 to 222,hz and ubuntu seems faster but cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 55
model name    : AMD Athlon(tm) 64 Processor 4000+
stepping    : 2
cpu MHz        : 1000.000
cache size    : 1024 KB
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up rep_good pni lahf_lm
bogomips    : 2219.82
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

---

### Post by 3Miro on 2009-11-16
Cool'N'Quiet technology keeps the CPU at 1000 until you need it. It is running as supposed to. Try running a demanding app (such as conversion of large sound/video file) and try that command again, it will show the max speed.

I have an AMD64 desktop and there is no need for special AMD support.

---

### Post by efflandt on 2009-11-17
If you look through /var/log/messages you may see something like this (only faster):

powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (1 cpu cores) (version 2.20.00)
powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x2
powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x6
powernow-k8:    2 : fid 0x0 (800 MHz), vid 0xa

So cat /proc/cpuinfo reports my current speed as 800 MHz, but it dynamically speeds up when required.

---

### Post by jeditalian on 2009-11-17
oh, ok. it takes quite awhile to convert a dvd to iso, but it probably takes way longer in windows. 
also, i've been playing quake live, and on windows i use to always lag on space maps, but the graphics are smooth on ubuntu. the graphics don't lag, but i do have to aim ahead of someone whos running if i want to be sure to hit them, like when i use to play delta force on dialup.  the issues i have with ubuntu are so minor. any issues related to graphics probably stem from the fact that my monitor is philips part # 4522 131 59342, which if you look it up, is the display for someones old MRI machine. so nvidia identifies this big ol' lcd screen as a big ol crt. i did have to unbend 1 pin on my cpu when i swapped mobos last. im not sure if it bent on the last install, or when i was taking it out, but i know it could probably run fine with 1 pin missing. i just got done playing quake live after i increased my fsb to 222 from 200, and i havent had any issues. not sure how hard i wanna push it, and i dont remember how far up it goes.
anyways, thanks for clearing that up. i was trying to find something that reported my specs to me like when you run dxdiag in windows.
i couldnt figure out what to do with a gamepad in ubuntu though. maybe because its a MICROSOFT sidewinder, but still i couldnt find anything to let me know it was connected, or a calibration tool or anything. i like to use something like Joytokey in windows, but theres really no need for all that, just extra wires. the keyboard is the biggest gamepad ever anyways.

---

### Post by jeditalian on 2009-11-17
> **3Miro said:**
> Cool'N'Quiet technology keeps the CPU at 1000 until you need it. It is running as supposed to. Try running a demanding app (such as conversion of large sound/video file) and try that command again, it will show the max speed.

I have an AMD64 desktop and there is no need for special AMD support.
 
thats nice because i didnt really add any arctic silver this last time i swapped motherboards. i finally got a ps/2 keyboard from a yard sale for like $2, and its what i needed to be able to get into the bios on my foxconn winfast, on which i blew the usb ports out, fooling around with a beheaded logitech headset. but thats what i'm using, because its so much better than that MSI board i got to replace it, since socket 939 became scarce pretty much immediately after i bought 2 identical processors and an overclocking mobo. i bought 2 identical cpus mainly because i was planning on setting up a dual-64-bit-cpu system, but also just incase i blew one up with the overclocking utility on my motherboard. the 128 bit computer i was gonna build (or just dual 64), never happened because it turned out they did not and will never make a dual socket 939. that sucks. unless i had some malaysian laboratory/factory, oh wait, thats where my processors usually made, not my motherboad.. 
you wouldnt happen to know what blows up when you blow up your usb ports, would you? for now (& most likely forever) i have a ps.2 keyboard hooked up just for bios and boot selection purposes, then once the os is chosen my 5port usb pci card kicks in and i can use my keyboard and the laser mouse.

anyway with the arctic silver, i didnt add anymore or clean it off, i just spread it with my finger so i couldnt see metal, and stuck on my gigantic "64 freezer pro" with the heatpipes &stuff, which keeps me from having a normal internal disc drive. that is, until my external dvd burner broke, then i took off the external enclosure, and the drive was small enough to comfortably fit inside my case.

---

### Post by jeditalian on 2009-11-17
so my cpu can work at 1000 to 2400 mhz. Detected 2387.788 MHz processor.
ok. im sleepy. muchos gracias!

---


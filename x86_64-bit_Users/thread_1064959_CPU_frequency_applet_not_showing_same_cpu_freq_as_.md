---
title: "CPU frequency applet not showing same cpu freq as BIOS"
date: 2009-02-09
forum: x86 64-bit Users
---

### Post by janbbeck on 2009-02-09
Ok, I just installed a core i7 965 in a tpower x58 motherboard. I installed ubuntu 8.10 x64. 

I disabled speed step in the BIOS. 

Now when I adjust the front side bus multiplier from 133 Mhz to 150, then ubuntu displays the correct cpu frequency as displayed by the bios on bootup. I checked under ubuntu by using both the "cpu frequency monitor" applet and the "sysinfo" program under applications->system tools->sysinfo

on boot up the applet informs me that frequency scaling is not supported, so disabling the speed step in the bios seems to work.

now, when I adjust the cpu multiplier itself, from 24 to something else, the bios will show the correct frequency on boot up - bus speed times multiplier. As soon as ubuntu is loaded the applet and sysinfo both show the frequency based on the bus speed and the original multiplier. So for example, if the bus speed is 140 Mhz, then it will show 140*24 Mhz regardless of what the bios reports and what multiplier I set in the bios.

One of 2 things is happening:
1. ubuntu is displaying the wrong frequency in both the applet and sysinfo
2. ubuntu is changing the settings away from the bios setting somehow.

I would like to know how I can tell what is happening. Is there a sure fire way to measure the cpu frequency?

Thanks in advance.

---

### Post by Yellow Pasque on 2009-02-09
What does your boot log show?
```
dmesg | grep MHz
```
or look through the whole thing with:
```
dmesg
```

For example, the CPU detection portion of my boot log says:
```
Initializing CPU#0
PID hash table entries: 1024 (order: 10, 4096 bytes)
Fast TSC calibration using PIT
Detected 935.478 MHz processor.
```
(I'm stuck on a Pentium3 using Arch Linux at the moment. Yours may look a little different)

---

### Post by janbbeck on 2009-02-10
> **Temüjin said:**
> What does your boot log show?
```
dmesg | grep MHz
```
or look through the whole thing with:
```
dmesg
```

For example, the CPU detection portion of my boot log says:
```
Initializing CPU#0
PID hash table entries: 1024 (order: 10, 4096 bytes)
Fast TSC calibration using PIT
Detected 935.478 MHz processor.
```
(I'm stuck on a Pentium3 using Arch Linux at the moment. Yours may look a little different)

Thanks for the reply.
My dmesg reports Detected 3600.012 MHz processor.
the BIOS states 4 GHz (I have tried a multiplier for 3.8 GHz too with the same result). It behaves as if the BIOS pretends to set the multiplier, but does not actually do so while setting the bus speed as requested. Alternatively Linux may not report the speed correctly or set the processor to a different multiplier somehow.

Any ideas how I can find out what is going on?

---

### Post by nayab on 2009-03-09
Hello janbbeck and Temüjin.

Firstly, thanks for the grep code as I am new to Ubuntu. I too have the x64 8.10 with all the relevant updates. My grep output showed that even though the CPU frequency monitor is showing the frequencies I should be running at if not overclocked, the system logs are different. I am guessing (at the moment) that the CPU frequency monitor does nothing for my desktop PC if I choose to scale it down to save power.

What I have done however is installed wine and have super_pi (the Windows overclockers favourite). Give me about half an hour and I will post results. I think the way for me to do it personally would be as follows.

1 Boot to XP with overclocked speed and check super_pi
2 Boot to XP with stock speed and check super_pi
3 Boot to Ubuntu with stock speed and check super_pi under wine (check both available speeds under the cpu scaler)
4 Boot to Ubuntu with overclocked speed and check super_pi under wine (check both available speeds under the cpu scaler)

Notes
XP is 32bit Pro SP3
DDR400
Athlon 64 3000 Venice core 1.8MHz on Gigabyte 939 mobo
Dual boot to Ubuntu 8.10 x64

Don't laugh at the hardware. It cost me nothing and I do not have a job.;)

OK. So not the most scientific approach, but maybe it will help answer the quesion and it gives me an excuse to be thorough about this. Expect to see 6 measurements of time taken for pi calculated to 1 million decimal places.

---

### Post by nayab on 2009-03-09
So here are the results.

XP overclocked FSB 240MHz                40s

XP stock speed FSB 200MHz                49s
Ubuntu stock speed 200MHz                57s (1m42s when stepped down)
Ubuntu overclocked FSB 240MHz            46s (1m20s when stepped down)

This suggests to me that Ubuntu does not directly interfere with any bios settings that you may have set for overclocking purposes. However, if you step down using the cpu scaling, even when overclocked, it does appear to take proportionate effect.

The difference for me was quite significant. Stock speed of CPU is 1.8GHz, and stepping down takes me to 1.0GHz. When overclocked, the CPU is rated at 2.16GHz and stepping down is 1.2GHz.

If there are any Windows x32 purists out there pointing out how much slower the application runs under Ubuntu x64, then please recall that this was done by running the application within another application. Please take your ranting, finger-pointing and mockery elsewhere.:D The exercise here was to prove that the application for CPU frequency scaling actually performs a function, and does so reliably and accurately.

Hopefully, Quod Erat Demonstrandum.:guitar:

---


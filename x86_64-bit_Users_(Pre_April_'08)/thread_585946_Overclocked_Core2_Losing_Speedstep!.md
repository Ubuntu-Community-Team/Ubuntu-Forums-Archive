---
title: "Overclocked Core2 Losing Speedstep!?"
date: 2007-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by gururise on 2007-10-21
I've got a Q6600 Quad with a modest overclock to 3ghz.  The system is perfectly stable; however, Ubuntu reports upon bootup that there is a problem with CPU frequency scaling, and that my CPU will run w/o frequency scaling.

This is normally not a problem, but I'm trying to run a server, and would like to save electricity by enabling frequency scaling.  When the CPU is not overclocked (stock 2.4Ghz), frequency scaling works great. 

Has anyone else experienced the loss of Frequency Scaling on overclocked intel cpu's?

---

### Post by Jouke74 on 2007-10-22
I really am surprised on what you're doing. You want to run an overclocked CPU on a server system, and besides that, you try to downclock the CPU when not in use with frequency scaling? Is this oveclock so neccessary? I suggest you put it back to normal. I also think the overclock that you set-up in your BIOS will repress the frequency scaling function.

---

### Post by gururise on 2007-10-24
> **Jouke74 said:**
> I really am surprised on what you're doing. You want to run an overclocked CPU on a server system, and besides that, you try to downclock the CPU when not in use with frequency scaling? Is this oveclock so neccessary? I suggest you put it back to normal. I also think the overclock that you set-up in your BIOS will repress the frequency scaling function.

Well, I would really like a 3Ghz quad core processor.  I could go out and buy a Q6750 for $999 or simply clock my Q6600 to 3Ghz, which it handles with no problems at stock voltages.  If I got a Q6750, I would have speedstep enabled in Ubuntu... so it would be nice to have it enabled on my overclocked Q6600 processor.

Has anyone else been having problems with speedstep on overclocked processors?

---

### Post by gururise on 2007-10-29
Is nobody else having this problem?

---

### Post by paulsundvall on 2007-10-31
Yes, I also had this problem (and found your post when I googled for someone else having the same problem!).
I run debian testing on a Q6600, running atFSB375 with multiplier 9=3375 MHz
My motherboard turned off speedstep automagically when I changed the setting, make sure you have enabled it.
Then I hade to change the settings in /etc/init.d/cpufrequtils  to

```
ENABLE="true"
GOVERNOR="ondemand"
# previous value: MAX_SPEED="2400000"
# previous value: MIN_SPEED="1600000"
MAX_SPEED="3000000"
MIN_SPEED="2000000"
```

Note that the frequency is not correctly detected. Frequency scaling now works fine for me. My load temperatures are 55-60 degrees.

Good luck!
Paul

---

### Post by gururise on 2007-11-02
> **paulsundvall said:**
> Yes, I also had this problem (and found your post when I googled for someone else having the same problem!).
I run debian testing on a Q6600, running atFSB375 with multiplier 9=3375 MHz
My motherboard turned off speedstep automagically when I changed the setting, make sure you have enabled it.
Then I hade to change the settings in /etc/init.d/cpufrequtils  to

```
ENABLE="true"
GOVERNOR="ondemand"
# previous value: MAX_SPEED="2400000"
# previous value: MIN_SPEED="1600000"
MAX_SPEED="3000000"
MIN_SPEED="2000000"
```

Note that the frequency is not correctly detected. Frequency scaling now works fine for me. My load temperatures are 55-60 degrees.

Good luck!
Paul

Tried what you suggested; however, upon booting, I still lose speedstep.  I am unable to load a governor on my OC'ed system, even though Speedstep is enabled in the bios.  I have a sneaky feeling that my motherboard (Gigabyte) is disabling speedstep while overclocked.

---

### Post by Jouke74 on 2007-11-02
>  also think the overclock that you set-up in your BIOS will repress the frequency scaling function. 

>  I have a sneaky feeling that my motherboard (Gigabyte) is disabling speedstep while overclocked. 

You see :mrgreen: that's what I meant.

---

### Post by hazridi on 2007-11-02
This happens to me with a Core 2 E6300 when it is overclocked to 2.33 GHz.

And most Core 2 processors can handle overclocking so well to the point I no longer even considering it overclocking, just getting a good deal. ;p

---

### Post by timzak on 2007-11-02
I had a slightly different problem.  When I'd enable speedstep, Ubuntu would disable my overclock.  Yes, Ubuntu, because in Windows my overclock would hold (I dual-boot).  So my options were to run speedstep at stock speeds or overclock w/o speedstep.  Basically what you're facing right now.  I never found out why Ubuntu overrode my OC (or how it could, for that matter), I just disabled speedstep.

BTW, this was on 32 bit Feisty Fawn.  I just installed 64 bit Gutsy and haven't tried enabling speedstep yet on this version.

---

### Post by henrikn on 2007-11-08
> **gururise said:**
> Is nobody else having this problem?

I am having the exact same problem. What motherboard do you have? I use a Gigabyte GA-P35-DS4. Have you found any more information regarding this problem? In case I find a solution I will come back to this thread.

---

### Post by simoncullen on 2008-02-17
Same problem here.  It's driving me nuts!  

Interestingly the system temps have not gone up since OCing, making me suspect that the mobo is taking care of the EIST functions??  I'm not sure if that's possible ... I'm using a Gigabyte GA-P35-DSL3 with an E8500 OCed to 3.6Ghz on stock voltages.  Completely stable.

Has anyone had any luck with this?

---

### Post by khensucat on 2008-02-17
Um. Forgive me dear, but why would you want to overclock (potentially destabilize) a server core? Surely you're hardly stressing that core at even *factory* clock speeds on a non-corporate server? (I'm guessing non-corporate, as your IT-manager would have already handed you your buttocks or your walking papers for OC'ing a company server :lol: )

But anyway - have you updated your BIOS recently? In a recent BIOS update for my board (just a few days ago), speedstep was disabled :-(

And lastly - I'm guessing you're using the default powernowd? Have you tried using cpufreqd?

---

### Post by henrikn on 2008-02-20
Just as a separate data point, I will note that the speedstep does work in windows even while overclocked. So it shouldn't be a hardware limitation.

---

### Post by fjgaude on 2008-02-20
> **henrikn said:**
> I am having the exact same problem. What motherboard do you have? I use a Gigabyte GA-P35-DS4. Have you found any more information regarding this problem? In case I find a solution I will come back to this thread.

I think this is a feature of Intel Core 2s. And likely it is carried over by Gigabyte. I have a DS4 running an E8400, overclocked to 3.8MHz with 1066MHz memory, using the stock Intel fan, PWM. Fan runs at 1430 RPM and CPU temp is 30C.

I've not gotten cpufreq to work, but the fan speed follows the CPU load and keeps the temp below 55C at full-load.

This is not a bug but just the way Intel is doing things in both their 45nm and 65nm Core 2 chips.

---

### Post by simoncullen on 2008-02-20
> **fjgaude said:**
> I think this is a feature of Intel Core 2s. And likely it is carried over by Gigabyte. I have a DS4 running an E8400, overclocked to 3.8MHz with 1066MHz memory, using the stock Intel fan, PWM. Fan runs at 1430 RPM and CPU temp is 30C.

I've not gotten cpufreq to work, but the fan speed follows the CPU load and keeps the temp below 55C at full-load.

This is not a bug but just the way Intel is doing things in both their 45nm and 65nm Core 2 chips.

I'm using a similar board: a Gigabyte GA-P35-DSL3.  If it's purposefully built into the hardware by Intel, presumably it will occur in any OS.  Can you check if SpeedStep will scale the frequency in Windows?  It is a funny way to do things -- I'm not sure what their motivation might be . . .



edit:  note that Fjgaude reports that scaling works in Windows ...?

---

### Post by fjgaude on 2008-02-20
I don't have Windows on my main box, except as a VM.

I think the board manufacturers are so tied in with Intel they pretty well do as Intel would suggest. For it is Intel who knows how their chips are built and how to keep them healthy.

So be it...

One issue I've had with the GA-P35-DS4 motherboard is if I use anything other than 2X for the memory multiplier I run into extreme amounts of I/O waits once booted into Ubuntu. Strange!

---

### Post by Peturrr on 2008-03-07
So, why is it that on windows XP speedstep just works with the OC values, and on Ubuntu, it doesnt??

My problem is related: I have my 1.8Ghz e4300 OC'd to 2.2Ghz and in windows it works fine with speedstep, but on linux, it clocks back to the original 1,2/1.8Ghz.  Only when I disable speedstep it gives me the 2.2 Ghz. How could this be?

---

### Post by fjgaude on 2008-03-07
I have the cpufreq scaling issue too. I don't have a /etc/init.d/cpufrequtils file to change. Where is it?

My MB is a Gigabyte GA-P35-DS4 running an Intel E8400, 445 x 9 = 4.0GHz. Runs fine but no speedstepping.

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1790 MHz) 02/26/2008, fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.35/1.34v:
```

/dev/md32:
 Timing cached reads:   18948 MB in  2.00 seconds = 9487.52 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec
```

There likely is no work around for the speedstep issue, eh? Unless Ubuntu programmers want to fix it.

---

### Post by Peturrr on 2008-03-07
It looks like it's a kernel issue. 

Please confirm that you have this bug on here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/132403](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/132403)

However, I am afraid that it won't be fixed overnight...

---

### Post by fjgaude on 2008-03-07
I added to the bug report... but it sure looks like it will not be a show stopper, eh? "No intention to fix" is what is stated. Hardy is doing the same thing, at least so far.

I'm sure there is something that can be done that is not too difficult. Someone, maybe me, will find it as time goes by.

---

### Post by ori_ab on 2008-04-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/213119](https://bugs.launchpad.net/bugs/213119) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				gigabyte ga-p35-ds3l +e2200 here - no cpu scaling :(

I've opened a bug at [https://bugs.launchpad.net/bugs/213119](https://bugs.launchpad.net/bugs/213119)

---


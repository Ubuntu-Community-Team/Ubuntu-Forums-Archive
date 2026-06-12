---
title: "Q6600 BSEL &quot;tape mod&quot; issue"
date: 2008-06-04
forum: x86 64-bit Users
---

### Post by Brian96 on 2008-06-04
I am running a Dell Inspiron 530 desktop with the Intel C2Q Q6600 processor. I performed the infamous "tape mod" to increase the FSB to get 3.0 GHz performance. In Vista, CPU-Z detects the change and the processor runs at ~3 GHz (or ~2 GHz when scaled down). However, in Ubuntu, the processors are only detected as having 2400 MHz and 1600 MHz options.

Is this a detection issue and I am really getting the increase? Does the mod for some reason only work with Windows? Any ideas?

---

### Post by Brian96 on 2008-06-05
(bump)

Surely I am not the only Ubuntu user who has tried the tape mod, eh? Anybody have any idea why I am having this problem?

---

### Post by rev0lv3r on 2008-06-06
What are you using to detect the processors

I have a E6300 which I've ramped up the FSB in BIOS and Ubuntu never reports the correct speed

However my bogomips are doubled my freq. when viewed using "cat /proc/cpuinfo" (i think that's the command) AND my BOINC benchmarks do reflect increases (from default clock speeds)

1.86ghz now at 3.08ghz. :) Love these Intels!

---

### Post by Brian96 on 2008-06-06
> **rev0lv3r said:**
> What are you using to detect the processors

I have a E6300 which I've ramped up the FSB in BIOS and Ubuntu never reports the correct speed

However my bogomips are doubled my freq. when viewed using "cat /proc/cpuinfo" (i think that's the command) AND my BOINC benchmarks do reflect increases (from default clock speeds)

1.86ghz now at 3.08ghz. :) Love these Intels!

Thank you for responding!

I have been using cat /proc/cpuinfo for the longhand and emifreq (and its applet plugin) for a simpler one.

The emifreq applet usually shows 1.6 GHz, and I can switch it to performance and get 2.4 GHz. However, the cat /proc/cpuinfo shows 1600 MHz (except when I switch to "performance" in emifreq, and then the first core shows 2400 GHz in the terminal output for cat /proc/cpuinfo).

I am still new to all of this, so I had to look up bogomips. That shows 5985 for each core. If I am doing the math right, then that should be about 3 GHz, right?

I will try BOINC and see what it comes up with.

Thanks for your help. And please let me know if you think of anything else.

---

### Post by Brian96 on 2008-06-07
So I have BOINC running, and at least I can see the processors scaling up and down with Conky. However, I still can't "see" the increase I am supposedly getting from the tape mod.

Is it possible to edit some file so that it is displays custom numbers? Like, in CPU-Z in Vista it shows me scaling between 1995 and 2995 MHz. If I can reliably believe I am getting similar numbers in Ubuntu, can I change something so that it shows these numbers in Ubuntu (without really screwing anything up)?

---

### Post by rev0lv3r on 2008-06-07
> **Brian96 said:**
> So I have BOINC running, and at least I can see the processors scaling up and down with Conky. However, I still can't "see" the increase I am supposedly getting from the tape mod.

Is it possible to edit some file so that it is displays custom numbers? Like, in CPU-Z in Vista it shows me scaling between 1995 and 2995 MHz. If I can reliably believe I am getting similar numbers in Ubuntu, can I change something so that it shows these numbers in Ubuntu (without really screwing anything up)?
Let me know if you figure something out

As of now I've had to resort to the bogomips indicator and even worse, using the Boinc built-in benchmark figures to determine if my o/c was working

I oced within the BIOS and during boot up the BIOS displays the correct ghz, but Ubuntu just poops
Sometimes it says 1.86ghz (original speed), sometimes it'll show 2000mhz, sometimes it'll show 2333mhz when I know all of those three are false. Bogomips shows something around ~6000 indicating near 3ghz speeds.

---

### Post by Brian96 on 2008-06-07
> **rev0lv3r said:**
> Let me know if you figure something out

As of now I've had to resort to the bogomips indicator and even worse, using the Boinc built-in benchmark figures to determine if my o/c was working

I oced within the BIOS and during boot up the BIOS displays the correct ghz, but Ubuntu just poops
Sometimes it says 1.86ghz (original speed), sometimes it'll show 2000mhz, sometimes it'll show 2333mhz when I know all of those three are false. Bogomips shows something around ~6000 indicating near 3ghz speeds.

Similar situation here, except that I don't know how to interpret the BOINC benchmarks. :(

Now I am weighing the pros and cons of somehow configuring it to always run at "performance" speeds. Of course, I don't know how I'd go about doing that.

---

### Post by Brian96 on 2008-06-11
Maybe somebody can help me interpret this and shed some light on the matter. If I don't get any hits on this thread I may start a new thread with BOINC in the title to draw from a larger base than just Q6600 users.

So I have installed and run BOINC on my system on all 3 OSes, but I don't know how to interpret the benchmarks. However, I am hoping that someone who DOES know how to interpret the benchmarks can help me understand whether I am getting the 3.0G Hz in Hardy. The benchmarks reported below are rough estimates of 3 runs of the BOINC Manager's CPU benchmarks utility. I got very consistent results within each system with each run of the utility.

Windows Vista 32 Bit: ~2915 floating point MIPS (Whetstone)/ ~6515 integer MIPS (Dhrystone) (Also, CPU-Z shows 3.0 GHz with the FSB bump from the tape mod.)

Linux Mint 5.0 (based on 32 bit Hardy): ~2100 floating point MIPS (Whetstone)/ ~6600 integer MIPS (Dhrystone)

Ubuntu 8.04 64 Bit: ~2360 floating point MIPS (Whetstone)/ ~9935 integer MIPS (Dhrystone)

1) Is there a way to roughly convert these numbers to something like GHz? (Sorry if that is a naive question.)

2) Regardless of the answer to number 1, based on these numbers, does it look like I am getting the benefit of the tape mod, which I appear to be getting in Vista?

---

### Post by rev0lv3r on 2008-06-12
Hey my friend
I have a Q6600 at work
I have written down some of the numbers I get from FSB overclocking

Your 64bit numbers sound right
I think I get similar numbers as this
> Ubuntu 8.04 64 Bit: ~2360 floating point MIPS (Whetstone)/ ~9935 integer MIPS (Dhrystone)
But once I get to work I will double check, they are written on a piece of paper on my desk

BTW: How many bogomips does "cat /proc/cpuinfo" give you
I've found it to be a relatively good way of telling my frequency
Worked decently on an AMD 5000+ BE I just built as well as a dual quad core workstation

Have you run any of the BOINC projects? You can also compare workunit times for certain projects.

---

### Post by Brian96 on 2008-06-12
Thanks for the reply.

My bogomips are this:  5985.07

My concerns is why my floating point MIPS as reported by BOINC are so much higher in Vista than in either 32 or 64 bit Hardy derivatives?

I don't know if it is a legitimate comparison, but 2915 floating point MIPS is a similar figure to the 2995 MHz that CPU-Z gives me in Vista. That makes me wonder whether the ~2300 I get from BOINC in Ubuntu is comparable to ~2300 MHz, which would suggest I am NOT getting the extra oomph from this "tape mod" deal.

Does anybody know any reason why this mod, which is supposed to increase clock speed by bumping up the FSB, would work in Vista but NOT work in Linux?

---

### Post by rev0lv3r on 2008-06-12
Okay I run only 64bit because I have more than 4gb ram, but here are a bunch of figures

1100 <-- fsb mhz, quad pumped, divide by 4 to find out clock
830 <-- ram mhz, my board supports unlinked, I play on the safe side
=
2383 <-- floating point
10135 <-- int

1333
880
=
2903
12181

this is another q6600, i believe on windows xp sp3 32bit (god i hate windows)
1066
933
=
2354
5451

1200
933
=
2637
5960

1400
933
=
3090
7080

That's all I have on this sheet

Your bogomips indicate that you are oced
5985 / 2 = 2992.5mhz, that sounds kinda close to your said 3ghz.

---

### Post by Brian96 on 2008-06-12
> **rev0lv3r said:**
> Okay I run only 64bit because I have more than 4gb ram, but here are a bunch of figures

1100 <-- fsb mhz, quad pumped, divide by 4 to find out clock
830 <-- ram mhz, my board supports unlinked, I play on the safe side
=
2383 <-- floating point
10135 <-- int

1333
880
=
2903
12181

this is another q6600, i believe on windows xp sp3 32bit (god i hate windows)
1066
933
=
2354
5451

1200
933
=
2637
5960

1400
933
=
3090
7080

That's all I have on this sheet

[B]Your bogomips indicate that you are oced
5985 / 2 = 2992.5mhz, that sounds kinda close to your said 3ghz[/B].

That's what I'm thinking, but why would my BOINC benchmarks for floating point MIPS be so much higher in 32 bit Vista?

Also, where are you getting the FSB from? Is that in the BOINC output (I don't remember seeing that)?

Thanks for your help.

---

### Post by rev0lv3r on 2008-06-12
Sorry, I have no idea why the benchmarks show much higher numbers in Vista
Did you try running it a few times?

I wrote down the FSB numbers as I changed them from within the BIOS
I did not do the tape mod, I just do FSB overclocking, it's not within the BOINC output

You can find out your FSB speed usually be taking your cpu clock speed and dividing by your multipler

By default, 2400 / 266 = 9
That is correct since through googling, we can find that the Q6600 multipler is infact, 9.
Since I changed, for example, my fsb speed (after quad pumped) from (266 * 4 = 1066) to something higher, like 1400, essentially I've changed the 266 to (1400 / 4 = 350).
I hope I am making sense, overclocking is pretty easy once you understand how all the numbers are related.

---

### Post by Brian96 on 2008-06-12
> **rev0lv3r said:**
> Sorry, I have no idea why the benchmarks show much higher numbers in Vista
Did you try running it a few times?

I wrote down the FSB numbers as I changed them from within the BIOS
I did not do the tape mod, I just do FSB overclocking, it's not within the BOINC output

You can find out your FSB speed usually be taking your cpu clock speed and dividing by your multipler

By default, 2400 / 266 = 9
That is correct since through googling, we can find that the Q6600 multipler is infact, 9.
Since I changed, for example, my fsb speed (after quad pumped) from (266 * 4 = 1066) to something higher, like 1400, essentially I've changed the 266 to (1400 / 4 = 350).
I hope I am making sense, overclocking is pretty easy once you understand how all the numbers are related.

I was hoping it was in BOINC. Oh, well.

I am brand spanking new to overclocking, which is why I only did the tape mod. (Plus, I am using stock Dell everything, so I don't really have other options.)

My understanding is that this mod works by increasing the FSB from 1066 to 1333. In Vista I can "see" this because CPU-Z ups both my FSB and my clock speed after the mod.

Ubuntu, however, reports my clock speed as 2.4 or 2400 MHz (even though I think technically it should be 23xx MHz if it is really 2.4). That fact, plus the BOINC output has me thinking that Ubuntu somehow does not detect the bumped up FSB speed, but I don't know where to check FSB. I can't find a Linux utility as easy to interpret as CPU-Z.

The ONLY thing I have seen in Ubuntu that gives me hope is the bogomips. But if the bogomips reading is correct, why do I get consistently better readings in Vista than in Ubuntu? (The numbers I reported earlier were rough averages of 3 runs in each OS of the BOINC cpu benchmarks. My results were very consistent, always within 15 points per reading in the same OS.)

Anybody know anything about interpreting the floating point MIPS that BOINC gives? As I said above, those figures look eerily similar to the figures I get in MHz with something like CPU-Z, and if that is a valid comparison then I am NOT getting any increased clock speed in Ubuntu.

Thanks for your help.

---

### Post by rev0lv3r on 2008-06-12
BOINC numbers are given after running a bunchmark
CPU-Z doesn't run a benchmark, it gives you raw speeds

The easiest way to tell if the OC works in linux is to undo the tape mod, do the benchmark and record the numbers
Then do the tape mod, do the benchmark again and see if you have a roughly ... I think 10-30% increase?

1333 - 1066 = 267
267 / 1066 = .25 -> 25% increase?
My math might be a little off, I haven't had to crunch numbers in decades

From your bogomips though, it looks like your OC is working :)

---

### Post by jrharvey on 2008-06-12
Is this thread still alive???? I am desperately trying to figure this out also. I did the tape mod on my q6600 also and am running into issues with ubuntu. I am starting to wonder if it REALLY is overclocked or if windows is just being FOOLED into thinking its faster than it is. I have tried benches and 3dmark and cpumark but seem to be getting scores of a 2.4ghz and not my 3.0

---

### Post by rev0lv3r on 2008-06-13
If you're running Windows you can just use CPU Z to tell your frequency
[http://www.cpuid.com/cpuz.php](http://www.cpuid.com/cpuz.php)

---

### Post by jrharvey on 2008-06-13
Ok so i have spent the past 8 hours running benchmark after benchmark and have come to the conclusion that this isnt real. YES, in windows it says that your CPU is running at 3ghz but when you run a few test, it tells you the truth. There is absolutely no speed gain from this mod. In fact, some test showed that my q6600 OC was slower than the stock.

---

### Post by wolfe on 2008-06-13
> **rev0lv3r said:**
> If you're running Windows you can just use CPU Z to tell your frequency
[http://www.cpuid.com/cpuz.php](http://www.cpuid.com/cpuz.php)

you can also use perlmon for linux:

[http://www.overclock.net/linux-unix/212320-perlmon-cpu-z-like-program-linux.html](http://www.overclock.net/linux-unix/212320-perlmon-cpu-z-like-program-linux.html)

---

### Post by jrharvey on 2008-06-13
Perlmon is nice BUT it still states a 2.4ghz instead of 3.0 like windows.

---

### Post by rev0lv3r on 2008-06-13
> **jrharvey said:**
> Perlmon is nice BUT it still states a 2.4ghz instead of 3.0 like windows.

It works for me
Although for CPU Model it says "Q6600 @ 2.40GHZ" at the bottom it says
"CPU speed: 3059.998"
Which is right for 1360FSB and 933RAM
1360 / 4 * 9 = 3060 which is close to 3059.998

BOINC benchmarks give me
2966 floating point MIPS
12508 integer MIPS

---

### Post by jrharvey on 2008-06-13
Well I dissabled the mod until i learn more about it. Will mess around with ram speeds and get back to you and hopefully it works.

---

### Post by jrharvey on 2008-06-13
I retract my precious statement about it not working, it just doesnt work for me YET!!!! I see other people that are running benchs that prove it works. My ram speed says 667mhz but its running as if its 533mhz. I need to upgrade to ddr2-800 anyways.

---

### Post by jrharvey on 2008-06-14
Ok, this totally works now for me. The best way to see your clock speed in linux is look at bogomips i guess. Someone should really make a CPU-Z like program that works. Perlmon doesnt really work for me. Im not sure what its reading but it still says 2.4ghz. Oh well, at least now i know it really is overclocked.

---

### Post by Brian96 on 2008-06-16
> **jrharvey said:**
> Ok, this totally works now for me. The best way to see your clock speed in linux is look at bogomips i guess. Someone should really make a CPU-Z like program that works. Perlmon doesnt really work for me. Im not sure what its reading but it still says 2.4ghz. Oh well, at least now i know it really is overclocked.

Just out of curiosity, how did you decide it really was overclocked? Just the bogomips?

Also, perl-mon also shows me at 2.4.

Finally, how can I find out how my memory is being detected. CPU-Z shows it on the Memory tab at ~400 MHz. I don't really know much about all of this; is that how 800 MHz memory should show up (I have PC6400 RAM installed)?

---

### Post by cariboo on 2008-06-16
After all that wondering and sweating does it really make any difference in the way the OS works?

Jim

---

### Post by rev0lv3r on 2008-06-16
> **cariboo907 said:**
> After all that wondering and sweating does it really make any difference in the way the OS works?

Jim

Depends if you LOVE SPEED

---

### Post by jrharvey on 2008-06-18
> **cariboo907 said:**
> After all that wondering and sweating does it really make any difference in the way the OS works?

Jim

It really does increse the speed about 25% and ubuntu does get faster. IF YOU DO NOT USE CPU INTESIVE PROGRAMS I would not sugguest this mod unless your motherboard can handle it, BUT it is completely reversable and it really does work. Most all motherboards are built for 1333 FSB anyways so you should be fine. I tried a few benchmarking programs and CPU speed incresed about 25%. Its just like any other overclock and make sure you have proper cooling because the stock cooler SUCKS!!!! I really mean it, at stock speed the q6600 is still a beast to keep cool. Im not talking about some cheap cooler but i have a Tuniq Tower, a beast of a heatsink. For some reason ubuntu does not read the overclock but it is in fact overclocked. CPU-Z is correct so i just use that. Besides, its just a number in ubuntu.

---

### Post by mips on 2008-06-20
64bit FP will be considerally better than 32bit FP.

---

### Post by aflicted on 2008-12-09
I don't have a q6600 and am unfamiliar with the tape mod.  If it is really just an OC to the FSB (which is pretty traditional to an overclock) then I don't think most readings see that.  I have messed around with my system in windows and linux while playing with the FSB.  Speedstep allows the proc to change its multiplier up and down a small scale (that allows a fairly large) difference in clock speed.  For example.  My E8400 runs native at 333mhz fsb with a multiplier of 9.  When you quad pump that FSB it gives you 3.0 GHz.  The speedstep allows the multiplier to drop to 7.  If you overclock the FSB to 400mhz (quad pumped to 1600FSB) it gives you a core clock of 3.6GHz.  Now Linux does not recognize my overclock while I have speedstep enabled in BIOS.  It also does not allow me to play with CPU scaling since it is BIOS disabled.  If you enable speedstep then all portions of linux I have found show the cpu at it's native core clock.  If I enter this in console (  dmesg | grep MHz  ) It gives me the OC core clock.  I have verified this through benchmarking the OC settings in handbrake vs. the stock settings in handbrake.  The encode was the only thing running on a fresh boot with the same settings, source, and output.  Hope this helps verify the OC.

---

### Post by rev0lv3r on 2008-12-09
Might want to turn off speedstep

I don't know how it is completely... but it used to give me problems in Windows


Besides, if you run BOINC or F@H or something, it's not like your CPU is ever idle anyways :)

---

### Post by aflicted on 2008-12-10
It is not a good idea to use speedstep if you are playing with the core voltage to get your overclock.  I have mine set manually along with the FSB.  It scales just fine in Windows and Linux.

---


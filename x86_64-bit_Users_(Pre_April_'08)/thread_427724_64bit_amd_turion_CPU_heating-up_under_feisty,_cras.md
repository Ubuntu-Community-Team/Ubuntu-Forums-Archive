---
title: "64bit amd turion CPU heating-up under feisty, crashing computer!!!"
date: 2007-04-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by bakermiller on 2007-04-29
I Set -up the thermometer in the panel and keep an eye out for high Temp. I blocked the CPU at 800mhz using sensor applet. It seems to stabilize the  temperature, but am i missing out on extra power?? Can someone help me if it's possible? I have to tell the CPU to be "conservative" on every boot. It's kind of annoying.

---

### Post by octoberdan on 2007-04-29
Sounds like a hardware problem in desperate need of being addressed. Have you over clocked or done anything funky? Are all your fans working? Do you have any other OSes installed to verify whether or not it is a hardware issue?

---

### Post by bakermiller on 2007-04-29
you are correct.
I had XP and Ubuntu on this machine for over one year. 
XP started crashing periodically. I figured it was a software problem, so  i got fed-up with it, and installed feisty all across the HD, crushing XP in the act. :)
Now, Feisty crashes much less since i have more control over the CPU speed.

Should i change the CPU? Or is there another (less radical) alternative in your opinion?

Having a CPU at half it's potential speed is a price i am willing to pay to keep working with ubuntu.

---

### Post by kuja on 2007-04-30
When it starts to heat up, can you hear/feel the fan running? If not, you've got a serious problem on your hands, and should probably get it looked at.

---

### Post by bakermiller on 2007-04-30
Yes. the fan works... Should I go see a CPU doctor?
everything works fine at 800mhz, but as soon as i set it to 1800mhz, it goes up one degree every 10-15 secs. 
Could it be dust clogging the fan?
what are my options? This is the first time i have such a major problem.

---

### Post by jamesford on 2007-04-30
if i were you id remove the cpu fan/heatsink and apply some thermal paste there (thin layer) and attach it properly again. it sounds almost as if theres little contact between the cpu and heatsink

---

### Post by bakermiller on 2007-04-30
I live in a very dusty environment!!! 
I opened-up my machine (i don't recommend this. It was done at my own risk!) and cleaned the fan, it seems to have solved the problem for now. 

But it seems this 64bit turion AMD CPU tends to heat-up very fast, and the computer shuts down  to prevent damage to the cpu.
the heat sink is so far from the cpu, i don't know how it can absorb heat!!!

thanks for your input guys.

---

### Post by ronacc on 2007-04-30
even in "clean" environments , you would be supprised how many dust bunnies can breed. A periodic cleaning is very benificial.

---

### Post by rmfought on 2007-04-30
I just blow some canned air into my laptop input/exhaust periodically to clean out the dust, does wonders.

Which CPU do you have?  I have the ML-37 Turion in an Acer Ferrari 4005 and it idles around 41-42 C at 800 MHz, and 44 C at 2000 MHz (according to EmiFreq).

---

### Post by dptxp on 2007-04-30
> **bakermiller said:**
> I live in a very dusty environment!!! 
I opened-up my machine (i don't recommend this. It was done at my own risk!) and cleaned the fan, it seems to have solved the problem for now. 

But it seems this 64bit turion AMD CPU tends to heat-up very fast, and the computer shuts down  to prevent damage to the cpu.
the heat sink is so far from the cpu, i don't know how it can absorb heat!!!

thanks for your input guys.

THE HEAT SINK IS PRESSED REAL HARD ONTO THE CPU USING CLIPS ON TWO SIDES AND YOU NEED
TO USE A THIN LAYER OF THERMAL PASTE BETWEEN YOUR CPU AND HEAT SINK BEFORE MOUNTING
THE HEAT SINK.

THE FAN IS ALWAYS FAR, NOT THE HEATSINK BELOW IT.

ONLY MY Pentum- 100 desktop works without Fan on CPU or power supply or anywhere.
I Wonder How you are even reaching 800 MHz.

CPUs have to be run at some minimum clock frequency.

---

### Post by Skeorx13 on 2007-04-30
I'd say clean that out real good, get yourself some arctic silver and possibly upgrade your cpu fan. My pentium D used to get so hot it would shut off the system too. I couldn't play a graphic intensive game for more than 30 minutes without it overheating. I moved into watercooling for my cpu and gpu because of this issue.

---

### Post by back2ubuntu on 2007-05-26
Hello,

I have a serious CPU heating problem.
I don't believe it's a hardware problem because in WinXP and PCLOS I have no such problem at all.

Could you please advise me as to how to check this and possibly solve the problem ?

Many thanks in advance.

---

### Post by IoCaster on 2007-05-26
> **back2ubuntu said:**
> Hello,

I have a serious CPU heating problem.
I don't believe it's a hardware problem because in WinXP and PCLOS I have no such problem at all.

Could you please advise me as to how to check this and possibly solve the problem ?

Many thanks in advance.

What CPU do you have?

Go into your BIOS/Setup ---> hardware monitor and check temps. I'd recommend you let it sit there for a few minutes and see if the temps keep rising. 

If the temps are bad and/or keep rising past normal then you'll have to make sure that the CPU heatsink and fan are mounted correctly and that the fan is functioning.

If you have to replace the CPU HSF then match up a good third party unit for your specific CPU and follow the installation instructions to the letter. Modern processors will burn themselves out in just a few seconds if they're not sufficiently cooled. That's why they're set to shutdown automatically.

---

### Post by eddieb on 2007-05-26
It sounds to me like you are using a Turion cpu in a desktop. You need a heatsink with a small footprint. A normal Desktop heatsink will bear off on the cpu clip. I have used the same with no probs , the the running temp was always 31 deg.

---

### Post by back2ubuntu on 2007-05-26
Thank you for your replies.

I have a (TravelMater8204) IntelCore Duo processor T2500 (2.O GHz, 667 MHz).
I haven't had time yet to reboot and look for temps in the BIOS. I'll do and let you know.

In fact, I had a HD failure a few months ago, and I wonder if after the repair (by Acer) something got skrewed up.

cheers.

---


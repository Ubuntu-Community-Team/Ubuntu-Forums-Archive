---
title: "Stoopid 64-bit question"
date: 2008-02-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Esskie on 2008-02-18
Hi there,
Firstly excuse my apparent stupidity re this questions but if you don't ask then you will never know as they say.

My CPU is an AMD64 3200+ (Sckt-939), yes I know it's time I upgraded to a X2 processor 8-[, anyway, can I run 64 bit versions of linux as up to now I have always used i386, i585 & i686 versions.

I will post back this evening with more info as I'm just about to head out the door into this cold therefore my time is limited at the moment.

Thanks in advance,
Regards, Esskie

ps: Gave the ubuntu-7.10-desktop-i386 a spin using the live cd & loved what I saw but I'll get to 'play' longer tonight, using Mandriva 2008 cooker version atm

---

### Post by jan quark on 2008-02-18
please post the out put of the terminal command

```
sudo lshw -C cpu
```

---

### Post by Jouke74 on 2008-02-18
Yes you can run the AMD 64bit version of linux....

---

### Post by Esskie on 2008-02-18
Hi there,
Thanks for the quick response to my question :).
 
I shall do **sudo lshw -C cpu** tonight when I get home jan quark & post it here.
 
Jouke74 - Thanks also friend, I had wondered?. Even with the 64-bit version of XP but the plan is to migrate 100% with no windows install at all (on **my** system in my home lan anyway).
 
Always liked linux & have been since my first look at Mandrake 7.1 but had problems with USB DSL modems, dare I mention the SpeedTouch 330 USB modem [-(.
 
With my linux box running via a router with a NIC now though my connection problems are long gone ):P. That and getting my NVidia card working properly were the two main problems I had.
 
Thanks for now & I shall post  the output of the terminal command tonight.
 
Regards, Esskie

---

### Post by Jouke74 on 2008-02-18
Mind yourself that you first check if 64 bit drivers are available for your network hardware, because the 32 bit won't work. 

Your Nvidia card might become an issue once more, as there is the famous 64bit black screen bug, which can be solved by adding "nosplash" to your grub startup command (see the many forum posts about this). 

Good luck.

---

### Post by Kilz on 2008-02-18
> **Esskie said:**
> Hi there,
Firstly excuse my apparent stupidity re this questions but if you don't ask then you will never know as they say.

**My CPU is an AMD64 3200+ (Sckt-939), yes I know it's time I upgraded to a X2 processor 8-[, anyway,** can I run 64 bit versions of linux as up to now I have always used i386, i585 & i686 versions.

I will post back this evening with more info as I'm just about to head out the door into this cold therefore my time is limited at the moment.

Thanks in advance,
Regards, Esskie

ps: Gave the ubuntu-7.10-desktop-i386 a spin using the live cd & loved what I saw but I'll get to 'play' longer tonight, using Mandriva 2008 cooker version atm

There are , or were a few x2 socket 939 processors. I upgraded my athlon 3500 (939) to a x2 4600 (939). It was a drop in replacement.

---

### Post by Esskie on 2008-02-18
Hi there,
Well first off I haven't had a chance to boot into linux at all tonight :(, my daughter, grandson & eldest son were at the house when I arrived home.

Of course I'm always happy to see them even if it is the back of their head whilst they are using m$n messenger! ](*,).
It did mean however I haven't been able to post the outcome of **sudo lshw -C cpu**, my apologies **jan quark**, I shall make it priority tomorrow as I'm at home all day. I dare not fire up Linux atm or I'll be sitting here until daybreak!.
It's an AMD64 3200+ (939) running unclocked at 2.01Ghz, I'm sure I saw stepping 6 somewhere??, sorry for being so vague atm.

Good point about the 64-bit drivers **Jouke74**, I never considered that at all, that if I remember correctly?, is the reason XP 64-bit was never installed here although I'm not sure if the 64-bit driver support has improved for XP or not.

I think tbh, I should probably just stick with the i586 release of Mandriva and Ubuntu desktop/7.10 to spare any headaches.
As mentioned further up, I have got things running well and setup to my liking, plus  
would it make that much of a difference anyway?, I don't do excessive multi-tasking.

**Kilz** do you have any sources in the UK for the sckt-939 X2s at all?, never came across any myself but worth looking into methinks.
When you say a **drop in replacement** is it a sckt converter placed into the 939 sckt which the 940 fits into?.

[SIZE=2]An upgrade has been on the cards for a little while now, been thinking X2 4200+ 1Mb  [/SIZE]or X2 4600+ 1Mb? & either an Asus M2N-E SLI or M2N8-xxx based mobo or an Abit KN9 (MCP55P chipset) nForce5 SLI board.

I haven't read anything concerning any problems with these boards & Linux but?.....

You have started the wheels in motion again my friend :-k, the drop in converter you mentioned would certainly save cash and be a much quicker upgrade than replacing the motherboard.
I'd probably even be quite happy to just leave the OS as is too whereas with a new mobo, chipset, ram & probably graphics card too I would definitely be doing a clean install .

Well I must 'hit the hay' my friends as it's gone 01.50z & I've been up since 06.15z this morning.

Regards, Esskie

---

### Post by Kilz on 2008-02-18
> **Esskie said:**
> 

**Kilz** do you have any sources in the UK for the sckt-939 X2s at all?, never came across any myself but worth looking into methinks.
When you say a **drop in replacement** is it a sckt converter placed into the 939 sckt which the 940 fits into?.

Regards, Esskie

Hi Esskie
Nope, im in the USA so Im not sure where you would get one in the UK. The processor I replaced was a socket 939, the replacement was a 939 so no converter was necessary. At the time about a year ago I was able to find quite a few, but the socket 939 is no longer being made so the supplies of the chips is drying up. Here is a [link to a list of whats left at newegg]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2000340343+50001028+1051707439&name=Socket+939"), the place in the usa where I got mine. There are still a few x2 opterons for 939 left.
Its worth a search,  and the cost of the chips are low. [Here is a 3800x2 socket 939 for $59 ]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2927576&CatId=1948")here in the usa, perhaps they will ship it.

---

### Post by Esskie on 2008-02-20
This is another stoopid question but you probably have come to expect it by now!,

Having run **lshw -C cpu **in Konsole (wouldn't accept the exact command you told me **jan quark**?), I now have my CPU info but can't copy & paste it or rather I don't know how!.
I didn't mention despite the time spent messing with Linux I hadn't mastered the cmds yet didn't I? lol.

I can select all the text, is there a Linux cmd for copy such Ctrl + C in Win, really sorry about this guys!, first I make you wait then I can't do anything other than take a screengrab of what you require :(

It does mention physical id: 5, width: 64-bits amongst other stuff like the  speed, the capabilities etc.
It's version is 15.15.2
slot:939
size: 2Ghz
Capacity: 3Ghz
width: 64-bits
clock: 201Mhz
and a long list of it's capabilities, it's this I wanted the copy & paste for

I'm, perhaps prematurely?, assuming that from the 'width: 64-bit' entry that it can indeed do a 64-bit OS then yes?

Once again my apolz but what you have posted so far has been noted and well appreciated!

---

### Post by Tanno on 2008-02-21
The copy and paste functions are there. I'm new to linux and that's one thing I definately had to find out first.

Terminal is the oddest I found:

CTRL-SHIFT-C    =    Copy
CTRL-SHIFT-V    =    Paste

Like this:
```
tanno@Tanno-Linux:~$ sudo lshw -C cpu
[sudo] password for tanno:
  *-cpu                   
       description: CPU
       product: AMD Turion(tm) 64 X2 Mobile Technology TL-56
       vendor: Advanced Micro Devices [AMD]
       physical id: 4
       bus info: cpu@0
       version: AMD Turion(tm) 64 X2 Mobile TL56
       slot: Socket S1
       size: 1800MHz
       capacity: 1800MHz
       width: 64 bits
       clock: 200MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq
  *-processor UNCLAIMED
       description: Co-processor
       product: MCP51 PMU
       vendor: nVidia Corporation
       physical id: a.3
       bus info: pci@0000:00:0a.3
       version: a3
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master
       configuration: latency=0 maxlatency=1 mingnt=3
tanno@Tanno-Linux:~$ 
```

CTRL-C and CTRL-V seems to work everywhere else. What I have yet to find is the ability to select all in terminal like windows' CTRL-A function.

Just my noob 2 cents.

---

### Post by NightwishFan on 2008-02-21
If you have a 64bit processor, use the AMD64 Ubuntu. The speed difference is impressive. My friends 32bit Xp with twice the ram cannot outperform my 64bit Ubuntu. I believe his clock speed is higher as well. 64-bit is my baby. :)

---

### Post by Esskie on 2008-02-21
Thanks for that Tanno, very similar  just with 'Shift' added huh

Here's the output of **lshw -C cpu** at last.......:popcorn:

*-cpu:0
       description: CPU
       product: AMD Athlon(tm) 64 Processor 3200+
       vendor: Advanced Micro Devices [AMD]
       physical id: 1
       bus info: cpu@0
       version: 15.15.2
       slot: Socket 939
       size: 2GHz
       capacity: 3GHz
       width: 64 bits
       clock: 201MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc cpufreq
  *-cpu:1 DISABLED
       description: CPU
       vendor: Unknown
       physical id: 5
       bus info: cpu@1
       version: 15.15.2
       slot: Socket 939
       size: 2010MHz
       capacity: 3GHz
       clock: 201MHz

I think, from what's already been posted that 64-bit will run ok on this cpu? but I don't much fancy having to go through all the messing around with 64-bit drivers again....it took me longer than I would have liked to get the geforce working as it is

I know this is O.T and apologise now but could any of you guys tell me how to change my runlevel please?.
Am I correct in saying that if I'm runlevel 3 then X isn't running? (I'm trying to install NVIDIA-Linux-x86-169.09.pkg1.run & need to stop the X Server),

One thing after another :rolleyes:

---


---
title: "4 GB Ram with 64Bit OS and Quad Core Intel Processors"
date: 2008-01-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by rousseau09 on 2008-01-06
hi,
I am after some help. I have been reading about this 4GB RAM issue in 32 bit PC and its incompatibility. This is what I intend to get: 
Processor Type   	  Intel Core 2 QUAD Q6600	
Motherboard   	  Gigabyte GA-P35-DS3L	
Hard Disk   	  320GB SATA II 16MB Cache	
RAM Memory   	  4GB DDR2 800MHz
Now could you please tell me if UBUNTU going to support it? 
Any help would be much appriciated.
Regards

---

### Post by ryanVickers on 2008-01-06
First of all, I would steer away from the Intel quad cores... yes, intel beet AMD to the market, but they did it wrong... you now have twice the cores yes, but its on the same bus apparently so you can't take advantage of them ... ends up being a waste (twice the power, same pipes for the data as the 2 cores lol)

AMD did it right and they are a real quad core with the data path to be able to use them to their full potential :D

---

### Post by bollix47 on 2008-01-06
> **rousseau09 said:**
> hi,
I am after some help. I have been reading about this 4GB RAM issue in 32 bit PC and its incompatibility. This is what I intend to get: 
Processor Type   	  Intel Core 2 QUAD Q6600	
Motherboard   	  Gigabyte GA-P35-DS3L	
Hard Disk   	  320GB SATA II 16MB Cache	
RAM Memory   	  4GB DDR2 800MHz
Now could you please tell me if UBUNTU going to support it? 
Any help would be much appriciated.
Regards

The short answer is yes, ubuntu 64-bit will support that setup.  Mine is quite similar to yours and it works great.

If you're going to need a reliable java plugin you will have to install a 32-bit version of Firefox or Swiftweasel.  [Automatix2]("http://getautomatix.com/wiki/index.php?title=Installation") can make this fairly painless and will not only install Swiftweasel but also the necessary plugins.

---

### Post by Yellow Pasque on 2008-01-06
> **ryanVickers said:**
> AMD did it right and they are a real quad core with the data path to be able to use them to their full potential :D
No offense, but you sound like an AMD fanboy or someone who's looking at the specs on paper" Have you actually looked at any benchmarks?

---

### Post by rajeev1204 on 2008-01-06
> **Temüjin said:**
> No offense, but you sound like an AMD fanboy or someone who's looking at the specs on paper" Have you actually looked at any benchmarks?





 i too  think the comparison is wrong and the intel quad cores are not a waste

---

### Post by fjgaude on 2008-01-06
> **bollix47 said:**
> The short answer is yes, ubuntu 64-bit will support that setup.  Mine is quite similar to yours and it works great.

If you're going to need a reliable java plugin you will have to install a 32-bit version of Firefox or Swiftweasel.  [Automatix2]("http://getautomatix.com/wiki/index.php?title=Installation") can make this fairly painless and will not only install Swiftweasel but also the necessary plugins.

Can you tell us if the sound, suspend, hibernate, recover, work correctly? And what about the speed of the SATA controllers? Do you know if they work off the PCI-E bus at X1 or X4?

Thanks for any info on that motherboard.

---

### Post by bollix47 on 2008-01-06
[Gigabyte GA-P35-DS3L specs.]("http://www.xbitlabs.com/articles/mainboards/display/ga-p35-ds3l_5.html#sect0")

---

### Post by macaholic on 2008-01-06
> **bollix47 said:**
> The short answer is yes, ubuntu 64-bit will support that setup.  Mine is quite similar to yours and it works great.

If you're going to need a reliable java plugin you will have to install a 32-bit version of Firefox or Swiftweasel.  [Automatix2]("http://getautomatix.com/wiki/index.php?title=Installation") can make this fairly painless and will not only install Swiftweasel but also the necessary plugins.
I use the 64-bit version of swiftweasel with flash and iced tea for java and it works fine.

---

### Post by fjgaude on 2008-01-06
> **bollix47 said:**
> [Gigabyte GA-P35-DS3L specs.]("http://www.xbitlabs.com/articles/mainboards/display/ga-p35-ds3l_5.html#sect0")

I've read the specs but does the board under Ubuntu do all the things we all wish it to do?

Thanks for the very good link.

---

### Post by ryanVickers on 2008-01-06
> **Temüjin said:**
> No offense, but you sound like an AMD fanboy...
ok I admit to that :D but...
> **rajeev1204 said:**
> i too  think the comparison is wrong and the intel quad cores are not a waste

... what they did apparently was just layer another dual core on top of the core 2 duo, and I'll give them credit for however they managed that, but if you now have twice the processing power, but the same system bus, it would be like having 2 lanes of traffic going to 2 tole booths - you add 2 toll booths to speed things up, but don't bother having 4 lanes, just fork the 2 :lolflag:

and regardless of if is true or not, like a Sun UltraSPARC (RISC CPU) compared to anything, you will run with the same performance out of an AMD at lower heat and speed than you would get with the intel (and this is indisputable - numerous tests have been done, and I have read benchmarks)!!

---

### Post by fjgaude on 2008-01-06
> **ryanVickers said:**
> ok I admit to that...
and regardless of if is true or not, like a Sun UltraSPARC (RISC CPU) compared to anything, you will run with the same performance out of an AMD at lower heat and speed than you would get with the intel (and this is indisputable - numerous tests have been done, and I have read benchmarks)!!

What do you do with these benchmarks?

[http://www.xbitlabs.com/articles/cpu/display/amd-phenom.html](http://www.xbitlabs.com/articles/cpu/display/amd-phenom.html)

---

### Post by ryanVickers on 2008-01-06
with those I rest my case - the AMD's are clearly superior in every aspect except L2 cache, and size of the CPU and internal parts - but everything else is better, they make less heat, it has the "true quad-code design", more instruction sets, and they can run a ~800Mhz slower and deliver the same power!!!

As for the tests on page 10 and after, I'm not sure how they got those results because inside the chip, the path to the CPU from the base is much less and this has been proven... a 2.8Ghz AMD is ~= to a 3.4Ghz intel
also for power consumption, I find that hard to believe because every other site, and there are numerous ones, have stated that the AMD's produce less heat and require less power overall because they are slower but more efficient... It really is a superior architecture, like SPARC (I acknowledge that RISC would not be a gaming CPU though ;))
In fact, this page even contradicts itself! in the early pages, they are saying how AMD is cooler, but later on they say the intel is faster and takes less power!! :confused:
What you also have to consider is how good the benchmark tools are... are they running on windows? are they multi-threaded, and properly? I think its safe to assume that they are multi-threaded, but if they are on windows and/or have not been multi-threaded, then the results are immediately inaccurate and preposterous.  I would assume they ARE on windows because it was listing games like "half-life"...

---

### Post by fjgaude on 2008-01-06
I must say you have an unusual way of reading results. So be it...

---

### Post by ryanVickers on 2008-01-06
I will admit that years ago AMD wasn't even in the picture and intel ruled the CPU world, but things are changing now and on some game boxes they no longer say "intel ___ or comparable AMD" but "AMD ___ or comparable intel"!! :D

---

### Post by John.Michael.Kane on 2008-01-06
> **rousseau09 said:**
> hi,
I am after some help. I have been reading about this 4GB RAM issue in 32 bit PC and its incompatibility. This is what I intend to get: 
Processor Type   	  Intel Core 2 QUAD Q6600	
Motherboard   	  Gigabyte GA-P35-DS3L	
Hard Disk   	  320GB SATA II 16MB Cache	
RAM Memory   	  4GB DDR2 800MHz
Now could you please tell me if UBUNTU going to support it? 
Any help would be much appriciated.
Regards

Here is what I'm currently testing
Processor Type  Intel Pentium E2140 Allendale 
Motherboard   	  Gigabyte GA-P35-DS3L	
Hard Disk   	  1x WD800JD 
Hard Disk	  1XWD2500YD
DVD                   LH-20A1L-06
RAM Memory   CORSAIR XMS2 TWIN2X2048-6400C4 
Video                 Geforce 7900GTX

Distro's tested on the above configuration 
1) Ubuntu 7.04-7.10 As well as 8.04 alpha
Note's:
7.04 installed without issue, and all hardware was recognized. Edit: lm-sensors version included does not seem to show cpu temp.

7.10 exhibit the known splash screen bug which was addressed by editing grub.however. all hardware was fully recognized.  Edit: lm-sensors version included does show cpu temp properly after configuring.

8.04 while an alpha still installed without out issue.

2) Fedora 8
Note's: Light testing done, however. all hardware sound video etc. was recognized.

I would say Ubuntu will support your particular set-up.

---

### Post by Yellow Pasque on 2008-01-06
> **ryanVickers said:**
> it would be like having 2 lanes of traffic going to 2 tole booths - you add 2 toll booths to speed things up, but don't bother having 4 lanes, just fork the 2 
The Core2 architecture isn't starved for memory bandwidth like the Netburst-based Pentium D was,  plus DDR2-800 in dual-channel is common these days.

> you will run with the same performance out of an AMD at lower heat and speed than you would get with the intel (and this is indisputable - numerous tests have been done, and I have read benchmarks)!!
What benchmarks are you reading? If you look at these benchmarks and tell me that Phenom is faster, then we'll know you're delusional: [http://www.techreport.com/articles.x/13741/3](http://www.techreport.com/articles.x/13741/3)
Also, the Core 2 is a lot more OC'able than Phenoms.

Hey, at least AMD competes on price and that's what's important. However, we don't need fanboyism. (In case you think I'm an Intel fan, the last CPU I used from them was a P3 and I've bought two CPU's since then.)

---

### Post by ryanVickers on 2008-01-06
Well clearly theres something wrong with that one phenom :p - twice as long to load Firefox as everything else ...

but what I'm talking about is the AMD's make less heat because they run at a lower speed, and get better relative performance because they can do more **per hz** than the intel's because of the internal workings.  the old PowerPC's from Apple were like this too...

I don't know why they are showing up as slower in these 2 benchmark pages though because they really are more efficient!!! ](*,)
I don't get it!!! :mad: lol

A also am not familiar with all those chips!  A test that would mean the most to me would be comparing a AMD Athlon 64 X2 3800+ (2Ghz dual core) to an intel Core 2 Duo E6850 or E6750 - 3 and 2.66Ghz... I would bet a lot that the AMD would outperform the intel in this case for sure...

---

### Post by fjgaude on 2008-01-06
Ryan, I do believe you are living 18 months in the past. What you have said is about that old and true then but not now.

AMD will have lots of trouble coming back from where they were two years agao. Intel is that far ahead of them now.

---

### Post by ryanVickers on 2008-01-06
well... that may be, I got my computer and did all this research in may of last year :D

Intel has really come a long ways rather quickly then.... 
hm, in light of this new concept, the prosecution withdraws its case. ;)

---

### Post by fjgaude on 2008-01-06
Great, Rayan, now we don't have to send over the guys with the straight jackets. <smile>

---

### Post by PurposeOfReason on 2008-01-06
To kindly get back on topic. . 

The **linux kernel** will support that hardware with no problems. **Ubuntu** will easily give you the tools required to make it work no problem. I see a lot of people here with similar stuff (Loke comes to mind) using Ubuntu. Also, as someone mentioned Automatix, avoid it like the plague. It usually (see always) is far better to get it done in a bit "dirtier" method. This is in terms of effectiveness and ease of use later on, not just because I dislike automatix.

---

### Post by Red Shift on 2008-01-06
I have an Intel E2160, Gigabyte GA-P35-DS3L motherboard, and (2 x 1 GB) of G.SKILL DDR2 800 Dual Channel Kit Desktop Memory Model F2-6400CL5D-2GBNQ.

I am using Kubuntu 7.04.

All SATA, PATA, audio ports, and USB ports are recognized.

The board can adjust the CPU voltage automatically if you decide to change the FSB, multiplier, etc.

I use the 64-bit version of Swiftweasel built for the Nocona architecture.  I used Kilz's script to install Flash.  Video and sound work.  I don't remember installing or configuring a Java plugin.

I don't use suspend, hibernate, or recover.  I have no idea about the speed of the SATA controllers.  How would I check that?

lm-sensors displays CPU temp, motherboard (?) temp, CPU voltage, RAM voltage, some other voltages, and fan speeds.  The values are not nicely labeled (CPU voltage, CPU temp, etc) but I haven't messed around with the lm-sensors config files.

I discovered [_this_](http://clubit.com/product_detail.cfm?itemno=CA1938460) site which supposedly guarantees G0 stepping.  You'd probably want an after market cooler anyway.

---

### Post by fjgaude on 2008-01-06
Thanks, Red Shift, for the report... sounds good... I'll likely go for such a MB soon.

The SATA controller speed? I can't tell you how to check that directly, but can if you have a fast raid0 or 5 with fast drives. I have a raid5 with four 77MB/sec drives and with my controller connected to the PCI bus on the MB I cannot get anything over about 115MB/sec sequential read througput from the array.

My raid5 should get about three times the 77, i.e., 210MB/sec but it gets only 115 because of the relatively slow bus. PCI-E X1 goes to about 250MB/sec. <sigh>

You may test your drives using hdparm. You can get it using apt-get. After installing:

```
sudo hdparm -tT /dev/sda
```

Use for each individual drive you have or for any array, by its name.

Thanks again for the report.

---

### Post by Red Shift on 2008-01-06
> **fjgaude said:**
> You may test your drives using hdparm.

I have a Seagate Barracuda 7200.9 ST3320620AS 320 GB SATA Hard Drive.

I did three tests.
```

/dev/sda:
 Timing cached reads:   3202 MB in  2.00 seconds = 1600.91 MB/sec
 Timing buffered disk reads:  204 MB in  3.01 seconds =  67.73 MB/sec

/dev/sda:
 Timing cached reads:   3164 MB in  2.00 seconds = 1581.69 MB/sec
 Timing buffered disk reads:  204 MB in  3.01 seconds =  67.78 MB/sec

/dev/sda:
 Timing cached reads:   3178 MB in  2.00 seconds = 1589.04 MB/sec
 Timing buffered disk reads:  204 MB in  3.00 seconds =  68.00 MB/sec
```

---

### Post by fjgaude on 2008-01-06
Very good. Here's my raid5 with 1.2TB capacity:

/dev/md32:
 Timing cached reads:   1520 MB in  2.00 seconds = 759.78 MB/sec
 Timing buffered disk reads:  344 MB in  3.01 seconds = 114.15 MB/sec

You can see how your fast memory is so much better than mine, and that my array is limited by the PCI bus that's at 33 MHz, 32 bits wide, equals 132 MB/sec.

Ubuntu rules!

---

### Post by Yellow Pasque on 2008-01-06
> I have no idea about the speed of the SATA controllers. How would I check that?
You could check a drive attached to it and see what speed it's running at. Of course, your drive would have to be SATA300 capable and not be jumpered to SATA150.

```
sudo hdparm -I /dev/sd<a,b,...>
```

That's a capital i, not an l.

---

### Post by rousseau09 on 2008-01-07
Great. I was just reading the replies and 1st thing I felt, how lively this forum is. Thanks all again for replying.

Now to the point. I already read all the hardware compatibility issues and of course the tech sheets from the manufacturers. I know and believe this is a good system I am getting. 

Only thing that worried me a bit was the 4Gb RAM and possible compatibility issues and the known factor on 32bit system unable to utilize more than 3.25 ram (with PAE which make it 36 bit- correct me if i am wrong). I prefer to do my homework 1st before jumping into something. 

I used both MS and NIX. ;) i guess i might get some flames even saying it here but sometimes its necessary to have both to do certain things. And i know 64bit certain version of MS product will be able to utilize that 4GB ram. I knew Linux also can. 

Anyway, let me summarize all of it. 

Following is somewhat the specs I got. Its already ordered and so don't make me feel sad saying that old AMD vs Intel tag-of-war. I know AMD is cool and quiet but even though I couldn't resist myself of having a Quad core. :). Cause at the end Intel is somewhat better than AMD and with NIX you can get the better of it, cause NIX knows how to crunch it. 

Processor Type     Intel Core 2 QUAD Q6600
Motherboard     Gigabyte GA-P35-DS3L
Hard Disk     320GB SATA II 16MB Cache (Seagate)
RAM Memory    4GB DDR2 800MHz
Graphics    Asus 2400PRO 256MB PCIe Graphics DirectX10
Case    ATX MID Tower
LCD Monitor    22" Acer WideScreen

To do: 
I need 64 bit os to get the full outcome/resource of this system. (comment expected)
Gutsy does support it except for that grub issue.
My OS should be able to install without any issues. (comment expected)
64 Bit is without any issues should be able to utilize all 4GB RAM.(comment expected)
Might have to do some tweaks with some programs due to possible incompatibility. (comment expected)
Now time to get some more feedbacks.
What about the Monitor?  Response rate? official is 5ms. Do you think the same? 
I know the GFX card is pretty basic. I will get something else ASAP. But till then will it be fine? Any known issues? 

I believe everything 's possible. Might take a few more cups of coffee and banging your head on wall, but yes possible. And with Linux its sooner than anyone else. What say you ? :popcorn:

---

### Post by John.Michael.Kane on 2008-01-07
> **rousseau09 said:**
> To do: 
I need 64 bit os to get the full outcome/resource of this system. (comment expected)
There has been numerous debates about this, and the responses will vary. Your best off making your own conclusions from testing on your particular hardware.

> **rousseau09 said:**
> Gutsy does support it except for that grub issue.
Correct. you will have to make a minor adjustment for the splash screen to show.

> **rousseau09 said:**
> My OS should be able to install without any issues. (comment expected)
Yes this is correct,however. I would still advise checking with the maker of the distro you plan to use.

> **rousseau09 said:**
> 64 Bit is without any issues should be able to utilize all 4GB RAM.(comment expected)
I will say no Os/architecture is perfect. users of 64bit have had problems, and in most cases there has been a fix/workaround for the issue,however. Should there be an issue i'm sure one of the forum members will be able to assist you.

> **rousseau09 said:**
> Might have to do some tweaks with some programs due to possible incompatibility. (comment expected)

Currently two issues reported circle around the Java plug-in  eg: icetea not working with every site, Work around for that seems to be to install the 32 bit Firefox and Java method out lined by Kilz. 

The other issue circles around the currently installable version of flash which when installed has an md5 mismatch thus the package is effectively broken, and no eta on fix is known. There are a few workarounds for this issue.
1) [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)
2) [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669)
3) [http://ubuntuforums.org/showthread.php?t=202537&highlight=java](http://ubuntuforums.org/showthread.php?t=202537&highlight=java)

> **rousseau09 said:**
> Now time to get some more feedbacks.
What about the Monitor?  Response rate? official is 5ms. Do you think the same? 
More information would be need on the LCD in question eg: the model number.

> **rousseau09 said:**
> I know the GFX card is pretty basic. I will get something else ASAP. But till then will it be fine? Any known issues?
Some users have said ATI cards are a pain to install Vs say install an nivida card under Linux/Ubuntu. You would have to do research on this particular card. 

Most install the driver is either with the restricted driver manager a tool called Envy or the manual way [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

> **rousseau09 said:**
> I believe everything 's possible. Might take a few more cups of coffee and banging your head on wall, but yes possible. And with Linux its sooner than anyone else. What say you ? :popcorn:
You should not need to bang your head on the wall. I would advise to take your time, and keep a note pad handy, as this will allow you keep track howto's you use, as well as modifications you do.

---

### Post by rousseau09 on 2008-01-08
Thanks John.Michael.Kane. That was a nice post. 
Yes since the HDD is big enough, I will have all potential OS's installed so that I can compare them. 
and I certainly don't plan to bang my head on the wall.
Been reading posts and discussion boards mainly. Interestingly enough, most issues had some kind of workarounds or fixes. All I can hope to find the right one for me. 
Guess all I need is dumb luck not to have any issues. But again, then you don't learn anything new. except issues I run into have some solutions. 
I will run some stress tests on that machine and posting them here. Also if I run into something I will post the possible solutions here.

---

### Post by rousseau09 on 2008-01-31
Finally back with the system I wanted to have.

Got 7.10 64-bit version Ubuntu. 

Installation was clean. No issues at all. 

Had that flash plugin issue. Installed the plugin from [here]("http://ubuntuforums.org/showthread.php?t=476924")

Didn't worked after I restarted Firefox. Lucky me, firefox gives u a drop down "Install Missing Plugin" option. I clicked on that and installed Adobe Flash. didnt worked out either as its 32 bit. Then closed firefox and reopened it. This time I selected Gnash. This worked fine.

A bit confused. How would I know which plugin is being used by firefox in website like youtube.com ? 

Any ideas?

---

### Post by matty13 on 2008-01-31
> **ryanVickers said:**
> I will admit that years ago AMD wasn't even in the picture and intel ruled the CPU world, but things are changing now and on some game boxes they no longer say "intel ___ or comparable AMD" but "AMD ___ or comparable intel"!! :D

I have to post offtopic here but all the windows games i bought, Crysis, UT3 etc all show the Intel Core 2 Extreme logo which is an absolute amazing quad processor running at 3.0ghz

---

### Post by jpittack on 2008-01-31
> **matty13 said:**
> I have to post offtopic here but all the windows games i bought, Crysis, UT3 etc all show the Intel Core 2 Extreme logo which is an absolute amazing quad processor running at 3.0ghz

True, it is fast, but how many are willing to spend $1,000 on one part?  A quad core amd build cost less for the whole system!  Just wait on b3 stepping, and you have perfection.

I am a fan of the underdog, but even more of a fan of my wallet.

---

### Post by rousseau09 on 2008-02-01
> **jpittack said:**
> True, it is fast, but how many are willing to spend $1,000 on one part?  A quad core amd build cost less for the whole system!  Just wait on b3 stepping, and you have perfection.

I am a fan of the underdog, but even more of a fan of my wallet.

Cant beat that!

---

### Post by ghandi69_ on 2008-02-01
I am going to add a little anecdote to the Intel Vs Amd debate here.

I have been, and probably will be, an AMD fan boy.  However, I always am looking for bargain cpus (I still don't have a dual core processor, still using AMD 3200+) and AMD tends to price well at the low end.

However, I have a cousin who works on the Itanium processors at Intel, so whenever he comes over for the Holidays, we banter a little back and forth.  I would say, about a year and half ago, as I would bragging about AMD recent market share gains, he told me this --

"You you will find that Intel NEEDS AMD to stick around, in order to remove themselve from 'monopoly' status.  So there will definitely be times AMD is allowed to gain some market share.  However, I want you to notice that whenever AMD starts gaining any kind of serious momentum, you will see us here at Intel squash them like a bug [pounds fist into hand].  Intel does not view AMD as a competitor."

Needless to say, after the last few years, I havent been bringing the subject up as much.

---

### Post by nixi on 2008-02-01
Hi,all! 

I use Ubuntu 7.10 AMD64 on a workstation with two Intel quad core processors and 16 GB fbDIMM memory, and it seems to work well.

motherboard: Tyan i5400XT
processors: Xeon E5345 quad core x 2
memory: KVR DDR2-667 fbDIMM 2GB x 8
hard drive: WD Raptor 150GB
graphics card: Nvidia QuadroFX1500
chassi: Antec P190

I have yet to fix the splash screen bug (if you can, then please link me to a howto), and then there are three things I am trying to find out regarding temperatures and cpu frequency scaling.  

First, lm-sensors seem to give some silly temperature results for CPU, AUX and SYS: -48°C, i.e. minus degrees (!), and regardless of workload. I don't know why. Perhaps it has to do with an inactive lm-sensors setting, or possibly the motherboard's first BIOS version? 

Second, the minimum frequency scaling for all cores is at 85%, which seems too high. On my other computer, which uses AMD's dual core processor Athlon 5600+, the minimum is 35%, which seems reasonable. Is 85% normal for Intel's quad core processors, or is this something I should fix? 

Third, the Xeons are cooled with Intels passive heat sinks, and air is ducted from the chassi fans. However, I plan to replace the heat sinks with a pair of Noctua NH-U9F, because now on 100% work load the core temperatures tend to peak at 70°C, or 77°C even, which seems high. The thermal specification for the Xeons at max TDP is 66°C. I am not sure whether this specification means that the core temperatures at 100% work load should remain below 66°C. Do you know?

---

### Post by ryanVickers on 2008-02-01
> **matty13 said:**
> I have to post offtopic here but all the windows games i bought, Crysis, UT3 etc all show the Intel Core 2 Extreme logo which is an absolute amazing quad processor running at 3.0ghz

I said some boxes, not all of them, and regardless intel is back in the lead for now, as we agreed earlier...

---

### Post by glenbuck1914 on 2008-02-02
Hi Guys (as it's my first post round here),

Just wanted to say how unbelievably good 7.10 64 bit runs on my system :). This is the first 64 bit OS I've used and it really has blown my socks off.

Although I still use Windows for games (and only games) Gutsy 64 has finally pushed me to using linux fulltime.

The Good Points:

ffmpeg- I can't believe how quick it is at h264 video encoding- 40-50 mins for a 2 pass encode!

Folding at home SMP client 6.0b- I was running 4 clients that took 40 mins per frame- That's roughly what you get running the Windows SMP client on a Pentium HT/ 1.6Ghz Core2 (about 1400 Work Unit points every 24 hours. The gutsy x64 system posts about 7000 Work Unit points every 32 - 48 hours. 

Stability- Folding at home can run 4 clients 24/7 without as much as a hiccup on my overclocked system. 

Flash & Java have worked fine for me (so far)

ATI driver is running perfectly. 
Games: (I downloaded Micropolis last night to give it a whirl and it runs flawlessly)
Compiz- Runs fine for the most part, if it does cause a graphical glitch a quick Alt+F2 metacity replace resolves it.

The Bad Point!

I have one and only one miniscule bad point- Sopcast.
Sopcast runs fine when selecting a channell from the list but I get the dreaded "Segmentation Fault" when I try to launch a channell not in the list. I've tried various fixes but alas it remains my 1 and only bad point.

Just want to show my appreciation for such a fast and rock solid OS. I found a lot of guides and help across various forums while setting up the system so I registered here in the hope of giving something back and hopefully convert some new users to the power of Ubuntu amd64!

Finally here's my system specs:

CPU: 3.0Ghz Q6600
RAM: 2GB Gskill PC6400
Mobo: Asus P5W DH
VGA: 2900xt 1GB

---

### Post by SpiderGorilla on 2008-02-02
Okay, lads, here's how I get along:

Dell Inspiron 530 with Intel Core 2 6420 @ 2.13gHz dual 64-bit processors
4GB of On-Board RAM
250 GB internal SATA HD with Windows Vista
250 GB externa IDE HD running Ubuntu 7.10 on USB 2.0
nVidia GeForce 8600 GT 256MB (very nice card for what I paid)

etc etc etc ad nauseam. When I first got the system back in August, I couldn't get Windows to recognize that I was missing about half a Gig of RAM. I thought it was because my system shipped with 32-bit Vista rather than 64-bit Vista. So I ran Linux via LiveCD and... guess what? Same problem. So I huffed and grumped and didn't upgrade to Linux becase I felt "what was the point?"

But you know what? I downloaded the Mobo's new BIOS from Dell, upgrading it from 1.0.8 or some-such to 1.0.10... and... guess what? Both Linux and Windows now see 4 GB of RAM without fail. So it was the Mobo all along.

Made me a happy camper, because I paid through the nose to have that extra RAM!

*EDIT*

Of course, I just configured the same system (slightly faster processor) without the 12% discount I got through the company I worked for... and I paid $1500 for this system back then. I can now get 70GB more data, and 0.07 more GhZ processing power for $999... that makes me want to kick myself in the crotch.

---

### Post by Yellow Pasque on 2008-02-03
> **rousseau09 said:**
> A bit confused. How would I know which plugin is being used by firefox in website like youtube.com ? Any ideas?
Enter about:plugins in the URL bar. That will show you the version of the Flash player you're using. If you're using Gnash, then I would recommend searching around this forum for Kilz's script thread to get the real Flash player (Gnash wasn't a full replacement the last time I checked).
EDIT: The Flash Script thread is stickied now, so no need to search.

---


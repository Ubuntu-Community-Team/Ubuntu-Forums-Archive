---
title: "amd x64 seems less responsive than i386"
date: 2008-03-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by keratos on 2008-03-15
installed xubuntu x64 on my AMD LE-1100 CPU, 512MB DDR2, onboard (crap) VIA K8M890 VGA and 4yr old DiamonMax IDE drive.

Seems less responsive than the i386 ISO on the same machine. 

So, questions:


Could the i386 be more responsive due to perhaps x64 use of more memory than i386?

Is this the most lean way to get xfce / ubuntu on my machine? 

Im concerned about bloat so installed xubuntu but perhaps a better way would be ubuntu then install xfce4 rather than xubuntu desktop, then remove ubuntu desktop?

---

### Post by kaivalagi on 2008-03-16
On a machine with the sort of specs you have given, I don't think there is anything for you to gain from running 64bit ubuntu. There is lots of discussion on whether a 64 bit distro is better performing or not when compared to it's 32 bit equivalent...I think the answer depends on what you use your OS for. For standard internet/office use I think it's just down to personal choice.

If you were happy with a i386 version of the OS I would just stick with that.

If you do stick with i386, you might want to consider Linux Mint XFCE edition, it is a ubuntu based distro centered around XFCE. I haven't used this flavour of the Linux Mint distros, but a friend has and swears by it...I have used the main edition though and for a i386 distro it is very well polished (and supports all the ubuntu repositories too :) )

I am running 64 bit on both my home PC's, and do so because it is where things will ultimately head towards. With my hardware I generally don't find that performance is better or worse than what I'd find with a i386 OS, probably because nothing is being developed with 64 bit performance in mind....Right now there is no major reason to use 64 bit over 32 bit, being a bit of a techy helps sway the decision though :D

It's your call, just go with what you think is a better performer for what you need.

---

### Post by keratos on 2008-03-16
Interesting.

I should declare that I am a systems and software engineer working for ICL here in London. Most of my development involvement is within the 3rd level languages (C, C++) and 2nd level such as 6502 and MC68xxx CPUs, alas not x86 or indeed i32.

From my experience, 64 bit programming consumes far more memory than 32 bit , not least because most of the data and operands are double-long aligned (64bit). Extra cycles are required to convert address mappings from long to double-long aligned.

still with me ??

Well, all that is fine if you have a fast CPU and lots of memory. In my case, neither and I seriously doubt 64 bit gives any advantage on a desktop system with the exception of gaming perhaps and certainly scientific modelling where accuracy of data and floating points are critical.

I've read all the hype about 64bit and 32bit. I was programming in 64bit some 8yrs ago and it has still not caught on.

My personal view is that its all marketing hype. I seriously doubt whether "joe average" guy with a desktop linux box will notice any difference.

What I was not sure about was whether ubuntu x64 was a simple port or recompliation. If any code in here was not using extended modes and addressing offered by x64 then the 32bit addressing would, I would argue, lead to REDUCED performance on 64bit architecture. That is my experience having been in the business for 22years.

I have recompiled my kernel to remove all bar the essentials and using various benchmarks (zcpu etc) and adopt pre-emptive scheduling. I  have noticed a slight improvement but nothing drastic.

Swap space is in use, circa 100MB thus a 512MB RAM boost is probably the way forward.

So, I'm non the wiser...for now.

Thanks anyway.

---

### Post by kaivalagi on 2008-03-16
I am also a developer, mostly .net these days, so I guess you could call that 4th level :) I've not had quite the same amount of working experience as yourself.

I do know where you're coming from, I come from a engineering background, initially working on micro controllers as you've done it seems, so I appreciate the hardware aspect.

> What I was not sure about was whether ubuntu x64 was a simple port or recompliation. If any code in here was not using extended modes and addressing offered by x64 then the 32bit addressing would, I would argue, lead to REDUCED performance on 64bit architecture. That is my experience having been in the business for 22years.

I think, someone please correct me if I'm wrong,  that the libraries we install have just been recompiled for the 64 bit kernel, using the same code with alternative references to 64 bit support libraries.

What I'm really not sure about is the kernel and it's code, I don't know how much effort has gone into ensuring it is using the x64 instructions as it should with an AMD 64 or Core 2 Duo. Or indeed whether this needs to happen, given AMD 64 and Intel Core 2 CPU's are arguably not true 64 bit as they use some 32 bit technologies I think, EM64T technology, for example, is a 64bit emulation from what I've read...again someone correct me if I'm wrong.

I would really be interested in the answers to what you're asking, it would be useful if anyone out there doing development specifically for 64 bit Linux can comment. Can anyone in the know shed some light?

I think it's a safe bet that you should to get another 512MB for a 64bit OS...cheap enough these days anyway.

---

### Post by Jouke74 on 2008-03-17
It completely depends on what software you use in Ubuntu. But for the general stuff e.g. Firefox, Openoffice etc. there is no noticable improvement.

For rendering, scientific calculations and other number crunching the speed improves. But also here it depends a lot on the program and it's compilation.

---

### Post by NightwishFan on 2008-03-17
My experience is quite the contrary. I tried 64-bit edition and I have noticed huge improvements in performance. Using more ram will not be slow unless you do not have enough ram in the first place. I believe I read 64-bit has less errors and a more efficient memory operations as well. Also it does largely depend on how the program is made to use it. (Think on how at first nothing was made to use 2x core cpus correctly)

I plan on doing some good reading into this I will keep you updated.

---

### Post by keratos on 2008-03-17
Ah well

Isn't life exciting when we all have a rich and varied experiences.

Yes, 512MB DDR2 is about £20 but hey, I'm looking to bring my phoenix hardware from the ashes of dispair so if I can bring it back to life for free, why not!

As I type I have installed Zenwalk which is reporting i686 arch. 

I have to say the response is terrific and the boot time is about 1/3 of xubuntu - I have tried to make the two like-for-like in that I have identical where possible, daemons, services, kernel modules etc running.

Interestingly the xubuntu kernel takes 18 seconds to load whereas Zen, about 6 seconds. I spent a week trimming down my xubuntu kernel and have done nothing to the zen. And yes, both kernels are loaded from the same physical HDD albeit different partitions (of equal size) so no issue of disk performance here. 

There is definitely some bloat in xubuntu and my perception from analysis to date is that the 64bit addressing and execution is detrimental, I'm running out of all other avenues of explanation here.

It really is a shame. I like ubuntu family as the support is terrific, the packages are abundant and the distro is regularly updated (mind you some might say this is not a + point !!).

I read about Zen over the last few months and having installed it and using it as I type, the performance is like no other I have tried (latest versions as of last 4weeks):
Slackware, Vector, Sam, DSL, Puppy, Mandriva (got to be the slowest!), Fedora, SuSE, Knoppix, Kubuntu, Xubuntu, Ubuntu, Dreamlinux, Wolvix, PClinux, Debian, Mepis, Mint, CentOS, Arch, Gentoo (fast but a nightmare to setup - if you like GUIs!!), Elive, fluxbux, Foresight ... 

to name a few!

I keep coming back to Zenwalk but the lack of packages really hacks me off, despite availability of Slack and Vector etc repos.

ANyway, I've decided x64 is no good for minimal hardware but probably excels when furnished with 1GB+ of RAM and a decent CPU (AMD LE-1100 not being such an item!)

Have you performed any similar tests/experiences to report?

---

### Post by NightwishFan on 2008-03-17
Cpu: AMD Athlon 64x2 3800+ 2.0ghz (Normally stepped down to 1.0ghz when not as much is needed)
Ram: 2x512 (Total = 877mb because of shared gpu)
in 64-bit Ubuntu Hardy:
Free -m reports:
```
used: 505mb free: 372mb
I am using compiz with many plugins running firefox with 8 tabs, pidgin, rhythmbox playin cd, and tracker
```
My load average is:
```
load average: 0.44, 0.40, 0.35
```

Overall the system is snappier and less crashes than the 32-bit. (No proof just what I have noticed) Encoding my music to flac or ogg time is cut down from 1m:30s to at times 22 seconds. Normal apps I have noticed gimp is very fast at loading, saving, and using plugins. Amarok and Rhythmbox build my library faster. Other than that differences are not apparent. The ram use is around 100mb more however I am never full and my swap is unused. On a lesser system I would still use 64-bit if compatible, however with 512 or less it would be cutting it close to run compiz and emerald. Also note Hardy is not ready for release and is not trimmed down yet. I am using GNOME.

---

### Post by Jouke74 on 2008-03-17
AMD X2 4200, 2 GB of Ram, 74GB WD raptor as system disk. 

Speed differences are dependent on a lot of factors: To compare a Zenwalk XFCE environment with a full Gnome - Compiz Ubuntu environment is not really fair. Same goes for Xubuntu vs Ubuntu in that manner, and I don't think this is a 386 vs AMD64 discussion.

I would also not call the loading of programs from HD a speed improvement caused by 64bit instead of 32 bit (solely). The same goes for the start-up of a computer, which depends almost fully on disk IO. If your partitions are far apart, disk IO can make a difference, my WD does from 80 Mb/s at start to 55 Mb/s at the end. 

I left out disk influences to measure architecture speed improvements once. I ran programs directly from memory (small ramdisk). My Merlin (genetic software) calculations went from 1 hour 5 minutes to 42 minutes after a 64bit recompile. Now THAT saves time.

---

### Post by Kilz on 2008-03-17
I think it has more to do with the Sempron processor the original poster is using.  The system also has the minuimum ram that is common with 64bit systems. A stick of ram may improve things. But if something works better and you dont have the cash for ram, install it.

---

### Post by natros on 2008-03-17
Let me tell you my experiences with 32 and 64 bits. I'm both a gentoo (32 and 64) user and a ubuntu (32 and 64) user. I see a big difference between ubuntu 32 and ubuntu 64 and that's because the amd64 packages are optimized for x86_64 while the 32 bits version uses a lower optimization  (what is the default architecture for 32? gcc -march=i486?) . With gentoo I don't see a big difference because I use the same optimizations for 32 and 64bit.

---

### Post by keratos on 2008-03-17
> **Jouke74 said:**
> AMD X2 4200, 2 GB of Ram, 74GB WD raptor as system disk. 

Speed differences are dependent on a lot of factors: To compare a Zenwalk XFCE environment with a full Gnome - Compiz Ubuntu environment is not really fair. Same goes for Xubuntu vs Ubuntu in that manner, and I don't think this is a 386 vs AMD64 discussion.

I would also not call the loading of programs from HD a speed improvement caused by 64bit instead of 32 bit (solely). The same goes for the start-up of a computer, which depends almost fully on disk IO. If your partitions are far apart, disk IO can make a difference, my WD does from 80 Mb/s at start to 55 Mb/s at the end. 

I left out disk influences to measure architecture speed improvements once. I ran programs directly from memory (small ramdisk). My Merlin (genetic software) calculations went from 1 hour 5 minutes to 42 minutes after a 64bit recompile. Now THAT saves time.

My original post refers to a plethora of O/S installed, including Xubuntu (xcfe) and Zen (xfce).

Without wishing to go into my benchmarkings (far too detailed and time consuming for post here)  I have compiled the same kernels on all installs as closely as possible thus they are identical in terms of included modules and code etc. Similarly identical versions of X and modules have been used, in addition to packages used in benchmarks.

My analysis leads me to conclude this is most definitely a x86 versus  x64, certainly for AMD. Incidentally I have not trialled an x86 CPU yet !!

---

### Post by keratos on 2008-03-17
> **NightwishFan said:**
> Cpu: AMD Athlon 64x2 3800+ 2.0ghz (Normally stepped down to 1.0ghz when not as much is needed)
Ram: 2x512 (Total = 877mb because of shared gpu)
in 64-bit Ubuntu Hardy:
Free -m reports:
```
used: 505mb free: 372mb
I am using compiz with many plugins running firefox with 8 tabs, pidgin, rhythmbox playin cd, and tracker
```
My load average is:
```
load average: 0.44, 0.40, 0.35
```

Overall the system is snappier and less crashes than the 32-bit. (No proof just what I have noticed) Encoding my music to flac or ogg time is cut down from 1m:30s to at times 22 seconds. Normal apps I have noticed gimp is very fast at loading, saving, and using plugins. Amarok and Rhythmbox build my library faster. Other than that differences are not apparent. The ram use is around 100mb more however I am never full and my swap is unused. On a lesser system I would still use 64-bit if compatible, however with 512 or less it would be cutting it close to run compiz and emerald. Also note Hardy is not ready for release and is not trimmed down yet. I am using GNOME.


I would certainly not consider output from uptime as a definitive bechmark, I mean it is only giving an average over 1, 5 and 15 mins. Very subjective and depends on what you were doing the last 15 minutes.

---

### Post by NightwishFan on 2008-03-17
I did not say it was a benchmark. Just an example. I also stated what I was doing for last 15 mins. :)

My pc sucks, but 64bit makes it great.

---

### Post by keratos on 2008-03-17
sucks ??? sucks what?

BTW I note your PC is much much higher spec than mine so if you find that rather inadequate then hell only knows what you'd think of this pile of junk I'm using. :lolflag:

---

### Post by Kilz on 2008-03-17
> **keratos said:**
> My original post refers to a plethora of O/S installed, including Xubuntu (xcfe) and Zen (xfce).

Without wishing to go into my benchmarkings (far too detailed and time consuming for post here)  I have compiled the same kernels on all installs as closely as possible thus they are identical in terms of included modules and code etc. Similarly identical versions of X and modules have been used, in addition to packages used in benchmarks.

My analysis leads me to conclude this is most definitely a x86 versus  x64, certainly for AMD. Incidentally I have not trialled an x86 CPU yet !!

Are you comparing Zenwalk 32bit to Ubuntu 64bit?

---

### Post by NightwishFan on 2008-03-17
Out of everyone I know computer geek or not, they have pcs far superior to mine except the OS and Processor. Since 3 months ago my pc was:

Pentium 3 800mhz
128mb ram
20gb HD
Windows XP Sp2 (SLOW!!!!!)

My new one is sufficient for Hardy/Suse but I still would like a more modern one.

---

### Post by keratos on 2008-03-17
:lolflag:

me 2 !!

I already have three in the house, but my 8yr old/young! daughter has the most powerful and ...

yuk

it has the "other" O/S on it....I guess linux hasnt made it into schools here yet.

Kilz....

NO! I am comparing xubuntu 7.10 on XFS with a homebrew kernel , to Zen 5.

After much more investigation , I think I have found the answer.

I believe the Xserver in xubuntu is .3 and Zen uses a newer version (.4) I think. The vesa display module in Zen is much more responsive and I seem to be getting better blt and video map results. Screen paint and draws are refreshed much quicker thus giving an "appearance" of snappier response however this is only within the X framework. I'm sure if xubuntu can run the same X as Zen, then my xubuntu would be as good if not better than Zen.

I believe xubuntu is v11 r1.3 and Zen is v11 r.1.4

???

---

### Post by Kilz on 2008-03-17
> **keratos said:**
> :lolflag:

me 2 !!

I already have three in the house, but my 8yr old/young! daughter has the most powerful and ...

yuk

it has the "other" O/S on it....I guess linux hasnt made it into schools here yet.

Kilz....

NO! I am comparing xubuntu 7.10 on XFS with a homebrew kernel , to Zen 5.

After much more investigation , I think I have found the answer.

I believe the Xserver in xubuntu is .3 and Zen uses a newer version (.4) I think. The vesa display module in Zen is much more responsive and I seem to be getting better blt and video map results. Screen paint and draws are refreshed much quicker thus giving an "appearance" of snappier response however this is only within the X framework. I'm sure if xubuntu can run the same X as Zen, then my xubuntu would be as good if not better than Zen.

I believe xubuntu is v11 r1.3 and Zen is v11 r.1.4

???

Your comparing apples to oranges. If you compared stock 32bit Ubuntu to Stock 64bit Ubuntu you may see the difference we are speaking of. But there are to many variables in comparing one distro to another. Then may be both Linux distributions, but there is a difference. Just like apples to oranges are both fruits, but are not alike.

---

### Post by keratos on 2008-03-17
Of COURSE there are lots of variables,

However in order to reach some form of common denominator, it is logical to fashion the benchmarks with some form of brown field.

I think to call it "apples and oranges" is with respect, a much more worrying statement and degrades the debate.

What is clear is that people are experiencing a wide range of results and performance, and unless two individuals have the SAME spec, bit for bit, byte for byte, chip for chip, it is never going to be a one horse race.

---

### Post by kaivalagi on 2008-03-17
Have you tried out the ubuntu 8.04 alphas yet? The stable release is due next month and looks good. There is a xubuntu derivative available

I am running standard ubuntu 64 bit alpha 6 on a spare partition and it does seem to be faster than 7.10,  albeit a bit buggy at present as to be expected. It uses Xorg 7.3 and implements a better process scheduler, both of which go a long way to improve overall performance I think. Check out the improvements here: [http://www.ubuntu.com/testing/hardy/alpha6]("http://www.ubuntu.com/testing/hardy/alpha6")

I can't provide anything in the way of benchmarking results, so this is all I can offer as a suggestion. Good luck in your endeavors...

---

### Post by Jouke74 on 2008-03-17
I agree with Kilz, see also my previous posts why.

If you want to see the real difference between 32 and 64 bit, then you can burn 2 live cd's. 
The first one a "i386 7.10 Ubuntu live CD" and the other the "AMD64 7.10 Ubuntu live CD". 

Now start-up the i386 live cd and run this benchmark in a terminal: 
[I]
time echo "scale=5000; 4*a(1)" | bc -l -q ; cat /proc/cpuinfo | grep "model name"; cat /proc/meminfo  | grep MemTotal[/I]

Now run this test twice, cause the first time it does not use cache optimally.
Save the time data somewhere (easiest is a USB stick I noticed), and restart your computer with the AMD64 live cd.

Now rerun the test twice under AMD64.

Compare the results of the two second runs. The quickest time is best. Now you're comparing apples with apples since the only variable you are changing is 32 vs 64 bit, assuming that your computer remains the same while switching CDs...

AMD64:
real    0m40.723s
user    0m40.715s
sys     0m0.000s
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
MemTotal:      2063624 kB

I386:
real    0m44.416s
user    0m44.415s
sys     0m0.004s
Rest is the same.

As you can see 64 bit vs 32 bit saves about 3 seconds on my machine for the calculation of pi for 5000 decimals behind the comma.

People who do not want to waste CD's can use their current AMD64 install as well. There will not be much difference I noticed.

---

### Post by kaivalagi on 2008-03-17
Bangs goes my theory on 8.04 alpha 6 being quicker than 7.10...at least for this benchmark

It does seem more responsive though, process scheduler handling more than one process better?

Anyway, this isn't going to help the discussion...I'm interested in knowing what the outcome of Keratos running the 32 v's 64 bit benchmarks...

Ubuntu 7.10 64 bit:

real    0m33.125s
user    0m33.110s
sys     0m0.000s
model name      : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
model name      : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
model name      : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
model name      : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
MemTotal:      4054224 kB

Ubuntu 8.04 64 bit:

real	0m34.620s
user	0m34.618s
sys	0m0.000s
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
MemTotal:      4053904 kB

P.S. Can anyone explain why the memtotal differs between the 2 OS versions?

---

### Post by Jouke74 on 2008-03-17
This is a CPU and memory benchmark and it uses only one CPU. So no multitasking disk loading etc. included. Nice Quad core score (looking a bit jealous at your scores :-) ).

---

### Post by kaivalagi on 2008-03-17
My HW is a bit overkill really, had the cash at the time so geared myself up for the next couple of years (I hope). Next will be some overclocking, when I need the extra grunt :)

Whats the core GHz for the 4200+ anyway, is it around the 2.4Ghz range also?

Quick side question: Are there any thorough benchmarking tools for linux out there? I used some of the windows benchmarking tools when windows was my main OS,. It would be nice to have something similar for Linux, so I can gauge OS performance when trialling alpha/beta releases for example.

---

### Post by gunthergloop on 2008-03-17
I've been using 32-bit Ubuntu for the past few months (Vista is an excellent advert for Ubuntu), but my pc died for no apparent reason and I replaced the motherboard & cpu with similar spec -Intel Core2 Duo. I bought 2GB, but one of the chips failed so I need to send it back. For now I have 1GB. 

This time I installed 64-bit Ubuntu 7.10.

I get strange pauses from time to time -like when copying large files, there are delays in my typing appearing onscreen. That never happened before. I've also noticed 'darkened screen' pauses in Firefox from time to time, Opera won't install because the makers haven't yet made it "compatible with my hardware" and for some reason some java apps don't seem to work (and it's not an adblock issue).

I ran the above test and get...

64-bit (installed)
real    0m36.155s 
user    0m36.138s 
sys     0m0.004s 
model name      : Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz 
model name      : Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz 
MemTotal:      1028200 kB 



32-bit (from cd)
real    0m38.715s 
user    0m38.702s 
sys     0m0.000s 
model name      : Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz 
model name      : Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz 
MemTotal:      1034432 kB

I'm hoping most of the above will be sorted when I get the extra 1GB, but I would have thought 1GB is sufficient for Ubuntu.

I might stick with 64bit to see if these issues iron-out, but I'm wondering if maybe the 32-bit install would suit me better. I generally don't run anything too cpu-draining anyway.

---

### Post by Jouke74 on 2008-03-18
I think the pauses will only get bigger with the 32 bit system. But if you have no serious things to do with your computer you can try. Slower disk copying I noticed as well with Gutsy as compared to Edgy, but both on 32 bit as well as 64 bit btw.

My processor runs at 2.2 Ghz.

---

### Post by keratos on 2008-03-18
> **Jouke74 said:**
> I agree with Kilz, see also my previous posts why.

If you want to see the real difference between 32 and 64 bit, then you can burn 2 live cd's. 
The first one a "i386 7.10 Ubuntu live CD" and the other the "AMD64 7.10 Ubuntu live CD". 

Now start-up the i386 live cd and run this benchmark in a terminal: 

......


.


This is not a system benchmark, it serves to demonstrate the numerical accuracy and speed of 64bit  registered instruction mathmatics, over 32bit; any logical and educated individua will be concious that this would always be executed faster and with more accuracy than 32bit instructions.

This test fails and fails demonstrably in assessing device IO (disc/networking), RPC/IPC (Xserver), and desktop performance issues (library cache, memory performance, swap activity). All of these require data pools and resources far greater than the sum of 

```
time echo "scale=5000; 4*a(1)" | bc -l -q ; cat /proc/cpuinfo | grep "model name"; cat /proc/meminfo | grep MemTotal
```

This is simply one, and a very minor "one", test out of many that would constitute a considered application of benchmarking. 

Readers beware!

---

### Post by keratos on 2008-03-18
> **Jouke74 said:**
> This is a CPU and memory benchmark and it uses only one CPU. So no multitasking disk loading etc. included. Nice Quad core score (looking a bit jealous at your scores :-) ).

Now this guy CLEARLY knows what he is talking about. 

I definitely agree.

kaivalagi: Running the test is, as you can see, pointless as it is ridicouls in the sense of a "bechmark".

Does anyone know if there is a Winstone/Winbench equiv for linux. If so, then I would be happy to participate to prove my theory.

---

### Post by keratos on 2008-03-18
> **gunthergloop said:**
> I've been using 32-bit Ubuntu for the past few months (Vista is an excellent advert for Ubuntu), but my pc died for no apparent reason and I replaced the motherboard & cpu with similar spec -Intel Core2 Duo. I bought 2GB, but one of the chips failed so I need to send it back. For now I have 1GB. 

This time I installed 64-bit Ubuntu 7.10.

I get strange pauses from time to time -like when copying large files, there are delays in my typing appearing onscreen. That never happened before. I've also noticed 'darkened screen' pauses in Firefox from time to time, Opera won't install because the makers haven't yet made it "compatible with my hardware" and for some reason some java apps don't seem to work (and it's not an adblock issue).

I ran the above test and get...

64-bit (installed)
real    0m36.155s 
user    0m36.138s 
sys     0m0.004s 
model name      : Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz 
model name      : Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz 
MemTotal:      1028200 kB 



32-bit (from cd)
real    0m38.715s 
user    0m38.702s 
sys     0m0.000s 
model name      : Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz 
model name      : Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz 
MemTotal:      1034432 kB

I'm hoping most of the above will be sorted when I get the extra 1GB, but I would have thought 1GB is sufficient for Ubuntu.

I might stick with 64bit to see if these issues iron-out, but I'm wondering if maybe the 32-bit install would suit me better. I generally don't run anything too cpu-draining anyway.


YES! I see this too with x64 but not with x86. Also see artefacts when heavy graphics apps open/close or are repainted. This is particulary bad with firefox and gimp. Sometimes drawing the menu bars from the panel results in artefacts as a panel menu appears/closes. Most strange.

This doesnt happen in any other distro Ive used (Wolvix, Dreamlinux, Gentoo, Vector, DSL, Slack, Mandriva, PClos, Etch, Fedora, Zenwalk)  - just ununtu x64 

I doubt whether we have similar spec machines so could this be an issue with x64 ubuntu - I am certainly minded to conclude so. 

I've no ideas where to start debudgging or even if I should given my concerns over x64 anyway.

---

### Post by Jouke74 on 2008-03-18
YES, i am sorry, but I am one of those guys who won't reply if he does not know what he's talking about. :lolflag: I also don't want everyone to start burning CD's now... The point is alreeady clear. Time for a good Benchmark.

---

### Post by keratos on 2008-03-18
> **Jouke74 said:**
> YES, i am sorry, but I am one of those guys who won't reply if he does not know what he's talking about. :lolflag: I also don't want everyone to start burning CD's now... The point is alreeady clear. Time for a good Benchmark.

I hope I have not insinuated that people dont know what they're talking about - I only merely wished to recognise that I agreed with you and we're on the same page.

Yes - time for a objective and rationaled benchmark, is there such a toolset in existence and available, that we could all agree on I wonder?

---

### Post by Jouke74 on 2008-03-18
Hi Keratos, no insinuations taken, just funny to read your subsequent posts. My excuses for the earlier reply, which was a bit insinuating people replying and not knowing what they are talking about. Obviously you do, I guess we addressed the TS post with a different angle in the beginning.  

I don't know about a good linux benchmark tool.

I use glxgears as a benchmark for my videocard, I don't know how it relates to X server. Although it is explicitly stated that it is also not a benchmark. The reason is obviously, that when you resize the window it gets different results already, and therefore it cannot be compared between computers.

For Disk IO you can use: 
"sudo hdparm -tT --direct /dev/sda"

Run that one also twice, as the second time the cached read will go better.

As a benchmark tool current days I guess you want to have a tool which does this things also simulateneously.

---

### Post by keratos on 2008-03-18
Ahem

glxgears is a reasonanle starting point I think, for glx performance through X. fglxr* and alike are also a good starting point. In my view a decent benchmark would incorporate a series of such acute tests rather than rely entirely on a specific focused test.

Incidentally, hdparm only tests sequential reads. It is highly unlikely that a "typical" desktop environment would be utilising the disk in this way. More realistic, is it not, is for the disk access to be random indexed access for which head movement over the platters and thus seek times would be far greater than that given in a sequential (and cached read).

However I would conceed that something like video conversion where a stream of data is input/read sequentially might be suitable for hdparm benchmarking, however I am sure that during the process, access to other files and libs would inevitably require indexed random access and thus invalidate hdparm benchmark.

If we look at disk IO I would suggest the following non-exhaustive list of factors need to be considered:

indexed random access (fragmented blocks)
indexed sequential access (fragmented blocks)
serial access (contigous blocks) - this is what hdparm measures if I'm correct?
buffered IO
non buffered IO
cached IO (disk cache)
cached IO (kernel buckets/cache)
swap page activity (dirty & clean)
no swap.

etc.etc.

---

### Post by keratos on 2008-03-18
This may have reasonably scientific provanance ...
[http://www-zeuthen.desy.de/technisches_seminar/texte/amd64_znsem.pdf](http://www-zeuthen.desy.de/technisches_seminar/texte/amd64_znsem.pdf)

Of course it would mean that I was completely wrong !!!

---

### Post by fjgaude on 2008-03-18
> **keratos said:**
> This may have reasonably scientific provanance ...
[http://www-zeuthen.desy.de/technisches_seminar/texte/amd64_znsem.pdf](http://www-zeuthen.desy.de/technisches_seminar/texte/amd64_znsem.pdf)

Of course it would mean that I was completely wrong !!!

Historical data, no longer true, what with the Intel Core 2 chips... <sigh>

AMD is in a bind to catch up.

---

### Post by kaivalagi on 2008-03-18
You can install hardinfo from the repo's, it's still not a good overall benchmark test, all computational, but it does have some variety which may highlight strengths/weaknessnes between the distro's...? Screenshot attached

Maybe the only real benchmark would be the use of the same version app, for a set piece of work, which uses all system areas...what would accomplish that on the livecd? Maybe a script with a set amount of command line tasks which covers all areas, and a simple time difference to start?

---

### Post by Jouke74 on 2008-03-18
When you type "linux benchmark" in Google there are quite a few hits. Mostly indicating that there is no good program. There are some programs, but these are still counting 486 processors as the best possible. "Bonnie" looks promising, as well as "Linux Benchmark 4.01". Anyway, I'll leave it to this. My PC is running fine and it won't go faster after benching.  :)

---

### Post by kaivalagi on 2008-03-18
I've played with Bonnie (no pun intended) and it's okay, it would be nice to have an all round tool though...something I'll be keeping a look out for now :)

Good luck keratos

---

### Post by keratos on 2008-03-19
Dang, I'll just live with it

:-)

Thanks for the feedback guys.

---

### Post by BIGtrouble77 on 2008-03-19
Wouldn't rendering a blender scene work as a good benchmark? The Elephant's Dream project has some very complex blender scenes that should tax the system a bit more than a scientific benchmark would.

The problem is that I don't know if Blender is optimized for 64bit, or just a recompile.  I'm also not sure if the Ubuntu compile will utilize multiple cores.

---

### Post by kaivalagi on 2008-03-19
I think Blender would be a great benchmark, it might take a while though :)

Ideally I think we need something simple and fairly quick that can be run from a live cd and/or a usb drive, so that we can benchmark an os without installing it etc...

---

### Post by dacorr on 2008-03-19
I built my current system on a Shuttle base unit and stuck an AMD AM2 5400+ 64 Duel Core (FSB 1000mhz) 2GB 800Mhz DDR2 soon to be 4GB and 64bit ubuntu hardly touches well anything i barely use one core unless VM are running.

I have used 64 bit processors since the AMD Athlon 64 brick thing was out as the first 64bit processor. yeah then performance was somewhere near my ankles but with hardware now the performance is improving in leaps and bounds as processors and RAM get faster and larger not to mention cheaper its easier to build high end 64 bit computers now than it used to be.

---


---
title: "Lots of lag, ubuntu is turning into windows..."
date: 2008-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tsukasah on 2008-04-11
Yeah, title basically says it all. I don't know why but recently Ubuntu has been lagging alot, applications take longer than normal to load, it takes about 10 seconds to bring up the update manager, then as its starting up the computer completely lags alot. Firefox's screen turns gray and doesn't respond. Just... everything is going absurdly slow. It even takes awhile for me to close things out, and that makes my computer lag alot too. I'm a MAJOR multi-tasker and really need this lag to stop.

I'm on a custom built PC(my first one, im 16 years old :P). The motherboard is a gigabyte, i have an HD soundcard, Soundblaster Audigy something(Creative). Running on onboard graphics which is 128 or 256mb, not sure. It's Nvidia 6150 i believe it's called. My CPU is an AMD 64 dual core processor 4200+ 4.2ghz. I'm still somewhat of a nub when it comes to computer building but I know the terms and stuff. Oh, and I have 1gb of RAM as well. 

So is there anything I need to do to keep my computer faster? Something like defragment like windows has? I haven't really dumped out my internet files for a little over a week. I still need to keep the history though for my research paper. So yeah, anything I can do to fix this problem?

---

### Post by Half-Left on 2008-04-11
Look at the system monitor or type top in the terminal and see if anything it using up alot of CPU.

If you can post a screenshot of your top output while it's lagging that would be great.

---

### Post by Guilden_NL on 2008-04-11
Half-Left is right, this will help us understand what's running on your system.

My guess is that you may have file indexing going on in the background.  Did you perhaps turn it on with Beagle, Google Desktop (a real resource hog!) or the default under System\Preferences\Search and Indexing?

Here's an example of TOP output. It's lined up and formatted in a terminal window:
top - 10:58:43 up 21:16,  2 users,  load average: 0.07, 0.08, 0.06
Tasks: 131 total,   1 running, 130 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.1%us,  0.5%sy,  0.0%ni, 96.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3356040k total,  2958672k used,   397368k free,   449860k buffers
Swap:  1261060k total,        0k used,  1261060k free,  1906956k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                         
 5708 root      20   0  163m  62m  10m S    3  1.9   9:36.03 Xorg                            
 6163 NL     20   0  264m  35m  13m S    2  1.1   9:48.95 compiz.real                     
17207 NL     20   0  263m  25m  11m S    1  0.8   0:00.38 gnome-terminal                  
16934 NL     20   0  532m 122m  26m S    0  3.7   0:46.01 firefox                         
    1 root      20   0  5168 1996  592 S    0  0.1   0:00.92 init                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                     
    4 root      15  -5     0    0    0 S    0  0.0   0:00.06 ksoftirqd/0                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                     
    7 root      15  -5     0    0    0 S    0  0.0   0:00.12 ksoftirqd/1                     
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                      
    9 root      15  -5     0    0    0 S    0  0.0   0:00.48 events/0                        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.32 events/1                        
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                         
   46 root      15  -5     0    0    0 S    0  0.0   0:00.02 kblockd/0                       
   47 root      15  -5     0    0    0 S    0  0.0   0:00.04 kblockd/1

---

### Post by Tsukasah on 2008-04-11
Here's some screenies, I took them at the times i saw it jump most. Alot during Totem movie player. I pressed Print Screen a number of times, but only 3 showed up. Lag again. Oh, also I noticed that when I'm browsing my system files/folders/what ever the computer lags alot then. The only program taking up alot of CPU power is Firefox... which is only in double digit megabyte size.

[http://i114.photobucket.com/albums/n250/12ed_XIII/Screenshot3.png](http://i114.photobucket.com/albums/n250/12ed_XIII/Screenshot3.png)
[http://i114.photobucket.com/albums/n250/12ed_XIII/Screenshot2.png](http://i114.photobucket.com/albums/n250/12ed_XIII/Screenshot2.png)
[http://i114.photobucket.com/albums/n250/12ed_XIII/Screenshot1.png](http://i114.photobucket.com/albums/n250/12ed_XIII/Screenshot1.png)

It takes 1.5 seconds to switch tabs in mozilla, and then another 2 seconds for me to be able to type in this box. I sware this is ALMOST  as bad *** windows usually does for me, almost....

Grr.. firefox completely froze up. Also, restarts do nothing. Nautilus and Firefox are the only programs running at all. Well I gotta scram, I'll be back to see your replies in a couple hours or so :/ Thanks, I'll try typing top in the terminal first i suppose. here's a screenie:

[http://i114.photobucket.com/albums/n250/12ed_XIII/Screenshot4.png](http://i114.photobucket.com/albums/n250/12ed_XIII/Screenshot4.png)

---

### Post by Half-Left on 2008-04-11
Is that after a fresh reboot?, your using alot of memory and your in swap thats why it's lagging.


Ok, compiz is the problem, turn it off or kill it and then restart compiz and see if it's still taking up aloads of memory. It's compiz.real thats lagging your system out.

---

### Post by ianhaycox on 2008-04-11
I had a similar problem with everything running very slow and Firefox was terrible. It turned out to be Compiz and some problem with my NVidia 6200 drivers.

To confirm turn off Advanced Desktop Effects (set it to None). You might need to log in again and confirm it's turned off. Doing this for me returned performance back to super fast again.

Bad news is I can't remember how I fixed it except that I installed/re-installed/deleted... various combinations of NVidia drivers etc. and now everything works fine with no lag and desktop effects on.

---

### Post by Half-Left on 2008-04-11
Disable compiz until you get updates for it or try it again on the next round of updates.

---

### Post by Tsukasah on 2008-04-11
> **Half-Left said:**
> Is that after a fresh reboot?, your using alot of memory and your in swap thats why it's lagging.


Ok, compiz is the problem, turn it off or kill it and then restart compiz and see if it's still taking up aloads of memory. It's compiz.real thats lagging your system out.

What do you mean i'm using alot of memory and i'm in swap? I realized im using alot of memory but please tell me what swap is.

And how do I disable compiz? I'm still a nub with ubuntu x.x

---

### Post by Half-Left on 2008-04-11
> **Tsukasah said:**
> What do you mean i'm using alot of memory and i'm in swap? I realized im using alot of memory but please tell me what swap is.

And how do I disable compiz? I'm still a nub with ubuntu x.x

When you run out of main ram memory it uses a part of your hard drive for memory which is many, many times slower. So if you start a application up while your using swap it will start much slower.

Right click on the desktop--->Change Desktop Background--->Visual Effects and select the None option. This will stop compiz.

---

### Post by bford16 on 2008-04-12
Chiming in:

I also build my own computers (I'm on my third), and I have been using Ubuntu Linux for just over a year.  I have an Asus A8V-VM motherboard, with an AMD 64 X2 3800 (which actually only runs at 2.0 Ghz max).  I had several problems with this motherboard; CPU-frequency-scaling kept crashing, the Ethernet card's IRQ kept falling asleep ("nobody cared" errors), and slow performance to boot.  Solving the ethernet card problem was easy.  I just grabbed one out of another computer, and the problem went away.

The other two problems had the same cause.  I was using an NVidia 6200 LE video card with only 256 MB RAM.  It was sharing RAM with the motherboard (I have 2GB).  This was degrading performance, and causing the CPU frequency scaling to crash.  I upgraded to an NVidia 8400 GS, and now everything works fine.

Now my computer stays up for weeks at a time, and I can use Compiz without any problems.  I am eagerly awaiting the new Hardy Heron (8.04) release.  I plan to switch from Gnome to KDE on my main computer, just for something different.  I already use Xubuntu on my second machine.  Wish me luck!

---

### Post by autowiz on 2008-04-14
I heard compiz sometimes make the problem(etc. memory leak).

And, I recommand add 1GB RAM.

I don't know what program is used to your multi-task,
but, in many case 1GB is so small.

Just I think so. have a good day~

---

### Post by PmDematagoda on 2008-04-14
> **autowiz said:**
> I heard compiz sometimes make the problem(etc. memory leak).

And, I recommand add 1GB RAM.

I don't know what program is used to your multi-task,
but, in many case 1GB is so small.

Just I think so. have a good day~

1Gb isn't really small, I use it on my PC along with full graphics on Compiz and a few other memory intensive applications like Firefox and they work perfectly, granted there are times when I feel that the amount of RAM I have is rather low but those times are very rare.

---

### Post by articpenguin on 2008-04-14
I had 2GB in my computer before and i noticed no difference in speed except when playing flightgear. I had to downgrade to 1GB after upgrading my sempron CPU to X2 my computer was a more fast although the speed increase was a result of my new x2 cpu.

---

### Post by crjackson on 2008-04-14
> **autowiz said:**
> I heard compiz sometimes make the problem(etc. memory leak).

And, I recommand add 1GB RAM.

I don't know what program is used to your multi-task,
but, in many case 1GB is so small.

Just I think so. have a good day~

1GB is PLENTY.  If the system is working fine otherwise it will FLY with 1GB.  I have 3 machines in front of me right now with only 512MB and they fly.  The machine I using right now has 2GB and it's no faster than one of my identical machines running only 512MB unless I'm dong video editing and encoding files.

---

### Post by digger95 on 2008-04-14
> **autowiz said:**
> And, I recommand add 1GB RAM... I don't know what program is used to your multi-task,
but, in many case 1GB is so small.
Good grief, if 1GB of RAM is too small for Ubuntu, then we might as well call it Vista.

---


---
title: "Need for speed"
date: 2008-08-13
forum: x86 64-bit Users
---

### Post by Flag on 2008-08-13
OK, OK, I know there are a lot of posts regarding speed and I think I read, tried most of them.
I'm running Ubuntu 8.04, 64 bit on an Acer Aspire 7520, which is fitted with 2gig of RAM and 120gig harddisk in four partitions :
sda1=boot, sda2 and 3 are abt 20gig each, one is used for the present OS, the other is used for the upcoming one, so on sda4 is Ubuntu 8.04 installed, sda2 is void ( reserved for the upcoming beta). sda3 is the home partition.
Speed : From grub to login 40 secs, from login to working desktop 50 secs., clocked.
To improve this tried : readahead ( thanks jdong ), preload, profile, plus a number of tweaks found.
Whatever I try above mentioned times remain the same.
After a fresh install and all updates installed I noted to my surprise that my desktop background loads first then after 15 secs the applications are loaded, Microsoft way.
I think these times are far too slow, especially as the 2gig RAM present is NEVER fully used, max abt 800 MB is used. 
Isn't there a way to call on all this unused RAM to speedup booting, cq. loading Gnome ?
Like I said tried, but to no avail.
Any suggestions, are welcome.
rgds.

---

### Post by kerry_s on 2008-08-13
first, with only 2gig ram you really don't need to use the 64bit version, it's just adding a bit of extra processing to run 32bit programs on 64bit compatibility.

the slow desktop startup is a gnome-session quirk, i'll try and talk you through it, but i'm not sure i remember everything i did.

1. goto preferences> sessions> startup, disable all of them

2. log out and back in

3. open the session settings again, click "save current session", now look at the current session to see whats running, in startup, enable what ever is not already running.

4. now log out and back in, hopefully it will be faster.


theres nothing you can or should do about ram use, linux only loads what you actually use, trying to preload only adds to startup time and a slower feeling.

---

### Post by Flag on 2008-08-13
Well.. thanks for this, it was something I hadn't tried yet, but ..... situation is the same, though to mu surprise everything loads normal.
Yes I do realize I actually don't need a 64 bit OS, but my thoughts were it would help optimize RAM usage, like I said before at this moment the system never uses more then 800 MB, so there is actually no benefit in investing money in more RAM.
It's a pity as I have to boot and exit this laptop a nimber of times daily and I feel a bit weird when a colleage starts his XP machine, sam model as mine, and has it running ( not just the desktop ) while mine is still loading Gnome.
Anyhow thanks.

---

### Post by Flag on 2008-08-13
Oh, typing fast causes errors

---

### Post by Thelasko on 2008-08-13
> first, with only 2gig ram you really don't need to use the 64bit version, it's just adding a bit of extra processing to run 32bit programs on 64bit compatibility.
What?  That makes no sense.  What 32bit programs are loading during startup?  NONE!

The bottleneck in Flag's startup is either the processor or the hard drive.  I don't know what you can do about the processor.  I suppose there are some hacks, but I'm not that interested in boot time.  But there are some high performance hard drives on the market, [but they will cost you.]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822332004")  I also don't know about their compatibility with your system.

---

### Post by Thelasko on 2008-08-13
Woops, I missed the fact it's a laptop.  Laptops tend to have even slower hard drives than desktops.

You say your colleague's laptop is identical and still boots faster?  You can try installing BUM.  You can use this program to shut off hardware checks you don't need at startup. If you really need to beat your friend at bootup, run Xubuntu.

I wonder if your colleague is using some tricks with XP.  Service pack 1 boots faster in my opinion (I never really timed it).  Running without a virus scanner will also make it faster.  Your colleague might also be using hibernate instead of a complete shutdown.

---

### Post by Flag on 2008-08-13
Thanks you as well, all reactions are welcome. I tried BUM, but I doubt if disabling some things will make a huge difference, obviously the ones I certainly won't use are disabled.
My friend runs on the twin of this laptop XP by P***ck,SP 2 which is a stripped down XP version,with AGP, and no complete off and on, no hibernating,  but still......, I run the same version under VM with only 768 MB Ram assigned, it's slow OK, but reasonable for an OS under VM but not much slower then my Ubuntu 8.04 to boot.

---

### Post by kerry_s on 2008-08-13
> What? That makes no sense. What 32bit programs are loading during startup? NONE!

most programs are 32bit so it's working through compatibility, which basically are extra steps more resources, etc...

> The main disadvantage of 64-bit architectures is that relative to 32-bit architectures the same data occupies more space in memory (due to swollen pointers and possibly other types and alignment padding). This increases the memory requirements of a given process and can have implications for efficient processor cache utilization. Maintaining a partial 32-bit model is one way to handle this and is in general reasonably effective. In fact, the highly performance-oriented z/OS operating system takes this approach currently, requiring program code to reside in any number of 32-bit address spaces while data objects can (optionally) reside in 64-bit regions.

Currently, most commercial x86 software is written in 32-bit code, not 64-bit code, so it does not take advantage of the larger 64-bit address space or wider 64-bit registers and data paths on x86 processors, or the additional registers in 64-bit mode. However, users of most RISC platforms, and users of free or open source operating systems have been able to use exclusive 64-bit computing environments for years. Not all such applications require a large address space nor manipulate 64-bit data items, so they wouldn't benefit from the larger address space or wider registers and data paths. The main advantage to 64-bit versions of such applications is the ability to access more registers in the x86-64 architecture.

---

### Post by Flag on 2008-08-14
Yeah, I've read this as well, but still decided to install a 64 bit OS, the additional memory requirment doesn't bother me, as like I said before, Ubuntu uses at best 40 % of the total RAM present.
It's my laptop I want to increase speed at, the dektops don't have any priority, these are switched on in the morning, boot while you're heading for the coffee machine, and are shut down in the afternoon, don't care how long they take to boot.
Tried Xubuntu in the past, had it running the same stuff I'm using now, but I wasn't imperessed.

---

### Post by Thelasko on 2008-08-14
I don't know where you read that, but most of what you posted doesn't apply.  The only part that applies is:
> However, users of most RISC platforms, and users of free or open source operating systems have been able to use exclusive 64-bit computing environments for years. Not all such applications require a large address space nor manipulate 64-bit data items, so they wouldn't benefit from the larger address space or wider registers and data paths. The main advantage to 64-bit versions of such applications is the ability to access more registers in the x86-64 architecture. [ Here is the correct info.]("http://en.wikipedia.org/wiki/X86-64#Operating_mode_explanation")

Programs on 64-bit Ubuntu have been recompiled to take advantage of 64-bit.  The 32-bit issues you mention is basically only applies to Windows (with a few exceptions, Flash mostly)

---

### Post by Jouke74 on 2008-08-14
1. You are using preload and prefetch. This will slow down the boot and make it "Windows style", as your most frequently used programs are pre-fetched during boot. In other words, more data is being read to be ready in memory. The speed advantage comes when starting the programs, NOT during boot. If you want a faster boot, but slower system when loading programs for the first time, remove these tools!

2.1 You cannot use RAM to make your boot times faster. The RAM is emptied everytime you shutdown the computer. 

2.2 An exception might be to use hibernation, where everything what is loaded into Ram is put on your swap partition (needs to be at least 2 GB). Restoring from hibernation goes a bit faster than shutdown and reboot (in XP at least) I think because all data is read from 1 file.

3. To speed up the system still, if not done before you can use boot Profiling. Edit the grub startup kernel line and add "profile" (without quotes) to the sequence. Don't save the line but let it boot with this option. This boot will go very slow, because now it will sort of defrag all Linux boot files to be read after each other. On subsequent boots, the bootspeed should be increased. Don't save or leave the "profile" in the kernel line, otherwise it will be slower since profiling / file rearrangement will be done each time you boot.  

4. 64 bit or 32 bit should not matter in speed when running (64 bit could be faster). However, with loading I am not so sure. The filesize of 64bit executables and libraries seems bigger at least with the few files I checked. Furthermore, you won't need to prefetch ia32-libs and wrappers so yes 32bit might LOAD a bit faster.

5. All the time you spent with this tweaking, has probably already far exceeded the time you gained by increasing the boot & run speed of your laptop.

6. Ubuntu vs Xp boot is an unfair comparison.

---

### Post by Thelasko on 2008-08-14
> Furthermore, you won't need to prefetch ia32-libs and wrappers so yes 32bit might LOAD a bit faster.
The only thing that will "LOAD" faster is Flash.

---

### Post by Flag on 2008-08-14
Well, all, thanks for your comments.
Will give Xubuntu another go, it simply, in my opinion should at least be comparable to the boottimes XP is setting down, I do know some people say you can't compare and to a certain extend I do agree, but the bottomline is : " A " computer needs " An " OS. The fastest OS is not always the best for a certain person with his personal needs / likings, agreed. On the other hand we're all, I am at least promoting whatever Linux distro and I surely would like to show some people that this Linux box can also beat WS with speed and not just the " it's free " slogan.
Thanks again and rgds to all.

---

### Post by Jouke74 on 2008-08-14
If course, if you really want speed you can also start with Arch-linux, Gentoo or build a distro yourself from a Ubuntu server install... :)

---

### Post by Thelasko on 2008-08-14
> **Jouke74 said:**
> If course, if you really want speed you can also start with Arch-linux, Gentoo or build a distro yourself from a Ubuntu server install... :)

Yeah, every Gentoo user I have ever heard of is obsessed with speed or being on the bleeding edge.  Be prepared to spend **a lot** of time setting up your system though.

---

### Post by jerome1232 on 2008-08-14
Note you are comparing XP, a what 9 year old OS, to 8.04.1. A barebones installation of XP will be faster than 8.04. Although XP is usually bloated with gadgets and gawhozets galore. Try and beat Ubuntu boot times while running vista ;)

Personally my 2.8 ghz dual core 3 gigs of ram computer with vista is marginally slower than my 2.4 ghz single core 1 gig of ram with 8.04.

---

### Post by Flag on 2008-08-15
Yeah, the issue is that part of my friends run a computer and as long as their basics work they don't care, some are digging a bit deeper and then the discussion starts sooner or later which OS do you prefer and why. One of them is a fervent XP user, no mentally sane person will by Vista with a computer build around it, and myself. He's using pretty up to date versions of XP, OK not the official ones, but with all features, if wou want. I'm using as basis Ubuntu, as it easy to install, also tried Fedora, Suze bit I'm stuck now with Ubuntu, or at this very moment Xubuntu. For am discussion DSL or Puppy don't qualify, though they are faster, they need a lot of work.
I still think this 2 x 1,7 ghz / 2 gig RAM machine should do better with Ubuntu, but I'm beaten, don't know what to try next within Ubuntu, because that's the issue. The time I spend on this is not wasted in my opinion as it is not a must but more something like a hobby, this as info for Jouke.
rgds

---

### Post by Duckyspetrie on 2008-08-15
Delete my account!!!


Delete my account!!!


Delete my account!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Jouke74 on 2008-08-15
Hi Flags, sorry did not want to offend you. It was also sort of my hobby during the Edgy-Gutsy times. I got much more speed with Arch linux, but wasted too much time on getting everything to run. Gentoo? The :) was not there for nothing... 

Debian is also a bit more faster by the way, and is very similar to Ubuntu (yet also very different). Ubuntu is a great distro when you don't want to tinker with hardware and get it going as much as possible straight after install (exceptions there).

I hope you tried my "Profile" tip already because it saved much boot time on my PC. 
And I assume you have done this already: [http://lifehacker.com/software/feature/slim-down-and-speed-up-linux-333798.php](http://lifehacker.com/software/feature/slim-down-and-speed-up-linux-333798.php)

Another killer of speed I noticed is Compiz. Of course, many people like the effects, including myself, but without that running things in Gnome speeds up.

---

### Post by grndrush on 2008-08-15
Another thought (from an old mainframer who still thinks like one sometimes):

While fragmented filesystems and needless daemons being initiated at boot will slow it down and need to be combated rationally, note many things which happen at boot time (the preload example above is a trivial but real example) do so to save time later. This was once considered the PREFERENCE - on multi-million $$$ machines that (hopefully) rebooted a couple of times a week. In that world, adding 2-3 MINUTES to the boot process (for a large-scale, multi-user machine, no less) in order to shave 5-10% off (in particular) terminal response times (EVERY response, to EVERY device, for several DAYS), was considered a stroke of genius! LOL...

My guess is most time-consuming (even minor) activities that occur at boot today are either to make a critical component available quickly, or to save time later on. I doubt we'll be able to shave much more than a few seconds off as long as we're saddled with the current BIOS infrastructure...   :(

---

### Post by Yellow Pasque on 2008-08-15
You can speed up boot time by compiling your own kernel and removing all of the extra features you don't need, customizing the kernel for your architecture, etc.

[https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way](https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way)

---

### Post by Flag on 2008-08-15
Jouke, I was not offended, just tried to make myself clear, I like to do these kind of things, other people do other things.
As for compiling my own kernel, I bookmarked your link and will try it someday on a spare computer which I only use for these kind of things.
Again thanks to all for the reactions.

---


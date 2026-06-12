---
title: "What are your reasons for Upgrading to Edgy?"
date: 2006-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kilz on 2006-10-26
I have looked at the spec's and don't really see a compelling reason to move to Edgy. I am thinking I must be missing something. Do you have a real good reason for wanting to run edgy or is it just the hype and the old "must have the latest" thing that makes you want to upgrade?
For those that are listing a specific feature. Please list the exact feature. Not a group of things like updated packages, or bug fixes. But the specific package that was updated, or the bug the fix fixed. For those listing Gnome 2.16. What feature of 2.16 do you think is the reason for switching

---

### Post by ilushkin on 2006-10-26
i upgraded my desktop to 6.10 but will leave my laptop running 6.06. 
a) i didnt like edgy's start up screen where all start up processes are hidden
b) i didnt like resseting video drivers for my ati card
c) im afraid that i will have probles with ndiswrapper and/or with my wireless card
d) i can get mozilla 2 from mozilla.com if i want too. dont need edgy for that

---

### Post by fabertawe on 2006-10-26
Well that was quite painless :D 

It's like nothing changed, so why not ;) I did get an error right at the end informing me to report it but I rebooted fine and everything is great!

Even when using Windows in the old days when you could easily and quickly re-install '95 or '98 (ok, maybe not that quickly), I got some sort of perverse pleasure from just 'fiddling' (even defragging!)... so yes, I must have the latest version 'just because' ;) There's always that nagging doubt in the back of my mind that I **might** be missing out on something :rolleyes: 

If you enjoy computing then it's all part of the fun :mrgreen: 

Paul

---

### Post by kuja on 2006-10-26
> **ilushkin said:**
> i upgraded my desktop to 6.10 but will leave my laptop running 6.06. 
a) i didnt like edgy's start up screen where all start up processes are hidden
b) i didnt like resseting video drivers for my ati card
c) im afraid that i will have probles with ndiswrapper and/or with my wireless card
d) i can get mozilla 2 from mozilla.com if i want too. dont need edgy for that
I heard in some other thread that you can change this behavior by removing the quiet option from the kernel line in /boot/grub/menu.lst, not sure if that's true.


Anyhow, I have my reasons for upgrading to Edgy.
- LIRC is less problematic in Edgy, though I must say the installation process for it could use some serious usability work.
- It's lovely to see a hardware database tool too.
- An ugly problem with QTDesigner is fixed in Edgy
- sudo support in kdesu is nice
- Among other things, it's nice seeing faster, more stable software too. KDE gets better with every release :)

---

### Post by fabertawe on 2006-10-26
> **kuja said:**
> I heard in some other thread that you can change this behavior by removing the quiet option from the kernel line in /boot/grub/menu.lst, not sure if that's true.

That's actually one of the first things I did ;) I need to know what's going on!

Paul

---

### Post by HeresJohnny on 2006-10-26
I'd like to try it out to see whether CJK input methods work better in my two primary programs, FF and OOo.  Right now, the only other program I use everyday that allows Korean input is Evolution.  Hope I don't have to go through all the steps with ndiswrapper and figuring out the video drivers.  I still don't have Wine working 100% yet, either.  Might as well try the new thingy.:mrgreen:

---

### Post by Bionic_Beefpile on 2006-10-26
For me, upgrading to Edgy fixed a few annoying bugs with the old version of gnome and OpenOffice.  It also improved performance across the board, and also fixed (on its own) a few of the minor hacks I was running to get full functionality from my system.

---

### Post by Blender on 2006-10-26
My reasons:
- AIGLX
- Firefox 2.0
- GNOME 2.16
- Overall updated packages, bugfixes, etc.

---

### Post by Relain on 2006-10-26
I'm just thinking about doing it now. I put edgy on my laptop and i like it quite a lot, mr laptop has a dual core chip and was running a dapper kernel with 686-smp support etc. Edgy seemed to object quite highly to any kind of kernel specialization and i'm now on the generic kernel again. Well that's ok because i don't think there were any build specific implications (does that even make sense?). 

But i'm slightly concerned that my desktop, which is happy on the 2.6.15-27-amd64 with SMP is going to get borked down to a generic kernel. Making all my 64bit apps : matlab, amira, intel compiler etc somewhat broken?  Can anyone tell me if this happens? 

I was lurking on the devel list for quite a while and they seemed to be indifferent at best towards the 64bit line of things. 

Well if it dies i guess it's gentoo time!

---

### Post by IYY on 2006-10-26
I want the new Gnome, new Gaim and new Firefox. Of course, I am already using them in Dapper, but I'd like it to all be official, properly configured and in the main repos (or installed by default, which is the case here).

---

### Post by cafg10 on 2006-10-26
I made programs with gtk+ and the printing support included on 2.10 is exists only on Edgy, aside of the improvements of the LIRC (have a TV turner) and some other stuff like gnome 2.16 and firefox 2 (which newer cache features have astonished me)

---

### Post by kuja on 2006-10-26
> **Relain said:**
> I'm just thinking about doing it now. I put edgy on my laptop and i like it quite a lot, mr laptop has a dual core chip and was running a dapper kernel with 686-smp support etc. Edgy seemed to object quite highly to any kind of kernel specialization and i'm now on the generic kernel again. Well that's ok because i don't think there were any build specific implications (does that even make sense?). 

But i'm slightly concerned that my desktop, which is happy on the 2.6.15-27-amd64 with SMP is going to get borked down to a generic kernel. Making all my 64bit apps : matlab, amira, intel compiler etc somewhat broken?  Can anyone tell me if this happens? 

I was lurking on the devel list for quite a while and they seemed to be indifferent at best towards the 64bit line of things. 

Well if it dies i guess it's gentoo time!

You'll be changed to A generic kernel, a generic 64-bit kernel that is. Nothing should be broken.

---

### Post by Paul133 on 2006-10-26
Three reasons:
1. What's in feisty? Maybe it'll be worth upgrading to from dapper? You'll probably have to upgrade from edgy.

2. Whenever IU close my laptop, the GUI dies and I get no prompt. I do have a workaround, however, I switch to a non graphical terminal and then back (just hit shift F1 and then shift F7) I hope this is fixed in edgy. however. 

3. I also want to see what's up with the AIGLX they keep talking about. I dont have xgl/compiz but I'm considering it. Then I heard compiz forked and xgl is now xgl and aiglx? Now I'm confused, so I hope edgy can help me

-1. However, I don't want to reset my wireless and all my settings, so I think I'll stay with dapper until I know what the risks are.

---

### Post by Funzo22 on 2006-10-26
Well its true I would need to be on the latest software no matter what, and if it didnt work I would keep trying till I lost all my data and it worked!

But I read amazing reviews about the performance for edgy and also I love how it comes with beta software, it takes out the need to search for upgrades all the time for my betas.... also it is much much snappier for doing anything, plus I was just ready for a slight gui tweak to make it feel different!

but it was definitely worth it for the speed upgrade!!!

---

### Post by John Jason Jordan on 2006-10-26
> **Funzo22 said:**
> Well its true I would need to be on the latest software no matter what, and if it didnt work I would keep trying till I lost all my data and it worked!

But I read amazing reviews about the performance for edgy and also I love how it comes with beta software, it takes out the need to search for upgrades all the time for my betas.... also it is much much snappier for doing anything, plus I was just ready for a slight gui tweak to make it feel different!

but it was definitely worth it for the speed upgrade!!!
The performance reviews are enough to get me to upgrade. But I have tons of stuff installed and even more tweaks and things that would be a PITA if I had to do a fresh install. I mean, things like Crossover Office with Adobe and Microsoft products. When I tried to upgrade from Breezy to Dapper it totally broke my Breezy and I had to wipe out and start over. That was not fun. Furthermore, I'm a graduate student and I totally need this computer working. I can't afford to spend days fixing stuff right now. So my plan is to wait until December 7, when finals are over. By then all the fallout will be known and major problems should have been resolved. And I'll have the time to futz with it if I need to.

---

### Post by JAPrufrock on 2006-10-27
When I'm bored I like to fiddle, so when I get some time, I'm gonna setup a triple boot (XP, Dapper and Edgy).  That way I can edge into Edgy.

---

### Post by Magnes on 2006-10-27
The main reason I'll install Edgy is because it has newest versions of programs and libs. I need for example newest MonoDevelop.

---

### Post by frodon on 2006-10-27
Xorg 7.1 with built-in AIGLX support which neans beryl/compiz running without any limitations, it was enough for me to run the upgrade.

---

### Post by zero gravity on 2006-10-27
Firefox 2
10 sec faster boot
had already some bugs in dapper with beryl, needed a fresh install
liked the diskanalysator

---

### Post by Funzo22 on 2006-10-27
> **John Jason Jordan said:**
> The performance reviews are enough to get me to upgrade. But I have tons of stuff installed and even more tweaks and things that would be a PITA if I had to do a fresh install. I mean, things like Crossover Office with Adobe and Microsoft products. When I tried to upgrade from Breezy to Dapper it totally broke my Breezy and I had to wipe out and start over. That was not fun. Furthermore, I'm a graduate student and I totally need this computer working. I can't afford to spend days fixing stuff right now. So my plan is to wait until December 7, when finals are over. By then all the fallout will be known and major problems should have been resolved. And I'll have the time to futz with it if I need to.


This seems like a good strategy, basically as long as all your important data is backed up, its just time that can be lost in an upgrade, however I know if this was me I would probably just back up my stuff, and spend a little time convincing myself that nothing would go wrong and then do it... but that would be a bad idea :D

---

### Post by oblivion on 2006-10-27
I wanted to try AIGLX and it was quite difficult to find updated beryl packages in dapper.

---

### Post by rplantz on 2006-10-28
> **Magnes said:**
> The main reason I'll install Edgy is because it has newest versions of programs and libs. I need for example newest MonoDevelop.

Newest versions of libs turned out to be bad for me. I do some 32-bit development on my 64-bit system, and at least one (crucial) 32-bit header file got left out. Hopefully, there will be an update.

With Edgy I can now sync my Palm Pilot m100 with evolution.

My main reason is that I like to keep up with the latest stuff. And since I'm retired, it's mostly just fun for me.

---

### Post by pony-tail on 2006-10-28
There is this great feature in "edgy"
It actually detects my hard drives (4 of) in the correct order every time - unlike "dapper" which could not make up it's "mind" whether the first hard drive was sda or sdc (changed from boot to boot at random)
On my A64 (asus A8NSli-premium) It always detects the first drive as sdc !
Plus I just love completely screwed up xserver (I have a Radeon X850XT-PE )
Before anybody says to replace it with an nVidia - I replaced a pair of 6800gt cards that were in SLI with it because (1) they kept freezing during anything 3D - either singly or paired and (2) the Radeon was in my cupboard collecting dust (from a previous build that I scrapped out - a PressHot ) The SLI nVidias worked very well in windoze - so who knows (i will try them again with nVidias next driver release )

---

### Post by CyberAngel on 2006-10-28
I`ve already upgraded using dist-upgrade without any problem (So far at least I haven`t notified any).

I`ve upgraded my system because I want to be up to date (Especially my libs because if you want to compile many bleeding edge programs you need fresh libraries).

---

### Post by hajk on 2006-10-28
I like the Gnome 2.16 eye candy and find upstart an interesting technical advancement. But most of all, I wanted to do a fresh x86_64 install plus i386 chroot (my HD is large enough, my processor powerful enough, and my connection fast enough). Now I can run 32-bit versions of programmes that don't run (or don't run well) in the 64-bit host OS without those awkward and opaque work-arounds (yes Kilz...;)) and loving every minute of it.
Also installed Edgy in a Parallels VM on my MacBook, of course there I don't bother tweaking multimedia stuff, since OS X does all of that so well already.

---


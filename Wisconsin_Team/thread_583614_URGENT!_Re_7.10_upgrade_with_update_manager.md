---
title: "URGENT! Re: 7.10 upgrade with update manager"
date: 2007-10-20
forum: Wisconsin Team
---

### Post by rowanrook on 2007-10-20
Hello everyone, I want to give you a heads-up if you are considering 'upgrading' to Ubuntu 7.10 "Gutsy Gibbon" via the Update Manager. I strongly advise you not to, at least not at this point. I have just completed the process:evil::evil::evil:](*,)](*,)](*,), and now:
[LIST]
[*]My network connections (wireless, ethernet, even usb) are all nonfunctional.
[*]Upon boot-up the desktop gives me an "Internal error: HAL failed to initialize" message.
[*]My system hangs for long periods.
[*]My monitor display settings are screwed up and the Admin>Screen/Appearance app does not work.
[/LIST]
I have tried several suggested fixes for these problems (disable auto-login, change video drivers, edit Network settings) and so far none of them have worked. To summarize: my Ubuntu setup is now completely unusable and I don't know at this point if I will be able to fix it. I may do a reinstall from scratch at some point when I have time; probably that will erase all my current files and settings though.	](*,)

---

### Post by dsiddens on 2007-10-20
I posted of my disaster when following the prescribed update from feisty to gutsy.  (search dsiddens) At this time I am left with brick of a laptop.  I am definitely in the newbie class and am searching for explicit instructions to get back to a working computer with my /home intact.

---

### Post by lifewithryan on 2007-10-20
Man,

I"m sorry to hear that you guys both had trouble.  Currently my machine is a little over halfway through the process.

Did either of you get any messages during the upgrade?  (Warnings, errors, other wise?)

When you try to boot up, what happens??

Have you tried booting with a live CD?  If you can get a live cd up and running perhaps you can copy your important files to another machine or a DVD/CDROM and do a reinstall.  I know thats not always desirable, but if it mean you won't lose files, its always worth a shot.


We're here for ya :)
--Ryan

---

### Post by TH3_D0ct0R on 2007-10-20
last time I installed I didnt have to delete my files it asked me if i wanted to use the settings and files from the old account and I said yes...
so i dont know if you have to lose all you files...
I dont really know what will help all i can think of is the live cd...

and i did it thro the update manager 4 days b4 the release thinking what can they change in 4 days? and i just got the application updates two days which was fine...i havent had any problems other than a banshee crash here or there...so im sorry that it happened and that im no help

Th3 D0ct0R

---

### Post by mikeputnam on 2007-10-20
I cannot report any problems with an in-place upgrade from 7.04 to 7.10.  An HP 6230 laptop.   Works like a charm!

Mike Putnam

---

### Post by Ek0nomik on 2007-10-22
I was running Gutsy since Tribe 2 on my Server, and Tribe 3 on my Desktop.  I haven't upgraded my laptop yet, but I know that my wireless will become nonfunctional since I had to use ndiswrapper to load the drivers.

If you used ndiswrapped to get your wireless working, you will follow the same process you did before, but you will probably just need a newer version of ndiswrapper to handle the newer kernel.

As far as your video issues are concerned, you probably just need to get your drivers working.

> **rowanrook said:**
> I may do a reinstall from scratch at some point when I have time; probably that will erase all my current files and settings though.

Sometimes it seems people run into a lot of trouble with an upgrade rather than a fresh install.  Do you have an external hard drive or another computer you can store your files on?  There's no reason to have to lose any files that you want to keep.  :)  You can also backup settings for programs too if you wish.

---

### Post by lifewithryan on 2007-10-24
Hate to rub salt in the wound but everything went flawless for me as well...even got all the fancy effects and no crashes as of yet, but then again, i've rarely gotten crashes in anything ubuntu...

---

### Post by herteljt on 2007-10-24
I have had some issues with my radeon 9600 video card using 7.10.  I have found that booting kernel 2.6.17-11-386 resolves the issues.

---

### Post by AmyRose on 2007-10-25
I upgraded at the beta and had nothing but problems until I did a clean reinstallation a couple of weeks before the release.

---

### Post by PointyWombat on 2007-10-25
For what it's worth, I've upgraded four different boxes from fiesty to gusty, all with very different components via Update Manager and all went without issue.

---

### Post by lifewithryan on 2007-10-26
Has anyone heard back from rowanook or dsiddens on their predicaments??

Just wondering if they're getting help, etc.  They've never replied back as to whether they can even boot from a live CD etc...or what hardware they have and so forth...

---

### Post by Astrodan on 2007-10-26
I tend to agree that the Gibbon is a true monster.  I upgraded from Feisty about a week ago and still have problems.  The screensaver crashes my system when it activates.  Currently locked on the ANT Spotlight, and it will not let me access the settings to change it or disable it.  If I leave the machine for 10 minutes, it's instant lock out.

---

### Post by ag65151 on 2007-11-02
I had some issues with the update manager upgrade to Gutsy, but since I had /home on a separate partition, I did a clean install. (By the way, if you haven't moved /home to a separate partition from / I would suggest doing so with every stable system you have.) I had to reinstall some of my auxiliary programs, but over all, I am very pleased with 7.10

And I got the bonus of being able to run compiz and AWN to get some really fun eye-candy stuff. I could never get my video card to handle compiz on feisty. Overall, I am very pleased with Gutsy. 

My config: 
HP Pavillion ZE5500 laptop
Mobile Intel Pentium 4, 2.66GHz
Radeon IGP 340M Video card
BCM4306 Wireless card

Cool to have some other *nix users here. Nice to meet you all.

---

### Post by fred4444 on 2007-12-06
> **rowanrook said:**
> Hello everyone, I want to give you a heads-up if you are considering 'upgrading' to Ubuntu 7.10 "Gutsy Gibbon" via the Update Manager. I strongly advise you not to, at least not at this point. I have just completed the process:evil::evil::evil:](*,)](*,)](*,), and now:
[LIST]
[*]My network connections (wireless, ethernet, even usb) are all nonfunctional.
[*]Upon boot-up the desktop gives me an "Internal error: HAL failed to initialize" message.
[*]My system hangs for long periods.
[*]My monitor display settings are screwed up and the Admin>Screen/Appearance app does not work.
[/LIST]	](*,)

I jujst upgraded from a clean install of 7.04 to 7.10 and have identical problems as this user has describerd.  My solution was to reinstall from my 7.04 disc from scratch and not perform the upgrade to 7.10.  Its the only thing I could think of.  7.04 works fine.

---


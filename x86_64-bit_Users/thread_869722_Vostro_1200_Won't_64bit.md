---
title: "Vostro 1200 Won't 64bit"
date: 2008-07-25
forum: x86 64-bit Users
---

### Post by mr_skater99 on 2008-07-25
Hi All,

I bought a Dell Vostro 1200 back in April just as Hardy came out.  

At release time the 64bit version couldn't complete the boot process - so i could never install.  As i needed the laptop straight away i installed the 32bit version and have been using it flawlessly ever since.

I now however have a little time up my sleeve to try and get the 64bit version up and running for two reasons:

1. i have 4 gb of ram - and only 3gb is recognised by the 32bit version
2. because i can :)

Every time i try and boot the 64bit version it gets half to three quarters the way through and then the laptop simply reboots.  

I downloaded the fedora live cd 64bit to give it a go, and it did the exact same thing.  I also tried ubuntu 7.10 and it did the same thing too.  So it is obviously my laptop - but these forums have always helped me so much, so wanted to start my search here.

I've had a look in the bios - but there isn't anything i can change that would make a difference.  I also updated to the latest bios (A07), but it didn't make a difference either.

Any help/suggestions would be greatly appreciated.

Scotty
 - wanting to use 64bit -

---

### Post by felker2 on 2008-07-25
You are using the **8.04** 64-bit version, aren't you?

If so try these first analysises / long shots:
[LIST]
[*]In the boot options, have you removed the 'quiet' option? What's the last message you see on your screen (before it reboots)? 
[*]Have you tried the "safe graphics boot option"?
[*]Have you tried the always-safe-options "pci=nomsi irqpoll noapic acpi=off"
[*]Can you boot to a non-GUI setup? If so, the GUI is the problem
[*](Even longer shot): Try Intrepid just to see if that helps [http://cdimage.ubuntu.com/releases/intrepid/alpha-3/](http://cdimage.ubuntu.com/releases/intrepid/alpha-3/)
[/LIST]

HTH

---

### Post by mr_skater99 on 2008-07-25
Hi,

I am using 8.04 64 bit.

Have tried most of the options you listed - but will try again just in case i missed something.  

When i do a non-graphical boot - the funny thing is you can see it gets to a different stage before it reboots each time i try.  I will have to do it again to get the specific messages as i can't remember them off the top of my head.

Might give 8.10 a shot if i get a chance tomorrow.

Any other suggestions?

Cheers.

---

### Post by stchman on 2008-07-25
> **mr_skater99 said:**
> Hi All,

I bought a Dell Vostro 1200 back in April just as Hardy came out.  

At release time the 64bit version couldn't complete the boot process - so i could never install.  As i needed the laptop straight away i installed the 32bit version and have been using it flawlessly ever since.

I now however have a little time up my sleeve to try and get the 64bit version up and running for two reasons:

1. i have 4 gb of ram - and only 3gb is recognised by the 32bit version
2. because i can :)

Every time i try and boot the 64bit version it gets half to three quarters the way through and then the laptop simply reboots.  

I downloaded the fedora live cd 64bit to give it a go, and it did the exact same thing.  I also tried ubuntu 7.10 and it did the same thing too.  So it is obviously my laptop - but these forums have always helped me so much, so wanted to start my search here.

I've had a look in the bios - but there isn't anything i can change that would make a difference.  I also updated to the latest bios (A07), but it didn't make a difference either.

Any help/suggestions would be greatly appreciated.

Scotty
 - wanting to use 64bit -

The Vostro 1200 appears to have a Core 2 Duo processor so it is 64 bit capable.  I have a laptop with C2D and I run Hardy 64 bit no problem.

Were there versions that had a Core Duo (the Core Duo processors were dual processors that were 32 bit only)?

In the system monitor does Ubuntu identify the processor as a Core 2 Duo?

Let us know.

---

### Post by mr_skater99 on 2008-07-25
It's a Core 2 Duo - T7250.

Both cores show up in system monitor.

Cheers.

---

### Post by lavinog on 2008-07-26
Have you checked if there is a bios update?
I think if you use the alt install you can use ctrl-alt-F4 to see what is going on in the background during the install (use ctrl-alt-F1 to go back to the installation screen every now and then in case it needs user input)
try and figure out the specific part of the install that is causing a reboot.

---

### Post by Yellow Pasque on 2008-07-26
You can see the error messages with the LiveCD if you boot with nosplash.

---

### Post by mr_skater99 on 2008-07-27
Good news!

I have it booting consistently - by removing "queit splash --" off the boot options and adding "acpi=off".

I take it this means that my ACPI doesn't work with the 64-bit kernel? As it works fine under 32-bit.

What do people make of this?

Haven't installed yet - as a laptop without acpi support is a little useless (i think?).

Cheers

---

### Post by lavinog on 2008-07-27
> **mr_skater99 said:**
> Good news!

I have it booting consistently - by removing "queit splash --" off the boot options and adding "acpi=off".

I take it this means that my ACPI doesn't work with the 64-bit kernel? As it works fine under 32-bit.

What do people make of this?

Haven't installed yet - as a laptop without acpi support is a little useless (i think?).

Cheers
You may need to update your bios. Version A07 is the latest for your laptop.
[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R186991&SystemID=VOS_N_1200&servicetag=&os=BIOSA&osl=en&deviceid=18029&devlib=0&typecnt=0&vercnt=2&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=255874]("http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R186991&SystemID=VOS_N_1200&servicetag=&os=BIOSA&osl=en&deviceid=18029&devlib=0&typecnt=0&vercnt=2&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=255874")

---

### Post by mr_skater99 on 2008-07-27
Thanks lavinog, but i did the update to A07 a few weeks back.  Didn't help.

Any other suggestions?

---

### Post by mr_skater99 on 2008-07-28
If it helps at all, the vostro has the Intel®  GM965 Express chipset.

Anyone else having issues with this chipset and ACPI in 64 bit???

Cheers.

---

### Post by mr_skater99 on 2008-07-30
Could i raise this as a bug in launchpad?

---

### Post by mr_skater99 on 2008-08-13
Just as an update, i pulled one of the 2gb sticks out, and with just 2gb in there it booted fine and installed 64bit fine.  But once i put the 2nd 2gb stick back in the same thing - wouldn't complete the boot without resetting.  

What does this mean?

Cheers.

---

### Post by lavinog on 2008-08-13
See if there is an option for memory remapping in your bios.
There seems to be alot of issues with 4+gigs of memory.
my system was causing alot of issues with 4g of memory and the ati 8.6 driver...many people claimed that enabling memory remap fixed it, but I myself don't have that option...lucky for me the latest driver seemed to fix the issue.

enabling memory remap relocates part of the memory to another address space...this address space is only accessible with 64bit addressing...this will mean that if you are using a 32bit os you will only have 2 of the 4 gigs available, but you should have the full 4 gigs in 64bit mode.

---

### Post by mr_skater99 on 2008-08-19
Thanks for the suggestion lavinog, and sorry for the delayed response - work has been crazy.

Unfortunately like yourself i don't have that option in my bios, so its a no go.

Anything else i could try, anyone?

---

### Post by mr_skater99 on 2008-09-03
Hi Guys,

Still haven't had any luck with this.

Am i just stuck using a 32 bit OS and only 3gb of my 4gb of ram?

I really hope not....

---

### Post by lavinog on 2008-09-04
Does it do it with the live cd?
If so, does it do it with the Gutsy live Cd?
If no, we maybe able to narrow it down from the changes.

The problem is that it reboots when loading right? Most likely the load process too fast to see where it is rebooting at. If so maybe we can slow down the boot process.

I have yet to try this yet:

```
sudo nano -w /etc/init.d/sleepinit
```

copy this into it:
```

#!/bin/bash
WAITTIME=15

. /lib/lsb/init-functions

log_warning_msg "${0}: Waiting ${WAITTIME} SECS"

sleep $WAITTIME

exit 1

```

chmod it
```
sudo chmod 755 /etc/init.d/sleepinit
```

link it to the boot scripts 
```

sudo ln -s /etc/init.d/sleepinit /etc/rcS.d/S61-sleepS
sudo ln -s /etc/init.d/sleepinit /etc/rcS.d/S99-sleepS
sudo ln -s /etc/init.d/sleepinit /etc/rc2.d/S09-sleep2
sudo ln -s /etc/init.d/sleepinit /etc/rc2.d/S19-sleep2
sudo ln -s /etc/init.d/sleepinit /etc/rc2.d/S22-sleep2

```

In theory it should pause for 15 seconds at various steps in the bootup while showing the name of the link being executed.

I haven't tested it yet because I am in the middle of a download, but I will in a couple of mins. I will respond back if there is a problem


To go back to normal:
```

sudo rm /etc/rc2.d/S??-sleep2
sudo rm /etc/rcS.d/S??-sleepS

```

You can leave the sleepinit in /etc/init.d/. It wont affect the boot. To re-enable it you just have to re-link the file into rcS.d and rc2.d

If you want to remove sleepinit
```
sudo rm /etc/init.d/sleepinit
```

---

### Post by lavinog on 2008-09-04
Ok it worked on my system.
When you boot, do you have the ubuntu splash screen on? It will help to have that off.

---

### Post by mr_skater99 on 2008-09-04
It does it with the live cd, both gutsy and hardy.

I currently have 32bit 8.04 installed.  To do the changes you suggest i would have to pull the 2gb stick - install 64bit and edit the files you mentioned, and then stick the 2nd 2gb stick back in and boot.

I am a little hesitant to install 64 bit again - as if a fix can't be nailed down, i have to re-install again with teh 32 bit - like i did a few weeks ago.

Is it possible to edit the files in the iso for the live cd and then burn that?  So I don't have to reinstall to try what you suggest.

I really appreciate all of you help so far!

I'm also still perplexed as to why it boots fine with 4gb when setting "acpi=off"....

---

### Post by lavinog on 2008-09-04
You might be able to use isomaster to modify a cd image
if you don't have it already:
```

sudo apt-get install isomaster

```

---

### Post by mr_skater99 on 2008-09-04
Will give that try tomorrow and let you know how i go.

Again - thanks for all your help thus far.

---

### Post by mr_skater99 on 2008-09-07
Bit of an update/summary.

Booting 64bit 8.04:

No change to default options:     Reboot while trying to load all the stuff from the cd after choosing boot option (it starts to detect hardware and load stuff - then finds the cd and start to load things from there and reboot)

ACPI=off:     Boots to the desktop.  Recognizes all 4gb of ram - but no 2nd core on cpu, no battery, power options etc.

mem=4096:     Boots to desktop - everything looks as it should.  but only 3gb of ram!

So in essence i can get 64bit to boot and look like it should, but it only recognizes 3gb of ram - thus negating the main driver to run 64bit for me anyways, in the first place.

if i try and do a memory test from the inital boot menu - it detects 4gb (from bios im assuming) if i try and change it to probe the amount of memory - system hangs with a blank screen.

lavinog i tried your suggestion over the weekend - but am unable to edit the live cd (the cd is set up different to what its on a normal filesystem).  I'm not too keen on installing 64bit again just yet to try this.  

Thoughts?

---

### Post by lavinog on 2008-09-11
Does your video card share system memory?

Alot of people have been complaining about not being able to use the full 4gigs of memory with 8.04 64bit.
The memory remap feature of some bioses fixed booting issues, but users lost some memory doing it.

**It would look like the mem=4096 is your best option until 8.10 comes out.**
Yes, you won't be able to take advantage of that last gig of mem, but it looks like you won't have it with a 32bit kernel either.

At least with 64 bit installed you will be able to install updates that may fix the problem.
Have you tried testing the live cd for 8.10?

---

### Post by mr_skater99 on 2008-09-11
I have been trying each of the betas of 8.10 - but they're no different from 8.04  

I'll keep trying.  Sure it will work itself out in the end.

Thanks for all your help!

---

### Post by DrewM on 2009-08-25
Hi mr_skater99,

Did you have any luck running 32 bit Ubuntu?  I'm trying my very first install of Studio Ubuntu (9.04) on my Vostro1200 with the same processor as you.  I was curious if the driver problem i'm having was Vostro based.

Cheers.

---

### Post by mr_skater99 on 2009-08-26
I actually sold the vostro quite some time ago - sorry!

---


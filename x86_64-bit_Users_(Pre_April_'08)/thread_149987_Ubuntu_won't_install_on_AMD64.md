---
title: "Ubuntu won't install on AMD64"
date: 2006-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Nemesis2 on 2006-03-25
I tried two versions of Ubuntu: 

Breezy (original cd package sent from ubuntulinux.com):
 - it installs but while installing gnome-guide it shows up an error and does not install Gnome and the other missing packages which would install after gnome-guide

Dapper-Flights(4 and 5):
I cannot install these because the system does not react while choosing the install language. Maybe the Keyboard driver is not loaded properly but in the install menu choosing the install option (oem/server/etc) the keyboard works. 

System Specs:
 AMD64 3000+
 Gigabyte Nforce 4
 1024MB DDR RAM
 Gigabyte x800 256MB
 2x S-ATA HDD - no raid configured

---

### Post by Ubuntuud on 2006-03-25
Sorry for asking, but have you downloaded the 64bits version?

---

### Post by Nemesis2 on 2006-03-25
oh sorry I forgot to mention, yes the 64bit Version, both breezy and dapper.

---

### Post by stragee on 2006-03-25
I had the same issue just tryin to use the Ubuntu 5.1 Live CD.  It's almost as if the keyboard driver wasnt there.  All I got was the first splash screen asking me to hit F1 for advanced options or ENTER to continue.  I tried every key on my keyboard eventually and it completely ignored it.  

I've tried every version of Linux and never got any of them to even install.

---

### Post by Lonergan on 2006-03-25
I have installed Ubuntu, Kubuntu 3x each time using the 64 bit version.  I just plopped the cd in and let it do its thing. The only tweaking I needed to do for X was to go from the default nv driver to the nvidia driver.

I have:
AMD X2 4400+
Corsair TwinX 2GB (2x1GB) PC3200 C2 DDR Memory
ASUS A8N-SLI Premium nF4 s939
ASUS EN6800GT GEFORCE 6800 256MB PCI-E
2x SATA Maxtor 200 gigs

---

### Post by Nemesis2 on 2006-03-25
but this does not solve my problem ;)

---

### Post by maury on 2006-03-25
My System
System Specs:
AMD64 3200+
Gigabyte GA-K8NS
1024MB 2700 DDR RAM
N Videai 5200 128MB AGP
IDE 133mb  Runs 32 bit and 64 bit Ubuntu No problems

---

### Post by BoneKracker on 2006-03-27
Don't know what to tell you.

Athlon64 X2 4400+
A8N-SLI Premium (also nForce4)
TwinX 2GB (2x1GB) PC3200 C2 DDR Memory
7800GT 256MB PCI-E
Booting from 2x SATA-2 160GB RAID-0

You could try:
Install from the CD with the "server" option.
then layer on the rest from the mirrors, using apt 
[I]apt-get update
apt-get upgrade
apt-get dist-upgrade
apt-get ubuntu-desktop[/I]

If nothing else, this may help with fault isolation.

---

### Post by selina on 2006-03-27
I think im having the same problem.  I'm sorry I dont know too much about these things.  But uni here is kinda making us use linux to program.  So i took home the ubuntu version and chose to use live (cause i dont trust myself to install it without wiping everything out) but after everything loads and a brown screen with ubuntu appears it just freezes and my mouse no longer moves?  What should I do?  I can't do any work til I get this loaded.

---

### Post by Jason_25 on 2006-03-27
Post your hardware specs.  Also ctrl-alt-f1 to see if you can get to a virtual terminal.

---

### Post by selina on 2006-03-27
doesn't look like i can get a virtual terminal.

my specs are:
AMD64 3200+
1.99GHz, 1024MB RAM

dont know where else to find other information you want

---

### Post by henriquemaia on 2006-03-29
I had a similar issue when installing flight 5 amd64 on my box. What I did was to rerecord the CD (a rewritable), this time using the slowest speed of my recorder. It worked very well after that.

---

### Post by johnnymac on 2006-03-30
Your specs aren't too far off form mine and I'm not having any problems at all.  You may want to try and re-burn the CD your using at a slower speed....that may get you working.

---

### Post by bper on 2006-04-03
Sorry to jump in so late, but I just saw this post. I had some similar problems, but were able to resolve them.

What does it mean 'won't install'? At what point does it fail? Are you getting any messages? Does it read the CD?

---

### Post by NewbieNik on 2006-04-03
[QUOTE=henriquemaia]I had a similar issue when installing flight 5 amd64 on my box. What I did was to rerecord the CD (a rewritable), this time using the slowest speed of my recorder. It worked very well after that.[/QUOTE]

Hit one of the nails direct on the head. Most of my install issues in the past have been caused by a faulty or inadequate burn of the install image.
Also would not recommend the flight versions if you want a stable OS for everyday use. 
Keyboard errors I have experienced  before are sometimes due to the connection. Is your keyboard and mouse PS2 (Purple and Green, the safest) , USB or wireless connections. USB and wireless keyboards can and have caused issues with me.

---

### Post by WEBSOUL on 2006-04-04
--------------------------------------------------------------------------------------------------------
[QUOTE=Lonergan]I have installed Ubuntu, Kubuntu 3x each time using the 64 bit version.  I just plopped the cd in and let it do its thing. The only tweaking I needed to do for X was to go from the default nv driver to the nvidia driver.

I have:
AMD X2 4400+
Corsair TwinX 2GB (2x1GB) PC3200 C2 DDR Memory
ASUS A8N-SLI Premium nF4 s939
ASUS EN6800GT GEFORCE 6800 256MB PCI-E
2x SATA Maxtor 200 gigs[/QUOTE]
------------------------------------------------------------------------------------------------------

      Hi lonergan !! , acording with your post i can see that you figure out how to configure the Nvidia driver to work with your video card , so i'd like to see your's xorg.conf file if you could send it to my mail , because i have similarities with your hardware profile :

Checkit out:
AMD Athlon 64 3500+ (2.2Ghz)
1 GB RAM Kingston DDR 400 (PC3200)
ASUS A8N-SLI (nForce4 - socket 939)
XMDIA GeForce 6600 LE 256MB ( PCI-E )

So i would like to know how to configure my kernel to automacally load  the correct video driver at boot time.

(Sorry abour my english , i'm a mexican boy :S )

thanxs :)

---

### Post by garretwp on 2006-04-05
If you are using a usb keyboard, then this could be a cause of your problem. Everytime i want to go and install a fresh copy of ubuntu on one of my machines, I have to plug a ps2 keyboard in for me to proceed and once that is done, the usb keyboard detects right away!

Garrett

---

### Post by TriZz on 2006-04-07
[QUOTE=selina]I think im having the same problem.  I'm sorry I dont know too much about these things.  But uni here is kinda making us use linux to program.  So i took home the ubuntu version and chose to use live (cause i dont trust myself to install it without wiping everything out) but after everything loads and a brown screen with ubuntu appears it just freezes and my mouse no longer moves?  What should I do?  I can't do any work til I get this loaded.[/QUOTE]

I'm new to and completely excited about using Linux!

I have a similar problem with selina.  It loads the brown-ish slash screen with the reflective logo (very nice, btw) and it runs through a bunch of commands following each command with an "OK".

The only command that fails is "Synchronizing System Clock with ....linux.org.

I can't imagine an unsynced clock causing the freeze.

I bit of information would help I suppose:

I am using the Live CD.  I just want to try it out and make sure that things work with my networking devices before I go neck deep in it.

AMD Anthlon64 3400+
NVidia GEForce 6800

I don't know the name brand or type of RAM that I have - but it's 2 512MB sticks.

Thank you all for your suggestions!

---

### Post by skylark on 2006-04-07
Hi TriZz,

I'm glad you are still excited about Linux even though that liveCD didn't work for you! Not a great first impression I'm sure.

When it freezes, what do you see? Does it just hang so you can still see the list of commands but nothing happens ... or do you get a blank screen (or even a brown or blue screen?).

Also are using the Breezy or a Dapper "flight" AMD64 liveCD?

Edit: Hmm... from your description your problems look similar to: [http://ubuntuforums.org/showthread.php?t=13831](http://ubuntuforums.org/showthread.php?t=13831) and [http://ubuntuforums.org/showthread.php?t=24756](http://ubuntuforums.org/showthread.php?t=24756) neither of which were solved from the looks of things. Also similar: [http://ubuntuforums.org/showthread.php?t=16768](http://ubuntuforums.org/showthread.php?t=16768) . As suggested by one of those posts, try <ctrl> c to kill the NTP system clock sync and see what happens (if your system is even responding to the keyboard that is).

PS: have you double checked your system hardware is okay? Running memtest86 or as suggested in this thread, it could possibly be a burn error with the liveCD - maybe try re-burning it using a slower burn speed?

---

### Post by TriZz on 2006-04-07
[QUOTE=skylark]Hi TriZz,

I'm glad you are still excited about Linux even though that liveCD didn't work for you! Not a great first impression I'm sure.

When it freezes, what do you see? Does it just hang so you can still see the list of commands but nothing happens ... or do you get a blank screen (or even a brown or blue screen?).

Also are using the Breezy or a Dapper "flight" AMD64 liveCD?

Edit: Hmm... from your description your problems look similar to: [http://ubuntuforums.org/showthread.php?t=13831](http://ubuntuforums.org/showthread.php?t=13831) and [http://ubuntuforums.org/showthread.php?t=24756](http://ubuntuforums.org/showthread.php?t=24756) neither of which were solved from the looks of things. Also similar: [http://ubuntuforums.org/showthread.php?t=16768](http://ubuntuforums.org/showthread.php?t=16768) . As suggested by one of those posts, try <ctrl> c to kill the NTP system clock sync and see what happens (if your system is even responding to the keyboard that is).

PS: have you double checked your system hardware is okay? Running memtest86 or as suggested in this thread, it could possibly be a burn error with the liveCD - maybe try re-burning it using a slower burn speed?[/QUOTE]

Hey - Thanks for your response Skylark!  Again, I'm very new to this - so please excuse any "newbie" moments I may have.  

I'm not sure how to answer your question regarding which version I downloaded.  When I downloaded from the first mirror site (USA) there was only one type of LiveCD for AMD64 - and that option didn't distinguish which version/type it was.

The screen loads the rest of the commands.  The screen goes black - as if it's going to proceed to the next step, but the screen never shows anything else.  The "activity" light on the CD continues to blink for another minute or so - and then stops blinking.

When I get home from work tonight, I will try again with the suggestions above.  The <CTRL> C command - when during the process should I execute that?  Again - please pardon my extreme newness to this.  

I'm not discouraged by this - in fact, I'm quite dedicated to expanding my knowledge beyond Windows based PCs.  I'm an IT major at George Mason University - and all I know is Windows.  I figure that if I expand my knowledge - the more valuable I become.

...plus, if I get past this - then I have a peice of experience that maybe I can share with someone else down the road.

---

### Post by skylark on 2006-04-08
[QUOTE=TriZz]When I downloaded from the first mirror site (USA) there was only one type of LiveCD for AMD64[/QUOTE]Then it probably is "Breezy" since that is the latest stable release (although the next version "Dapper" isn't too far off).[QUOTE=TriZz]The screen loads the rest of the commands.  The screen goes black - as if it's going to proceed to the next step, but the screen never shows anything else.  The "activity" light on the CD continues to blink for another minute or so - and then stops blinking.[/QUOTE]Okay this gives me some clues. It probably has nothing to do with the NTP clock sync, it looks more likely it is something to do with the video drivers Ubuntu is trying to use. The part where your screen goes blank is usually where Ubuntu will try and launch X-Windows (which provides the framework for the graphical user interface). It seems to be a common problem since Ubuntu isn't perfect in guessing which video drivers to use.

Here are some suggestions:
* try using "live vga=771" as the boot argument for the LiveCD
* If that doesn't work check out my reply to a similar problem here:
[http://ubuntuforums.org/showpost.php?p=889687&postcount=4](http://ubuntuforums.org/showpost.php?p=889687&postcount=4)
at least see if you can bring up a terminal with CTRL+ALT+F1

Of course the problem with a LiveCD is that if you do get it working, you will have to repeat the procedure every time.
[QUOTE=TriZz]The <CTRL> C command - when during the process should I execute that?[/QUOTE] I don't think you need to worry since it gets past the clock sync step which was failing. Basically <CTRL> C will kill a command, in this case you might still want to kill the NTP clock sync (rather than wait for it to fail).

Some of the most useful stuff I've learned in Linux has been through playing with the command line GNU tools (similar varients exist on most Unix systems). For example commands like grep, sort, awk and sed are great for quick manipulation of text files, and you can combine them with pipes or put them in a shell script for more complex tasks. Also it is really easy to play with languages like Perl and Python in Linux (most of Ubuntu's scripting is done in Python so there are plenty of good examples).

---

### Post by TriZz on 2006-04-09
Thanks again Skylark for your help.  

The "live vga=771" didn't do much, but lower the quality of the graphics (almost retro looking.)

I was able to bring up the terminal (I think).  It was a text based area.  I tried to open the xorg.config file - which appeared to be blank.  

It seems like we're making progress - I hope you have more suggestions for me.

---

### Post by skylark on 2006-04-09
Strange, the xorg file shouldn't be blank.
Can you try one more time?...  boot up normally, get a terminal with CTRL ALT F1 then make sure you type "sudo nano /etc/X11/xorg.conf" exactly including the "/" before the "etc".

---

### Post by snp on 2006-04-11
Just a tought, did you use sudo when editing? Since you got a blank document it seems more like you don't have permission to the file.

---

### Post by filterpipe on 2006-04-11
In BIOS -> Advanced -> CPU -> DRAM, disable both Software and Hardware
memory remapping. Then your install of Ubuntu might proceed. According to
the following link, you can then re-enable the memory remapping to gain access
to all 4 GB of RAM. However, I found that our system won't boot correctly with
the memory remapping enabled. Disabled, it works like a charm.

[http://www.linuxcompatible.org/4GB_with_Asus_A8N-SLI_and_A8N-SLI_SE_t33994.html]("http://www.linuxcompatible.org/4GB_with_Asus_A8N-SLI_and_A8N-SLI_SE_t33994.html")

---

### Post by TriZz on 2006-04-11
I appreciate everyone's input and help.

I've decided to install the 32bit version on my laptop.  I've got it working on there, but I gotta get the wireless connection working.

Again, thank you for everyone's input and helping to keep me interested.  Really, the community here is just as (if not more) impressive than the OS itself.

Thank you all.

---

### Post by jgsp93 on 2006-04-13
What did you have to do with the NVidia driver?

---

### Post by TonB on 2006-06-20
Think the discussion diverted a bit from the original problem, and unfortunately I never did see a real solution for the original problem, which I am also experiencing.

My hardware:
Asus A8N-SLI SE motherboard
Athlon X2 3800+ processor
NVidia 7300GS
Memory 2x 512Mb
Mouse & keyboard old-fashioned PS2

I tried installing AMD64 versions of Ubuntu 5.10, Ubuntu 6.06 flight 6 and Debian latest "Testing" version, and all fail somewhere in the installation process (mostly at the beginning when asking language to be used, but sometimes later in the process...!!!) when the keyboard seems to be disabled. Not any key then works anymore! Might also be that the system then hangs, the result however is the same; I can only turn off the PC.

A Debian i386 install did not give this problem, but does not recognise the nforce4 chipset, so is no real alternative. Windows XP also does not give any problem.

Suggestions I found so far in previous replies:
   - Burn CD at lower speed
   - Disable memory remapping in BIOS

I will certainly try these suggestions, but would very much appreciate any other suggestion, especially (though not exclusively :)  ) from people who actually managed to solve this problem on their system.


Thanks, Ton

---

### Post by MonkeyChamp on 2006-06-20
My install of Ubuntu 6.06 on my new PC hangs on step 5.  Seems like it can't find the HD to install.  Checked the DVD integrity and it passes.  Have the 64 Bit Athlon version.  
I had tried the 32 bit version at first, and it wouldn't get past the "Edit manual partition" info.  Then I thought to burn the 64 bit Athlon version and install that.

AMD Athlon 64 3000+
Asus A8V-MX
Micro ATX motherboard  1 GB PC3200
HDD-SATA 1 250 GB
DVD\CD - RW  (And NO other drives)

Went into Terminal and tried to use fdisk /dev/hda, etc etc.  Could find my DVD drive, but nothing else.  When I go into GParted all options are grayed out.  I'm a total Linux newbie and am not sure what else to try.

---

### Post by zXarth on 2007-11-15
Hiya,

I'm really new to the Linux scene (been with windows since Win 3.1) and I am just exploring out into the other OS possibilities and decided to try Ubuntu. From what I've read I have similar issues. Basically I insert the disc (and get it to boot) then at the 'main menu' I select the install option and up the top of the screen it has a loading bar... All good all good I think to myself, until my screen flashes and then goes black and does nothing. My keyboard looks as if it turns off (USB) and from the LED's on my Chassis the HDD seems to turn off or not repond... :( I would really love to explore this OS...

My PC:

AMD64 Athalon AM2 X2 6400+
Asus M2R32-MVP
2x ATI X1950 256mb crossfire setup
4x Corsair 1Gb PC5300/667Mhz
2x Seagate Barracuda 7200 SATA II 500GB HDD
Thermaltake toughpower 1200W PSU

---

### Post by justsomedude on 2007-11-15
Welcome to the forum. :)

Your problem sounds like you've got a badly burned CD.

-Be sure to verify the md5sum of your download:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Hashes can be found here:

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

-Burn the .iso file as slow as possible.

-Do an integrity check of your burned CD:

[https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)

---

### Post by danapayne on 2007-11-15
I'm having a similar problem on a new AMD64 laptop.  Installation won't go past initial hardware detection, screen goes black, hard drive becomes inactive.

I've tried reburning the CD at a lower speed, and got the same results.  CD checks out OK.  I get the same result with the 32 bit version.

I do get an error message during hardware detection that says that bcm43xx_microcode5.fw can't be found (and of course I have a Broadcomm wireless card).

I had a dual boot system on my old laptop (XP/Feisty) and would like to do the same on the new machine, using Gutsy.  

thanks,

Dana

Turion 64X2 Mobile
1.61 GHz
960MB RAM DDR2
120 GB SATA
NVIDIA GeForce 6150

---


---
title: "nVIDIA 8800GT is giving me HELL!"
date: 2008-02-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sean4000 on 2008-02-05
I am attempting to install 7.10 64 Xubuntu on my workstation but I cannot even load up into the Live CD because I can get no video feed out of my 8800GT card. After I get the typical install menu options the screen goes black and there is not even a blip to let me know that my system is working.

Specs:
EVGA 8800GT PCI-E 2.0
16GB DDR2 667 SDRAM
2TB RAID array
Areca 1210 PCI-E x8 controller card
Dual Quad-Core Opteron 2346HE
TYAN S2927-E motherboard
Samsung SATA 20X DVD-RW drive

I cannot load the live CD to even install of see what's wrong.   Any thought on how I could get this machine to load Xubuntu 7.10 64 bit?

---

### Post by NilsHG on 2008-02-05
i had the same problem with the 8800gt. you need the alternate install cd for ubuntu 64 bit. it is a text based installer. the install is not any more difficult as with the live cd. it just does not look as pretty.

hope that helps.):P


*edit* nice rig you have there :) */edit*

---

### Post by Jouke74 on 2008-02-05
:confused: Maybe the forum's search function is broken or so, because this is already the 20th person in about two weeks that is asking this question.

---

### Post by Toffeeapple on 2008-02-05
["here"]("http://ubuntuforums.org/showthread.php?t=670868") will probably answer your problem..

: )

---

### Post by Spydr4590 on 2008-02-05
A very simple work around.

1. Boot off the CD
2. At the list of options hit F6 and delete splash. Then hit enter twice. This will load Ubuntu so you can install.
3. After Ubuntu is installed and you're asked to reboot. You must hit escape before grub loads. Then you must select the first line ( not recovery) and hit e, then goto the second line and hit e again. Delete splash and hit enter, then hit b to boot.
4. Once you're in Ubuntu, open up the terminal and type ```
gksudo gedit /boot/grub/menu.lst
``` Search the file for splash and delete all entries. This will allow you to boot Ubuntu every time. Splash does not work at all even with updates for 8*000 cards. Even in alpha Hardy Heron you still have this issue.

---

### Post by Sean4000 on 2008-02-05
I think that the Alpha of Hardy still has the older nVIDIA driver. Ultimately I'll wait until the release April to use the 8800GT again.  I purchased a 7000 series card last night that should tide me over until the next release.  

Isn't HH expected to be a big release? If so, Microsoft will freak out. I've moved away completely from the XP Platform; it's all xubuntu from here on out.

Specs:
EVGA 8800GT PCI-E 2.0
16GB DDR2 667 SDRAM
2TB RAID array
Areca 1210 PCI-E x8 controller card
Dual Quad-Core Opteron 2346HE
TYAN S2927-E motherboard
Samsung SATA 20X DVD-RW drive
24" Gateway LCD w/ Ferjuda chip color calibrator.

---

### Post by dabl on 2008-02-05
> **Sean4000 said:**
> 

I think that the Alpha of Hardy still has the older nVIDIA driver. 

Au contraire!  The "nvidia-glx-new" package in HH Alpha 4 does a very nice job of installing the 169.09 Nvidia driver.  "sudo nvidia-xconfig --add-argb-glx-visuals --composite" and you're good to install compiz and emerald and enjoy the desktop effects.

However, the splash problem is as described above -- a problem.  :guitar:

---

### Post by Artemis3 on 2008-02-07
> **Jouke74 said:**
> :confused: Maybe the forum's search function is broken or so, because this is already the 20th person in about two weeks that is asking this question.

Yes, you didn't search 8800gt otherwise you would have found [this](http://ubuntuforums.org/showpost.php?p=4181856&postcount=363).

Or, you used the search box when reading a sub forum, this makes it search only that sub forum...

---

### Post by deadi on 2008-02-10
I had the same problem. I got by it by hitting F6 and editing the line to say nosplash instead of splash. The scripts would run and then stop. I hit enter and it gave a command prompt which typing startx started the gui. I then set my graphics to vesa with a display of generic LCD at  1280x1024 as its the default for my LCD and away it went! Once the install completed, I installed Envy.

---

### Post by Sean4000 on 2008-02-14
To tide me over I bought a 7950GX2 until 8.04 comes out.

---

### Post by NDJeff on 2008-02-14
I was having the same problem with my 8800gtx.  Deleting the "splash" entry from the livecd loader and grub respectively worked to get HH Alpha 4 installed and booted.  Now to try and make it work permanently ;)

---

### Post by Sean4000 on 2008-02-15
The new release can't come quick enough.

---

### Post by Drathas on 2008-02-15
It's really not "that" big of a deal - I had the same problem and just modified the boot loader to load without the splash.

---

### Post by DREMA on 2008-02-18
Maybe offtopic, but why the 16gb of ram? Its a server?
And why xubuntu? :o

---

### Post by PmDematagoda on 2008-02-18
There is a solution for using the 8800GT on Ubuntu, if Sean4000 wants to try again then just post your decision.

---

### Post by Sean4000 on 2008-03-11
Come back!!!!!   I need an answer!  I just gave up on the card until Hardy. 

How is hardy with the 800GT?

16GB Of ram because I do VFX rendering, HD Editing, and I am starting to do Blender modeling. Plus it was only a total of 700$ for the 16GB (8X2GB). No Lie.

xubuntu64 because I like the clean stripped nature of the interface and OS.

---

### Post by PmDematagoda on 2008-03-11
If you are looking for a stable system then Hardy may not be your best option since, as you may know, it is still under development. Why not use Gutsy?

---

### Post by Sean4000 on 2008-03-11
I am using Gutsy 64 because it's the only one that can boot on a RAID volume.

---

### Post by PmDematagoda on 2008-03-11
> **Sean4000 said:**
> I am using Gutsy 64 because it's the only one that can boot on a RAID volume.

Ok, now is the VGA card working properly?

---

### Post by guisar on 2008-03-11
I don't know about all of this- I didn't have any problem installing Hardy (8800GT) however while the open source (nv) drivers work PERFECTLY, the proprietary (nvidia) drivers detect only a 640x480 resolution on my Westinghouse 37" display (1200x1080). I've tried envyng, manual install of drivers, manual xorg.conf construction, noedid, etc. Always, the nvidia proprietary drivers detect the native panel frequency wrong and ignore any and all attempts to adjust them to something correct. I've come to the conclusion that the drivers (as of 169.12 anyway) are just broken and I should forget using compiz until sometime a long time in the future.

---

### Post by PmDematagoda on 2008-03-12
You are saying that you tried to install the drivers manually, however did you even try to use the Hardware Drivers(Restricted Drivers Manager) before trying to install the driver manually?

---

### Post by Sean4000 on 2008-03-12
> **PmDematagoda said:**
> Ok, now is the VGA card working properly?

The card is working fine as far as I can tell.  I have a 7950GX2 in ther e right now because my 8800GT is not working with linux at all. I tried switching drivers from the nv to the nvidia version with no success.   It only frezes when I have Firefox running.

---

### Post by PmDematagoda on 2008-03-13
> **Sean4000 said:**
> The card is working fine as far as I can tell.  I have a 7950GX2 in ther e right now because my 8800GT is not working with linux at all. I tried switching drivers from the nv to the nvidia version with no success.   It only frezes when I have Firefox running.

What Nvidia driver version are you using?

---

### Post by Therion on 2008-03-14
> **Spydr4590 said:**
> 

1. Boot off the CD
2. At the list of options hit F6 and delete splash. Then hit enter twice. This will load Ubuntu so you can install.
3. After Ubuntu is installed and you're asked to reboot. You must hit escape before grub loads. Then you must select the first line ( not recovery) and hit e, then goto the second line and hit e again. Delete splash and hit enter, then hit b to boot.
4. Once you're in Ubuntu, open up the terminal and type ```
gksudo gedit /boot/grub/menu.lst
``` Search the file for splash and delete all entries. This will allow you to boot Ubuntu every time. Splash does not work at all even with updates for 8*000 cards. Even in alpha Hardy Heron you still have this issue.
Worked for my 8800GT.  Like always (sighhh).

I've been down this path/using this fix since Feisty, so it's disappointing to see that this issue STILL has not been addressed.  

I'd just like to add that it **TOTALLY _SUCKS_** not having splash-screens.  Just in case the point has not yet been driven home.  Very nice, very professional looking.  Guaranteed to impress those you're trying to swing over to the Linux team what with all that scrolling text and what not.  :mad:

---

### Post by exaulz on 2008-03-14
> **Therion said:**
> Worked for my 8800GT.  Like always (sighhh).

I've been down this path/using this fix since Feisty, so it's disappointing to see that this issue STILL has not been addressed.  

I'd just like to add that it **TOTALLY _SUCKS_** not having splash-screens.  Just in case the point has not yet been driven home.  Very nice, very professional looking.  Guaranteed to impress those you're trying to swing over to the Linux team what with all that scrolling text and what not.  :mad:
I'm running an 8600GT XXX and I don't have any splash screens either. Only when in x86_64 though. When it's supposed to go to the splash screen, the screen just goes black and the monitor doesn't turn off, but it's "idle". As in, the power button isn't green, it's yellow/orange.

Does anyone know if this is a problem on NVIDIA's or Ubuntu's end? I'd like to report this bug since it's ben going on ever since I got this new graphics card.

---

### Post by scarrabri on 2008-03-16
Hi have a bliss 8800 gt graphics card,and i had the same problem with the disc i downloaded so i bought the  ubunu 7.10,64 bit disc and after putting the disc in a menu came up,this took about 3 mins or maybe a little longer,and in the menu was a option to start abuntu in a graphics safe mode,and this then allowed me to install ubuntu,and wow was i impressed, totaly amazed ,it was christmas and birthday rolled into one,i have always done multitracking,so i downloaded ARDOUR, a  recording studio,oh boy was it just brilliant,and did ubuntu run it like a pro,better in fact,which reminds me i must make a few donations ,because all this was virtualy  free ,if i am dreaming please dont wake me,what a outstanding workhorse ubuntu is,brilliant ,best wishes scarrabri:guitar:

---

### Post by nonewmsgs on 2008-03-16
> **scarrabri said:**
> Hi have a bliss 8800 gt graphics card,and i had the same problem with the disc i downloaded so i bought the  ubunu 7.10,64 bit disc and after putting the disc in a menu came up,this took about 3 mins or maybe a little longer,and in the menu was a option to start abuntu in a graphics safe mode,and this then allowed me to install ubuntu,and wow was i impressed, totaly amazed ,it was christmas and birthday rolled into one,i have always done multitracking,so i downloaded ARDOUR, a  recording studio,oh boy was it just brilliant,and did ubuntu run it like a pro,better in fact,which reminds me i must make a few donations ,because all this was virtualy  free ,if i am dreaming please dont wake me,what a outstanding workhorse ubuntu is,brilliant ,best wishes scarrabri:guitar:

it's a little off-topic but im certain everyone is pleased it's to your liking.  :)

---


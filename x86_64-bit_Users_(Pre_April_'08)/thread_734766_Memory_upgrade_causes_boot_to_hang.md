---
title: "Memory upgrade causes boot to hang"
date: 2008-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by RIClark on 2008-03-25
I am new to linux (4 weeks) but I have made great strides in that time (installed on 4 computers, 3 dual boot). however my recent ram upgrade to my laptop has stumped me.

I have a Hp pavilion zv6000 duel boot with XP Pro & ubuntu 7.10 AMD64 with 1GBit of ram in one of two slots. I am trying to add a 2nd 1Gbit module in the 2nd slot (the same manufacturer & part number as the existing module).

When i add the 2nd module the Bios sees the full 2GBit of ram, XP sees 2Gbit and works a lot faster. However, ubuntu will not boot with the new ram added. It gets about one inch into the orange bar and then reverts to a command line screen where various things can be seen to load (at progressively slower speeds) until it finally hangs at "loading apparmor profiles".

Once I remove the 2nd stick of memory ubuntu boots just fine. As XP works fine with the new memory, I do not expect that I have a hardware issue. I adjusted my swap file to 2 x the installed ram, that did not help.

I will run a memory test in GRUB just in case, also I will try and boot from the CD with the new memory in.

Thanks in advance for any help.

---

### Post by felker2 on 2008-03-25
> **RIClark said:**
> 
Once I remove the 2nd stick of memory ubuntu boots just fine. As XP works fine with the new memory, I do not expect that I have a hardware issue. I adjusted my swap file to 2 x the installed ram, that did not help.

I will run a memory test in GRUB just in case, also I will try and boot from the CD with the new memory in.


It's a good thing run the GRUB (or live CD) memory test for a few hours; it's my experience that Linux is more picky about memory than Windows is (which is a good thing, IMHO).

---

### Post by Jouke74 on 2008-03-25
Yeah and subsequently test if the live CD is working, to check if it is possible to run Ubuntu or not.

---

### Post by RIClark on 2008-03-25
I ran the memory test overnight, the memory passed the test 9 times without errors, also I booted from the live CD with the memory installed. Ubuntu booted just fine & the system tools saw all of the installed RAM.

---

### Post by RIClark on 2008-03-25
The latest update, 
After googling around for boot error strings I made the following changes in grub. At the grub logon i pressed "e" to edit and changed the end of the boot line of code from

ro quiet flash

to 

ro acpi=off

then I pressed "b" to boot

The boot was successful (and fast) and i am now logged into Ubuntu using both memory sticks, the system tool shows 2Gbit of memory and all is well, except:

i have no idea what     acpi=off    does or how to make it permanent

my wireless card stopped working (i'm using ndiswrapper)

also, a popup window of Update Information tells me that my Xgl server setup has changed (whatever that is) this tells me that the Xgl server will start automatically next time I login and that to disable Xgl autostart for this user i need to create a file named ~/.configxserver-xgl/disable         Do I want to do that?

Well, at least I am into Ubuntu (one step forwards) now just to fix the wireless & Xlg (two steps backwards) I will now reboot my laptop in XP to see if I can find the browser page that suggested acpi=off in the 1st place

Thanks again in advance for any suggestions

---

### Post by dcstar on 2008-03-26
> **RIClark said:**
> 
............
Thanks again in advance for any suggestions

Put the extra memory in, and then go into your BIOS and do a full reset to defaults.

Possibly some system devices remained mapped to addresses that the new RAM was using and didn't automagically relocate when you installed the new memory.

---

### Post by RIClark on 2008-03-26
David,

Thanks for the suggestion, I reset my bios (it is a greatly restricted HP bios) but it made no difference, I still cannot boot without acpi=off

I am finding things that do no work, i wonder how many of them are associated with the acpi module. no battery indication, no wifi (wifi button does not work), computer now hangs on shutdown/restart & requires a hard power down.

---

### Post by felker2 on 2008-03-26
> **RIClark said:**
> David,

Thanks for the suggestion, I reset my bios (it is a greatly restricted HP bios) but it made no difference, I still cannot boot without acpi=off

I am finding things that do no work, i wonder how many of them are associated with the acpi module. no battery indication, no wifi (wifi button does not work), computer now hangs on shutdown/restart & requires a hard power down.

You can read [http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface) to see what ACPI does.

---

### Post by RIClark on 2008-03-26
I am now considering my options here, I do not want to use my laptop without acpi, it is clear that the lost functionality would become too annoying. 

I could remove the second memory chip and  live with 1GBit of memory

or

I could clear out my Linux partitions and reload Linux (I'm not scared, I have a super grub disk and know how to use it) with the new memory installed from the get go (I don't know if this would help but its worth a shot).

If I reload Linux what distro should I use?

Ubuntu 32 bit - this is running on one of my desktops, how does it work on Laptops?
Ubuntu 64 bit - the current distro with the issues
Kubuntu 64 bit - this disrtro would not install from the live disk when I tried. I tried that before loading Ubuntu, but at that time (2-weeks ago) this laptop only had half a Gbit of ram
Or I have a couple of OpenSuse KDE discs

I am not (not yet anyway) a big fan of KDE, but I will take functionality over features any day.

or

I could buy a Mac..... (like I could get that by my wife).

---

### Post by RIClark on 2008-03-27
Now I am getting close

I re loaded Ubuntu 7.10 AMD64 from scratch with the new memory in.

everything went great except I was having problems with my wireless configuration.

ndiswrapper worked on this laptop for over a week.but not now

Anyway while muddling thru some forum wireless threads i edited my /etc/modules file 

I added "ndiswrapper" to the end of the list

then I tried to reboot and the boot hang error returned.

once i reboot with acpi=off and remove "ndiswrapper" from the /etc/module file the boot up process is normal again.

so do i need  the line ndiswrapper in my /etc/module file?

Can I get ndiswrapper to work without that entry?

I have no idea why the extra memory triggered (or appeared to do so) the boot error in the 1st place.

if i have to i can use the standard bcm43xx driver for now (but it is very slow)

---

### Post by RIClark on 2008-03-28
It appears that my issues were related to ndiswrapper. ndiswrapper worked just fine on this computer until I added the 2nd GBit of ram.
This computer works just fine if i use the restricted driver provided by Ubuntu for my wireless card (bcm43xx). However that only runs at 24mb the windows driver work twice as fast (if i can get it working).
I am going to close this thread (if i can work out how to) and open one in the wireless forum.

thx for all the suggestions above

---


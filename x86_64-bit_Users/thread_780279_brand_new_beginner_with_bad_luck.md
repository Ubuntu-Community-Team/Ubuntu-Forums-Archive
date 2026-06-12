---
title: "brand new beginner with bad luck"
date: 2008-05-03
forum: x86 64-bit Users
---

### Post by bigx86 on 2008-05-03
I just installed Ubuntu and wanted to try it for the first time ever...

But I have two problems, When I connect my old IDE HDD, my computer keeps on restarting all the time (just before the bootloader)

2. When logging in to Ubuntu, after the first few clicks (on anything) it freezes and I have to restart my computer.

Ubuntu Hardy Heron 64-bit

My computer specs:

Pentium 4 HT 3.0 Ghz
2 GB DDR2
Nvidia Geforce 7600GT

2 HDD, one of them S-ATA (which ubuntu is on)

I hope someone helps me so I can migrate from windows :mad:....

---

### Post by scorp123 on 2008-05-03
> **bigx86 said:**
>  Ubuntu Hardy Heron 64-bit

My computer specs:

Pentium 4 HT 3.0 Ghz Pentium-4 CPU's are not 64-bit as far as I know.

---

### Post by bigx86 on 2008-05-03
Not true , The copy of Vista am using is 64 bit edition....

Im sure my CPU is EM64T

---

### Post by retiree on 2008-05-03
You need to download the i386 ISO version of ubuntu and burn it to Cd and then boot from cd  (go in to bios and change to boot from cd first) and then you can run it from live cd without doing anything to change windows, and you can also install from live cd if you want to. If you have a DVD it will be the same process. I'm almost certain your Pentium 4 will not run 64 bit.Hope this helps. I've been on Ubuntu a short and I love it.

---

### Post by bigx86 on 2008-05-03
Huh...

maybe you guys didnt understand me right....It is already installed.....

---

### Post by retiree on 2008-05-03
If you are sure you have 64 bit then it will run.A problem I had at first was when I burned to DVD I burned it to fast and had some errors on the DVD. I slowed the burn down and reinstalled and it worked.

---

### Post by bigx86 on 2008-05-03
I cant wait until I can try it.....but there have to be someone who had the same problem....I tried to search...but in vain ... :(

---

### Post by retiree on 2008-05-03
You might also want to try Gutsy Gibbon version since it is a stable version still supported.Hardy Heron is a new release and it is a Long Term Support version. I have run Hardy from live DVD but I have not upgraded yet.

---

### Post by scorp123 on 2008-05-03
> **bigx86 said:**
> Not true , The copy of Vista am using is 64 bit edition.... Im sure my CPU is EM64T I looked it up in Wikipedia. Yes you are right, some of the last series of the Pentium-4 were indeed 64-bit.

In order to troubleshoot this a little and to find out whether or not we have a hardware issue or an OS issue I'd suggest this:

- Download the "Linux Mint" live CD from here:
[http://www.linuxmint.com/mirrors.php?id=15](http://www.linuxmint.com/mirrors.php?id=15)

"Linux Mint" was once based on 32-bit Ubuntu, but has since taken a different path and is now a distribution in its own right. It's still similar enough to Ubuntu though.


- Download the "OpenSUSE" live CD from here:
[http://software.opensuse.org/](http://software.opensuse.org/)

I'd suggest the "GNOME Live CD" because it's smaller (less to download). OpenSUSE is from Novell, they have their own set of packages, their own set of kernel patches, and Canonical --the makers of Ubuntu-- have pretty much nothing whatsoever to do with them.

Now: Why you are doing this ...

- If the Linux Mint Live CD crashes too + The OpenSUSE CD crashes as well:
==> You have a hardware issue. Might be a compatibilty problem somewhere somehow. Or might be something like defective RAM.

- If only the Linux Mint Live CD crashes but the OpenSUSE CD doesn't:
==> Your hardware doesn't like stuff based on Ubuntu! Try OpenSUSE. If it still doesn't crash and everything works tip top there ... well then it's obvious that Ubuntu is to blame for the crashes.

- If Linux Mint doesn't crash but OpenSUSE crashes:
==> That would be funny because it would not make sense if this situation occurred.


I assume you have a dual-boot and your system still has Windows somewhere somehow? And you are perfectly sure it's working tip top? ... just to make sure we can exclude completely defective hardware ....

---

### Post by ASULutzy on 2008-05-03
Yea, I would make sure of a few things. You're sure you have no problems booting into Windows?

If that's the case you can probably rule out bad RAM.
Which means it's one of 3 things. Either your install of Ubuntu didn't complete correctly, most likely because of a bad CD (Always check cd-integrity from the live-cd before installing), your SATA drive is bad, or there is of course always the possibility that Ubuntu does not like some piece of hardware you have.

Are you sure that your CD had no defects?
Are you sure that the SATA drive has no errors?

---

### Post by bigx86 on 2008-05-03
Thanks I will try that...

---

### Post by bigx86 on 2008-05-03
I checked the integrity of the CD before install, I also run memtest64...

All test results was ok.....

How can I check my SATA ?

---

### Post by bigx86 on 2008-05-03
until I burn the disc...any ideas guys?

---

### Post by bigx86 on 2008-05-03
Both of them crashed (mint and OpenSuSe).....Now should I start to check if any of my hardware have compability problem with Linux ?...

---

### Post by scorp123 on 2008-05-03
> **bigx86 said:**
> Both of them crashed (mint and OpenSuSe)..... That's bad. :(

Can you describe the crashes in more details please? e.g. did they crash in what looked to be the same process, e.g. during the same step in their boot sequences?

From my experience:

- if you have an overclocked system: slow it down again. Overclocking may work in some cases, but it's bad for the system's overall stability.

- if you have a "tuned" BIOS, e.g. a BIOS set to the "Max. Performance" option: Try what happens if you disable some of those options. If you're not aware that you have anything like that: Don't bother! If you never ever touched anything in the BIOS then we can exclude this. (and remember: Please WRITE DOWN what you changed when you change something, just in case!)

- if you have multiple RAM chips in your system: Try if it helps if you remove one (and please do it *GENTLY* !!!). Could be that one RAM chip is defective or that it has a wrong timing (e.g. they are not the same speed). But please be cautious, don't touch the golden contacts of your RAM banks and try avoiding any of the delicate metal parts. Try to hold the RAM banks on the outermost upper corners where everything is of plastic. And when you reinsert the RAM bank back into its slot make sure you aligned it correctly and that you don't use too much force!! (you could seriously damage your motherboard if you exaggerate it!)

- if you have a fast graphics card, try what happens if you slow it down. e.g. I had once a system where both the Nvidia card and the system were supposedly "AGP 8x" compatible. Turned out that it wasn't the case, I had to go the BIOS and slow it down manually to "AGP 4x". That stabilized the system.

Also: You said you have Windows Vista. If you have any tools over there (e.g. memory checkers, hardware analysis tools, etc.) run those too. Can't hurt to see if those Windows tools find anything.

---

### Post by retiree on 2008-05-03
Run Chkdsk under windows to see if your harddrive has any bad sectors. I am running x64 bit Ubuntu on AMD dual core and it runs quick and flawlessly. You can have a few compatibility,both software and hardware problems,but all of those can be worked out with the help of those guys that are really good at Linux. Don't become discouraged and give up. The final outcome will be worth it. Good luck, and regards

---

### Post by bigx86 on 2008-05-04
> **scorp123 said:**
> That's bad. :(

Can you describe the crashes in more details please? e.g. did they crash in what looked to be the same process, e.g. during the same step in their boot sequences?

From my experience:

- if you have an overclocked system: slow it down again. Overclocking may work in some cases, but it's bad for the system's overall stability.

- if you have a "tuned" BIOS, e.g. a BIOS set to the "Max. Performance" option: Try what happens if you disable some of those options. If you're not aware that you have anything like that: Don't bother! If you never ever touched anything in the BIOS then we can exclude this. (and remember: Please WRITE DOWN what you changed when you change something, just in case!)

- if you have multiple RAM chips in your system: Try if it helps if you remove one (and please do it *GENTLY* !!!). Could be that one RAM chip is defective or that it has a wrong timing (e.g. they are not the same speed). But please be cautious, don't touch the golden contacts of your RAM banks and try avoiding any of the delicate metal parts. Try to hold the RAM banks on the outermost upper corners where everything is of plastic. And when you reinsert the RAM bank back into its slot make sure you aligned it correctly and that you don't use too much force!! (you could seriously damage your motherboard if you exaggerate it!)

- if you have a fast graphics card, try what happens if you slow it down. e.g. I had once a system where both the Nvidia card and the system were supposedly "AGP 8x" compatible. Turned out that it wasn't the case, I had to go the BIOS and slow it down manually to "AGP 4x". That stabilized the system.

Also: You said you have Windows Vista. If you have any tools over there (e.g. memory checkers, hardware analysis tools, etc.) run those too. Can't hurt to see if those Windows tools find anything.

Okey the first and the second one is checked....No overclocking or tuning...

.............I runned Tune Up utilities... checked memory and hdd...nothing seems wrong from Vista Ultimate....

---

### Post by bigx86 on 2008-05-04
> **retiree said:**
> Run Chkdsk under windows to see if your harddrive has any bad sectors. I am running x64 bit Ubuntu on AMD dual core and it runs quick and flawlessly. You can have a few compatibility,both software and hardware problems,but all of those can be worked out with the help of those guys that are really good at Linux. Don't become discouraged and give up. The final outcome will be worth it. Good luck, and regards

Thanks retiree :)

---

### Post by bigx86 on 2008-05-04
Noone.... :s ?

---

### Post by howlingmadhowie on 2008-05-04
i'd like to know more about how it crashes.

can you boot ubuntu, but when selecting ubuntu from the list in grub press e and then edit the boot parameters to remove the words "quiet" and "splash". you can then boot by pressing enter and b

switching off quiet and splash will call a large number of messages to be displayed on the screen.  once it's booted (if it gets this far), the messages can be found in /var/log/messages

the contents of this file or anything suspicious in the text that flows past could shed some light on the situation.

---

### Post by bigx86 on 2008-05-05
I ll try that right ahead

> **howlingmadhowie said:**
> i'd like to know more about how it crashes.

can you boot ubuntu, but when selecting ubuntu from the list in grub press e and then edit the boot parameters to remove the words "quiet" and "splash". you can then boot by pressing enter and b

switching off quiet and splash will call a large number of messages to be displayed on the screen.  once it's booted (if it gets this far), the messages can be found in /var/log/messages

the contents of this file or anything suspicious in the text that flows past could shed some light on the situation.

---

### Post by bigx86 on 2008-05-07
Well I think im stuck with windows.....

Are there anyone who can tell me how I can uninstall Ubuntu?

---

### Post by stringkarma on 2008-05-08
Before you reload win, have you tried any kernel boot options. The power management on some computers causes problems. For example my laptop had similar (not exactly the same) problems until I searched for model specific help. As someone said before go into the grub list and add options like

noapic nolapic noapci irqfixup

some combination of the above (or all as I needed) may help.

Also search for either your processor or motherboard model and see if anyone else needed kernel options to get them to work.

Sorry your Ubuntu experience hasn't been the best. I had a hard time getting in (as I have said) but I am glad that I have. There is always something more to iron out, but I feel that having worked to get it right I really understand how things are working.

Good luck.

---


---
title: "Clock running fast In Hardy heron"
date: 2008-05-08
forum: x86 64-bit Users
---

### Post by rob-1 on 2008-05-08
Hello, I'm not sure if there is a thread that has already been started for this problem, so I apologize in advance. I have been using ubuntu since about 6.04, and have found it easy to work with, prompting my mother to want to try it. Her system was more powerful than mine. (A Home built AMD x64 3500+ based system with 1g of PC 3200 Ram, An MSI NX7300LE 256mb video card, 20x dual-layer SATA burner and 160gb HD Running on an ECS Geforce6100SM-M mainboard.) Ubuntu was already fast on my system, so I figured it would be even better on mother's. well, the setup was okay, and the only problem I had at the time was having to use the "Fixboot" command in the windows recovery console to solve the sudden problem windows was having booting. after all that I loaded up Ubuntu to let mother see how it looked. the first thing I noticed is that was fast, Really fast, too fast for mom in fact, as she had to slow down her typing to get the keystrokes to register properly. (I had figured it would be faster, but this was ridiculous). the other was the clock, it was blazing along at a rate of 3 seconds to one second in real time. in two minutes the clock was way off.(by about 6 minutes). I had a problem that I couldn't solve just by changing the settings. I have searched the forums, and have tried all of the fixes I could find, to no avail. I had noticed that this appeared to have been a persistent bug that dates back earlier than 6.04. but all of the fixes for it, or other instances of the problem have been ineffective, and setting the clock to update via server, doesn't help much, due to the drift between updates.:confused: I'm at my wit's end, and have told mother to stop trying to boot ubuntu right now. It might even be removed from her system at this point, as it's virtually unusable, due to the speed at which it's running.:( If anybody has any ideas please let me know.

---

### Post by rob-1 on 2008-05-22
> **rob-1 said:**
> Hello, I'm not sure if there is a thread that has already been started for this problem, so I apologize in advance. I have been using ubuntu since about 6.04, and have found it easy to work with, prompting my mother to want to try it. Her system was more powerful than mine. (A Home built AMD x64 3500+ based system with 1g of PC 3200 Ram, An MSI NX7300LE 256mb video card, 20x dual-layer SATA burner and 160gb HD Running on an ECS Geforce6100SM-M mainboard.) Ubuntu was already fast on my system, so I figured it would be even better on mother's. well, the setup was okay, and the only problem I had at the time was having to use the "Fixboot" command in the windows recovery console to solve the sudden problem windows was having booting. after all that I loaded up Ubuntu to let mother see how it looked. the first thing I noticed is that was fast, Really fast, too fast for mom in fact, as she had to slow down her typing to get the keystrokes to register properly. (I had figured it would be faster, but this was ridiculous). the other was the clock, it was blazing along at a rate of 3 seconds to one second in real time. in two minutes the clock was way off.(by about 6 minutes). I had a problem that I couldn't solve just by changing the settings. I have searched the forums, and have tried all of the fixes I could find, to no avail. I had noticed that this appeared to have been a persistent bug that dates back earlier than 6.04. but all of the fixes for it, or other instances of the problem have been ineffective, and setting the clock to update via server, doesn't help much, due to the drift between updates.:confused: I'm at my wit's end, and have told mother to stop trying to boot ubuntu right now. It might even be removed from her system at this point, as it's virtually unusable, due to the speed at which it's running.:( If anybody has any ideas please let me know.

Well, I've come to a decision here. I'm going to remove ubuntu (Or at least the bootloader.)until I can figure out a way to get it running properly once installed. there are so many variations of the 2x clock bug that I'm no longer sure that I have tried them all. though most of those existing fixes date back to 2005. while common sense would suggest that these older bugs have indeed been fixed, I can't be sure. I have noticed that when trying to change the clock setting once I had trouble getting root access to unlock the settings panel getting "Unexpected error" Messages on several tries I would have to close the date and time panel out and start again, eventually I would get in, but only after three tries. I get the errors more often than not. If it hasn't been considered as a recurring bug I would ask that it should be. Ubuntu runs fine on my system, but I am disappointed that I can't seem to get it to run properly on my mothers system. Any ideas at this point would be much appreciated.

                                                    Robert

---

### Post by Thelasko on 2008-05-22
Your computer speed and incorrect time are related.  I have run into this issue every time I upgrade to the latest and greatest version of Ubuntu.  For some reason they never manage to fix this bug.  You said you checked everything, but have you [tried this]("http://ubuntuforums.org/showthread.php?t=53094&highlight=clock+double+speed")?  It has always worked for me, even though my clock is persistently slow and I run an Intel processor.

---

### Post by rob-1 on 2008-05-22
I might try that one. I can't think of any others I haven't tried. My mother's system was the first 64-bit system I have built, and this is the first time I have had so many problems with ubuntu. Hopefully this will work. I just can't believe this bug hasn't been patched.


UPDATE: trying that only resulted in ubuntu booting to a "Recovery" menu, that won't work correctly. I have to hit a bunch of random keys, and ENTER before getting it to continue booting. it wouldn't save the changes to menu.lst. I don't know what's going on at this point.

---

### Post by Yellow Pasque on 2008-05-22
Is your BIOS updated? If you're not sure:
```
sudo dmidecode -t 0
```

[http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?detailid=685&DetailName=Bios&MenuID=7&LanID=9](http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?detailid=685&DetailName=Bios&MenuID=7&LanID=9)

---

### Post by rob-1 on 2008-05-22
I'll check the bios when I can get a chance. mother is using windows xp on it right now. I have not removed the Grub bootloader. though I might have to figure out the "Recovery menu" Issue when I'm done

---

### Post by Thelasko on 2008-05-23
Sorry, I haven't read that post in a while and it didn't say what I thought it said.  The part that worked for me is as follows:
> If you have installed Ubuntu and you want to see if it works for you:

Turn on your computer and keep pressing "ESC" until you get to the GRUB menu.

Select your kernel with your keyboard arrows (DO NOT PRESS ENTER) and Press "e".
Then you will see 3 lines:
Code:

root (hd0,0)
kernel	/boot/vmlinuz-2.6.12-10-k7 root=/dev/hdb1 ro quiet splash
initrd	/boot/initrd.img-2.6.12-10-k7

Select the line which begins with the word "kernel" and press "e" to edit it.

Add one [ONLY ONE i.e. only 1) or only 2) ] of the following things at the end of the line:

1) noapic nolapic
so that it will look like this:
Code:

kernel	/boot/vmlinuz-2.6.12-10-k7 root=/dev/hdb1 ro quiet splash noapic nolapic

OR
2) noapic acpi=noirq
OR
3) noapic acpi=off
OR
4) noapictimer
OR
5) noapictimer irqpoll
OR
6) noapic acpi=off
OR
7) noapic acpi=noirq nolapic

Then get off the text field and press "b" to boot the kernel.

---

### Post by Thelasko on 2008-05-23
Also, did you try the mp3 test mentioned in the article I linked earlier?  I also noticed the issue with video.  It won't play at the correct speed.  These are symptoms of the kernel not interacting properly with the processor, not a BIOS issue.

---

### Post by rob-1 on 2008-05-23
ugh I never tested to see how it played mp3s, as I was too focused on the other. The bios was an option but I didn't want to start unnecessarily flashing the bios. (I'm a little oldschool on that one. e.g dont flash the bios unless you really have to.) I've always heard that the bios can be ruined.

---

### Post by Thelasko on 2008-05-23
I should have also mentioned that if Windows works properly on the machine then it definitely isn't the BIOS.  I had the same problem, Vista kept perfect time and Ubuntu was messed up.  I followed the steps above and it's been working fine since November.

---

### Post by rob-1 on 2008-05-23
the mp3s play fine. I cannot get the edit trick to work as there is a "UUID" string in place of the actual location, adding noapic nolapic did nothing. I still am having a problem with that "Recovery" menu

---

### Post by Yellow Pasque on 2008-05-23
> **rob-1 said:**
> the mp3s play fine. I cannot get the edit trick to work as there is a "UUID" string in place of the actual location, adding noapic nolapic did nothing. I still am having a problem with that "Recovery" menu
It is normal (and best) to use the UUID to mount the root file system as the devfs links are susceptible to change. That is not contributing to your problem.

---

### Post by rob-1 on 2008-05-23
UPDATE: I managed to fix the recovery menu issue, for some reason I had single in the kernel options. setting the "noapictimer" option did take care of the cursor speed at login. but the seconds on the clock are jumping by three every second (ie 23, 28,31, etc) the bios is out of date, but I'm trying to save that as last resort.

---

### Post by rob-1 on 2008-06-02
Update (Probably final). I went ahead and decided to update the bios on the board, a process I've done countless times. unfortunately this time, it appeared to kill the board. The bios file for my particular board included a windows-based flashing utility, so I decided to use it, halfway through the flashing process, the system suddenly shut off and started beeping, (One short beep each second, no pause.) no video, nothing. I was lucky that there was a warranty on the board, so I'm in the process of getting it replaced. I will not try updating the bios again, so I'm removing ubuntu from her system entirely. if there ever is a version of ubuntu that comes out with that bug fixed. I will try it, but it's not worth killing the board to fix the problem. I just can't take that risk.

---

### Post by rob-1 on 2008-06-29
Update (Pt.2) After a lengthy process I obtained the replacement board and put it in the system. this board is a slightly newer model of the original. (Geforce6100 PM-M2) The install of ubuntu was still on the hd, so I decided to give it another chance, It booted, and I decided to open the adjust date and time dialog, to check the rate the seconds ticked by. The rate was normal! the fast clock was gone! I still cannot figure out why this board behaved differently than the last, but at last there is a perfect install of ubuntu on my mother's system. thanks to all for their help. and as a precaution, anyone who has a ECS geforce6100 SM-M should reconsider installing ubuntu. If anyone actually managed to get this board to run Ubuntu properly, I would love to know.

---

### Post by Maybelline on 2008-07-08
Glad you got Ubuntu to work.  From my experience, ECS boards (I believe I had a 6100 from Fry's) vary wildly in regards to quality.  I had a faulty PCIe slot, and the replacement card had a faulty BIOS.  Finally, I just upgraded the mobo to an Asus, and have had no issues since.

---

### Post by stchman on 2008-07-08
> **rob-1 said:**
> Hello, I'm not sure if there is a thread that has already been started for this problem, so I apologize in advance. I have been using ubuntu since about 6.04, and have found it easy to work with, prompting my mother to want to try it. Her system was more powerful than mine. (A Home built AMD x64 3500+ based system with 1g of PC 3200 Ram, An MSI NX7300LE 256mb video card, 20x dual-layer SATA burner and 160gb HD Running on an ECS Geforce6100SM-M mainboard.) Ubuntu was already fast on my system, so I figured it would be even better on mother's. well, the setup was okay, and the only problem I had at the time was having to use the "Fixboot" command in the windows recovery console to solve the sudden problem windows was having booting. after all that I loaded up Ubuntu to let mother see how it looked. the first thing I noticed is that was fast, Really fast, too fast for mom in fact, as she had to slow down her typing to get the keystrokes to register properly. (I had figured it would be faster, but this was ridiculous). the other was the clock, it was blazing along at a rate of 3 seconds to one second in real time. in two minutes the clock was way off.(by about 6 minutes). I had a problem that I couldn't solve just by changing the settings. I have searched the forums, and have tried all of the fixes I could find, to no avail. I had noticed that this appeared to have been a persistent bug that dates back earlier than 6.04. but all of the fixes for it, or other instances of the problem have been ineffective, and setting the clock to update via server, doesn't help much, due to the drift between updates.:confused: I'm at my wit's end, and have told mother to stop trying to boot ubuntu right now. It might even be removed from her system at this point, as it's virtually unusable, due to the speed at which it's running.:( If anybody has any ideas please let me know.

I have never seen this even on my 3.0GHz quad core setup running Hardy.

---

### Post by rob-1 on 2008-07-08
Thanks for the info. I Guess I'll keep that in mind when I'm looking for boards in the future. so far the replacement board seems to be working fine I'll be sure not to try updating the bios though.

---


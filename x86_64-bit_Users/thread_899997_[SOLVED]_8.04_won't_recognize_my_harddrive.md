---
title: "[SOLVED] 8.04 won't recognize my harddrive"
date: 2008-08-24
forum: x86 64-bit Users
---

### Post by kjb34 on 2008-08-24
I have an Asus 8V-X motherboard with athlon 64 and 1.2 G of ram with a Maxtor 60 gB hdd. I have tried to install the 64 bit 8.04 with the live CD and the alt install but neither of them works. The alt install tells me that it doesn't recognize my hard drive and  shows a list of drivers but it won't go further than that. I checked the cd integrity it checked out okay. I currently have the 32 bit 8.04 running with no problems but i would like to switch to the 64 bit version.

---

### Post by felker2 on 2008-08-25
I think the exact message / logging would help. 

Is it a (P)ATA/IDE or a SATA harddisk?

Furthermore: when booting the normal live CD (not the alternate), in the boot options remove the "quiet" and "splash" options so that you can see the message during the live boot.
You could also play with the boot options: "pci=nomsi irqpoll noapic acpi=off". That worked for me in older Ubuntu versions.

FYI: I had a similar problem with 64-bit ([https://bugs.launchpad.net/ubuntu/+bug/112906](https://bugs.launchpad.net/ubuntu/+bug/112906)), but that was caused by my 4 GB RAM, very new hardware (which you haven't got) and a bug in the Linux kernel.

---

### Post by kjb34 on 2008-08-25
It's a SATA. I will have to try to turn off splash and quiet.

---

### Post by cyrus_the_virus on 2008-08-25
Hi,

A friend of mine had problems with a SATA drive too. He fixed be changing a setting in his BIOS. Don't recall exactly what setting it was. Something like SATA compability. He had to change it from enhanced to IDE and then it worked (also asus mobo)

You could also try to install the 32 bit version.

Marty

---

### Post by kjb34 on 2008-08-25
I have the 32 bit version up and running but I want to switch the 64 bit version. I think you're right about switching the BIOS setting. I'm not sure how to do it be may they might have something in motherboard manual.

---

### Post by cyrus_the_virus on 2008-08-26
I checked the setting in my BIOS. I had to go into the* SATA Configuration* menu and then select *Configure SATA* as *Compatible* instead of the default *Enhanced*

To get into the BIOS, watch the screen while booting. It should says something like press DEL to to go into the BIOS. On my Asus P5K, it's the DEL button but on your system it might be something else. I'm sure this is in the manual of the motherboard.

Anyway, be VERY careful in the BIOS. Messing around with the wrong setting may stop your system from functioning properly.

Marty

---

### Post by kjb34 on 2008-08-26
> **cyrus_the_virus said:**
> I checked the setting in my BIOS. I had to go into the* SATA Configuration* menu and then select *Configure SATA* as *Compatible* instead of the default *Enhanced*

To get into the BIOS, watch the screen while booting. It should says something like press DEL to to go into the BIOS. On my Asus P5K, it's the DEL button but on your system it might be something else. I'm sure this is in the manual of the motherboard.

Anyway, be VERY careful in the BIOS. Messing around with the wrong setting may stop your system from functioning properly.

Marty

The BIOS on my system doesn't have a sata configuration menu. Maybe I need to update my BIOS.

---

### Post by Blackcabs on 2008-08-28
> **kjb34 said:**
> I have an Asus 8V-X motherboard with athlon 64 and 1.2 G of ram with a Maxtor 60 gB hdd. I have tried to install the 64 bit 8.04 with the live CD and the alt install but neither of them works. The alt install tells me that it doesn't recognize my hard drive and  shows a list of drivers but it won't go further than that. I checked the cd integrity it checked out okay. I currently have the 32 bit 8.04 running with no problems but i would like to switch to the 64 bit version.

Hi kjb i had a similar problem like this the other day,, i wanted to install a copy of "Dare i say it XP" to redundant pc that i had lying around, However after loading the disc the Hardware inspector screen came up and the the system froze, and i couldn't get any further than this point no matter how hard i tried. So next i thought that i would try a live copy of Ubuntu as usually it will run on anything, although to my dismay the same problem reared its ugly head, the live installer would go as far as looking for the hard drive then fail.Now i Knew that the hard worked as it was showing up in the bios, and it already had win98 installed on it which booted and ran fine "Time to scratch my head and think" I Know i thought !! i will try and run a copy of BT3 on Slax which is also a liux live cd, guess what same problem!!!.Totally stumped by this and with nothing to lose i decided to reset the cmos ram on the motherboard  and start from scratch. When i booted up again i got a warning "Bad cmos checksum" use F1 to run setup defaults, which i expected. I then rebooted again after pressing F1, stuck in the live Ubuntu cd and HEY PRESTO it worked.:popcorn:

Now i am not saying that you should go ahead and do this, as it was said earlier that messing with your bios can mess up you machine. First of all i would suggest checking that your hard drive is definitely showing up in the bios, and that when you are trying to run the live cd make sure your cdrom or dvdrom drive is set as the first boot device in your bios. 
Hope this helps

Ps This isn't a new hard drive is it ?? as you have said that you already had 32bit running fine, so it cant be a bios update problem..

---

### Post by kjb34 on 2008-08-28
Thanks for your help. I think I have figured out what the problem is. After searching the forums I found this []("http://ubuntuforums.org/showthread.php?t=765195&highlight=busy+box")  thread. It seems like a lot of people have been having problems with Ubuntu reading SATA drives. Also I see a lot of them have ASUS mobos. I think one of the solutions in there will defintely help.

---

### Post by kjb34 on 2008-08-28
[http://ubuntuforums.org/showthread.php?t=765195&highlight=busy+box]("http://ubuntuforums.org/showthread.php?t=765195&highlight=busy+box") Sorry this link.

---

### Post by kjb34 on 2008-09-01
I finally got around to installing 64 bit Hardy. At first tried the alt-install nothing. Then I used the live cd and used all_generic_ide floppy=off irqpoll in the boot options. This caused problems with my hard drive so I had to reinstall 32 bit but I made sure I set up a partition for the 64 bit. I tried the live cd again but this time, I used all_generic_ide floppy=off and I was able to install. When this restarted I had to use all_generic_ide floppy=off irqpoll to get it to boot properly. then I had to make changes in the boot menu so I wouldn't have to type every time I boot up.

---


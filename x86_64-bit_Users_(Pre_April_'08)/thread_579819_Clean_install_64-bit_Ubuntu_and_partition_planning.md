---
title: "Clean install 64-bit Ubuntu and partition planning"
date: 2007-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by annikos on 2007-10-18
Hi to all Ubuntu fans!

I plan to install Ubuntu 7.10 Desktop AMD64 in my PC.

I want to totally replace WinXP Prof. and I want Windows only through Virtualbox (is it really possible?)

I own a 60GB ATA disk (currently WinXP Prof. boot disk), 
a 80GB SATAII disk (currenty NTFS - I use it as a media disk) 
and a 300GB SATAII disk (currently Ubuntu Desktop 7.04 x86).
I have installed 1GB DDR dual channel in AMD Athlon 64 3500+

What do you suggest me to do? Do you think I have to install WinXP? 

Do you think I have to format everything? Where to put /,  /home and swap partitions and Windows (if it is needed)? 

Is it easy to find 64-bit drivers for my printers HP Laserjet 1000 and Canon MP600 and for my Logitech Orbit/Sphere MP?

I'm sorry for the bulk of my questions but I want to be sure about doing this BIG step... :-k
Thank you in advance,

Nikos

---

### Post by John.Michael.Kane on 2007-10-18
> **annikos said:**
> Hi to all Ubuntu fans!

[QUOTE=annikos;3560801]I plan to install Ubuntu 7.10 Desktop AMD64 in my PC.

I want to totally replace WinXP Prof. and I want Windows only through Virtualbox (is it really possible?)

I own a 60GB ATA disk (currently WinXP Prof. boot disk), 
a 80GB SATAII disk (currenty NTFS - I use it as a media disk) 
and a 300GB SATAII disk (currently Ubuntu Desktop 7.04 x86).
I have installed 1GB DDR dual channel in AMD Athlon 64 3500+

First off it's going to be a real tight fit running a virtual machine on only a gig of ram. This aside if you want to try to do it you can.

Taking your drive setup as is. I would switch somethings around.
300GB Would run the OS, and virtual stuff
60GB, and 80GB I would use for media/backup storage


> **annikos said:**
> What do you suggest me to do?
Personally I would relegate XP to it's own dedicated partition, and not run it in a virtual environment.

> **annikos said:**
> Do you think I have to install WinXP?
Sure I could say you don't need windows.however. that would not be very responsible. IMHO your use of, and keeping of windows will be based on your needs, and what machine end use will be. 
You will have to give us more info on what the machine will be used for. You will also have to ask yourself can you do your work with the currently available equivalents.

> **annikos said:**
> Do you think I have to format everything? Where to put /,  /home and swap partitions and Windows (if it is needed)?
Most users in the section would suggest backing up all data deemed valuable, and doing a clean install.

With regards to dual booting.Below is one known method of doing this.
[WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

Regarding how to layout your Ubuntu partition most users run. space amounts will vary.
/
swap
/home

> **annikos said:**
> Is it easy to find 64-bit drivers for my printers HP Laserjet 1000 and Canon MP600 and for my Logitech Orbit/Sphere MP?
HP Laserjet 1000 should work using the  foo2zjs free software printer driver. All you should have to do is navigate to System-->Administration-->Printer.

Canon PIXMA MP600 I'm unsure about this piece of hardware. From what I can find on it I would class it as a pain in the rear to get it working.

Logitech Orbit/Sphere MP some users on the forums have it classed as working with previous releases, some have it classed as not working.  you will have to test it .

> **annikos said:**
> I'm sorry for the bulk of my questions but I want to be sure about doing this BIG step... :-k
Thank you in advance,

Nikos

Hope these answers have helped you some.

---

### Post by annikos on 2007-10-18
First of all thank you very much for your instant reply!

> **SD-Plissken said:**
> 
First off it's going to be a real tight fit running a virtual machine on only a gig of ram. This aside if you want to try to do it you can.


So, I cannot afford having a virtual machine. I didn't expected it. But, I think you're right. If I use 512MB for the virtual machine, then what?

> **SD-Plissken said:**
> 
Taking your drive setup as is. I would switch somethings around.
300GB Would run the OS, and virtual stuff
60GB, and 80GB I would use for media/backup storage
Personally I would relegate XP to it's own dedicated partition, and not run it in a virtual environment.


So, I have to delete 60GB Windows XP boot disk? I think it's better having XP in a different disk instead of having it in the same disk with Linux.

> **SD-Plissken said:**
> 
Sure I could say you don't need windows.however. that would not be very responsible. IMHO your use of, and keeping of windows will be based on your needs, and what machine end use will be. 
You will have to give us more info on what the machine will be used for. You will also have to ask yourself can you do your work with the currently available equivalents.


I don't have any problem to work with the currently available linux equivalents but 
1. mytv.exe (a program to watch greek tv via internet - not p2p) doesn't run through wine (maybe because it's needed media player), 
2. Canon MP600 maybe works fine with printing but scanning is problematic even in x32 version, from what I read in threads
3. Games such as Fifa or PES I don't think they have equivalents in Linux and I don't know if wine can load them.

> **SD-Plissken said:**
> 
Most users in the section would suggest backing up all data deemed valuable, and doing a clean install.
With regards to dual booting.Below is one known method of doing this.
[WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")
Regarding how to layout your Ubuntu partition most users run. space amounts will vary.
/
swap
/home


HP Laserjet 1000 should work using the  foo2zjs free software printer driver. All you should have to do is navigate to System-->Administration-->Printer.

Canon PIXMA MP600 I'm unsure about this piece of hardware. From what I can find on it I would class it as a pain in the rear to get it working.

Logitech Orbit/Sphere MP some users on the forums have it classed as working with previous releases, some have it classed as not working.  you will have to test it .



Hope these answers have helped you some.
Thank you very much for your help! 

Nikos

---

### Post by John.Michael.Kane on 2007-10-18
> **annikos said:**
> First of all thank you very much for your instant reply!

So, I cannot afford having a virtual machine. I didn't expected it. But, I think you're right. If I use 512MB for the virtual machine, then what?
I'm not saying it wouldn't work, It's certainly  doable.however. you have ask at what cost. I'm pretty sure you would be heavy on the swap side of the picture. 

The only real way to find out if your hardware configuration is up for it is to run it, and see if how it runs is tolerable to you.

> **annikos said:**
> So, I have to delete 60GB Windows XP boot disk? I think it's better having XP in a different disk instead of having it in the same disk with Linux.

No you don't run Windows on the same drive as Ubuntu. That was only a suggestion. You can dual boot Windows, and Ubuntu using two drives.
[How to dual-boot Ubuntu and XP after installing them separately on two HDs]("https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs?highlight=%28two%29")

> **annikos said:**
> I don't have any problem to work with the currently available linux equivalents but 
1. mytv.exe (a program to watch greek tv via internet - not p2p) doesn't run through wine (maybe because it's needed media player), 
This might be an issue. I'm unsure as I don't use the program.

> **annikos said:**
> 2. Canon MP600 maybe works fine with printing but scanning is problematic even in x32 version, from what I read in threads
Like I said you have to do a trial and error run on this piece of hardware.

> **annikos said:**
> 3. Games such as Fifa or PES I don't think they have equivalents in Linux and I don't know if wine can load them.
Games working under Linux/Ubuntu will always depend on them being supported by wine or cedega.

> **annikos said:**
> Thank you very much for your help! 

Nikos

No problem. Please post should you have any further questions.

---

### Post by annikos on 2007-10-18
> **SD-Plissken said:**
> I'm not saying it wouldn't work, It's certainly  doable.however. you have ask at what cost. I'm pretty sure you would be heavy on the swap side of the picture. 

The only real way to find out if your hardware configuration is up for it is to run it, and see if how it runs is tolerable to you.

No you don't run Windows on the same drive as Ubuntu. That was only a suggestion. You can dual boot Windows, and Ubuntu using two drives.
[How to dual-boot Ubuntu and XP after installing them separately on two HDs]("https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs?highlight=%28two%29")


After your suggestions I think I'll keep my boot disk with XP (keeping my data) and I'll reinstall Ubuntu 7.10 x86_64 on the 300GB disk. Then I'll try installing XP on Virtualbox. If it is good for me then I'll keep it making things more convenient. And, I hope in the future to wipe out my XP disk!

Thank you again for your help.

Nikos

---

### Post by oodledoodle on 2007-10-19
further to the virtualbox question with windows, i installed windows yesterday (and im pretty much an ubuntu noob) with very little hassle. the problems that arose were easily remedied as virtualbox did a great job of telling me what they were and how to fix them. and xp works really nicely, you can maximise it in such a manner that you'd never guess you had linux running underneath! it's really neat and a great solution to those annoying windows only programs like my mobile phone updating software. 

if you have any problems with it give me a shout via pm or something. like i say im not an ubuntu expert and maybe we can stumble through it together :)

---

### Post by saru411 on 2007-10-19
my recommendation would be to keep the windows partion where it is, maybe shrink the size of the partition to free up some spare space if needed. next i would take the other hdds and put them in an LVM using the alt cd and make volumes with the approriate size for /boot(about 500mb max), / (this is root and should be about ~20 gb...this is your o/s), swap(2-4gb...depends on how much ram you have.less ram more swap), and the rest should be /home. once you are installed you can develop you home folder into seperate libraries, incoming folders, and such. I run multiple software raids on my pc and have set up lvm before. LVM is very useful for when you find out that you didnt make a partition big enough. you can always shrink and grow these volumes according to your needs.

cheers

---


---
title: "How do I reformat &amp; reorganize my hard disk after installing Ubuntu?Boot order?"
date: 2006-10-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Nilanjan on 2006-10-11
The problem is that installing Ubuntu has made a terrible mess of my hard disk- since I attempted installation 5 or 6 times and the installer kept crashing. The free 30 GB I had allotted for it after partitioning with windows has been further subdivided into 8/9+ seperate sub partitions and swaps! How do I now reconcile all the free unutilised disk space that is left in between in different patches/unused partitions/unutilised space/unutilised swaps - almost 20GB and bring it together for use with windows?? how do I tell which spaces are being used by ubuntu and which are not?? Because this is wasting so much precious hard disk space. How do I reconcile all this unused hard disk space and reformat /organise it for windows to use?

Also, how do I get the machine to boot windows first by default rather
than ubuntu from the chainloader?? What an ordeal.

:-k Thank you.

---

### Post by bodhi.zazen on 2006-10-11
I would fdisk and re-do your patitioning scheme.

As to booting windows first, edit /boot/grub/menu.lst and change your default.

---

### Post by ReaderRat on 2006-10-11
> **Nilanjan said:**
> The problem is that installing Ubuntu has made a terrible mess of my hard disk- since I attempted installation 5 or 6 times and the installer kept crashing. The free 30 GB I had allotted for it after partitioning with windows has been further subdivided into 8/9+ seperate sub partitions and swaps! How do I now reconcile all the free unutilised disk space that is left in between in different patches/unused partitions/unutilised space/unutilised swaps - almost 20GB and bring it together for use with windows?? how do I tell which spaces are being used by ubuntu and which are not?? Because this is wasting so much precious hard disk space. How do I reconcile all this unused hard disk space and reformat /organise it for windows to use?

Also, how do I get the machine to boot windows first by default rather
than ubuntu from the chainloader?? What an ordeal.

:-k Thank you.

Partitioning? Try This: [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

---

### Post by Nilanjan on 2006-10-13
> **bodhi.zazen said:**
> I would fdisk and re-do your patitioning scheme.

As to booting windows first, edit /boot/grub/menu.lst and change your default.
Thanks, but where do i type this line:edit /boot/grub/menu.lst?? And then how do I change the boot order? Pls tell me step by step. Pardon the ignorance.
Thanks!

---

### Post by morequarky on 2006-10-13
ReaderRat is telling you to reinstall windows first then Ubuntu... then boot into Ubuntu and in a command-line window type "sudo gedit /boot/grub/menu.lst"

You probably have to enter your password.

In the gedit window that opens, change the order.  save and exit.  reboot.

KK :)

---

### Post by Nilanjan on 2006-10-13
I spent so much time - over 10 days installing Ubuntu - it was virtually impossible to install the 64 bit version - and now you wantme to install Ubuntu all over again and ALSO Windows??! Thats presposterous! Well I already have both windows and Ubuntu installed so cant I type this into the ubuntu terminal window as it is on my system already??? Also, how do I connect to the internet through Ubuntu, thru both dial up and cable??

Thanks.

---

### Post by morequarky on 2006-10-13
> **Nilanjan said:**
> I spent so much time - over 10 days installing Ubuntu - it was virtually impossible to install the 64 bit version - and now you wantme to install Ubuntu all over again and ALSO Windows??! Thats presposterous! Well I already have both windows and Ubuntu installed so cant I type this into the ubuntu terminal window as it is on my system already??? Also, how do I connect to the internet through Ubuntu, thru both dial up and cable??

Thanks.

He wants you to reinstall because you made so many basicly useless partitions on your hard drive for Ubuntu.

I had like 8 partitions for Ubuntu for a total of like 10 on my drive, I ended with partitions too small because I didn't know how much Ubuntu used which parts of it's filesystem.  I suggest you read up a lot on what each "directory" (partition) does.  Very different for Linux.

I had to reinstall.  When you install you only need one '/' partition, one '/home' partition, and one 'linux-swap' partition.

If you reinstall, keep '/home'.  Everything else has to go.

Currently I had boot issues after my wife messed up my computer so I reinstalled with an added /boot partition just so I can fix it easier if my wife has another day where she thinks she knows how to install winblows.

10 days to install??? it only takes us an hour at most.  What did you do to make it so long?

You do NOT need to reinstall to fix the boot issue.  Just open a terminal and type the command like my last message said.

Hope that helps.

---

### Post by Nilanjan on 2006-10-13
> **morequarky said:**
> He wants you to reinstall because you made so many basicly useless partitions on your hard drive for Ubuntu.

I had like 8 partitions for Ubuntu for a total of like 10 on my drive, I ended with partitions too small because I didn't know how much Ubuntu used which parts of it's filesystem.  I suggest you read up a lot on what each "directory" (partition) does.  Very different for Linux.

I had to reinstall.  When you install you only need one '/' partition, one '/home' partition, and one 'linux-swap' partition.

If you reinstall, keep '/home'.  Everything else has to go.

Currently I had boot issues after my wife messed up my computer so I reinstalled with an added /boot partition just so I can fix it easier if my wife has another day where she thinks she knows how to install winblows.

10 days to install??? it only takes us an hour at most.  What did you do to make it so long?

You do NOT need to reinstall to fix the boot issue.  Just open a terminal and type the command like my last message said.

Hope that helps.


Ok. Well I didnt make the so many useless partitions on my disk - Ubuntu did. It actually took over a month to install, because the damn 64 bit version wouldnt install on my AMD lap. The installer kept crashing. Finally a few days ago I decided to stay up 2 nights and the damn thing finally took over 12 hrs to install after crashing 8 times - creating nine partitons and swaps! the good thing was I just left my lap on and went out leaving it on battery power. When i came back 12 hrs later, everything was neatly installed - the lap had installed itself - and turned its own power off. Now isnt that great!?! I definitely cant reinstall now after this ordeal - i cant go thru it again. 

But hey man - thanks about the boot issue!! Ok?!](*,)

---

### Post by Nilanjan on 2006-10-13
P.S. Do you know how to connect to the internet using Ubuntu - thru both dial up and cable broadband?

---

### Post by argie on 2006-10-13
well, you don't really need to reinstall windows to use fdisk. I think if you make a boot floppy in windows, fdisk will be on it.

Also, why not just use the alternate CD and delete all the ubuntu partitions and make the partitions yourself. I've noticed that the alternate CD has less trouble. (none, in my case)

Also <code>gksudo gedit /boot/grub/menu.lst</code> and copy pasting the relevant sections should be easy.

---

### Post by Nilanjan on 2006-10-13
> **morequarky said:**
> He wants you to reinstall because you made so many basicly useless partitions on your hard drive for Ubuntu.

I had like 8 partitions for Ubuntu for a total of like 10 on my drive, I ended with partitions too small because I didn't know how much Ubuntu used which parts of it's filesystem.  I suggest you read up a lot on what each "directory" (partition) does.  Very different for Linux.

I had to reinstall.  When you install you only need one '/' partition, one '/home' partition, and one 'linux-swap' partition.

If you reinstall, keep '/home'.  Everything else has to go.

Currently I had boot issues after my wife messed up my computer so I reinstalled with an added /boot partition just so I can fix it easier if my wife has another day where she thinks she knows how to install winblows.

10 days to install??? it only takes us an hour at most.  What did you do to make it so long?

You do NOT need to reinstall to fix the boot issue.  Just open a terminal and type the command like my last message said.

Hope that helps.

> **argie said:**
> well, you don't really need to reinstall windows to use fdisk. I think if you make a boot floppy in windows, fdisk will be on it.

Also, why not just use the alternate CD and delete all the ubuntu partitions and make the partitions yourself. I've noticed that the alternate CD has less trouble. (none, in my case)

Also <code>gksudo gedit /boot/grub/menu.lst</code> and copy pasting the relevant sections should be easy.


If I could have deleted all the partitions and made them myself I would have. The problem was that manual partitioning didnt work, so I had to do it automatically. The alternate CD is what has caused all the problem in 64 bit, because it was so diffficult to install - the install icon never responded or the installer kept crashing. Thanks.

---

### Post by elchinovi on 2006-10-13
For what I've heard, the 64bit version is for more experienced users, so I would suggest that you go ahead and install the 386 version, wich will run as good as the 64 bit, and when you get a little more experience, you go and try the 64bit...
Hope that helps!

---

### Post by morequarky on 2006-10-13
manual partitioning didn't work...By some chance did you lose your partition table?  The live CD can make a new one for you.  My wife installed XP Home inside of a XP64bit partition recently, how I don't know, and it wipped my partition table.  You should never be forced to use automatic partitioning, but I can imagine you feeling that way if your partition table was missing.

---

### Post by Nilanjan on 2006-10-13
> **morequarky said:**
> manual partitioning didn't work...By some chance did you lose your partition table?  The live CD can make a new one for you.  My wife installed XP Home inside of a XP64bit partition recently, how I don't know, and it wipped my partition table.  You should never be forced to use automatic partitioning, but I can imagine you feeling that way if your partition table was missing.
I dont know if I lost my partition table- must have- but whenvr i partitioned with the manual partition editor - it didnt do what i wanted it to do and the installer kept crashing - after waiting for HRS! So I was forced to use the automatic partitioning which was better cos it was more convenient. I dont think I lost my partition table because all the partitions were showing up clearly - but the manual editor just didnt do what I wanted it to do. Finally when I tried editing the partitions thru windows partition manager- which is much better- I deleted one of the crucial ubuntu partitions by mistake i think, cos i couldnt make out which was the valid used partition and which was not. After that NO OS would load - neither windows nor Ubuntu. I just got Grub loading error 17, so I was really screwed, nothing was working. So I was forced to reload from the Live CD and reinstall  Ubuntu for 12 hrs, after which both windows Pro(as it was) and ubuntu came back - fortunately no data had been lost from my windows files and everything was it was - the windows partition was intact. It was just loading now thru Ubuntus chainloader, so when Ubuntu got deleted it couldnt load either. Reinstalling Ubuntu did the trick, but I would like it the other way round- loading ubuntu thu windows since I would still like to leave windows as my primary OS, since that is what the machine is fine tuned to and understands best. This ubuntu partion editor is v slow and quite useless. 

I still dont know how to rectify the 9 partitions that the 30 GB i had allotted Ubuntu has beeen divided into and how to consolidate it into 1 partiton and reformat the unused space for use with windows - even after all these posts on this forum. Can I add and reformat the unused space to my existing windows C: partition? How? What a nightmare.

Thanks.

---

### Post by confused57 on 2006-10-13
You might want to boot into Ubuntu, open a terminal(Applications---Accessories---Terminal) and post the output(s) of:
```
sudo fdisk -l
```
The -l is a small "L"

and

```
cat /etc/fstab
```

If you can determine which partitions you want to delete, you can probably use the gparted live cd:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

### Post by Nilanjan on 2006-10-14
> **Nilanjan said:**
> I dont know if I lost my partition table- must have- but whenvr i partitioned with the manual partition editor - it didnt do what i wanted it to do and the installer kept crashing - after waiting for HRS! So I was forced to use the automatic partitioning which was better cos it was more convenient. I dont think I lost my partition table because all the partitions were showing up clearly - but the manual editor just didnt do what I wanted it to do. Finally when I tried editing the partitions thru windows partition manager- which is much better- I deleted one of the crucial ubuntu partitions by mistake i think, cos i couldnt make out which was the valid used partition and which was not. After that NO OS would load - neither windows nor Ubuntu. I just got Grub loading error 17, so I was really screwed, nothing was working. So I was forced to reload from the Live CD and reinstall  Ubuntu for 12 hrs, after which both windows Pro(as it was) and ubuntu came back - fortunately no data had been lost from my windows files and everything was it was - the windows partition was intact. It was just loading now thru Ubuntus chainloader, so when Ubuntu got deleted it couldnt load either. Reinstalling Ubuntu did the trick, but I would like it the other way round- loading ubuntu thu windows since I would still like to leave windows as my primary OS, since that is what the machine is fine tuned to and understands best. This ubuntu partion editor is v slow and quite useless. 

I still dont know how to rectify the 9 partitions that the 30 GB i had allotted Ubuntu has beeen divided into and how to consolidate it into 1 partiton and reformat the unused space for use with windows - even after all these posts on this forum. Can I add and reformat the unused space to my existing windows C: partition? How? What a nightmare.

Thanks.


Im not going to reinstall Ubuntu again - once was enough - dont ask me to sit up for more nights and do it again - Im not going to. If i can reformat without reinstalltion thats OK but i dont know if I can do that without erasing ubuntu. In the partition editor, I dont know which partition I shd erase and reformat. And whether I shd do it?

---

### Post by confused57 on 2006-10-14
The first command I gave(sudo fdisk -l) just **displays** your partition table(Windows, Ubuntu, swap, and all the various and sundry partitions that you want to get rid of).
The second command(cat /etc/fstab) shows your partition mount points.

You might also want to post the output of your /boot/grub/menu.lst:
```
cat /boot/grub/menu.lst
```
menu.lst is short for menu.list, not menu.first
You really just need to post the kernel entries for booting Windows & Ubuntu.

You shouldn't have to reinstall Ubuntu or Windows, but if you can give more information about your partition tables, someone may be able to help you.  None of the commands I gave you will affect your installations, but it will display information that could help.

You might be able to delete all the unwanted partitions and create a single FAT partition that you can use to share files between Windows & Linux.

Here's a thread you may be interested in reading, particularly the advice given by Herman for using the gparted live cd:
[http://www.ubuntuforums.org/showthread.php?t=276842](http://www.ubuntuforums.org/showthread.php?t=276842)

---

### Post by Nilanjan on 2006-10-14
I dont understand, where do I have to type all these commands?? When I typed them in terminal they didnt work.

Thank you.

---

### Post by Nilanjan on 2006-10-14
Ubuntu - too difficult to install and partition/format.

---

### Post by Nilanjan on 2006-10-14
:confused: Ubuntu - too difficult to install and partition/format.

---

### Post by morequarky on 2006-10-14
Can I ask a pretty basic question?

Why do you truly NEED Ubuntu?  What brought you to Linux?

---

### Post by Nilanjan on 2006-10-14
> **morequarky said:**
> Can I ask a pretty basic question?

Why do you truly NEED Ubuntu?  What brought you to Linux?

Its the only 64 bit OS readily around. Met Mark Shuttleworth ,the creator of Ub., at a conference in New Delhi - Linux Asia - begining of this year. This was where i was first introduced to Ub. Everybody sung such high praises of it, that I felt that i just had to try it - in fact everyone insisted that I do so. Thats why.

Im sorry that its made such a mess of my hard disk, and none of the advice I have received here has really helped or made much sense to me - since Im too scared to crash, do anything to the hard disk or reinstall. im afraid the system wont recover. I wish people here would speak in terms of steps to give step by step explanations of what to really do. I dont even know where to type in all these commands that have been suggested at this thread. Where do I type them in?

Is that ok? is there a problem? thanks.

---

### Post by morequarky on 2006-10-14
You could attempt to get Windows XP Professional 64 if you really wanted it.  I guess it isn't that readily available.

You type the commands in a terminal.  Terminal is located inside Ubuntu.
Select Applications at the top of the screen.
Select Accessories.
Select Terminal.(more commonly refered to as Apps - Accessories - Terminal)

You will be given a prompt similar to running "run" in windows and then typing "command".

Once your in the terminal, in Ubuntu.  Type the commands character for character one at a time.  You should be able to cut and paste the output of the commands for us to help fix your system. (cuting and pasting in the terminal is done with 'ctrl - shift - c' and 'ctrl - shift - v')

It sounds like your just playing with Ubuntu and don't really NEED it.  Perhaps after some time you'll feel more comfortable with Ubuntu and you will be on here helping others who have never touched it before.

---

### Post by Nilanjan on 2006-10-15
> **morequarky said:**
> You could attempt to get Windows XP Professional 64 if you really wanted it.  I guess it isn't that readily available.

You type the commands in a terminal.  Terminal is located inside Ubuntu.
Select Applications at the top of the screen.
Select Accessories.
Select Terminal.(more commonly refered to as Apps - Accessories - Terminal)

You will be given a prompt similar to running "run" in windows and then typing "command".

Once your in the terminal, in Ubuntu.  Type the commands character for character one at a time.  You should be able to cut and paste the output of the commands for us to help fix your system. (cuting and pasting in the terminal is done with 'ctrl - shift - c' and 'ctrl - shift - v')

It sounds like your just playing with Ubuntu and don't really NEED it.  Perhaps after some time you'll feel more comfortable with Ubuntu and you will be on here helping others who have never touched it before.
Thanks a lot. Well im not really playing - im trying it out- trying to learn - and see if it has any real advantages and if i can use it daily for my work. Im sure its a bful sytem and alternative to windows, v well designed. I used to be a unix programmer 13 yrs ago, so thats where my interest lies - in using unix - but i am very rusty/out of touch. At the moment I find the ubuntu links to be v slow in responding. I have to click all icons and bars over 2/3 times before they respond. This is too slow. Obviously the system isnt synced to my turion 64 bit system. I would have expected the 64 bit OS to whiz past - this is the only one available now- but even to open topics in the help page I have to keep clicking many times and wait minutes/ages, before they open. Obviously it isnt fine tuned to my lap. So there is a problem - to slow to respond to the clicks right now. Also if I cant connect to the internet then this isnt of any use - since all my work will require the transmission and receipt of data. If this doesnt happen, then obviously Ubuntu doeas become a plaything for me, and has no real advantages until I can use it for something useful in real life or work. At the moment it is so slow/reluctant  to respond even to the clicks - i have to wrestle with the system - that I dont really see where the advantage of the 64 bit OS is. And it is necessary that I be able to connect to the net. 

But I love learning new things and experimenting and that s why I  have installed Ub. and tried enjoying it - to hope that it is a viable alternative to windows. So thank you for yr reply, and yes, I do hope that soon I will be helping others learn to use it! As I said i am experimenting and learning. I had red hat fedora core4 linux installed before and Ub. is certainly better.

Thanks for the help. This step by step guide you have given is really good. I just wonder if i cut a command in windows, will it then transfer in memory to paste in ubuntu? i dont think so. So i will have to write the commands down.

Thank you!

---

### Post by Nilanjan on 2006-10-15
> **morequarky said:**
> You could attempt to get Windows XP Professional 64 if you really wanted it.  I guess it isn't that readily available.

You type the commands in a terminal.  Terminal is located inside Ubuntu.
Select Applications at the top of the screen.
Select Accessories.
Select Terminal.(more commonly refered to as Apps - Accessories - Terminal)

You will be given a prompt similar to running "run" in windows and then typing "command".

Once your in the terminal, in Ubuntu.  Type the commands character for character one at a time.  You should be able to cut and paste the output of the commands for us to help fix your system. (cuting and pasting in the terminal is done with 'ctrl - shift - c' and 'ctrl - shift - v')

It sounds like your just playing with Ubuntu and don't really NEED it.  Perhaps after some time you'll feel more comfortable with Ubuntu and you will be on here helping others who have never touched it before.

I guess I'll have to write down the input and output of the commands since I havent managed to connect ubuntu to the net yet and the cut and paste wont transfer to the windows memory & windows from where I connect to the net and acccess this forum. right? Am I getting too involved?

Thanks.:-k

---

### Post by Nilanjan on 2006-10-16
I am a little confused, exactly what command shd I type in terminal to change the boot order and make windows my default startup OS?

This is very complicated.

---

### Post by Sef on 2006-10-17
First, I moved this thread to the 86x 64-bit Users forum.

Second, [Read this sticky.]("http://ubuntuforums.org/showthread.php?t=191205")

---

### Post by confused57 on 2006-10-17
> **Nilanjan said:**
> I am a little confused, exactly what command shd I type in terminal to change the boot order and make windows my default startup OS?

This is very complicated.

Here's how to change the grub default OS:
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by Nilanjan on 2006-10-19
Sorry the boot order change coomand is not working. After typing sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup in the terminal prompt I am getting Sudo: ....... no such command etc.

What shd I do?

Thank you.

---

### Post by Nilanjan on 2006-10-22
The sudo command you gave me on "how to change the default OS" is not working. When I type it into terminal it says sudo: no such command. So what do I do? How do I change the default boot OS??

---

### Post by bodhi.zazen on 2006-10-22
> **Nilanjan said:**
> The sudo command you gave me on "how to change the default OS" is not working. When I type it into terminal it says sudo: no such command. So what do I do? How do I change the default boot OS??

Edit /boot/grub/menu.lst:```
sudo gedit /boot/grub/menu.lst
```

See here for details:[Grub How to set default OS](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

---

### Post by Nilanjan on 2006-10-22
Sorry I do not understand. Do I type Edit /boot/grub/menu.lst in terminal? Is that all i have to type?  Pls explain step by step.

---

### Post by bodhi.zazen on 2006-10-22
> **Nilanjan said:**
> Sorry I do not understand. Do I type Edit /boot/grub/menu.lst in terminal? Is that all i have to type?  Pls explain step by step.

LOL :lol:

In a terminal type (or copy-paste)```
sudo gedit /boot/grub/menu.lst
```

This will open menu.lst in an editor (gedit).

Look for the line "default        0" (it may be another # then 0).

Change the number to point to your Windows entry. I assume your default number is 0 and you have an Ubuntu, Ubuntu failsafe, and windows entry. In that case, the default should be changed to 2.

If that is not your layout, just count the entries starting with 0 (not 1). ie first entry =0, second entry =1, ...

An entry is an OS (ie title  Ubuntu).

Save and exit.

That is all there is to it.

If you are unsure, post the content of the file (/boot/grub/menu.lst).

Note: that is a small "L" and not the number 1.

8-)

---

### Post by Nilanjan on 2006-10-23
> **bodhi.zazen said:**
> LOL :lol:

In a terminal type (or copy-paste)```
sudo gedit /boot/grub/menu.lst
```

This will open menu.lst in an editor (gedit).

Look for the line "default        0" (it may be another # then 0).

Change the number to point to your Windows entry. I assume your default number is 0 and you have an Ubuntu, Ubuntu failsafe, and windows entry. In that case, the default should be changed to 2.

If that is not your layout, just count the entries starting with 0 (not 1). ie first entry =0, second entry =1, ...

An entry is an OS (ie title  Ubuntu).

Save and exit.

That is all there is to it.

If you are unsure, post the content of the file (/boot/grub/menu.lst).

Note: that is a small "L" and not the number 1.

8-)
OK. I just did that but it showed the contents of the menu.lst file as being empty and said the root file / was not opening. So i tried typing default[3] in the empty menu.lst file and saving and closing and rebooting but it did not work. Boot order is still the same.  So what does one do now?

When one boots after the list of OSs it gives the option to type e for edit c for command line etc. when i typed e for edit it gave a list which included savedefault. Is it possible to change the boot order from here?? 
Im sorry but i dont know why i still havent been able to change the boot order.

---

### Post by confused57 on 2006-10-23
Your menu.lst should not be empty, try copying & pasting the command in a terminal:
```
sudo gedit /boot/grub/menu.lst
```

You can copy by highlighting the command in your browser, then in the terminal you just press the middle mouse button(or scroll wheel).

---

### Post by Nilanjan on 2006-10-23
> **confused57 said:**
> Your menu.lst should not be empty, try copying & pasting the command in a terminal:
```
sudo gedit /boot/grub/menu.lst
```

You can copy by highlighting the command in your browser, then in the terminal you just press the middle mouse button(or scroll wheel).

Thanks! Finally got that! Had to type default 4 for my boot order to bring up windows. Thanks! 
I assume one uses the same command to change the time delay before the system boots?

---

### Post by bodhi.zazen on 2006-10-23
> **Nilanjan said:**
> Thanks! Finally got that! Had to type default 4 for my boot order to bring up windows. Thanks! 
I assume one uses the same command to change the time delay before the system boots?

Yes. ```
sudo gedit /boot/grub/menu.lst
```The line you are looking for is:> timeout        10

---

### Post by pony-tail on 2006-10-24
I have had issues with K/Ubuntu mis-detecting the order of my drives in 2 machines (Asus P4C800-E deluxe and A8NSli-Premium ) both machines have 4 hard drives and dual boot with windows , both have separate hard drives for Ubuntu and windows , both mis behave once the third HDD is installed .
Work around on the P4C800 is to boot windows off the onboard Promise controller and keep the storage drives on the Intel controller.
Awork around for the A8N is yet to be found at present I have the storage drives on a PCI Sil 3112 Satalink controller card and boot off the onboard nVidia controller's first and second port as I am unable to use the third and fourth with both windows and Ubuntu installed as Ubuntu mis detects the third controller as the first every second (give or take ) boot and will not boot reliably with any drives on 3 & 4 - I have no Idea as to why but Gentoo works with both machines - Mepis works on the P4C800 but not the A8N -Debian Sarge works on both - Sid only on the P4C800 - the issue seems to be in how the kernel loads the driver and wether they are modular or compiled into the kernel as I found that Gentoo's "Genkernel" does the same as the Ubuntu kernel but a Kernel compiled for the machine works correctly.
I spent a couple of weeks mucking with this and did not come up with a result that I am happy with - The result on the P4c800 I can live with - the A8N is another story !

---

### Post by Nilanjan on 2006-10-25
Well I find 64 bit ubuntu too slow clumsy complicated and difficult to use compared to windows. 

Also the controls and buttons and commmands in the toolbars for opening firefox etc. are too slow and unresponsive. They dont respond to the touchpad taps on my lap. I literally have to bang and click many times to make them work. NOTHING OPENS EASILY.

Too slow and clumsy/difficult to use. :(

---

### Post by Nilanjan on 2006-11-03
Ubuntu 64 bit - tooo slow. :neutral:

---

### Post by Nilanjan on 2006-11-10
Any replies to this?

---


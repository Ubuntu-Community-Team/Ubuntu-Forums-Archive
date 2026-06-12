---
title: "please wait loading kernel..."
date: 2006-01-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by imacQ on 2006-01-06
installation seems to be sucessful, but on reboot it gets as far as "Please wait, loading kernal..."

i can't even turn it off by pushing power button? kinda scary pulling the plug!

searched forum and read some similar posts. does anybody know what to do to get past this? :???: 

installed on tray loader imac g3 333mhz. worked fine on the 6gb drive i had in there. now have a 20gb drive in same imac and i'm installing on freespace  approx. 12gb partition. 

i do hope someone has an answer.

---

### Post by imacQ on 2006-01-07
okay, where are all the great saturday morning :cool: linux geeks? 

ubuntu is great! i want it back; however, at this point it's turning my imac into a doorstop! 

i did another clean install of os 9 last night (after leaving post here and getting no response) 
initialized hd and left unallocated partition for ubuntu. os 9 clean installation flawless, and everything goes well with ubuntu install, until reboot without cd, and then the same f-ing thing "Please wait, loading kernel..." come onnnnnnnnnnn where's the damn kernel and how do i get going here?
 
please help me and the kernel we're desperate.

---

### Post by imacQ on 2006-01-08
problem solved.

well, after much surfing google/forums/etc. and intializing/partitioning/installing both os 9 and ubuntu several times, i came up to white screen after reboot of ubuntu install. i searched "white screen" on this forum and found:

[http://ubuntuforums.org/showthread.php?t=108266&highlight=white+screen](http://ubuntuforums.org/showthread.php?t=108266&highlight=white+screen) 

THANK YOU! :cool:  oswaldkelso  

"imac models from 233mhz through to 333mhz can only recognise the first 8gb (7.95gb) of a harddrive so even if you partition a larger harddrive into many smaller 7.95gb sections the mac can only boot from the first 7.95gb so all  os's osx, os 9, linux,must be within this first 7.95gb.

once booted you can use any other 8gb image to store your data"

---

### Post by flygis on 2006-10-03
> **imacQ said:**
> 
"imac models from 233mhz through to 333mhz can only recognise the first 8gb (7.95gb) of a harddrive so even if you partition a larger harddrive into many smaller 7.95gb sections the mac can only boot from the first 7.95gb so all  os's osx, os 9, linux,must be within this first 7.95gb.

once booted you can use any other 8gb image to store your data"

Please help me.
I am in this situation and understand what you're writing. But not how to do the partitioning.
Since I can't boot the live CD, I have to cope with the text based partitioner and I just can't figure it out how to set things up...

The HD shows as hda 20.4GB. The options is to use all of it (obviously a bad thing) or set up the partitions manually.
Exactly how should I set it up to work? Please help me.

/Johan

---

### Post by linear on 2006-10-03
There is a thread about partitioning Mac disks [here]("http://www.ubuntuforums.org/showthread.php?t=89960"). Haven't tried it myself, so I can't explain anything in it that may be obscure.

---

### Post by flygis on 2006-10-04
Thanks for the link linear, however my setup will not involve dual boot.

My intention is to have only linux (xubuntu for a start) on my system. I can partition my 20GB hd inside OS9 to several partitions, but the xubuntu installer (text mode) just gives me the options to use the hole disk, 20GB, or to partition it manually. It doesn't detect the partitions made with OS9.

If anyone could give me an example of how to partition the disk manually so that xubuntu will install only in the first 7GB, then I would be a happy child.

/Johan

---

### Post by oswaldkelso on 2006-11-17
> **flygis said:**
> Thanks for the link linear, however my setup will not involve dual boot.

My intention is to have only linux (xubuntu for a start) on my system. I can partition my 20GB hd inside OS9 to several partitions, but the xubuntu installer (text mode) just gives me the options to use the hole disk, 20GB, or to partition it manually. It doesn't detect the partitions made with OS9.

If anyone could give me an example of how to partition the disk manually so that xubuntu will install only in the first 7GB, then I would be a happy child.

/Johan
1. use the alt cd
2. the **easy way** is to use your os 9 or osx install disk to partition your drive.

3. in os 9 use disk utility on your install cd to partition your drive into 2 or 3 partitions,the first being 7.95gb
4. make all 3 partitons linux first then go and make the first free space.
eject the cd.
5.start the xubuntu install cd by holding down the c key on start up and  go through the install but select "install to largest free space"
6. any problems with seeing the screen on boot seee this thread [http://ubuntuforums.org/showthread.php?t=296870](http://ubuntuforums.org/showthread.php?t=296870) 

good luck

---


---
title: "installing 64bit ubuntu"
date: 2006-06-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jonathan987 on 2006-06-28
hey guys, I'm a real noob with linux; first time installer here, so I'm looking for some help if you are willing to give it!!!

My question: I have just built a new system that uses the am2 socket! I have heard that the live cd doesn't work well with this.....but I don't know much about linux so the alternative seems scary to me! The other thing is, I would like to setup the OS on a Raid 1 configuration...so I have been told to do this that you have to use the alternative anyways........what about the dvd image?!?! will this work, what is the difference between the alternative, just the regular 64bit install and the dvd image......the description on the download page is "weak sauce" at best....!?!?

so I guess that's it for now, thanks for reading and I hope someone can help!

Jonathan

---

### Post by Kilz on 2006-06-29
[QUOTE=Jonathan987]hey guys, I'm a real noob with linux; first time installer here, so I'm looking for some help if you are willing to give it!!!

My question: I have just built a new system that uses the am2 socket! I have heard that the live cd doesn't work well with this.....but I don't know much about linux so the alternative seems scary to me! The other thing is, I would like to setup the OS on a Raid 1 configuration...so I have been told to do this that you have to use the alternative anyways........what about the dvd image?!?! will this work, what is the difference between the alternative, just the regular 64bit install and the dvd image......the description on the download page is "weak sauce" at best....!?!?

so I guess that's it for now, thanks for reading and I hope someone can help!

Jonathan[/QUOTE]
I don't know much about the dvd, my understanding is that its a more complete live experience that holds more programs. Don't be scared of the alternate install cd. The difference is it doesn't have a live cd experience. Its just an installer. It also doesn't have all the fancy graphics that a live experience dose. But its easy to understand and use. Since it isn't a live cd, when there are choices you use the arrows on your keyboard to chose and enter to select. Then type in the answers to questions like your username and password. Sorry I cant give you any info  on a raid setup, maybe someone else can.

---

### Post by jvictor on 2006-06-29
IMHO its like the fear of learning swimming where one is scared that he'll get drowned and turns away :). 

If u have a new computer u have nothing to lose .. whats the max damage u have ?.. maybe 25 mins installing the stuff ?!! :rolleyes: 

just go ahead and try it :) 

Best of luck happy ubuntu-ing  :)

---

### Post by Jonathan987 on 2006-06-29
thanks for your help guys, I burned the alternate version and tried installing it in text mode.....only to have a crc error when it says it says it"s loading linux.......so I"m redownloading the iso....and re burning.......lets all hope it works.....must have been the torrent......although it said it dowloaded correctly!

---

### Post by Kilz on 2006-06-29
[QUOTE=Jonathan987]thanks for your help guys, I burned the alternate version and tried installing it in text mode.....only to have a crc error when it says it says it"s loading linux.......so I"m redownloading the iso....and re burning.......lets all hope it works.....must have been the torrent......although it said it dowloaded correctly![/QUOTE]
[Check the md5 sum]("https://help.ubuntu.com/community/HowToMD5SUM") before burning the cd. There should be a md5 sum file where you downloaded the torrent. That way you wont end up with any shiny coasters with holes in the middle.

---

### Post by Jonathan987 on 2006-06-29
Yeah, I've now burnt 3 cds from two different images (one from BT the other from an ftp on the downloads page). Both cds either give me one of two different errors when I try and install: crc error -system halted or invalid compressed format (err=1) ..............so I highly doubt that I am burning these cd's incorrectly......I found this: [http://acm.case.edu/pipermail/sigunix/2003-June/001712.html](http://acm.case.edu/pipermail/sigunix/2003-June/001712.html)

and it seems that I now have to troubleshoot on some random crap....yes I have already unplugged all the usb devices (as mentioned in the link above)!!!...........yay for linux and how user friendly it is.......sigh

just read: [http://www.ubuntuforums.org/showthread.php?t=189915&highlight=crc+error](http://www.ubuntuforums.org/showthread.php?t=189915&highlight=crc+error)
[http://www.ubuntuforums.org/showthread.php?t=188657&highlight=crc+error](http://www.ubuntuforums.org/showthread.php?t=188657&highlight=crc+error)
[http://www.ubuntuforums.org/showthread.php?t=188018&highlight=crc+error](http://www.ubuntuforums.org/showthread.php?t=188018&highlight=crc+error)

can anyone verify that the iso isn't supported with nero in windows (this is what I am using)....I thought I was going to run into troubles, but not during the freakin installation!

I am burning at slow speeds there are two different types of media between the 3 cds...

---

### Post by Kilz on 2006-06-29
[QUOTE=Jonathan987]Yeah, I've now burnt 3 cds from two different images (one from BT the other from an ftp on the downloads page). Both cds either give me one of two different errors when I try and install: crc error -system halted or invalid compressed format (err=1) ..............so I highly doubt that I am burning these cd's incorrectly......I found this: [http://acm.case.edu/pipermail/sigunix/2003-June/001712.html](http://acm.case.edu/pipermail/sigunix/2003-June/001712.html)

and it seems that I now have to troubleshoot on some random crap....yes I have already unplugged all the usb devices (as mentioned in the link above)!!!...........yay for linux and how user friendly it is.......sigh

just read: [http://www.ubuntuforums.org/showthread.php?t=189915&highlight=crc+error](http://www.ubuntuforums.org/showthread.php?t=189915&highlight=crc+error)
[http://www.ubuntuforums.org/showthread.php?t=188657&highlight=crc+error](http://www.ubuntuforums.org/showthread.php?t=188657&highlight=crc+error)
[http://www.ubuntuforums.org/showthread.php?t=188018&highlight=crc+error](http://www.ubuntuforums.org/showthread.php?t=188018&highlight=crc+error)

can anyone verify that the iso isn't supported with nero in windows (this is what I am using)....I thought I was going to run into troubles, but not during the freakin installation!

I am burning at slow speeds there are two different types of media between the 3 cds...[/QUOTE]
Did you check the md5 sum and still have errors? the md5 sum is the hash of the file. It makes sure you got an error free file. If you have a iso with an error in it, burning slow is just going to give you a slow burnt error. If you are still using windoz there are programs that do md5 sums. [Look here]("http://www.pc-tools.net/win32/md5sums/") of google for one.

---

### Post by Jonathan987 on 2006-06-29
my isos were md5 checked and working fine.....sorry I didn't post it earlier......I didn't think to test the memory (because it was brand new Kingston HyperX RAM), but one stick is completely f*cked up.

I then get the the scanning drives page and it finishes it, and just hangs, my buddy who has been using gentoo for the last 4 years came over and said it's probably the ubuntu and lack of support for am2 chipset....I read another post on this forum confirming this and that the person had better luck with fedora....this is what I'm now trying......thanks for your help and if you have any other ideas, I'll be willing to try them out!

---

### Post by jvictor on 2006-06-30
Just a sugesstion try a different CD-DRIVE and run the install .. I had this problem of CRC-ERROR coz the DvD+RW wasnt supported in 5.10

---


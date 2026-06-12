---
title: "Failed to start the x server (new to linux)"
date: 2006-07-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by foots2015 on 2006-07-04
Hi I am brand new to using linux.

Here is my hardware

celeron d 3.06 ghz. (64 bit)
1 gig ram
nvidia geforce 6200 by pny

Here is my problem and since i am new to ubuntu i don't understand jack about what is going on. 

I have tried to install ubuntu with both the 32 and 64 bit from a disk. When I restart the pc the ubuntu screen comes up and asks me to install. I choose start/install. the next thing that happens is a screen comes up with text (loading restricted drivers ... ok, etc) then I get a screen that says <Failed to start the x server would you like to view the x server output to diagnose the  problem , yes, no.> I choose yes, it gives me a screen with a bunch of text and <Ok> next it says, <would you like to view the detailed x server output as well? , yes, no,>. I choose yes. More text comes up with <ok>. After this a new screen comes up with < x server is now disable. Restart GDM when it is configured correctly , ok, >. After this i get a command line with <ubuntu@ubuntu:~$>.

I have tried both the normal install, and the start in safe graphics mode install.


I don't know what to do can some one please help me?

---

### Post by foots2015 on 2006-07-04
My main problem is that i need to get ubuntu installed in the first place but i don't' know how to install it from the command line. ( i was hoping to install from the desktop like they advertised). The reason that i need to get ubuntu installed to the hard disk is so i can than restart the computer without reseting the, sudo dpkg-reconfigure xserver-xorg, settings. Is it not true that if you are running off the live cd that when i restart the computer it resets the settings? So i guess what i need is to know how to install ubuntu from the command line.

Ps. I am going to download the alternate version of Dapper Drake, and try it.

---

### Post by jkwarras on 2006-07-05
I had myself some problems installing dapper from the live cd (for another reasons, a kernel panic). So I wasn't able to install from the commandline. At the end I had to install breezy and then update the sources.list to get dapper repositories.

---

### Post by foots2015 on 2006-07-05
So if i install breezy, than once it is running, i can upgrade it to dapper?

---

### Post by s_spiff on 2006-07-06
I have tried both ubuntu breezy and dapper in beta, and got the same result. I got a new cpu a 64 bit with a Gigabye motherboard having a onboard 6200 nvidia chipset.  My installation was old, so initially I thought, that must be the cause. I reinstalled  Ubuntu Breezy, and got the same problem, so I thought, probably BB doesnt have the drivers. I downloaded the then beta version of Dapper, only to end up with the same problem! Anyone has a soln to foots2015' s problem, please pm me with the soln. I have simply stopped using linux since this problem, and am desperately tryin to get back on to it!

---

### Post by Lil_Eagle on 2006-07-06
The command to reconfigure xserver is:
```
sudo dpkg-reconfigure xserver-xorg
```
Start in recovery mode (then you don't need the sudo) and follow the instructions.  It may sound a bit confusing, because it is written in semi-geek, but it's not too difficult.  The most confusing part is actually the keyboard.

Once that is finished, type exit or reboot and see what happens.

You can always run it again and try different options.

Oh, since you have a nVidia card, run this too:
```
sudo apt-get install nvidia-glx
```
That will get you the latest drivers for your video card.  If you do that before you reconfigure X, then make sure you pick nvidia as your graphics driver and not nv (which is the open source version).

---

### Post by foots2015 on 2006-07-06
You have to have the internet set up previously on linux to be able to access the nvidia drivers, correct?

---

### Post by Kilz on 2006-07-07
> **foots2015 said:**
> You have to have the internet set up previously on linux to be able to access the nvidia drivers, correct?

Have you tried the Alternate install cd? It doesnt have a livecd experence, but is just an installer. I have never been able to use the livecd. It has always refused to load.

---

### Post by Lil_Eagle on 2006-07-07
Yes, you need the internet working to get the drivers.

---

### Post by s_spiff on 2006-07-07
Last time I had to continously reboot, download, burn all the driver etc. on to a cd from windows, boot into linux, install them, see what errors I got, come back to windows, find those files, and do the same thing over and over again, untill I got so frustrated I formatted my hdd, and removed linux! So the sol. of using sudo apt, wont work, or I would have tried it long time back. When u cant access the net, what the point of these commands! BTW, what did Kilz mean by the alternate cd? I thought the new DD is coming in a CD which will have both [ the live and the installations ] combined in one? [ sorry haven't got my copy of cd's from ship it yet ]

---

### Post by dinos22 on 2006-07-09
hi guys

i'm having the same issue here. I'm new to Linux hence my involvement on a support forum.

i've got a NVidia based chipset.......DFI Expert with Dual Core X2 CPU.....ATI GFX X800

i'll give the alernate ISO a go before i ask any more questions.......just downloading that now ;)

---

### Post by foots2015 on 2006-07-11
I downloaded the alternate install cd, and it works to a point...

It won't detect my SATA drive, and if I do get it installed I won't be able to connect to the internet because no one can tell me how to do it!!!!!!!

---

### Post by dinos22 on 2006-07-12
> **foots2015 said:**
> I downloaded the alternate install cd, and it works to a point...

It won't detect my SATA drive, and if I do get it installed I won't be able to connect to the internet because no one can tell me how to do it!!!!!!!

no sata support pffft who uses IDE drives any more ](*,) bit backward this linux caper i must say

---

### Post by Lil_Eagle on 2006-07-12
> It won't detect my SATA drive, and if I do get it installed I won't be able to connect to the internet because no one can tell me how to do it!!!!!!!What do you mean no SATA support?  My 64 bit version is running from /dev/sda2 which is an SATA drive, that's why it's sda and not hda.  Linux treats SATA drives as SCSI.  There is another drive in this computer which is an IDE drive and it is hda.  My dvd drive is both /dev/cdrom and /dev/hdc1.  Incedently, my external HD is /dev/sdb1 which is on a usb connection.

I think something is wrong with your computer.  

As for the network, if you have a router (if you have dsl or cable you should) then it most likely has a dhcp server built in.  If that is true, you shouldn't have to do anything other than make sure the dhcp server software in the router is enabled.  If you're still using dial-up, I would highly recommend getting a broadband connection.  The Internet is a far more enjoyable experience if a) it is fast and b) it's always on.

---

### Post by dinos22 on 2006-07-12
without needing to start a new thread

how do i get linux to see my existing partitioning table with 20+20+80+rest to make up500GB................i already have important data on first, third and forth partitions which is way too big to back up

---

### Post by foots2015 on 2006-07-12
> **Lil_Eagle said:**
> What do you mean no SATA support?  My 64 bit version is running from /dev/sda2 which is an SATA drive, that's why it's sda and not hda.  Linux treats SATA drives as SCSI.  There is another drive in this computer which is an IDE drive and it is hda.  My dvd drive is both /dev/cdrom and /dev/hdc1.  Incedently, my external HD is /dev/sdb1 which is on a usb connection.

I think something is wrong with your computer.  

As for the network, if you have a router (if you have dsl or cable you should) then it most likely has a dhcp server built in.  If that is true, you shouldn't have to do anything other than make sure the dhcp server software in the router is enabled.  If you're still using dial-up, I would highly recommend getting a broadband connection.  The Internet is a far more enjoyable experience if a) it is fast and b) it's always on.

Thank's for the replies. Any help would be much appreciated on the following issues.

In My pc I have one SATA II drive (300mbps).
I have Ubuntu Installed on my laptop which is dual booting with windows. Ubuntu works fine so far on the laptop.

I am currently having three separate issues with Ubuntu.

1. X server crashes on my desktop from the live cd. I got the suggestion to use the alternate install cd. So I tried that.. which brings me to the next problem.

2. Ubuntu won't show me my HDD. All that I get is the blue screen with a grey line at the bottom. This happens after install tells me that it is starting up the partitioner utlity. I have also tried using the resque cd and ran Qtparted from that, but it doesnt't show my drive their either. Here is a link to my thread: [http://www.ubuntuforums.org/showthread.php?t=213044]("http://www.ubuntuforums.org/showthread.php?t=213044")

3. Now on my laptop Ubuntu works, and it is installed. My problem   is that I can't get the internet to connect through my dsl provider. Here is a link my other thread: [http://www.ubuntuforums.org/showthread.php?t=213864]("http://www.ubuntuforums.org/showthread.php?t=213864")

---

### Post by spahn on 2006-07-13
> **Kilz said:**
> Have you tried the Alternate install cd? It doesnt have a livecd experence, but is just an installer. I have never been able to use the livecd. It has always refused to load.

Can someone post a link to the alternate install CD?

---

### Post by Lil_Eagle on 2006-07-13
The link to the Alternate CD is found on the same page as the regular download.  It's just a bit lower on the screen, so scroll down.

Since the download page is a list of mirrors, I'll just give you a direct link: [http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-alternate-i386.iso]("http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-alternate-i386.iso")

It's the first one on the list, and there are more all over the world, so you might just want to go to [http://www.ubuntu.com/download]("http://www.ubuntu.com/download") and pick your own mirror.

---

### Post by NvJuggalo on 2006-07-20
> I have tried to install ubuntu with both the 32 and 64 bit from a disk. When I restart the pc the ubuntu screen comes up and asks me to install. I choose start/install. the next thing that happens is a screen comes up with text (loading restricted drivers ... ok, etc) then I get a screen that says <Failed to start the x server would you like to view the x server output to diagnose the problem , yes, no.> I choose yes, it gives me a screen with a bunch of text and <Ok> next it says, <would you like to view the detailed x server output as well? , yes, no,>. I choose yes. More text comes up with <ok>. After this a new screen comes up with < x server is now disable. Restart GDM when it is configured correctly , ok, >. After this i get a command line with <ubuntu@ubuntu:~$>.

I have tried both the normal install, and the start in safe graphics mode install.


I am Having the SAME exact problem as the OP is/was having.
I am so new to Linux its not even funny. Was this problem ever resolved, Please Let me know how to fix it.

---

### Post by foots2015 on 2006-07-24
> **NvJuggalo said:**
> I am Having the SAME exact problem as the OP is/was having.
I am so new to Linux its not even funny. Was this problem ever resolved, Please Let me know how to fix it.

Did you try this [http://http://www.ubuntuforums.org/showthread.php?t=187177]("http://http://www.ubuntuforums.org/showthread.php?t=187177")

I tried it, but it didn't work for me. If it doesn't work try Mepis untill they come out with a new version of ubuntu that works right. Mepis runs on my machine just fine here is a link to their main site [http://http://www.mepis.org/]("http://http://www.mepis.org/")
Here is where i downloaded mine from:[ftp://ftp.ibiblio.org/pub/linux/distributions/mepis/released](ftp://ftp.ibiblio.org/pub/linux/distributions/mepis/released)

Best of luck ;)

---


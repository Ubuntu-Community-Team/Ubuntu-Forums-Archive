---
title: "Error while installing ubuntu 14.04"
date: 2014-08-23
forum: Wine
---

### Post by wibbenz on 2014-08-23
Going right to the point:
Maybe 2 weeks ago I posted about **wubi **not installing at all on windows 7, after waiting and doing nothing except the normal things it worked last night.
A new problem has occured and the message is "unable to find a medium containing a live file system".

What I could understand via the google seraches I did was that I should switch from IDE to AHCI, checked my bios settings and it was already set to AHCI.
And since that was already done what should I do? Just wanna go back to ubuntu and keep windows in case something isen't working as it should. (Last time I moved from ubuntu my sound on teamspeak sounded like I was ina bunker according to those I was speaking to).

Ive tried to do alot of seraches but can't find any good awnsers, hoping someone might have them out there. :)

---

### Post by CharlesA on 2014-08-25
Erm, wine runs on Windows?

What are you trying to do because the error you state makes it sound like a bad burn. Did you verify the md5sum of the iso before you burned it?

---

### Post by wibbenz on 2014-08-25
> **CharlesA said:**
> Erm, wine runs on Windows?

What are you trying to do because the error you state makes it sound like a bad burn. Did you verify the md5sum of the iso before you burned it?

No I dident, ill check that tomorow and report back! :)

---

### Post by mastablasta on 2014-08-26
wine does run on windows: [http://wiki.winehq.org/WineOnWindows](http://wiki.winehq.org/WineOnWindows)

but what are you trying to do? install Ubuntu inside wine or what?

you should install it in virtualbox if you want to use it inside windows.: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by wibbenz on 2014-08-26
> **mastablasta said:**
> wine does run on windows: [http://wiki.winehq.org/WineOnWindows](http://wiki.winehq.org/WineOnWindows)

but what are you trying to do? install Ubuntu inside wine or what?

you should install it in virtualbox if you want to use it inside windows.: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

Haha fail, its wubi not wine, failed there xD
Gonna try and check the md5sum right now and see if that works.


Edit:
Just tested it and it said this:
dccff28314d9ae4ed262cfc6f35e5153 *ubuntu-14.04-desktop-amd64.iso

And the sum I got was:dccff28314d9ae4ed262cfc6f35e5153

So its the right program im using I suppose?
I checked via this link: [http://releases.ubuntu.com/.pool/MD5SUMS](http://releases.ubuntu.com/.pool/MD5SUMS)

---

### Post by nsync on 2014-08-26
i dont understand the point of this topic , are you saying that you want to replace windows with ubuntu ?

---

### Post by wibbenz on 2014-08-26
No I want to install ubuntu as a second os, I still wanna be able to use windows to play games etc. But I prefer ubuntu over windows and its for that reason I want to use both, not to replace windows with ubuntu.

---

### Post by nsync on 2014-08-26
You need to have at least one partition in order to install Ubuntu without removing windows

---

### Post by nsync on 2014-08-26
if you have a exisiting partition , you can continue installing ubuntu but i recommend you to use YUMI instead in creating bootable installers

---

### Post by wibbenz on 2014-08-26
> **nsync said:**
> You need to have at least one partition in order to install Ubuntu without removing windows

Are you sure? I had ubuntu installed before with wubi and diden't have to do anything except run that exe file I downloaded and let it install.

---

### Post by CharlesA on 2014-08-27
Wubi is not supported on 14.04. Either set up a dualboot or run Ubuntu as a VM.

---

### Post by wibbenz on 2014-08-28
So what is it that I downloaded? ;o
Its in Swedish but maybe you understand the look of the program.
[IMG]http://1.ii.gl/qkG9mmq.png[/IMG]

Is it posible then to download ex. 12.04 that I installed last time and then use some command in the terminal to upgrade to 14.04?
I want it to be as a dual boot, I wanna be able to choose in the startup window Windows 7 or Ubuntu like last time.
Ill try to download the last wubi supported version and see if that works in that

---

### Post by mastablasta on 2014-08-29
Wubi was ment for testing and to try out the OS. it is not supported and therefore not recommended. so you can do it at your own risk. 
what is supported is a side by side install (where the two OS are running completely separated) as well as install in virtualbox. so choose either and open a help request in installation section of forums if you need help with side by side dualboot setup.

---

### Post by wibbenz on 2014-08-29
> **mastablasta said:**
> Wubi was ment for testing and to try out the OS. it is not supported and therefore not recommended. so you can do it at your own risk. 
what is supported is a side by side install (where the two OS are running completely separated) as well as install in virtualbox. so choose either and open a help request in installation section of forums if you need help with side by side dualboot setup.

Oh forgot to post, I found an old usb drive that and then followed the tutorial on how to install the ubuntu files on it. I then changed bios to start from the usb insted of my ssd.
The problem was that it did install and everything went well, but when I then started the computer without the usb drive(told it to install ubuntu on my C drive with a new partition) windows started like normal, no ubuntu in the black list to choose from or anything.
I then checked the space on my C drive and it had gone down from 27 gb to 7gb ~. I then tried to boot it once again from the usb drive but could not choose ubuntu then either.

When I booted it on the "try ubuntu without installing" I could find the partition with all the dirs that should be there, "etc, home" etc. 
Gonna try once more tomorow, removed all the partitions.

---

### Post by wibbenz on 2014-08-31
Well it seems to be installing:
I first put the bios to boot from my USB drive.
It installs everything #and I select where im from etc
Then it restarts #and once again I have to choose where im from etc.
I then turned the computer off, took out the usb drive and the computer started with windows 7, I diden't get that menu to choose if I wanted to start ubuntu or windows....

I tried googling it should I try the "boot repair" when I first get to the start menu? The only problem I see with that is that it says "Any changes you do won't affect the computer until you restart it" - after the installation has been completed.

---

### Post by mastablasta on 2014-09-01
you can use boot repair tool to generate report and post the report here. at the moment I am not sure how this is installed or where grub was placed.

---

### Post by wibbenz on 2014-09-01
> **mastablasta said:**
> you can use boot repair tool to generate report and post the report here. at the moment I am not sure how this is installed or where grub was placed.
Ok gonna try that tomorow, as I said I installed ubuntu 14.04 via my usb, it then told me to restart and after that I keept coming to the "would you like to install ubuntu" page. And when I removed the usb from the computer and started it up. When that was done I diden't get to the "what OS would you like to start?" It automaticly started windows, not even after trying to add the usb once again it worked.
And when I used the usb again I got to the "Would you like to install ubuntu~"

---


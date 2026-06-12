---
title: "Installation Problems!"
date: 2008-07-12
forum: x86 64-bit Users
---

### Post by Terrizzle on 2008-07-12
Okay, So after days of trying to download Ubuntu 8.04 AMD64 and
Ubuntu 8.04 i386....I finally was able to correctly download both versions. Now the problem:

Instead of burning the images to a cd (which I have tried and does not work, reason being, the cd's arent being read correctly...I cleaned the drive with a cleaning kit, also, burned using brand new cds. None of those attempts made a difference. I never have problems with my cd/dvd drive)I actually tried the 32 bit version first. I mounted the image in Alcohol 120%. Ran the install inside of windows and rebooted as told. Everything is fine until the actual installation on reboot. I get the following error:  [Errno 5] Input/output Error. CD/DVD drive or Disk drive is faulty.

That makes no sense. I tried installing on a different hard drive and still same problem. *(this goes for both versions)*

I checked my memory with Memtest86+ and no errors. (just making sure)

So now, I'm at a complete loss!
any ideas would be helpful!

Setup:
Microsoft Windows Xp Media Center
VERSION 2002
Service Pack 2

Gateway
818GM
AMD Athlon(tm) 64 Processor
3700+
2.40 GHz 1.00GB of RAM

TWO Seagate Harddrives:
ST3200021A= 200GB (7200RPM)
ST340801A= 40GB (5400RPM)

Also, I wanted to install Ubuntu on the second hard drive (set as slave)
do I mark the partition as active? Or would that even matter?

---

### Post by Ducksgoquak on 2008-07-12
Hmm it almost sounds like you are just dropping the iso onto a cd and not actually burning it as an iso. I know i've made that mistake before. Just my newbie guess:)


Edit: here's a link that might help 
[http://www.metacafe.com/watch/718036/how_to_burn_iso_using_alcohol_120/](http://www.metacafe.com/watch/718036/how_to_burn_iso_using_alcohol_120/)

---

### Post by Terrizzle on 2008-07-12
How would you just "drop" the iso? lol

No i've burned the image many times.
That's not the problem.

Thanks for the thought though

---

### Post by Ducksgoquak on 2008-07-12
as in just burning it as a data cd with the iso on it ;) sorry i don't know anything else about the subject:) gluck!

---

### Post by Terrizzle on 2008-07-12
Oh okay I understand what you said now. But, no that's not the problem at all...
It really pisses me off though, i've been trying to install this for three days now and NO known fix. 

Windows it is....
for now.

---

### Post by bford16 on 2008-07-12
I had a similar problem writing CDs. One after the other went bad. I tried burning the CDs on a different computer, and got it on the first try. I'm not sure what made the difference.  One computer was using the Gnomebaker software, the other was running Brasero (on Xubuntu). But it could just as easily have been the drives themselves. And my Windows machine with Nero 7 Express could not burn images at all for some reason. It handled data CDs just fine.  Bottome line: Xubuntu with Brasero worked.  Ubuntu with Gnomebaker failed.

---

### Post by Terrizzle on 2008-07-12
Interesting....
I think i'll try Xubuntu (8.04)
Give that a go and see what happens...

---

### Post by Shippou on 2008-07-12
Hello... 

Could you just narrate how did you really burn the iso file? Because most of the time most people (including me) just burns the .iso file itself, not its contents. 

I suggest not using alcohol. It is only a cd/dvd drive emulator, not a real one.

---

### Post by Terrizzle on 2008-07-12
Well, 

I mounted the image and burned it
I used a slow burning speed of 4x
MD5 hash is correct.
Used a DAO/SAO writing format

What burning software would you recommend for burning this
.iso?

---

### Post by Shippou on 2008-07-12
Sorry, I still didn't get it when you said you "mounted the iso."

Are you using Windows right now? If yes, you can use Nero 8. If no, and you are running Linux, you can use K3B or Brasero. But I prefer K3B.

For the sake of clarity, this is what I do when burning an .iso file:
1. Click on the iso file itself. If you are windows and has Nero 8, Nero 8 Burning ROM will usually open. If you are Linux, it usually opens K3B or Brasero (depending on what is installed on your system). 

If by some chance these applications will not open, or if the wrong one opens, do this steps:

A. Windows
1. Open Nero8 Burning ROM (from your start menu).
2. Follow the instructions there. Select burn image first.

Or you can look into this link: [http://answers.yahoo.com/question/index?qid=20080126143308AANY6rJ&show=7](http://answers.yahoo.com/question/index?qid=20080126143308AANY6rJ&show=7)

B. Linux (any distro)
1. First, make sure you have k3B or Brasero installed. If not, use sudo apt-get install <package>.
2. Open the application.
3. a. In k3b, click on the additional tasks, and select burn image.
   b. in Brasero, select Burn Image, and locate the iso file.

Just don't modify the default settings, and this should do the trick.

---

### Post by Terrizzle on 2008-07-12
Nero is horrible. IMO

(SORRY, I DIDN'T MEAN TO SAY I MOUNTED AND THEN BURNED)

I mounted the .iso image in Alcohol 120% this way I would not have to burn a CD. By doing this, I would be able to do an install directly in windows. (I mounted the image in a virtual drive created by Alcohol)
The install was perfect until I received the error above!

I'm not concerned with burning an image as I already have installed the OS.
It seems as though everyone has encountered this problem, *well from reading in these forums anyways*

Simply:
Didn't want to burn an image to a cd. (Wasn't working for me. Probably wrong cd brand or something)
So instead of burning, I somewhat "emulated" an image on a virtual drive to install. This worked.

But like I said, my problem is the ERROR.

---

### Post by Shippou on 2008-07-12
Ok. Now I get it.

Solutions:
1. Do not use Alcohol. Since you are using Windows, and I think you do not want to **really install Ubuntu** (as in making partitions; in short, just want to try it out), download VmWare. It is free. Then run the iso from there.
2. Search for other software. Try MagicIso (what is exactly your Nero version?) and boot from the CD.

I recommend option #1.

---

### Post by Terrizzle on 2008-07-12
No, I REALLY want to install lol
So since the cd burning wasn't working....I just mounted and installed that way. It then told me to reboot without the cd in tray (in this case, unmount the image and reboot)
It was going along great until that damn error. It seems very common actually and probably has nothing to do with anyones hardware.

---

### Post by Shippou on 2008-07-12
Before I give you the hard way, try re-downloading the iso. Maybe there was some file corrupted inside the iso. Just try to download it again. Then post here after.

---

### Post by Terrizzle on 2008-07-12
Okay sounds good (Ill just come back and edit this post and let you know)

by the way, thanks for taking the time to help me out..I really appreciate it :)

---

### Post by Shippou on 2008-07-12
No prob. :) I know your hardships. Do you know I reformatted by hard drive at least five times for two days this week just to get everything up and running? :)

---

### Post by Terrizzle on 2008-07-12
Goodness haha that's not fun....and i've been down that road before with repairing windows!

anyways, i downloaded Xubuntu 8.04.1 for 64 bit computers ( I have an AMD Processor) and checked the hash. It was good.

Now, im trying to install it inside windows (sort of like the option with Wubi) but for some reason, After it's done doing the "Checksum" it immediately starts to download the image again from the site??? This doesn't make any sense to me because I already downloaded the image and it's not corrupt otherwise the MD5 Hash would say different correct?
So i'm at another loss?

---

### Post by Shippou on 2008-07-12
Hmmnn... I am at loss to.... :(

Well, let's try the hard way. But first, is your hard drive partitioned?

---

### Post by Terrizzle on 2008-07-12
I want to install Xubuntu on my second hard drive (it's set as slave)
So basically I want to dedicate Xubuntu on the whole hard drive

but yes there's one primary partition on that drive

---

### Post by Shippou on 2008-07-13
Since you want that to happen, we have not so much problem.

Assuming you have backed-up all your files, burn the iso using magiciso or nero or whatever software you have there (the contents of the image) then reboot using the cd. (Burn the redownloaded iso. I suggest you use a cd-rw)

Then post here. :)

---

### Post by iclements on 2008-07-13
If you are having problems installing from CD - you could try installing from a 1 GIG USB memory stick - I've done this a few times - see [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

One possible related issue - when you install from USB it gets it into its head that the USB is a cdrom - and so when you try to mount the usb stick again - you get errors very similar to the ones you are seeing - the solution in this case is to remove an offending CDrom mount line from the /etc/fstab file ... so you could look in there and see if thats the cause of your problem - or go the USB stick route.

---

### Post by Terrizzle on 2008-07-13
Yeah I've been using the CD RW's 

But yeah, ill try again and see what happens.....

TO iclements:

Where do I find that mount line you're talking about?

---

### Post by Terrizzle on 2008-07-13
Okay...

Tried burning again...NO GO. Still won't boot. and I KNOW i burned it correctly
and yes i've set the cd to boot first.
This is unbelievable....
Despite the fact of trying to install by cd, it still won't work with a "install in windows" option

This is sad.
never had so much trouble with installing something.

---

### Post by Sef on 2008-07-13
> Tried burning again...NO GO. Still won't boot. and I KNOW i burned it correctly
and yes i've set the cd to boot first.
This is unbelievable....
Despite the fact of trying to install by cd, it still won't work with a "install in windows" option

Did you try with a different cd type?  Sometimes a batch of CDs will be bad.

---

### Post by Terrizzle on 2008-07-13
I don't have any at the moment...

But shouldn't I be able to mount the .iso image on a virtual drive and install inside windows? Because that works, but when told to reboot (after removing the image from  mount) halfway through the setup, I get the Errno 5 error

It's not a HD issue because I ran scans with seagate tools and both drives pass
and my cd/dvd drive is perfect.

no clue.

---

### Post by Shippou on 2008-07-13
Hello... Can I have your specs, I mean computer specs? Because if you have at least 256MB RAM you can download Ubuntu first, then try installing Xubuntu after Ubuntu by using sudo apt-get.

---

### Post by frankstin on 2008-07-13
This section will hold installation problems we have heard about and possible fixes for them between releases.the installation problem especially important when you perform an unattended setup.
_______________________________________________
frankstin
<a href="http://www.digitalinfo.in">outsourcing service</a>

---

### Post by frankstin on 2008-07-13
This section will hold installation problems we have heard about and possible fixes for them between releases.the installation problem especially important when you perform an unattended setup.
_______________________________________________
frankstin
 [Outsourcing services](http://www.digitalinfo.in)

---

### Post by Terrizzle on 2008-07-13
Okay well I finally got it to work...
Didn't do anything different.....just worked all of a sudden.
But yeah my specs are posted on the 1st page of this thread Shippou
if you want to look

and I have no idea what sudo apt-get is...
Remember I'm a Windows user.

---


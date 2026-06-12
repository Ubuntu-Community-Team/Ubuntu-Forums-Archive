---
title: "Corrupt 64 Bit install discs?"
date: 2005-12-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by dahli.llama on 2005-12-23
I've been trying to install a 64-Bit version of linux for the past couple of days now and every Ubuntu disc I have tried says that it is corrupted.  I get to the "Copy Installation Files" part and about 30% in and I get this error:

```
Couldn't retrieve locales.  This may be due to a network problem or a bad CD depending on your installation method.
```

And then it says that I should try buring the CD at a lower speed.  I've tried with about 5 different discs, of versions 5.04 and 5.10, as well as burning them with 2 different PCs.  I can't seem to figure out what's wrong.

Some of the files have had bad MD5 sums, but the latest ones I've tried have been fine when I burned them.  Has this happened to anyone else?  I really like Ubuntu, but I can't get a reliable install disc.

Thanks!!

---

### Post by ninotob on 2005-12-23
I had no luck installing amd64 breezy from CD or DVD, but I was able to use the hoary cd and upgrade to breezy.  But something was wrong with it in a hard to define way, so I tried again w/ the amd64 breezy CD.  Except I did a "server" install.  That worked, then I logged in (text mode only) and did "sudo apt-get install ubuntu-desktop".  That worked out fine -- I ended up with a system just like I would have gotten if I did a normal install from the DVD or CD.  Give that a shot and see how it goes.

---

### Post by bonzodog on 2005-12-23
hrmm...cannot explain this one. I download ISO's all the time and they are always fine. one thing though: ALWAYS md5sum the downloaded ISO BEFORE you burn it. 

(I once had to go through 3 attempts at getting a good ISO off a mirror.)

dhali.llama: It really does sound as though you are getting corrupted images on download, or your CD burner is faulty.

Have you both ordered ship-it discs? They will of course be good, so should install no problems.

---

### Post by dahli.llama on 2005-12-23
I will have to try the server thing and see if that helps.

I have ordered a set of discs, but 4-6 weeks is a long time to wait :)

One other thing... Is it possible to do an integrity check of the CD (without actually starting the installer) after I burn it to see if that's what's getting messed up?

Thanks for the help.

---

### Post by bonzodog on 2005-12-24
md5sum is a checksum integrity checker
 go to the directory where the downloaded ISO is and run:

$md5sum <name of ISO>

It will outut a hexadecimal string of letters and numbers.  There will be a file on the download site called md5sums. check the two strings to see if they match.
Similarly, you can do this from the burnt cd ISO to the one on your machine. 
If the md5sum of the burnt ISO is different from the file on the machine, then you know that it is having problems burning discs.

---

### Post by dahli.llama on 2005-12-24
Ok, thanks for all the help so far, but I'm still fighting tooth and nail with this problem.

I've gone through at least 5 different disks and have even attempted an install of Gentoo and Debian, which were also unsuccessful.

My latest attempt was with an Ubuntu 5.10 64bit install disk.  The ISO was fine and the CD was burned at a low speed.  I tried the install and at about 30% into the base system intall I got these errors:

```
Base system installation error.
The debootstrap program exited with an error (return value 1)
Check /target/var/log/bootstrap.log for the details
```

```
Failed to install the base system.
The base system installation into /target/ failed.
Check /target/var/log/bootstrap.log for the details
```

The thing is that /target/var/log/ doesn't have anything in it.  After I got this error I tried the "Check CD Integrity" option that is available on the install disk, and it went through successfully.

I really don't know where to go from here.  I'm trying an internet install of Suse 10.0, but I won't know if that works for a while.

Is it possible that something is goofed up with my hardware?  I'm able to install most 32bit distros that I have just fine, but the 64bit version are proving to be a real pain in my butt.

My system specs:
ASRock Socket 939 Dual SATA Motherboard
Athlon64 3200+
2gigs of Corsair DDR 3200 RAM
Maxtor 200Gb IDE harddrive
Western Digital 80Gb IDE Harddrive
3Com network card

Anything you can do to help will be hugely appreciated.

Thanks

---

### Post by tokyovigilante on 2005-12-25
I've never had any problems with the 64 bit edition on my system (below). If it's failing at about the same point every time while copying files it will be accessing about the same point on your hard disk, you might have some faulty sectors? Try scandisk in Windows, i'm not sure of a linux disk integrity scanner. SpinRite from grc.com is another excellent one which runs off a boot floppy.

---

### Post by bonzodog on 2005-12-25
dahli.llama: it really is starting to sound like a hardware problem - like tokyovigilante says, have a look at the integrity of the Hard disk - if that is ok, it could be that something is wrong with the cdrom drive. Are you trying to install on the 80gb hard disk - that sounds like an older one rescued from another machine?

---

### Post by dahli.llama on 2005-12-25
Yeah, that's kind of what I'm worried about.  Both of the drives are relatively new, and I have tried installing to both of them, with no luck.

The strange thing is that I have been able to install 32 bit versions on it with no problems.

As for checking the hardware, is there a program that I can download and load onto a disk to boot off of to check them, since I do not have a windows installation available?

Thanks a ton for all of the help so far.

---

### Post by tokyovigilante on 2005-12-25
Hmm, may not be your disks then, if both fail at the same point. I'm leaning towards faulty RAM now. Try booting from the install CD using the memory test one if you have one with the nice GUI (ie a recent Dapper build) or typing memtest86 at the boot prompt if you have a Breezy or Hoary build. (I think it's memtest86, may be memtest86+, someone correct me if I'm wrong. 

BTW, Merry Christmas :) It's a beautiful Boxing Day here.

---

### Post by dahli.llama on 2005-12-26
Thanks everyone for the help!

It turns out it was the RAM.  I was going to try taking out individual sticks of RAM and installing, and when you said MemTest, I figured I'd try that first, and sure enough when I ran that it almost instantly came back with a ton of errors.  So I took out the new RAM and tried again and it was fine.  

Everything seems to be happy, and I just finished stage 1 of my new Ubuntu 5.10 64-bit install!

Thanks again!

---

### Post by tokyovigilante on 2005-12-26
Glad you're all set.

Enjoy the 64-bit version!

---

### Post by cochingeek on 2005-12-27
There is really something wrong with the install cd discs this time.It was a breeze installing 5.04 and i had so much of trouble trying to install 5.01 that i have decided to wait for the new version....probably i will ask for a new set of cds?

---

### Post by bonzodog on 2005-12-27
are they self burnt discs or ship-it's?

---

### Post by cochingeek on 2006-01-03
sorry 4 the delay, It was ship-it

---

### Post by kurushi on 2006-01-04
I installed Ubuntu Breezy in my AMD Turion 64 various times, and the installation sometimes fails during : 'Coping remaining packages'.

It doesn't fails allways, and is never at the same percentage. I tried downloading Ubuntu again, and using different CD brands, but happens the same.

Maybe is my computer or maybe is Ubuntu installer, but other distros installers (or windows one) never fails, it looks like some kind of bug in Ubuntu installer.

---


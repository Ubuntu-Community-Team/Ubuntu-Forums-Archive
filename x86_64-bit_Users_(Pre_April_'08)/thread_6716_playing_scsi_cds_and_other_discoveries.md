---
title: "playing scsi cds and other discoveries"
date: 2004-11-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by dmallery on 2004-11-30
hi

spend an interesting day with my first amd-64 install.  i have a scsi cdrw drive rather than the ubiquitous atapi.  the cd player comes up looking for /dev/cdrom which is not there (in /dev).

finally, i see that indeed there is a /dev/sr0 which turns out to be the drive.

i have been using knoppix for a long time (hdinstall).  getting back to gnome is refreshing.

i discovered that ssh is not up by default.  (how anyone can live without it is beyond me!)  it was trivial to install, but i had to break down and give root a password so i could scp to the machine.

finally: boy does that 3400 put out the heat!  a case fan is an absolute necessity.

onwards!

dave mallery

---

### Post by dmallery on 2004-12-01
replying to myself:

the first fix is to create /dev/cdrom: in /dev:

         ln -sf /dev/sr0 cdrom

this allows you to go back and put /dev/cdrom into the device on the cd player program.

wondering:  did the installer fail to go around a certain corner when the install did NOT have an atapi cdrom?  my next problem adds weight to that since all of fd0 is missing from /dev/

still have cd problems bechase cdrecord -scandisk is not able to find the drive.  it complains that it "can't open /dev/pg*"..."can't open scsi driver"  btw, the device is a scsi plexwriter 12/4/32.

"/dev/pg*" is a new one on me.  it's not on any of my other knoppix/debian machines.

anyone have a quick answer to all of the above?

thanks

dave mallery

---

### Post by dmallery on 2004-12-02
still talking to himself:

BIG ISSUE: the ln for the cdrom link in the last post does NOT survive a re-boot!!!!

also: any changes made by /dev/MAKEDEV do not get made AT ALL!

i have written stuff all over the place on this machine with no problems.  everything else seems ok.

am i ringing any bells out there???

thanks in advance.

dave

---

### Post by leech on 2004-12-04
try a 'modprobe sg' and then it should work, though cdrecord has to be run with sudo, or it won't give you access to the devices...  Quite irritating if I do say so myself

Leech

---

### Post by dmallery on 2004-12-08
modprobe sg is ok, but, as you say, you have to sudo the cd player.

i changed the device in the player to /dev/sg0 and it works without the sudo.

the REALLY WIERD thing is that after a boot a few days ago, the player would work with /dev/cdrom even tho there was NONE.  then, in the middle of a cd, it went poof and would not start again, even with a reboot.

i still do not know why i can't add a link from /dev/cdrom to /dev/sg0 and have it outlive a boot.!!!
or why MAKEDEV does not.

can you do either of the above???

thanks

dave mallery

---

### Post by leech on 2004-12-10
On my system, once I have the sg module loaded, it works without changing anything on the gnome-cd player at all.  Didn't have to run it under sudo.  Look in gconf, under apps->gnome-cd and change the device name to /dev/sr0.  At least that's what I have.  It works great.  

I think the cause of the reboot removing the link you created, is due to udev/hal/hotplug creating the proper devices for you.  my /dev/cdrom actually links to /dev/scd1 (which is my CD-writer, it should actually go to /dev/scd0, not sure why it doesn't.)  Theoretically, you shouldn't have to create a link yourself.  Make sure the udev/hal/hotplug packages are the most current.

Leech

---


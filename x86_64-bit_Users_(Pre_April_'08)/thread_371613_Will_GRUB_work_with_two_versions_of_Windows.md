---
title: "Will GRUB work with *two* versions of Windows?"
date: 2007-02-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by NeilBlanchard on 2007-02-27
Greetings,

I have a system that is already running a dual Windows boot (WinXP Pro and WinXP Pro x64), and I want to know if I were to install Ubuntu 64bit, would GRUB handle the "triple" boot correctly?

I do my CADD work on this system, so I don't want to mess things up.

---

### Post by NeilBlanchard on 2007-02-27
Hello again,

While I still would like to know the answer to my above question, it is probably a moot point since I cannot get either the 64bit or the 32bit version of Edgy Eft to boot from the Live CD, on this machine:

Athlon 64 X2 4200+
Gigabyte GA-K8N Pro SLi
2GB RAM
2X XFX nVidia 7600GS video cards (I use three monitors; 1 is DVI, the other 2 are analog)
120GB SATA Seagate 7200.7
80GB SATA Samsung P80

Basically, the boot process gets to the blinking dash in the upper left corner, and the CD light continues for about 30 seconds, the floppy light comes on for a moment -- and then the 2nd and 3rd monitors lose the signal.

I have tried it with the Safe Video mode, and I have tried with an 60GB IDE HD attached, and the two SATA HD's disconnected -- nothing has helped, so far.

Anything else I should try?

---

### Post by lukej on 2007-02-27
Hopefully to answer both of your questions....

First, you should be able to use GRUB without any issues.  The grub menu will probably still just ask you for Windows or Linux.  If you choose Windows, you should see the Windows Boot loader, and then you can choose between the two versions of Windows that you currently have installed.  You should also be able to tweak the settings of GRUB a little to make it actually point to each installation of Windows, rather than to the Windows Boot loader, this may be more risky however.

Second, search for disabling ACPI via the command line boot option on the live CD.  I've had this issue many times in the past.  It usually results in some type of freezing/rebooting during the startup of the live CD.

Hope this helps.

---

### Post by t_anjan on 2007-02-27
GRUB definitely supports a triple boot. I've got XP, Vista and Ubuntu booting thru GRUB from a single menu.

To achieve the single menu, you will have to make GRUB overwrite the windows bootloader, and then edit your /boot/gub/menu.lst to add the individual Windows boot entries.

Articles for reference:
[http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/](http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/)
[http://hevnikov.com/blog/2006/12/24/triple-boot-qa-2/](http://hevnikov.com/blog/2006/12/24/triple-boot-qa-2/)

---

### Post by pxwpxw on 2007-02-27
> **NeilBlanchard said:**
> Hello again,

While I still would like to know the answer to my above question, it is probably a moot point since I cannot get either the 64bit or the 32bit version of Edgy Eft to boot from the Live CD, on this machine:

Athlon 64 X2 4200+
Gigabyte GA-K8N Pro SLi
2GB RAM
2X XFX nVidia 7600GS video cards (I use three monitors; 1 is DVI, the other 2 are analog)
120GB SATA Seagate 7200.7
80GB SATA Samsung P80

......

Anything else I should try?

=============

Another possibility, a bad CD or a CD drive bug?

Are you using the amd64 version, seems to be the one for your system.

I assume you are seeing no text at all on any screen when trying to boot from 
the CD and your bios is set to boot from CD, indicating a basic failure to boot up.
( If you find that the Live/Desktop  cd graphical interface is a problem, 
as a last resort there is the text based Alternate install CD.)

Some check points (you may have done these):

1. Confirm your CD drive is ok for booting, by booting from your XP install
 cd/dvd.
 That should also test the multiple video card/monitor configuration, which 
sounds difficult for an installer, but that may be irrelevant.

2. Did the CD come from ubuntu or did you download an iso and burn the
CD, if so did you check the MD5sum for the downloaded iso?

See:

[COLOR="DarkOrange"] [http://wiki.ubuntu.com/BurningIsoHowto](http://wiki.ubuntu.com/BurningIsoHowto)[/COLOR]

taken from:
[COLOR="DarkOrange"]  [http://releases.ubuntu.com/edgy/](http://releases.ubuntu.com/edgy/)[/COLOR]

You need to have read the above Howto and checked the MD5sum for the
downloaded iso.

3. More info at:

[COLOR="DarkOrange"] [https://help.ubuntu.com/community/UserDocumentation](https://help.ubuntu.com/community/UserDocumentation)[/COLOR]

---

### Post by lavinog on 2007-02-27
Have you tried the alternate install cd. I find it easier and quicker to use than the live.
Although I feel more comfortable using gtparted on the live cd to mess with the partions. (I recommend doing a full backup of your drive or make an image this way you can revert back if things don't go well.)

---

### Post by NeilBlanchard on 2007-02-28
Hello All,

Thanks for all the replies!  I was able to check the CD (using the option on the initial menu) and the first CD was NG.  I burned a second one, and it checked out -- but still did not boot properly.

I have two optical drives (Samsung DVD-CD/RW combo and Sony DVD burner, and neither one works with the Ubuntu CD's.  I have booted with Ultimate Boot CD and with Windows CD's, too -- I'm pretty sure they both work.

If I check the MD5sum, is that the same as the Check CD on menu?  I downloaded the 64bit ISO file (and I tried the 32bit one, too) and burned the CD with a neat utility (in Windows) called BURNCDCC.EXE.  

> Second, search for disabling ACPI via the command line boot option on the live CD.

What is the command line for this?  (I've worked with two versions of SuSE, and two versions of Linspire, and I've messed around with Knoppix, and I'm *still* a wicked noob with Linux.)  Come to think of it, I'm pretty sure that the Knoppix live CD boots this same machine -- I'll try it again to be sure.

TIA

Neil

---

### Post by NeilBlanchard on 2007-02-28
Uh oh,

My motherboard is not on the supported list:

[https://wiki.ubuntu.com/HardwareSupportComponentsMotherboardsAmdSocket939Gigabyte]("https://wiki.ubuntu.com/HardwareSupportComponentsMotherboardsAmdSocket939Gigabyte")

:( 

I was looking forward to using Ubuntu so I could run the Linux SMP Folding@Home client, and ripping through some work units!  My brother's Core Duo iMac is getting 880 PPD, which is about twice as much as my FIVE clients are doing!

I also would like to have such a clean Linux distro running on my box...

Maybe the list is old?  I hope so...

Neil

---

### Post by Cobikegeek on 2007-02-28
Do you get any error messages before the boot process stalls?  My amd althon 64 had an apic (not same as acpi mentioned above) bios bug that crashed edgy during bootup, but there was always an error msg before it crashed.  Solution was to add "noapic" to the kernel line in /boot/grub/menu.lst

You can change startup commands from the grub menu at bootup by typing "e" to edit.  Then move the cursor down to the line that starts with "kernel" and append a command to the end of that line (noapic for example).  Press enter and "b" to boot.  These commands "e", "b", "esc"  are listed at the bottom of the grub menu during boot.  This only adds the command for that one bootup (good for testing).  You have to edit menu.lst to make it permanent.

Don't give up because of a "not supported" list.  Most are not very up to date.  You *are* running a complicated system relative to most, so that alone makes diagnosing your problem harder.

---

### Post by hazza96 on 2007-02-28
> **t_anjan said:**
> 
Articles for reference:
[http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/](http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/)
[http://hevnikov.com/blog/2006/12/24/triple-boot-qa-2/](http://hevnikov.com/blog/2006/12/24/triple-boot-qa-2/)
Every search I did eventually referenced these two sites but I can't see them. Anyone have a mirror or the instructions somewhere else?

---

### Post by pxwpxw on 2007-02-28
> **NeilBlanchard said:**
> Uh oh,

My motherboard is not on the supported list:

[https://wiki.ubuntu.com/HardwareSupportComponentsMotherboardsAmdSocket939Gigabyte]("https://wiki.ubuntu.com/HardwareSupportComponentsMotherboardsAmdSocket939Gigabyte")

:( 

Maybe the list is old?  I hope so...

Neil

I think if its not on the list, dont worry, the list is not complete. 
Its a list under construction, by anyone.
The install manual supports amd64 if thats what you have. 

Hang in there!

---

### Post by t_anjan on 2007-02-28
> **hazza96 said:**
> Every search I did eventually referenced these two sites but I can't see them. Anyone have a mirror or the instructions somewhere else?

What do you mean you can't see them? Clicking on the links loads the site for me. Tell me if you still can't see the site and I'll send u an offline copy of the two pages.

---

### Post by pxwpxw on 2007-02-28
> **NeilBlanchard said:**
> Hello All,

Thanks for all the replies!  I was able to check the CD (using the option on the initial menu) and the first CD was NG.  I burned a second one, and it checked out -- but still did not boot properly.

I have two optical drives (Samsung DVD-CD/RW combo and Sony DVD burner, and neither one works with the Ubuntu CD's.  I have booted with Ultimate Boot CD and with Windows CD's, too -- I'm pretty sure they both work.

If I check the MD5sum, is that the same as the Check CD on menu?  I downloaded the 64bit ISO file (and I tried the 32bit one, too) and burned the CD with a neat utility (in Windows) called BURNCDCC.EXE.  

Neil

======

Having reread the thread, you are gettting stuck on step 4 (see below),
 not a cd boot problem now. My mistake.
 ( However, I dont know about the ACPI issue ).

(re MD5sum check - that is applied to the downloaded iso, not the burned cd).

Try step 6 below. and if you get a console, then you may just need 
to sort out a problem with /etc/X11/xorg.conf and the multiple 
video cards and monitors.

Good idea to try Knoppix to see if the same problem arises.

I just fired up xubuntu610-i386 live cd on an old ibm 700Mhz celeron, to
see what stages are visible (very few). Took 4 minutes from start to desktop. 
 Should be much faster on your system.

Stages seen:

1. Bios text screen shows boot from CD, isolinux etc.

2. Next screen ubuntu menu shows 5 items 
(start, startsafe, check cd, mem test, boot from hd) 

Help bar F key choices include vga or video, selection of resolutions,
might try vga options that to see if it is relevant.

ESC gets a text boot: prompt, but no options other
 than what already on the menu

start.

3. Message says Loading linux kernel, casper, 
 then pretty screen with progress bar for some time.

4. cursor up top left in blank screen for a short time
while it loads x and the desktop

5. Graphical empty desktop, then desktop menu bar, complete.
  and all go. (browser, net access).

6. can access a console (text mode) using 
Alt,Ctrl,F1 (or F2,...F6) ( possibly can do this from step 4 ).

7. checking  /etc/X11/xorg.conf shows the installer has detected 
the video card (nvidia) and monitor (benq) correctly. Otherwise no
desktop.
 =========

---

### Post by NeilBlanchard on 2007-02-28
Hello,

I was able to boot this system with the Knoppix 4.0.2, no problems and it is very quick.

I tried the F4 video resolution option and set it to 1280x1024x16 (the monitor's native resolution is 1600x1200), and it still hangs.  The hard drive activity light is on constantly when the system hangs.  I cannot use Control-Alt-Delete to reboot, and I have to use the Reset button on the case.

I cannot boot from the Local Disk option on the Ubuntu option menu -- is this significant?

How do I use the MD5 Checksum?

I will try to get to the CLI -- what do I then type to try to get the GUI started?

TIA folks!

Neil

PS: I have installed Ubuntu on an old K6-3 400mHz 256MB system with no problems other than having to limit the (80GB) HD to 32GB so that GRUB would work.

---

### Post by NeilBlanchard on 2007-02-28
Hello,

I am able to get to the text prompt (Control-Alt-F1), and it says:

ubuntu@ubuntu:~$

When I type 'dir' it says 'Desktop'.

Oh!  The text interface is on the main (DVI) monitor, and the second monitor (which is the primary monitor on the second video card is flashing the entire screen, alternating between a teal solid and teal vertical stripes, with the "ghost" of a cursor in the upper left corner.

I found a command:

gnome-display-properties

and it returns (after a few seconds):

(gnome-display-properties:7154): Gtk-WARNING **: cannot open display:

I'm not sure what that means, if anything.

What should I do now?

Neil

---

### Post by NeilBlanchard on 2007-02-28
Hello,

I followed the directions on another page, and I was able to execute this command:

chroot /root nano /etc/X11/xorg.conf

and reading the display info, it says:

NVIDIA Corporation NVIDIA Default Card

and the Monitor is:

SyncMaster

...so, they seem to be correct.  Before I got to this point, there were several error messages about the hard drives having bad sectors?  (I had deleted the quiet splash and added Break=Bottom command).  This would seem to be the problem, then?

Edit: I typed 'exit' and it seemed to go through a boot process -- and the screen stays blank, so maybe it is the video mode after all?

Neil

---

### Post by pxwpxw on 2007-03-01
> **NeilBlanchard said:**
> Hello,

I followed the directions on another page, and I was able to execute this command:

chroot /root nano /etc/X11/xorg.conf



Should not need to chroot for a normal console - have I missed somethiing?

> 

.....  Before I got to this point, there were several error messages about the hard drives having bad sectors?  (I had deleted the quiet splash and added Break=Bottom command).  This would seem to be the problem, then?

Edit: I typed 'exit' and it seemed to go through a boot process -- and the screen stays blank, so maybe it is the video mode after all?

Neil

None of the above I think.

That's good progress getting a workable console. Sorry I was slow to answer. 

 What you have is probably everything ready to go, but just not getting the Xwindows display going because it refuses to accept even minor problems with xorg.conf matching the peripherals as it sees them - frequently happens. The problem should show up in /var/log/Xorg.0.log.

re: 
 gnome-display-properties:7154): Gtk-WARNING **: cannot open display:

Thats the problem. No gui type commands will run until the display is up (meaning xwindows )

Same situation would probably arise with an install using the alternate cd, but might as well try to fix it with the live cd I think. If it crashes you have only wasted a few minutes.

Xwindows xorg.conf can be configured for multiple cards and monitors, but thats probably a bit beyond the scope of the live cd (and me), but ok for an installation. I havn't tried it.

If you can run the gui with knoppix, you may be able to compare its version of /etc/X11/xorg.conf with the ubuntu live version, possibly even use the sections that work.

The 2 key items you need to post for comment are the full text
 from:

 /etc/X11/xorg.conf
 /var/log/Xorg.log  (or Xorg.0.log)  

Check the dates for the files - they are written at each startup for the live cd.
```

 ls -l filename 
 less filename      

```

Its not only the video card and display and resolution that can stop the gui from coming up, but also the other peripherals in xorg.conf -keyboard, mice, tablets etc, the reason can appear quite trivial, which can make it hard to spot.

Your CAD system, maybe some special items you could temporarily unplug, to simplify getting to the gui initially.

You can ignore the 2 monitors that are garbled maybe switch off if they are being overdriven, the one good one is enough to work on now, it should handle the gui when it appears.

You can try to start the gui from a console by:
```

 startx

```
(or may need sudo startx)

The ubuntu live cd has man documentation to assist.
(man md5 md5sum openssl fdisk)

You have 6 consoles f1...f6.

If you can make a small FAT32 partiton on your disk(s) you can save copies of temporary files to it from the live cd and then 
access them from XP and for posting. Or use a usb flash drive.

As for original question,  the safety of your 2 XP systems and data, you need to clarify system details before deciding on the multiboot solution- could be safest to use the existing loader (XP or other?) to run the linux loader rather than putting grub in charge.

Check the disk partitions as seen by linux
```

 sudo fdisk -l > tempfile
 less tempfile

```

==pxw==

---

### Post by NeilBlanchard on 2007-03-01
Greetings,

Okay, I've got a further clue as to what is going on: I booted from the Live CD in the Safe Video mode -- and I heard the Ubuntu boot sound!  I'm just not seeing the desktop!  It is black with the cursor in the upper left corner -- it is not blinking.

If I hit Control-Alt-F1, I get the ubuntu@ubuntu:~$ prompt.

If I type startx it says:

> xauth: creating new authority file /home/ubuntu/.serverauth.6626

Fatal server error:
Server is already active for display 0
      If this sever is no longer running, remove /tmp/.X0-lock and start again

ubuntu@ubuntu:~$

What does this mean? Can I make the changes necessary for the display to work, and then can I install Ubuntu?  Would I need to make the same change(s) to the installation in order to get it to work?

BTW, this is the page I was referring to earlier for instructions on getting to the console: [http://www.ubuntuforums.org/showthread.php?t=370015](http://www.ubuntuforums.org/showthread.php?t=370015)

Thanks for your continued help and patience!

Neil

---

### Post by NeilBlanchard on 2007-03-01
Hello,

Okay, I removed the second video card -- and Ubuntu boots just fine!  :eek: :cool: 

Now, the question is: do I go ahead and install Ubuntu and then reinstall the second card, and get it working then?

Edit: I'm going to try the two video cards **without** the SLi jumper I had on there (even though I was not using the SLi mode).

Also, why doesn't Ubuntu show me the Windows hard drives?  This was also the case on the Win98 SE FAT32 system that I have Ubuntu installed on.  Knoppix lets you copy files from these NTFS drives.

Edit 2: Reinstalling the second video card causes it to have the same problems as before... :(   So, I guess the question goes back to installing Ubuntu with one card, and then installing the second card, and getting it working then.  Remember, I need to use three monitors in Windows so after I install Ubuntu, and use GRUB as the boot loader (I very much doubt that the Windows boot loader can/will handle a Linux partition) -- so, I need to "prove" out a solution for Ubuntu to boot this system with dual video cards BEFORE I can install it.

Neil

---

### Post by NeilBlanchard on 2007-03-01
Hello,

Well, I'm booted with the live CD, and I'm going to start the installation on an old HD I have laying around.  My plan is to A) try to solve the dual video card problem (w/o touching the dual Windows boot) and B) then see if GRUB will add the Windows boot afterwards if I reconnect those hard drives.

Is this possible?

It is taking it's sweet time on erasing the disk (it's 60GB) -- it has been sitting at step 5 of 6 for almost 30 minutes now.  Is this par for the course?

TIA

---

### Post by pxwpxw on 2007-03-01
good stuff.

Cant say what time it takes, probably its done by now. Works best with a network connection.



re the 2 video card issue, if you can get a workable linux system up and running, then you 
can  reconfigure for dual cards / monitors later, but you will need separate advice exactly how to edit the xorg.conf to do that. Would be very difficult to try during the install.
So 
1. install for minimal workable system, if possible make a grub floppy, or use rescue cd until sure. if you put grub loader files on the MBR, that overwrites your windows mbr, you can get it back with fixmbr,

2. pursue further configuration.

and its quite feasible to use the xp loader to start up the linux loader - many threads re that isue.

Have to go now, may have missed something above, will check back later.

---

### Post by NeilBlanchard on 2007-03-01
Hello,

I'm booted to an installed version of 64bit Ubuntu -- but the screen looks awful!  All sorts of moving horizontal dashed lines...  It is set to 1600x1200x60Hz and it looked great when booted from the live CD.

I'm running the updates now, and I want to install the 64bit SMP Folding@Home -- and I have to solve this video problem.

I'll look in other sections to see if i can figure it out.

This is currently a standalone ubuntu machine -- if I reconnect the other HD's, will GRUB detect them?

---

### Post by pxwpxw on 2007-03-02
Too many questions - overtaken by events.:) 

Here are some points I think might still be relevant.

1. Start separate topics for the video display problem (if it persists with single monitor), and another one for xorg.conf for multiple monitors. All separate issues worth raising to get hands-on response, but do a search first

2. The installation has completed OK on a single disk basis, having unplugged the
other 2 drives with your XP systems, but can be reinstalled to leave the ubuntu drive as is. 
Grub is set up for booting from the Ubuntu drive MBR.

3. The drive designations may change when you have 3 again
i.e. which is which, hda, hdb, hdc (or sdx etc). This may affect grub.

You will need to use ubuntu to get a full listing of all the partitions on all drives. (sudo fdisk -l ). 

You will need to run grub to find what it thinks the drive names are, after any reconfiguration. 

If you happen to have a floppy diskette drive, you can put grub on a floppy and do all sorts of amazing things. Otherwise use the CD for rescue.

Useful to have a FAT32 partition for XP<->Ubuntu file transfer.

4. If you can make the ubuntu drive the first preference of the 3 in your bios bootup order then grub should be easily be reconfigured to chainload to the XP drives. It sounds like a very good solution. But for backup, check that you can easily boot directly to XP by changing the bios boot disk order.

You will probably have an interesting time sorting out the multiple drive situation but should be ok with some edits to /boot/grub/menu.lst.

Grub needs some TLC with multiple drives.

---

### Post by NeilBlanchard on 2007-03-02
Hello,

The screen is all better -- it was either the update, or the fact that I downloaded the nVidia Linux driver and installed it.  (If I was successful at this, it sure was easy!)  Either way, the screen looks excellent again!

I'll move forward with the dual screens, and then add the other drives, and I'm sure that I'll have more questions!

Neil

---

### Post by pxwpxw on 2007-03-02
Happy ending.

Just had a look round and there are some interesting dual monitor threads if you search for 'xorg.conf' and have a few hours to spare to sift thru em.

Didn't see any 2 card three monitor.

---

### Post by NeilBlanchard on 2007-03-02
Hello,

Back on the original topic: I've reconnected the other two hard drives -- and GRUB does not "see" them, and the machine still boots straight to Ubuntu.  How do I get GRUB to list the Windows OS's (two different ones), so I can choose between booting to any of the three OS's?

---

### Post by pxwpxw on 2007-03-03
1. the full grub manual: [http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

2. grub on my system

```

xxxxx $ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

grub> root (hd0)
 Filesystem type unknown, using whole disk

grub> root (hd0,0)
 Filesystem type unknown, partition type 0x7

grub> root (hd1,0)
 Filesystem type is ext2fs, partition type 0x83

grub> find /boot/grub/stage1
 (hd0,1)

grub> find /boot/vmlinuz
 (hd0,1)

grub> quit

xxxxx $


```

3. At the end of menu.lst, in my case XP on hda1

```

# This entry automatically added by the Debian installer
# for a non-linux OS on /dev/hda1

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

More examples in numerous multi-boot threads.

Have fun.

---

### Post by NeilBlanchard on 2007-03-18
Greetings,

> **pxwpxw said:**
> As for original question, the safety of your 2 XP systems and data, you need to clarify system details before deciding on the multiboot solution- could be safest to use the existing loader (XP or other?) to run the linux loader rather than putting grub in charge.

Check the disk partitions as seen by linux
```

 sudo fdisk -l > tempfile
 less tempfile

```

==pxw==

I would like to pursue getting the Windows bootloader to work with Ubuntu -- where should I look for info on this, please?

For the moment, I have been using the BIOS to control which HD to boot from.  Windows *must* have the two SATA HD's in the correct order, or it won't boot; and the Ubuntu HD (IDE) has to be at the bottom of the list in order to get Windows to boot.

Another issue is Ubuntu and Windows are "fighting" over the clock -- each time I switch, the time is either changed forward or back 4 or 5 hours?  :confused:

---

### Post by t_anjan on 2007-03-18
> **NeilBlanchard said:**
> 

Another issue is Ubuntu and Windows are "fighting" over the clock -- each time I switch, the time is either changed forward or back 4 or 5 hours?  :confused:

in /etc/default/rcS 

```
UTC=yes 
```

specifies that RTC is UTC. Change it to 'no'.  Then set the time to ur local time. There is a tendency in Ubuntu (maybe in all Linux Distros) to treat the System hardware clock as GMT and then calculate the local time by software.

---

### Post by pxwpxw on 2007-03-18
I am still thinking. Need more info.

Have you got a floppy drive on that system.?
Are you familaiar with using windows <fixmbr> to restore mbr for windows if needed.?
Have you succeeded in getting grub setup to boot your multi everything system?

Can you post your XP boot.ini files from both XP systems? (Not clear how the dual XP boot works, you have to identify which XP is the controlling one in your preferred configuration).

Please post the output of  <sudo fdisk -l >  when run from linux with all drives connected and boot disk selection as for your preferred final solution. i.e. you may need to do tis from the rescue cd.

This will hopefully make it clear what drives are in what position, and where XP and linux are.

I have dual drives, one XP,  2 ubuntu on thiis oldibm pc, at present booting via XP boot menu to 2 grubs, your system is somewhat more complex but the XP menu part is simple if you get it right. 

Will check back later.

---

### Post by pxwpxw on 2007-03-19
NeilBlanchard

Very relevant thread for dual booting and windows tricks:

[http://www.ubuntuforums.org/showthread.php?t=56723](http://www.ubuntuforums.org/showthread.php?t=56723)

Try search for < xp bootloader > for lots of others.

---


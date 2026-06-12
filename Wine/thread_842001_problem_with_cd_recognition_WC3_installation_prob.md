---
title: "problem with cd recognition? WC3 installation prob"
date: 2008-06-26
forum: Wine
---

### Post by zapree on 2008-06-26
Ok so this might be related to WINE but this nOOb thinks that something is weird with my cd drive.... i used this guide to try and install wc3    

1. Put the game CD in the drive
   2. Open a terminal
   3. Type "wine /media/cdrom/setup.exe" and hit enter (change the path and executable name to match the actual game you are installing)
   4. Follow the prompts just like you would in Windows


Once installed, to launch the game you need to do this:

   1. Open a terminal (if you haven't already)
   2. enter "cd ~/.wine/drive_c/Program\ Files/<game install directory>" (change the path to match the game's actual install directory)
   3. Launch the game by entering "wine <game.exe>" (obviously change the name to match the actual executable for the game)

but when i do step 2. i get this message 

patrick@patrick-desktop:~$ wine /media/cdrom/setup.exe
wine: cannot find '/media/cdrom/setup.exe'
patrick@patrick-desktop:~$ 

(obviously this is the whole window)
So anyways im wondering if im doing something wrong, or if i need to configure the system so that it recognises .exe cause when i go into the computer display page, it just says cd-rm/dvd ext... and when double clicked gives the message "Unable to mount location...Can't mount file"
please help this ubuntu newbie out, thanks for all the hard work 
patrick 

(btw. i just switched O.S. and i was wondering how you do a screen shot in ubuntu?)

---

### Post by Hairy_Palms on 2008-06-27
The guide is giving a generalised path to the cd, just browse there and double click the .exe, as for taking a screenshot, its the same as windows just press the print screen button, ubuntu provides a program to save the file too, whereas windoze requires you to open up paint or something to save it.

---

### Post by zapree on 2008-06-27
ok so to what i was saying before...  when i go to view my computer, the cd-rm/dvd icon is still the same and not displaying that it knows that the cd is in the drive... anyone have any idea? if not redirection to the right place to get help?

---

### Post by prshah on 2008-06-27
> **zapree said:**
> 

patrick@patrick-desktop:~$ wine /media/cdrom/setup.exe
wine: cannot find '/media/cdrom/setup.exe'
patrick@patrick-desktop:~$ 




In ubuntu, unlike windows, filenames are case sensitive (lower, UPPER, Mixed). So the file you're trying to launch is probably SETUP.EXE or Setup.exe, or maybe even Setup.Exe.

Here's a nice tip; it's called filename completion. Open your terminal, and type the below command, but DONT press enter:```
wine /media/cdrom/s
``` then press [Tab] twice. If nothing changes, change the "s" at the end of the command to "S" and press [Tab] twice. One of these should give you a list of filenames starting with "s" (or "S"); note the correct capitalization. type in the whole filename and you should be good to go. If you still can't get it to work, post the output of these commands here```
ls /media
ls /media/cdrom

```

---

### Post by zapree on 2008-06-27
patrick@patrick-desktop:~$ wine /media/cdrom/S
wine: cannot find '/media/cdrom/S'
patrick@patrick-desktop:~$ ls /media
cdrom  cdrom0  floppy  floppy0
patrick@patrick-desktop:~$ ls /media/cdrom
patrick@patrick-desktop:~$ 
 thats what came up

---

### Post by prshah on 2008-06-28
> **zapree said:**
> 
patrick@patrick-desktop:~$ ls /media/cdrom
patrick@patrick-desktop:~$ 



Looks like your CD rom is not mounted. Did you insert the CD? What happens when you double click the CD icon in Places-Computer? Is it blank? (Make sure the CD is inserted.) 

If it is blank, eject, wait 10 secs, insert the CD, wait 10 secs and check again. If it is still blank, post the output of ```
dmesg | tail
```

---

### Post by zapree on 2008-06-28
i tried the 10 sec thing, and still nothing... but when i put other cds in (the boot disk, some audio cds, and video works...) it reads them or a least verifys that something is in the drive....  but also when i put the expansion pack disk in, it does the same thing as the first disk. :P

patrick@patrick-desktop:~$ dmesg | tail
[ 1149.086949] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1149.086957] end_request: I/O error, dev sr0, sector 60216
[ 1149.176618] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1149.176626] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 1149.176630] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1149.176637] end_request: I/O error, dev sr0, sector 60216
[ 1149.266664] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1149.266672] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 1149.266676] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1149.266682] end_request: I/O error, dev sr0, sector 60216
patrick@patrick-desktop:~$ 

thanks for the help
patrick

---

### Post by zapree on 2008-11-11
bumpity bump

---

### Post by prshah on 2008-11-12
> **zapree said:**
> 
patrick@patrick-desktop:~$ dmesg | tail
[ 1149.086949] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1149.086957] end_request: I/O error, dev sr0, sector 60216
[ 1149.176618] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1149.176626] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current] 


I'd say that the CD is bad. Take it out, clean the reflective surface with a soft lint-free cloth, and try again; otherwise, you may need a replacement CD.

If any other CDs are also affected, then it may be time to change the drive itself.

This type of error can also show itself if you use a CD burnt at a faster rate than the drive; eg., you use a CD burnt at 52x in a drive that has a max (CD) speed rating of 24x.

---

### Post by Espryon on 2008-11-12
go into the wine drive setup and just mount the cd drive permently and press apply, and if that doesnt work then the disk is bad

---


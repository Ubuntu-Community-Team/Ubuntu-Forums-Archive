---
title: "Boot prompt does not show on G4"
date: 2006-04-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by nat on 2006-04-24
I have got my ands on a PowerMac G4 and though I'd try dapper on it.

When I press C during boot it just displays a question mark. 
The OS9 installation (9.0.4) boots just fine.

any suggestions?

---

### Post by Rxke on 2006-04-24
More info needed.
does your computer boot w/o any disks into OS9?
I mean is it a booting computer?
The ? usually means it can't find a bootable image in the place it expects it to be.
How did you obtain the Dapper CD (And are you sure it isn't a DVD or a x86 or AMD disk?)

---

### Post by nat on 2006-04-24
When I got the powermac it didnt boot at all, same ? icon came whatever I did.

I inserted the cdrom with OS9, pressed 'c' and the os 9 installation started.
I installed os9 so after reboot it booted into os9.

I downloaded a daily dapper iso image, burned it by righ click -> write to disk in gnome on a gentoo box.

I also burned another iso directly with cdrecord. The size of the iso is 689.5 MB (722989056 bytes) so, no its not a dvd.

I have also tried to boot a ppc gentoo iso, but exactly the same ting happen.

I managed to get in to openfirmware and its an openfirwmare version 3 something. I tried to run:
boot cd:,\\yaboot

but it didnt find the image.
Do I need to upgrade teh openfirmware? I saw there was an update available but it required os9.1 an the version I have here is 9.0.something (its disconnected right now) so I didnt even try.

I dont want to buy anohter os to be able to install ubuntu.

---

### Post by Rxke on 2006-04-24
you'd probably do no harm to upgrade the openfirmware.
There are ways to upgrade it w/o having to look around for an 9.1 disk, but it's been so long since I did that, I don't recall where I found the instructions... Maybe someone more familiar w/ OS9 can help out?

the fact that it displays the '?' is indeed it can't recognize the disk as bootable :(

---

### Post by nat on 2006-04-24
But it managed to boot the OS9 CD? How come?

I see there is something called BootX, but it requires the OS to be installed on harddisk already.

---

### Post by jdp on 2006-04-24
A G4 will not need BootX, as that is for OldWorld beige machines.  Anything with a factory USB should automatically boot from the Ubuntu CD, provided that there isn't something else wrong.

---

### Post by nat on 2006-04-25
But it does not, and so does not the gentoo ppc boot cd.

Do I need to burn the CD in a special way?

---

### Post by Rxke on 2006-04-25
if you insert the cd, after having booted in OS9, can it then read the CD? I mean, can you access it? How does it show up on your desktop? (And are you sure it is a PPC boot CD? (edit: yes you did, sorry)

FWIW: on my (older G3) computer, I never succeeded in mounting CD's >650 Mb; so I didn't succeed in booing the Dapper disks, only 5.10 Breezy, then upgraded to Dapper...

---

### Post by jono.carnie on 2006-04-25
Nat,

Regarding the following;
-----------8<----------
I downloaded a daily dapper iso image, burned it by righ click -> write to disk in gnome on a gentoo box.

I also burned another iso directly with cdrecord. The size of the iso is 689.5 MB (722989056 bytes) so, no its not a dvd.

I have also tried to boot a ppc gentoo iso, but exactly the same ting happen.
----------->8----------
Can you be absolutly sure the iso's are created ok?
Can you browse the CD's ok is OS9?  They should have a whole series of files and directories...
Generally Right Click --> Burn to disk only copies the file to CD.  You'd have to specify Write Image to disk or something to make sure the ISO is created correctly...

Of course you could have done it all correctly and I'm wayy off.  But thought it might help.
The fact that the OS9 install disk works ok, seems to rule out any hardware issues with the machine.... leaving only the media/cd's as a possible problem.

JC

---

### Post by Ptero-4 on 2006-04-25
nautilus cd burner IIRC can't burn isos correctly. You need something like gnomebaker.

---

### Post by nat on 2006-04-26
[QUOTE=Rxke]if you insert the cd, after having booted in OS9, can it then read the CD? I mean, can you access it? How does it show up on your desktop? (And are you sure it is a PPC boot CD? (edit: yes you did, sorry)[/QUOTE]

Yes. It shows up as Ubuntu_PowerPC_dapper in OS9. I can open the cd where I can see the following directories:

install
.disk
dists
doc
etc
pics
pool
ppc
pressed

and the followin files:
md5sum.txt
README.diskdefines 

[QUOTE=Rxke]FWIW: on my (older G3) computer, I never succeeded in mounting CD's >650 Mb; so I didn't succeed in booing the Dapper disks, only 5.10 Breezy, then upgraded to Dapper...[/QUOTE]

I tried the gentoo minimal ppc bootcd too. same thing. I tried the freebsd 6.0 PPC bootonly cd, same thing. Those are pretty small

---

### Post by nat on 2006-04-26
[QUOTE=Ptero-4]nautilus cd burner IIRC can't burn isos correctly. You need something like gnomebaker.[/QUOTE]

I also tried using cdrecord directly from command line (from my gentoo box):
```
sudo cdrecord dev=/dev/cdrw ...
```

---

### Post by nat on 2006-04-26
An update:

I installed the OS 9.1 update (so its now OS 9.1) which allowed me to install the Open firmware upgrade. (to version 4.2.8 )

I downloaded the Ubuntu 6.06 PPC beta iso image and tried to bun it with gnomebaker (which uses cdrecord anyway..)

I tried to burn the iso using windowx XP and Easy CD Creator on another computer.

Same result. It shows a ? icon and the boots up to OS 9.1.

---

### Post by jdp on 2006-04-26
It's odd thatit boots the Mac OS CD and not Ubuntu.  Have you tried using the [Startup Manger](http://search.info.apple.com/?as_q=&as_epq=Startup+Manager&as_oq=&as_eq=&btnG=Search&lr=lang_en&kword=&type=ktech+OR+klearn&Submit=Search)?  Boot while holding the Option key down.  It should come up eventually in a screen with a list of bootable drives.  If the CD is in the drive and bootable it should show up.  It may take a while to get to the point of letting you select what to boot, as it also searches for network  shares to boot from.

---

### Post by nat on 2006-04-27
[QUOTE=jdp]It's odd thatit boots the Mac OS CD and not Ubuntu.  Have you tried using the [Startup Manger](http://search.info.apple.com/?as_q=&as_epq=Startup+Manager&as_oq=&as_eq=&btnG=Search&lr=lang_en&kword=&type=ktech+OR+klearn&Submit=Search)?  Boot while holding the Option key down.  It should come up eventually in a screen with a list of bootable drives.  If the CD is in the drive and bootable it should show up.  It may take a while to get to the point of letting you select what to boot, as it also searches for network  shares to boot from.[/QUOTE]

Aha... Those hints are very very helpful. Thanks to everyone helping me so far.

I see the harddrive and the cdrom with a small Tux icon. I press the tux cd button and arrow forward. The cdrom spins up, the screen blinks, and the same screen show up again.

Same thing happens with the freebsd 6.0 PPC cd.

I asked a guy here who have done support on this g4 if he thought there could be a problem with the cd player. He didnt think so "it has always worked". And it boots the mac os 9.

Wierd.

BTW... I think there might be 2 harddisks on this computer. Could that has sometihng to do with it?

---

### Post by jono.carnie on 2006-04-27
Hi Nat,

Is the CD rom an original Apple one?

I just bought myself a G3 on ebay, and the seller mentioned you needed an cd with the apple rom on it to boot up?
Not sure if he's correct or not?  I'm still checking on this, as I wanted to replace the drive with newer DVD burner.

JC

---

### Post by nat on 2006-04-27
[QUOTE=jono.carnie]Hi Nat,

Is the CD rom an original Apple one?

I just bought myself a G3 on ebay, and the seller mentioned you needed an cd with the apple rom on it to boot up?
Not sure if he's correct or not?  I'm still checking on this, as I wanted to replace the drive with newer DVD burner.

JC[/QUOTE]

Yes. Its a gray, original, norwegian, Apple cdrom.
"PowerMac G4
software installation"

Is is possible to install the apple rom into the firmware or something?
Can I use the apple rom from the original apple cd and install it on the ubuntu iso image?

Do you think it will help to replace the cdrom player?

This a G4 though..

---

### Post by jono.carnie on 2006-04-27
Sorry the ROM i'm talking about is the CD bios rom.  Not the disk.
But it doesn't appear to be the issue you're having if you've got the original drive.

Bottom line is you're machine can't seem to see any bootable CD's apart from the original OS9 one.
Very odd.

JC

---

### Post by jono.carnie on 2006-04-28
Ok... I think I might have something for you....

I got myself a powermac g4, 350mhz 256mb ram.  and ran into exactly what you described...
os9 starts and installs just fine.

Put in any ppc distro and you get nothing on the screen..
I spent some time reading up on the open firmware etc to try to figure out why the ubuntu disk wasn't getting read.

No amount of Control-Alt-O-F did anything for me...
Finally in frustration i pressed enter several times...
Lo and behold the linux startup text ran up the screen!!!

Now my monitor was showing no signal at this time, so I'm pretty sure some sort of invalid format is being sent to the monitor....

See how you go.
Currently installing Breezy on PPC...

JC

---

### Post by jono.carnie on 2006-04-30
Nat,

Which G4 do you have??

I'm trying to find the firmware upgrade for my G4 PCI machine without much luck??

Thanks
JC

---

### Post by nat on 2006-05-09
Sorry for the delay. I ordedered a breezy PPC from ubuntu.com (its free!) som im 100% sure that its not the cdrw's I have or the cd recorders.

meanwhile the g4 is disconnected and collects dust in a corner here.

[QUOTE=jono.carnie]Nat,

Which G4 do you have??
[/QUOTE]

I think it is a 400MHz. 256MB ram. Its the powermac tower.
Model number M5183.
[http://images.google.no/images?q=m5183](http://images.google.no/images?q=m5183)

[QUOTE=jono.carnie]
I'm trying to find the firmware upgrade for my G4 PCI machine without much luck??

Thanks
JC[/QUOTE]

Try this one.
[http://docs.info.apple.com/article.html?artnum=120171](http://docs.info.apple.com/article.html?artnum=120171)

I had to upgrade the OS to 9.1 before I could install the firmware.

---


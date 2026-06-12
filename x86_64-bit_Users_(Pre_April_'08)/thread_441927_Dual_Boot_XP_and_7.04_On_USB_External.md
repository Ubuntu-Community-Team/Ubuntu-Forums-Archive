---
title: "Dual Boot XP and 7.04 On USB External"
date: 2007-05-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by gaylapdancer on 2007-05-13
Heya Guys.

The Situation is this, I'm moving back to Ubuntu from openSUSE 10.2 as I managed to kill just about everything in it (Whoops). I have had previous experience with Ubuntu and Linux in general. openSUSE has been  booting from a USB SATA Hard Drive, and I would like to know if it will be possible to get Ubuntu to take its place.

At the moment, If the External is turned off or not connected, The PC will boot straight to WinXP from the Internal SATA Drive, but if the External is connected and on, I get a GRUB menu.

The PC I am using is a Dell Dimension E521, AMD Athlon 64 X2 4200+ with 1Gb of DDR2 Ram.

So will I be able to do It? I'm not worried about getting into some difficult stuff :)

---

### Post by gaylapdancer on 2007-05-13
Anyone?

---

### Post by Jouke74 on 2007-05-14
The only way is to try... I am not taking any responsibility for this but,

Make sure that Ubuntu **and Grub** are installed on the external drive. The ubuntu install should be no problem, but the Grub may be difficult, as Ubuntu tends to put it on the first harddrive (HD0) it sees. This first drive should NOT be your internal windows drive.

- Use the alternate install CD with with the external drive connected.
- During partitioning check which of the drives is HD0 (internal or external).
- Finish partitioning.
- Let install run until Grub install.
- Look at the information it shows, it wants to put itself on your MBR of HD0.
- If the internal is HD0 then replace HD0 with HD1 in the prompt when grub is installed.
- If the external is HD0 you can safely install Grub over your MBR.

---

### Post by maelgwyn_yyc on 2007-05-23
Hello,

I'll make this general, in case anyone using Google runs across this.

Jouke's advice matches alot of what I find out there -- see [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/") for a real comprehensive resource on dual booting.  And using Jouke's way, I got Ubuntu installed -- both 6.06 last year, and 7.04 this year.

I just got Feisty installed on a Dell, with an internal drive (labelled sda) for Windows (preinstalled), and my external USB drive (sdb) for Ubuntu (on a clean drive).

I used the alternate CD, though I noticed on the Live CD install that at the last screen -- the confirmation screen before the files get installed -- that under the <advanced> button there is an option for the boot loader location.  I am not sure if that works, as I got a bad ISO CD burn and decided to try the alternative version.

Like Jouke says, everything is explanatory for most of the install.  Make note (to confirm) at the partition screen which drive you're installing Ubuntu to.  Then, at the GRUB screen (when it sees Windows) you make sure the MBR is not put on the main drive (on sda or hd0).  If you do accidently, it means going into the Windows Rescue Console, and running 'fixmbr' to get rid of GRUB without reinstalling Windows.  (and for Dell users, apparently running this, or having GRUB on the main MBR, could mess up the hidden OEM ghost recovery drives -- this is what gives FAT16, FAT32 partitions in addition to NTFS on your original Dell drive.  See [http://www.goodells.net/dellrestore/index.htm]("http://www.goodells.net/dellrestore/index.htm") for more).

But I don't care about those ghost drives... reformatting is my friend, not recovery.  :p

So you will want to put it on (hd1) when you get to the next dialog box, if you're running Ubuntu on a 2nd hard disk, or (hd2) on a 3rd, etc.

Then, when you get to GRUB, you might get some error, saying the partition can't be found (I forget what error number this is).  For this, to get into Ubuntu, edit the command to run, and change the line

root (hd1,x)

where 'x' is the partition that you have it booting from (usually 0 -- same as your root)

to

root (hd0,x)

Then, if this works, change this permanently by going into the terminal, switch to the root directory, and 

sudo vi /boot/grub/menu.lst

And there, scan down until you come across the distro you're running, and change that root command to run from hd0.

The end result will be exactly what you want -- with the USB turned off or unplugged, Windows boots automatically (no GRUB menu).  With the USB turned on, and you boot to the USB drive, then GRUB appears.

Hopefully this helps the newbies out there...

---

### Post by rmcanany on 2007-05-27
This thread is addressing my exact situation.  

I wonder if you could clarify one thing for me?

As I understand it, during installation there is a partitioning setup screen.  That screen has a drop-down box that lists all the drives found.  They are in a certain order.  On my system it's sda, then sdb.  sda is my internal drive which has xp.  sdb is the drive onto which I want to install ubuntu.

At the end of the installation setup there is a confirmation screen.  It shows the target location for the grub installation.  In grub language, there's (hd0), (hd1), etc.

Are you saying that the order the drives are shown in the partitioning drop-down box corresponds to the grub order?  So in my case, sda = (hd0) and sdb = (hd1)?

TIA

---


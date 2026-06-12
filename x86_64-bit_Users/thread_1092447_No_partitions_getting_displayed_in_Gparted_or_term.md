---
title: "No partitions getting displayed in Gparted or terminal while installing ubuntu"
date: 2009-03-10
forum: x86 64-bit Users
---

### Post by Benjamin_button on 2009-03-10
Hi,

I am trying to install ubuntu 8.10 on my system and no partitions get displayed while installing.

There are no partitions displayed in Gparted It says "No devices detected"

I tried opening a terminal and executing the command 
"sudo fdisk -l"
and 
"fdisk -l"

and even that displayed nothing.

I even tried removing the data cord from the hdd and reconnecting it back, but it didn't help.

System configuration is:

HDD is : SATA: PM-WDC WD1600
I have an Intel Core 2 Duo processor E4600 

have kept is as the secondary boot device, while CD/DVD is the primary.

Suggestions are welcome...  please help me I am a newbie on ubuntu & I have been desperate to get ubuntu running on my system since the past 3 days staying awake for long hours googling and now its becoming a bit frustrating. ](*,)

---

### Post by cariboo on 2009-03-10
Your BIOS is probably set for emulation mode. Go into the BIOS and check to see if there is an ACHI setting. 

**Note**: Unless you have an up-to-date XP installation, it may not boot with ACHI enabled.

Jim

---

### Post by Benjamin_button on 2009-03-10
I could not find ACHI settings anywhere in BIOS.
Can you please give me pointers on where exactly should i check?

---

### Post by Benjamin_button on 2009-03-10
hello... plz help me sort it out...

---

### Post by ranch hand on 2009-03-10
What have you got, if anything, on your hard drive?

Have you done any formatting our partitioning on this drive?

---

### Post by Benjamin_button on 2009-03-10
I have windows XP installed.

I have partitioned my hard disk in 4 drives. but now, have deleted the partitions to have:

C drive which has winx xp and
unformatted disk

---

### Post by cariboo on 2009-03-10
Have you tried the manual option? Also does what you see look anything like the attached screenshot?

Jim

---

### Post by Benjamin_button on 2009-03-11
No, this is not what i see. To me it looks like something like the screen shot attached.[ATTACH]106120[/ATTACH]

---

### Post by ranch hand on 2009-03-11
Did you partition with XP or from your Live CD?

With the live CD try;
```

sudo cfdisk /dev/sda

```
If you do not have SATA drives use hda instead of sda.

---

### Post by Benjamin_button on 2009-03-11
for the command

sudo cfdisk /dev/sda

It gives me fatal error: Cannot Open Disk drive

Yes it is a SATA disk.

Please help it's testing my patience beyond limit now

After a day of hard labor on ubuntu and the different modes I strongly feel there is something related to APIC and AHCI mode which i am doing wrong.

I have enabled APIC mode in BIOS

from where do i enable AHCI mode? 

Some one plz. take a stab

---

### Post by ranch hand on 2009-03-11
Ok, this is wierd.

Does your XP installation work?

Did you partition with Ubuntu or XP?

I do not dual boot with any MS product.  I have setup one dual boot with Vista Home Basic.

Most people recommend that you partition from MS to set up the partitions as it makes your MS OS happy.  You can format the partitions later.

If XP is working can you see all of your drive with whatever partition tool it has? 

I do not seee how APIC can be the problem.  AHCP should not be a problem in Ubuntu as it is supported in the kernal, it may be a problem in XP if you are not running with SP2.

Seeing that your problem seems to be with Ubuntu, I doubt that AHCP is the problem.

Not know what BIOS you are running so you can find any info on it easier than anyone else from the MB manufacturers website.

I do not reccomend doing anything with it but it would be interesting to know if sfdisk can see the drive.  I am fairly fresh at fooling with this stuff and frankly sfdisk scares the crap out of me.  Just seeing if it picks up the drive can't hurt.

If XP is working the BIOS are not having any problem detecting the drive so I would leave it alone.

We really need to know how you partitioned the drive and with what.  We really need to know if XP works.  We really need to know if XPs partition tools see this drive and what it has to say about the unused portions.

This can be frustrating but take a deep brreath and realize that it is very likely something simple that we are missing here.

---

### Post by utnubuuser on 2009-03-11
My laptop had similar results with certain versions of gparted.  Had to dowload the latest gparted iso from their site.

Have you got an older version of ubuntu you could try?

---

### Post by nzadLithium on 2009-03-12
Did you check if the drive is mounted? It's unlikely it would be unless your mounting it yourself, but if its mounted unmount it :D
(to check if its mounted type 'mount' at a terminal and check the list for anything that says /dev/sd* and /dev/hd*). If you find something then do sudo umount /dev/(whatever it was called).

If thats not working I would suggest this:
cat /dev/hd*
cat /dev/sd*

check that something shows up for at least one of those commands. If you don't have something show up you've got something real weird going on :p
Once you've confirmed that /dev/hd* or /dev/sd* devices are created, run:
sudo fdisk -l (/dev/name)
so if you find a device called /dev/sda exists do
sudo fdisk -l /dev/sda
If you get multiple devices listed back from that command then try each of them until you find your hard disk.

If you sucessfully achieved all of that and can see the partitions on your drive it pretty much has to be an issue with the disk already being mounted, so check that its not mounted again. :D

---

### Post by Yellow Pasque on 2009-03-12
> **Benjamin_button said:**
> I could not find ACHI settings anywhere in BIOS. Can you please give me pointers on where exactly should i check?
It varies by motherboard/BIOS. Generally, you find the option in 'SATA Options' or perhaps under a menu for your southbridge.

---

### Post by ranch hand on 2009-03-12
I bet that nzadLithium has the right direction here.

When you boot your Live Cd there is probably some icon on the desktop that refers to "media" something or maybe "XP".  Right click on that and click on "unmount".

Then try your installer again.  Probably works fine.

---


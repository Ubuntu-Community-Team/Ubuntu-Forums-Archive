---
title: "dual boot U 8.10 desktop 64AMD live CD install;w/U8.04.2"
date: 2009-03-28
forum: x86 64-bit Users
---

### Post by ken78724 on 2009-03-28
Ubuntu 8.10 desktop 64AMD live CD install with multiple gparts; wanting 8.04.2 to remain operable & files accessible on either partition by either OS; eventually want to upgrade 8.10 to U Studio.

Quote:
Originally Posted by lse123 View Post
I want to install in my 64bit PC (vista 64bit one partition + vista 32bit anather partition) Kubuntu 9.04 64bit when get released the full dvd version ... Well when it will be released the full version exactly in April ? I must install to 64 bit partition ? There are Linux software runs only with Kubuntu(I mean Linux) 32bit ? May install alone , is it easy , I am web developer/designer ? I must first find install STEPS (Where?) print them, and follow them STEP-BY-STEP ? I have a textbook about "Fedora & XP ISBN:978-1-4188-3725-9 /E:05/19/2006" from course.com,
Please guide me on this.
am amidst manual 8.10 install to dev/sda3 ext 3 having 8.1 giB and
271.56 mb used on gparted 750 Maxtor HD/ have five partition. Yes, I
have backed up data made with ubuntu 8.04.2 found in
dev/sda1 Ext 3 62.5 giB with 16.8 Gib used
fdev/sda2 extended with 2.85 GiB unused
dev/sda3 ext 3 having 8.1 giB with 271.56 mb used
dev/sda4 jfs 625.4 giB with zero used
dev/sda5 linux swap with 2.81 GiB unused

tried this from live CD install, going to the loader and specifying
want to load only to dev/sda3 ext 3 but stopped after being prompted
to designate dev/sda3 ext where I could verify the 8.1 giB was there.
Immediately it scanned the partition and then it asked "Designate a
mount point and gave me a drop down menu with 6 options. in first
trial, I selected /opt and message said "you cannot do this"; so I
backed up and I selected another option and got the "you can't do
this" so I backed up and set it to "/" and the installer automatically
reset the selected gpart to I believe dev/sda1 jfs 8.1 giB and fore
warmed me that I would write over and delete data & program files in
all partitions;

so, I packed my bag so I could learn a correct selection which won't delete/lose the U 8.04.2 OS &/or data files on the gparted 62 gig as noted above.

Clarifying? what manual install decisions should I executive. :popcorn:

---

### Post by ken78724 on 2009-03-29
:( could use any guidance with Ubuntu 8.10 desktop 64AMD CD
 1) have insufficient know how to do the manual settings via a good CD live
     what do you mount? "/"; "/home"; "/boot" or "/tmp" or ,,,, I want to save data and the ubuntu 8.04.2 that I run an already existing partition; just do not know what mount setting to use to achieve that   
 2) update manager will not allow, updates but I see 460 that want to update
 3) from the U 8.04.2, I cannot go online; & firefox became dysfunctional for unknown reason, perhaps the long term problem arising if you click system and click on CNR, which again is non-functional or cannot be reached?

need your help as I am able 10 hrs later to come here only with live CD.  

:confused: am new to this kind of problem and have no book to guide me.
ken

---

### Post by 3Miro on 2009-03-29
Authomatic install would wipe out everything on your HDD, do not do it!!!!

I am trying to understand what is going on here. Basically you need a large drive and give it several partitions:

One partition for each windows (one for vista 64 and one for vista 32 - you probably already have those).

Linux in general uses at least two partitions (two is a good number). One partition is the / folder (it is kind of like c: under windows) and one partition for swap. I heard you can go without swap, but then make sure you have plenty of RAM (and still the system might be a bit slower). The swap partition should be about the size of your RAM.

When you have two Linux versions installed, they can share the same swap partition.

I am not currently sure about the state of your system. Did you actually install the 64-bit Linux? Did you reformat the HDD? Can you go into Vista?

Can you post the result of the following terminal commands:
df
sudo fdisk -l

---

### Post by 3Miro on 2009-03-29
OK maybe this would help:

When you get tot he partition part of the installer, select custom/manual partitioning, you don't want anything guided and/or automatic.

Select the partition where you want the new system to live and give it mount point /.

On the menu, you can choose which partitions are to be formated. You only need to format the new / partition, everything else should not be touched.

Then the rest should work. If you have made changes to the boot menu, you may give the advanced option of not installing grub, however, you will have to manually edit some files afterwards. If you have made no changes to the boot menu, it is safe to install the boot loader.

---

### Post by 3Miro on 2009-03-29
> **ken78724 said:**
> :( could use any guidance with Ubuntu 8.10 desktop 64AMD CD
 1) have insufficient know how to do the manual settings via a good CD live
     what do you mount? "/"; "/home"; "/boot" or "/tmp" or ,,,, I want to save data and the ubuntu 8.04.2 that I run an already existing partition; just do not know what mount setting to use to achieve that   
 2) update manager will not allow, updates but I see 460 that want to update
 3) from the U 8.04.2, I cannot go online; & firefox became dysfunctional for unknown reason, perhaps the long term problem arising if you click system and click on CNR, which again is non-functional or cannot be reached?

need your help as I am able 10 hrs later to come here only with live CD.  

:confused: am new to this kind of problem and have no book to guide me.
ken

If you have backed up all your data, then I can give you step by step instructions on how to install both 8.04.2 and 8.10 (64 or 32-bit), from the beginning. We could reformat/repartition everything (and delete all data).

Also, do you have/want to have any windows installed. It is important that I know so we can preserve/install that one when I give you the instructions.

If you want we can try to fix the current installation of 8.04.2, but I might be unable to do everything, we might need help form other people.

---

### Post by ken78724 on 2009-03-30
3Miro, sorry I must delay this till late tomorrow. I'll do the "df
sudo fdisk -l".  

solely linux partitions has been done to my 750 giB HD; gparting was done with linspire 6.017 live & then, an Ubuntu 8.04.1 64 AMD Hardy Herron install. in Mar 09 I tried to install Studio Ubuntu 8.10 desktop 64 AMD from a 1.2 giB DVD. Amidst the install the installer called for an update and that is when the update manager said, "Report this malfunction as a bug" as it had gone into a gyration and kept baulking till I quit and worked around the update manager and never let it take over. TheLasko advised, "instead of butting heads do a live CD install with Ubuntu 8.10 desktop 64AMD.iso." I started that but did not know in the manual install to use "/." as you advised. 

Regret my ole body won't take working late tonight and tending to a client early tomorrow or I would get over to the machine with the 750 gib HD and post what has been requested in this thread.

whereas I may not have new work backed up this problem may have to be delayed until project deadlines are met.

---

### Post by ken78724 on 2009-04-10
466 ubuntu updates will not update after all these days. Just received this quote: "Can't install 'ubuntu-desktop'

It was impossible to install a required package. Please report this as a bug."

---

### Post by ken78724 on 2009-04-24
the following scenario let me resolve my problem 
deb [http://ubuntu-bug](http://ubuntu-bug) apt-get
E: Malformed line 75 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Routine used to work around the problem: 
An error resulted as follows:
E: Type 'sudo' is not known on line 57 in source list /etc/apt/sources.list

E: The list of sources could not be read.

Go to the repository dialog to correct the problem.

E: _cache->open() failed, please report.

The message pretty well tells you what is wrong, to repair the problem press Alt-F2 and type:
Code:  gksu gedit /etc/apt/sources.list
Enter your password when prompted.

This will open the file /etc/apt/sources.list in a text editor as root

Next enable line numbering in the text editor by going to Edit-->Preferences-->View and check the line number box.

I scrolled down to line 75 and completely removed the line, then saved and followed by running the Ubuntu 8.10 intrepid installation update that synaptic program manager had before it over the past three (3; or was it four??) months????? from notes eight months earlier I learned Save the file and close the text editor. Go to System-->Administration-->Synaptic Package Manager and click the Reload button. You should now be able to download packages again.

While you have Synaptic open go to Edit-->Mark Packages By Task, a window will pop up, just scroll down to Video Creation And Editing Suite and mark it for installation, this should install most of the programs you need for what you want to do. :):)  

Truly and not sure how a notice "a source list /etc/apt/sources.list"
arrived, telling me that an internal error existed 

For Ubuntu Studio on 8.10 intrepid, TheLasko's solution may work but since he uses 8.04 not 9.04 I believe the developers should tell us how soon we'll have a working Studio.

---


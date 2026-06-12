---
title: "HOW CAN I USE TWO HDDs AT THE SAME TIME?"
date: 2006-05-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by sidy on 2006-05-25
Hello there, I am confusing here!
On my PC I have one hd40 (slave, where I run ubuntu 5.10 upgraded to 6.06) and another hd80 (10gb for windows and 70 for ubuntu). In other words I have 110GB for ubuntu.
Now, because my hd40 is full, I w'd like to transfer datos to the 80hd or 70gb partition.

- I have tryed:
1-  Installed ubuntu on the 70gb partition, but wasn't displaying graphic. To sort it, I did what I had done before when I had the same problem (graphic display) ctrl+alt+F1:
'sudo dpkg-reconfigure xserver-xorg'
then I choose
'nv' , enter, then
'nv nVidia FX5200LP'  ,and the problem was suppost to be sorted, but it didn't.
(as I typed 'lspci' I've got the following information of the graphic card 'nVidia Corporation NV34 [GeForce FX5200LP] (rev a1)' , I also typed this in full didn't work either).

2-  So I rebboted and logged in to ubuntu on 40hd. On the terminal, I was meant to reach the 70gb partition. It was mounted (hda1 hda2 hda3), so I did:
'sudo mount /dev/hda2 /mnt/hda2' then enter, came up 'mount: you must specify the file system file' , then I typed 'cd hda2' enter 'ls' , did'nt show any thing, because there is nothing there, then nautilus. ... I can only open, but not alowed to copy or even delete to mount again. (by the way, the hda1 2 3 had been mountend before the 70gb partition been done).

So basically, I would like to use both hdds.
WHAT CAN I DO TO USE BOTH HDDS AT THE SAME TIME?

Rgds,

---

### Post by kingmonkey on 2006-05-25
What do you mean use both hdds at the same time?

What are you trying to do exactaly?

---

### Post by sidy on 2006-05-26
[QUOTE=kingmonkey]What do you mean use both hdds at the same time?

What are you trying to do exactaly?[/QUOTE]

On my pc I have one hdd of 40gb (slave) and another of 80bg (master).

The hdd of 40 is full. SO in my little knowledge I could use the hdd of 80 gb through one of two ways.

- Logged on the hd of 40 gb (hdb1), I go on terminal and through there I put some commands and use the hdd of 80 gb. (I mean, being able to save, copy, delete datos, stuff in there), so then I can transfer information from the hd of 40 gb to the 80 gb. WHAT COMMANDS ARE THEY?

- The other way is installing ubuntu on the hd of 80 gb, but when I did it, graphic display didn't work. So, because I had this problem when I installed  ubuntu on the hdd of 40gb, I did the following:

ctrl+alt+F1:
'sudo dpkg-reconfigure xserver-xorg'
then I choose
'nv' , enter, then
'nv nVidia FX5200LP' 

And the problem was suppost to be sorted, but it didn't. I still don't have graphic displaying. 

So WHAT SHOULD I HAVE DONE?

I'm  not expert on it, but I can follow commands you give, please.

rgds.

---

### Post by frenchdm on 2006-05-28
umm...

As long as both HDDs are mounted correctly you can read/write to them as much as you want/need.  The only exception being NTFS formatted drives which can't be written to as standard.

Perhaps you are thinking you need to have each of the HDDs as ext2 or ext3 in order to access them?  ubuntu can read and write to FAT drives fine.

---

### Post by brt on 2006-05-28
i would recommend setting up your harddisk by setting up your filesystem-table which is stored in the file: /etc/fstab

if you are using ide drives the devices you have are like this:
hda - primary master   hda1, hda2, hda3, ...
hdb - primary slave      hdb1, hdb2, hdb3, ...
hdc - secondary master (mostly cd/dvd)
hdd - secondary slave  hdd1, hdd2, hdd3, ...

so your desired partitions should be named like hdb1, hdb2, ... or hdd1, hdd2, hdd3, ...

the advantages are that the partitions are mounted automatically on bootup, and mounting is even easier.

but first it would be a good idea to have a look at your partitions, e.g. what filesystemtype they are, etc:

if your HD is configured as slave on the primary ide controller you can use this:
**:~$ sudo cfdisk -P s /dev/hdb**

my second HD is connected as slave to the _secondary_ ide controller, thats why i have to use hdd and it looks like this:

Partition Table for /dev/hdd

               First       Last
 # Type       Sector      Sector   Offset    Length   Filesystem Type (ID) Flag
-- ------- ----------- ----------- ------ ----------- -------------------- ----
 1 Primary           0      385559     63      385560 Linux (83)           Boot
 3 Primary      385560    39070079      0    38684520 Extended (05)        None
 5 Logical      385560    39070079     63    38684520 Linux LVM (8E)       None
 2 Primary    39070080   321669494      0   282599415 Linux LVM (8E)       None


the first number in each line is the partition numer (leads to hdd1, hdd2, hdd3, hdd5) as you can see in the example partitions 3 and 5 have identical start and end -sectors, this is what happens if you use logical partitions. just notice these are not different partitions, its just like partion #3 is only a container for the "real" logical partion #5.
the other thing you see in the putput is the type of the partion, remember it as you will need it to set up your filesystemtable.

once you know your partions you can set up your /etc/fstab:

i assume you do not have setup LVM like me, maybe you have ordinary ext2/ext3 (Linux) partitions and ntfs from XP or vfat (=fat32) from w98, i assume e.g.:
hdb1 = ntfs
hdb2 = ext3 (ubuntus default)
hdb3 = vfat (fat32)

open up an editor to edit /etc/fstab:
**:~$ sudo gedit /etc/fstab**

do not change any lines which are already present, just add new lines for the partitions you want to mounted, like this:
#<file system> <mount point>  <type> <options> <dump> <pass>

/dev/hdb1   /mnt/hdb1  ntfs   defaults   1   1
/dev/hdb2   /mnt/hdb2  ext3 defaults   1   1
/dev/hdb3   /mnt/hdb3  vfat   defaults   1   1

just use the right values for <file system> <mount point>  <type> as you have found out before, save and exit.

after you have created the desired folders, you can mount the partitions this way:

:~$ sudo mount /mnt/hdb1
:~$ sudo mount /mnt/hdb2
:~$ sudo mount /mnt/hdb3

or even simpler using:
**:~$ sudo mount -a**  

which mounts everything which is listed in fstab.

and they will be automatically mounted at bootup :)

for more information just have a look at:

**:~$ man mount**

and

**:~$ man fstab**

its always easier if you are understanding what you are going to do ;)

---

### Post by sidy on 2006-05-28
[QUOTE=brt]i would recommend setting up your harddisk by setting up your filesystem-table which is stored in the file: /etc/fstab
...
so your desired partitions should be named like hdb1, hdb2, ... or hdd1, hdd2, hdd3, ...[/QUOTE]

Hi There, Thank you for lots of tips, most of then worked fine.

I mounted hdb1, 2, 3, hdd1, 2, 3.

When I typed 'sudo cfdisk -P s /dev/hdb' (if I add ':~$' says command not found), came up the following:

Partition Table for /dev/hdb  (HERE ON YOUR EXAMPLE IS '/dev/hdd')

                       First       Last
 # Type       Sector      Sector   Offset    Length   Filesystem Type (ID) Flag
-- ------- ----------- ----------- ------ ----------- -------------------- ----
 1 Primary           0        74927159     63     74927160 Linux (83)                   Boot
 2 Primary   74927159  78156224       0       3229065 Extended (05)            None
 5 Logical    74927159  78156224     63       3229065 Linux swap / So (82)   None

I whent to '**:~$ sudo gedit /etc/fstab**' and added:

/dev/hdb1   /mnt/hdb1  ntfs   defaults   1   1
/dev/hdb2   /mnt/hdb2  ext3 defaults   1   1
/dev/hdb3   /mnt/hdb3  vfat   defaults   1   1

And when I typed:
'sudo mount /mnt/hdb1' came up:
mount: /dev/hdb1 already mounted or /mnt/hdb1 busy (I pressume that is because I was running on hdb1)
mount: according to mtab, /dev/hdb1 is already mounted on /mnt/hdb1

When I typed:
'sudo mount /mnt/hdb2' (or **:~$ sudo mount -a**)  came up: 
mount: wrong fs type, bad option, bad superblock on /dev/hdb2,
            missing codepage or other error
            (aren't you trying to mount an extended partition,
            instead of some logical partition inside?)
            In some cases useful into in found in syslog - try
            dmesg | tail or so 

I typed 'dmesg | tail':

[      67.858911] Bluetooth: L2CAP ver 2.8
[      67.858916] Bluetooth: L2CAP socket layer initialized
[      67.863830] Bluetooth: RFCOMM socket layer initialized
[      67.863853] Bluetooth: RFCOMM TTY layer initialized
[      67.863855] Bluetooth: RFCOMM ver 1.7
[    884.462947] ibm_acpi: ec object not found
[12049.076058] NTFS driver 2.1.25 [flags: R/O MODULE].
[12054.615714] attempt to access beyond and of device
[12054.616015] hdb2: rw=0, want=4, limit=2
[12054.616020] EXT3-fs: unable to read superblock

(I did not understand the above information, specially how to enable to r/w superblock, how can I unblock and being able to copy or drag datos from hdb1 to hda2 or hdd?)

Then I typed:
'sudo mount /mnt/hdb3' came up:
mount: special device /dev/hdb3 does not exist

If you have further information, they will be welcome!

(AGAIN, I JUST NEED TO COPY STUFF FROM hdb1 to hda2 or hdd, I DON'T KNOW HOW TO DO IT)

thank you.

---

### Post by lcbu on 2006-05-28
I think this link will help you:

[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by brt on 2006-05-28
uuups, i used the **:~$** to show this is a command, just ignore it.
> 
First Last
# Type Sector Sector Offset Length Filesystem Type (ID) Flag
-- ------- ----------- ----------- ------ ----------- -------------------- ----
1 Primary 0 74927159 63 74927160 Linux (83) Boot
2 Primary 74927159 78156224 0 3229065 Extended (05) None
5 Logical 74927159 78156224 63 3229065 Linux swap / So (82) None

this shows that hdb2 and hdb5 are no real partitions, you can not mount them, hdb5 is only one small swap partion and forget about hdb2. (you can imagine hdb2 as the primary partition containing logical partitions like hdb5)

so you wont need to mount hdb2, hdb5 or hdb3 (you do not have a hdb3 partition)

you can not just copy and paste my examples because your computer is different then mine, i just gave examples.

remove the lines containing hdb2 and hdb3 from /etc/fstab and change the filesystemtype in the line containing hdb1 from ntfs to ext3, so it will look like this:

**/dev/hdb1 /mnt/hdb1 ext3 defaults 1 1**

after this you can type:
[B]
sudo mount -o remount /mnt/hdb1[/B]

now you should be able to access all data in /mnt/hdb1

---

### Post by sidy on 2006-05-29
Hello again.

A have done what you have told me last.

At the same time a friend of mine gave same extra information on how to use both HDDs at the same time or been able to copy datos from and to hdds.

On terminal instead of just 'nautilus' I did 'sudo nautilus', so I was on root, there I'd been able to change permissions, I changed on 'file group and users' to my name, so now, I AM ABLE TO COPY DATOS FROM AND TO BOTH HDDs.

But I have another concerne.

I WOULD LIKE TO BOOT DIRECT ON THE HD OF 80GB, NOT THROUGH THE 40GB.
But when I try to do so all what I have is a black screen with a dash on the top-left-corner.

No graphic graphic displaying, so ctrl+alt+F1:
' sudo dpkg-reconfigure xserver-xorg '
then I choose
' nv ' , enter, then
' nv nVidia FX5200LP '
' /etc/init.d/gdm stop '
' /etc/init.d/gdm restart '

And I was suppost to have graphic displaying , but it didn't.

WHAT CAN I DO NOW?

rgds

---


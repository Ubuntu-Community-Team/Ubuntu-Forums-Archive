---
title: "Dual Boot Problem"
date: 2009-01-12
forum: x86 64-bit Users
---

### Post by CCat47 on 2009-01-12
First off, I am very new to Linux systems (about 2 weeks). Please be patient if I dont understand you right away.
I've read and searched but can't find an answer to this problem.

I have Vista HP x64 installed on (hd2,0)
Ubuntu 8.10 x64 is installed on (hd0,0) grub is on this HDD.

If I put the Vista HDD first in the bios it starts and runs without any problems.

If I put the Ubuntu disk as the first disk the grub menu comes up with the Ubuntu options and the Vista Loader. I can then start Ubuntu without any problems.

Now the problem: If I select the Vista Loader it says "Bootmgr is missing...ctrl + alt + del to restart"
I looked in the root of the Vista drive and bootmgr is there.

I posted this problem on dslreports
[http://www.dslreports.com/forum/r21722205-Resident-PITA-With-Another-Boot-Question](http://www.dslreports.com/forum/r21722205-Resident-PITA-With-Another-Boot-Question)
but havent found anything yet. Most of my info is there.

Any Ideas???

---

### Post by caljohnsmith on 2009-01-12
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by CCat47 on 2009-01-12
Tried doing that. All I get is no such file or directory.
I typed it exactly as you have it posted. Tried it 3 times.

---

### Post by caljohnsmith on 2009-01-12
So did you download the script to your Ubuntu desktop? If so, how about posting the output of:
```
ls -l ~/Desktop
```
Note "-l" is a lowercase L, not a one.

---

### Post by CCat47 on 2009-01-12
Tried it again, get the same message. File / directory does not exist.

---

### Post by caljohnsmith on 2009-01-12
Can you copy/paste what is in your terminal session so I can see it? How about trying:
```
cd /home/[COLOR="Blue"]<username>[/COLOR]/
ls -l
cd Desktop
ls -l

```
And replace <username> with your Ubuntu user name.

---

### Post by CCat47 on 2009-01-12
dave@dave-desktop:~$ cd /home/dave/
dave@dave-desktop:~$ ls -l
total 32
drwxr-xr-x 4 dave dave 4096 2009-01-12 14:36 Desktop
drwxr-xr-x 2 dave dave 4096 2009-01-11 07:23 Documents
drwxr-xr-x 2 dave dave 4096 2009-01-11 12:34 dwhelper
lrwxrwxrwx 1 dave dave   26 2009-01-11 07:19 Examples -> /usr/share/example-content
drwxr-xr-x 2 dave dave 4096 2009-01-11 07:23 Music
drwxr-xr-x 2 dave dave 4096 2009-01-11 07:23 Pictures
drwxr-xr-x 2 dave dave 4096 2009-01-11 07:23 Public
drwxr-xr-x 2 dave dave 4096 2009-01-11 07:23 Templates
drwxr-xr-x 2 dave dave 4096 2009-01-11 07:23 Videos
dave@dave-desktop:~$ cd Desktop
dave@dave-desktop:~/Desktop$ ls -l
total 8

---

### Post by caljohnsmith on 2009-01-12
> **CCat47 said:**
> 
```
dave@dave-desktop:~$ cd Desktop
dave@dave-desktop:~/Desktop$ ls -l
[COLOR="Red"]total 8[/COLOR]
```
The above output shows there should be 8 items on your desktop, so did you paste the full output? Does one of those items listed include the "boot_info_script_011.sh" that you downloaded? If so, how about doing:
```
sudo bash /home/dave/Desktop/boot_info_script*.sh
```

---

### Post by briandu on 2009-01-12
CCAt47, u seem to have a grub config problem.

If u go to /boot/grub and look inot file menu.lst - in this file look for a reference to bootloader + 1, if not that is the problem.

Let us know, thx

---

### Post by CCat47 on 2009-01-12
Heres my menu.lst

default 6
timeout 10

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=6d976ebf-8c3b-4ad8-98d7-0e7b2148d9dc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6d976ebf-8c3b-4ad8-98d7-0e7b2148d9dc

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-9-generic
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=6d976ebf-8c3b-4ad8-98d7-0e7b2148d9dc ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=6d976ebf-8c3b-4ad8-98d7-0e7b2148d9dc ro  single
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=6d976ebf-8c3b-4ad8-98d7-0e7b2148d9dc ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=6d976ebf-8c3b-4ad8-98d7-0e7b2148d9dc ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows Vista/Longhorn (loader)
rootnoverify (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

---

### Post by CCat47 on 2009-01-12
Heres the results for other entry @ caljohnsmith

```
dave@dave-desktop:~$ sudo bash /home/dave/Desktop/boot_info_script*.sh
[sudo] password for dave: 
bash: /home/dave/Desktop/boot_info_script*.sh: No such file or directory
dave@dave-desktop:~$
```

Theres nothing on my desktop at all (that shows anyway)

There are 2 movies that I am downloading via torrent but other than that theres nothing.
I searched the HDD and didnt find any file like that.
Looked in file manager and nothing with that name is there.

---


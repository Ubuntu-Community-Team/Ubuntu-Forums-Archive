---
title: "HowTO: Compile WineCVS on 64 bit Ubuntu"
date: 2007-09-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by mikeym on 2007-09-24
Oh my God, that was hard!

That took 14 hours of constant work! But it's working now. I'll post what seemed to work in the end:

[SIZE="6"][COLOR="Red"]
**How To Install Wine CVS 32 Bit in 64 Bit Ubuntu**[/COLOR][/SIZE]

I'll keep this as general as I can and make links to the original documents so hopefully it wont go out of date to quickly.

[COLOR="Red"][SIZE="4"]Installing a 32 bit system with chroot[/SIZE][/COLOR]

This bit is taken from [this excellent post]("http://ubuntuforums.org/showpost.php?p=3231948&postcount=219").

So first get *chroot* and the utility for setting up basic systems, create a directory for your new *chroot* system and open the configuration file for *chroot* to set up your distribution - like so:

```

sudo apt-get install dchroot debootstrap
sudo mkdir /chroot/
sudo gedit /etc/dchroot.conf

```

Add this line into the file (where your distribution is feisty):

```

**[COLOR="Red"]feisty[/COLOR]** /chroot

```

Create a basic system under */chroot* and copy across the locals information from your system.

```

sudo debootstrap --arch i386 **[COLOR="Red"]feisty[/COLOR]** /chroot
sudo cp /var/lib/locales/supported.d/local /chroot/var/lib/locales/supported.d

```

(Note that this again assumes you are using feisty)

Enter your new *chroot* environment and setup the locals.

```

sudo chroot /chroot
dpkg-reconfigure locales
```

Exit *chroot* and add the **main, restricted, universe **and** multiverse** repositroes to your *chroot* system.

```
exit
sudo gedit /chroot/etc/apt/sources.list
```

Add the following lines:

```
deb http://archive.ubuntu.com/ubuntu **[COLOR="Red"]feisty[/COLOR]** main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu **[COLOR="Red"]feisty[/COLOR]**-security main restricted universe multiverse
```

(Again note the use of feisty repositories)

Re-enter *chroot* and upgrade all packages then exit again:

```
sudo chroot /chroot
apt-get update ; apt-get upgrade
exit

```

Copy across settings on users, passwords, groups and hosts to *chroot* then open */etc/fstab* (has settings for mount points) for editing:

```
sudo cp /etc/passwd /chroot/etc/
sudo cp /etc/shadow /chroot/etc/
sudo cp /etc/group /chroot/etc/
sudo cp /etc/sudoers /chroot/etc/
sudo cp /etc/hosts /chroot/etc/
sudo gedit /etc/fstab
```

Add mount points in the *chroot* system so it shares your */home* folders, */tmp *folder, */dev* (devices), */proc* (pseudo-filesystem for runtime state of the kernel and executing processes) and *fonts.*

```
/home /chroot/home none bind 0 0
/tmp /chroot/tmp none bind 0 0
/dev /chroot/dev none bind 0 0
/proc /chroot/proc proc defaults 0 0
/usr/share/fonts /chroot/usr/share/fonts none bind 0 0
```

[COLOR="Red"][SIZE="5"]****Warning once these are mounted if you  try to delete your /chroot system without un-mounting you will delete your home folders!*****[/SIZE][/COLOR]

I nearly did this!!!!

Create a script for un-mounting your file system from *chroot*:

```
sudo gedit /usr/bin/chroot_unmount
```

Add the following lines for un-mounting chroot:

```
#!/bin/bash
sudo umount /chroot/home
sudo umount /chroot/tmp
sudo umount /chroot/dev
sudo umount /chroot/proc
sudo umount /usr/share/fonts
```

Make the script executable then create a moujnt point in */chroot* for the fonts and auto-mount the file systems:

```
sudo chmod +x /usr/bin/chroot_unmount
sudo mkdir /chroot/usr/share/fonts
sudo mount -a

```

Auto-mount will automatically mount your directories in chroot each time you start your computer so you MUST UN-MOUNT CHROOT BEFORE DELETING IT!

[COLOR="Red"][SIZE="4"]Getting the dependencies for Wine[/SIZE][/COLOR]

Download the install file for the recommended 32 bit packages for your distribution from the [winehq wiki]("http://wiki.winehq.org/Recommended_Packages"). For the packages for [COLOR="Red"]**feisty**[/COLOR] click [here]("http://kegel.com/wine/feisty.sh"). Save the file to your home directory.

Following [the 64 bit guide on *winehq*]("http://wiki.winehq.org/WineOn64bit#head-08d4087d863019523214064680fcf26721c9a1af") get and install the necessary library packages for *wine*.

```

sudo apt-get install libfreetype6-dev fontforge ia32-libs
sudo apt-get install gcc flex bison libc6-i386 libc6-dev-i386 lib32z1-dev

```

I'm not sure about the ones marked *-dev* as these are development packages for compiling and we won't be doing that on the 64 bit system.

Next enter *chroot* and install the package requirements by running the script you downlaoded. 

```

dchroot -d
cd ~
chmod +x [COLOR="Red"]**feisty**[/COLOR].sh
./[COLOR="Red"]**feisty**[/COLOR].sh

``` 

Get one extra package so that you get ALSA support:

```

sudo apt-get install libasound2-dev

```

Make a directory for the CVS source code for *wine*, and as per the instructions [here]("http://www.winehq.org/site/git#clonecvs"), download the latest CVS of *wine*:

```

mkdir packages
cd packages
cvs -d :pserver:cvs@cvs.winehq.org:/home/wine login

```

Enter the password "cvs" and download *wine*.

```

cvs -z 3 -d :pserver:cvs@cvs.winehq.org:/home/wine checkout wine

```

Change into the "wine" directory and configure the source. (I don't believe the LDFLAGS="..." section is necessary as it tells it to look in the 32 bit library folders which is unnecessary as we are compiling in 32 bit *chroot*.) Tell the configure script to compile as 32 bit and prepare the files for installation to the "/usr" folder rather than the default "/usr/local" folder (which Ubuntu doesn't use for packages), and ask it to tell us if there are any missing dependencies at the end of the configuration.

```

cd wine
CC="gcc-4.1 -m32" LDFLAGS="-L/lib32 -L/usr/lib32.local -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32i -Wl,-rpath,/usr/lib32.local" ./configure --prefix="/usr" --verbose

```

Assuming that went OK with no obvious demands for missing libraries at the end, build the dependencies and then *wine*. 

```

make depend && make

```

Assuming that ended with no errors (warnings are to be expected), exit *chroot* and install the fantastic checkinstall package which will create a package from our source and install it for us.

```

exit
sudo apt-get install checkinstall

```

Right we're ready to install it. Quickly take a note of the version then start making the package.

```

cd ~/packages/wine
cat VERSION
sudo checkinstall

```

It will ask you if you want to create documentation. Select "y", you do. Enter a description like "WINE (Windows Layer Emulator)" then change the version (option "3") and enter the version of wine that you have just found followed by "-CVS". It should look like "0.9.45-CVS". 

Press <enter> to begin making the package and installing it.

Hopefully that all went OK and you have a nice new version of *wine*!

Run *winecfg* to set it up. Then follow the step below to make it fit with your Ubuntu colour-scheme.

Download the Ubuntu Human colour-scheme for wine from [this website]("http://my.opera.com/area42/blog/index.dml/tag/wine"), or download it direct [here]("http://files.myopera.com/area42/files/ubuntu_colors.reg"). and save it to your home folder. Open *regedit* with *Wine* and select **File->Import**. Find the "ubuntu_colors.reg" file you saved and import it.

```

wine regedit

```

And your done!

---

### Post by Kilz on 2007-09-24
Wow that looks like a lot of work, why didnt you just use the .deb file from the winehq?

---

### Post by mikeym on 2007-09-24
The deb file version didn't have to fix in it for getting half life 2 to work properly and that's the reason for me having wine.  

I cut out all the wrong steps I took to get there :)

P.S 

Please post if you have any problems because I didn't have a change to clear my system and run through the steps again following my guide, and I'll try to ammend them.

---


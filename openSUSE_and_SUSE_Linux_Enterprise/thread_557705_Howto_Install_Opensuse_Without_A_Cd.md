---
title: "Howto: Install Opensuse Without A Cd"
date: 2007-09-23
forum: openSUSE and SUSE Linux Enterprise
---

### Post by tuxcantfly on 2007-09-23
*Main Website At [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)*

**What This Does**

It's an installer for Windows or Linux users that lets you install OpenSuse 10.3 or the Factory version without a CD. The way it works is that a small (8 MB) installer places the PXE (netboot) version of the OpenSuse installer on your hard drive, and configures your boot loader, either NTLDR if using Windows, or GRUB if using Linux, to boot from the PXE installer, and downloads and installs OpenSuse from the net.

**Requirements**

You will need to either have a Windows (95-Vista) or Linux (any distro that uses GRUB) install already on your hard drive. You'll also need an internet connection. Apart from that, the requirements are the same as the standard OpenSuse 10.3 requirements.
[b]
Instructions[/b]

Download the appropriate installer package for openSUSE 10.3 or Factory from [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

If using Windows, download the .exe file, if using OpenSuse, Fedora, or another rpm-based distro, download the .rpm file, if using Ubuntu, Debian, or another deb-based distro, download the .deb file, and if using a distro that doesn't support rpm or deb, download the sh file.

Then, install the package, and reboot. A menu entry should appear in the boot menu, titled "UNetbootin". Select that entry, and boot.

If installing openSUSE, after rebooting, ignore any error messages and select back if prompted for a CD, then go to the main menu, select the "Start Installation" option, choose "Network" as the source, choose "HTTP" as the protocol, and for the server, specify:

```
download.opensuse.org
```

and for the folder, if installing openSUSE 10.3, specify:

    ```
distribution/10.3/repo/oss/
```

Or, if installing openSUSE-Factory, specify:

    ```
distribution/SL-OSS-factory/inst-source/
```

Then, the main installer will start, and wait as OpenSuse is downloaded and installed.

**More**

UNetbootin also supports Ubuntu, Fedora, Mandriva, Arch Linux, and Debian. Post a reply if you need any help, new features, or another supported distro. The website is located at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by tuxcantfly on 2007-09-23
I also posted this thread on the Suse Forums at [http://www.suseforums.net/index.php?showtopic=39081](http://www.suseforums.net/index.php?showtopic=39081) and the main UNetbootin thread with instructions for Ubuntu is at [http://ubuntuforums.org/showthread.php?p=3411879](http://ubuntuforums.org/showthread.php?p=3411879)

---

### Post by tuxcantfly on 2007-09-23
Also, in case you don't know the server details for the installation, use this:

Select "FTP" as the installation source option

server: **[ftp.mirrorservice.org](ftp.mirrorservice.org)**
folder: **sites/ftp.opensuse.org/pub/opensuse/distribution/10.2/repo/oss/**

You can also use other mirrors, see [http://en.opensuse.org/INSTALL_Internet](http://en.opensuse.org/INSTALL_Internet) for details.

---

### Post by BLTicklemonster on 2007-09-24
Hmmm, so I'm using hda7 as my main gutsy drive, and want to partition and set up suse on my hdd1 drive (partition so I keep some files I have in there safe), will I have an easy time doing this, or will it be a nightmare? (I also have two other partitions/drives that I want to keep safe. One is more storage space, the other is windows xp)

---

### Post by tuxcantfly on 2007-09-24
> **BLTicklemonster said:**
> Hmmm, so I'm using hda7 as my main gutsy drive, and want to partition and set up suse on my hdd1 drive (partition so I keep some files I have in there safe), will I have an easy time doing this, or will it be a nightmare? (I also have two other partitions/drives that I want to keep safe. One is more storage space, the other is windows xp)

Just don't delete the drives when you get to the partitioning stage, and you should be safe. I'd do the partitioning beforehand with GParted, that way you can be sure that everything's ready for the Suse installer; just make sure to do manual partitioning and select the partition you made beforehand as root; otherwise it might try to wipe out other partitions. Other than that, for the bootloader, I'd just keep Ubuntu's bootloader, and add an entry like this:

```
Title OpenSuse
root (hd3,1)
configfile /boot/grub/menu.lst
```

That way you'll be able to keep your current bootloader config and also be able to boot openSuse. I'd also keep a Super Grub Disk handy to fix GRUB in case something goes terribly wrong and GRUB won't boot.

---

### Post by BLTicklemonster on 2007-09-24
Super Grub Disk?

---

### Post by tuxcantfly on 2007-09-24
> **BLTicklemonster said:**
> Super Grub Disk?

It's a handy CD that lets you fix GRUB in case you totally screw it up and can't boot anymore. It's not necessary for this, but it's generally good to have, in case of a system emergency. [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by LuisAugusto on 2007-09-30
You can install basely all Distros without a CD.
I have "create" (possibly a lot of people thought it before myself) a method:

-Create a 5 GB partition (with 1 GB is enought for most cases).*
-Download the desire ISO image.
-Put it on the new partition.
-Extract the kernel file and the initrd (in SuSE: Linux and initrd)
-Reboot.

-On the grub menu press "e"
-On the root option, write the drive number (if sda1=hd0,0 if sda2=hd0,1 and so on)
-On the kernel option write: /linux (in SuSE case)
-On the initrd option write: /initrd 

You'll boot. Then select Installation/update from hard drive.
Then write the name location of the iso file, for example:
/opensuse103.iso

And you know the rest :P

*As a side note: You can even make everything I pointed out, without making a partition, however, during the instalation you won't be able to modify (resize, erase, etc.) the partition that host the kernel, initrd and iso files.

---

### Post by tuxcantfly on 2007-10-06
> **LuisAugusto said:**
> You can install basely all Distros without a CD.
I have "create" (possibly a lot of people thought it before myself) a method:

-Create a 5 GB partition (with 1 GB is enought for most cases).*
-Download the desire ISO image.
-Put it on the new partition.
-Extract the kernel file and the initrd (in SuSE: Linux and initrd)
-Reboot.

-On the grub menu press "e"
-On the root option, write the drive number (if sda1=hd0,0 if sda2=hd0,1 and so on)
-On the kernel option write: /linux (in SuSE case)
-On the initrd option write: /initrd 

You'll boot. Then select Installation/update from hard drive.
Then write the name location of the iso file, for example:
/opensuse103.iso

And you know the rest :P

*As a side note: You can even make everything I pointed out, without making a partition, however, during the instalation you won't be able to modify (resize, erase, etc.) the partition that host the kernel, initrd and iso files.

Only problem with that is that you need a Linux install already before you can install Linux, as most Windows users have only 1 partition so they wouldn't be able to do the resizing bit if they have the iso on the desktop already.

---

### Post by tuxcantfly on 2007-10-06
I've released a new build that can install opensuse 10.3 as well. Do the same as with 10.2, only for the server details, select "http", and enter the following:

server: **download.opensuse.org**
folder: **distribution/10.3/repo/oss/**

---

### Post by LuisAugusto on 2007-10-06
> **tuxcantfly said:**
> Only problem with that is that you need a Linux install already before you can install Linux, as most Windows users have only 1 partition so they wouldn't be able to do the resizing bit if they have the iso on the desktop already.

You can use a windows partition tool, drop the iso there, and use a Windows like GRUB tool, however, you're right, is quite more difficult if you didn't have Linux previously.

---

### Post by tuxcantfly on 2007-10-10
I've uploaded some 64-bit openSUSE UNetbootin builds. Check the download page... Since the packages are all marked as "noarch/all", you don't need to necessarily install 32-bit from a 32-bit OS, or 64-bit from a 64-bit OS; you can install 64-bit if your processor is capable of it (amd64 or intel core2 and above), even if you're running a 32-bit Windows or Linux install.

---

### Post by tommytabib on 2007-10-23
I just tried to use unetbootin to install opensuse 10.3. I have the iso downloaded already and opted to install from hard disk but when i told it which directory the iso was in it just said "no repositories found", when i know its in there.

I've already used unetbootin to install mandriva 2008 and it worked great, the 10.3 opensuse version doesnt seem to work or look as good.

Any help?

---

### Post by tuxcantfly on 2007-10-23
> **tommytabib said:**
> I just tried to use unetbootin to install opensuse 10.3. I have the iso downloaded already and opted to install from hard disk but when i told it which directory the iso was in it just said "no repositories found", when i know its in there.

I've already used unetbootin to install mandriva 2008 and it worked great, the 10.3 opensuse version doesnt seem to work or look as good.

Any help?

Perhaps try extracting the contents of the iso first?

---

### Post by ferpadro on 2007-10-23
I wanna install opensuse 10.3 KDE version. So what´s the deal? will i l have the chance to choose what DE i want to be installed? Or is this just for the Gnome flavour?

---

### Post by tuxcantfly on 2007-10-23
> **ferpadro said:**
> I wanna install opensuse 10.3 KDE version. So what´s the deal? will i l have the chance to choose what DE i want to be installed? Or is this just for the Gnome flavour?

Yes, you'll get to choose your DE.

> I just tried to use unetbootin to install opensuse 10.3. I have the iso downloaded already

Is the iso the install or live iso? Only the install DVD iso will work (though I've only tried net-install, so I don't know the precise procedure)

---

### Post by LuisAugusto on 2007-10-25
I tried your tool 2 days ago to install Ubuntu Gutsy Gibbon 7.10, and, I don't know why it took more than 10 hours  just to complete 18%, of course, I cancelled it. I'm aware that it was downloading every package, but my internet connection is not that slow, 10 hours are almost 2 GB with it, Ubuntu installed just take 2.5 GB, that means that .deb download packages are sensible less heavy.

---

### Post by tuxcantfly on 2007-10-27
> **LuisAugusto said:**
> I tried your tool 2 days ago to install Ubuntu Gutsy Gibbon 7.10, and, I don't know why it took more than 10 hours  just to complete 18%, of course, I cancelled it. I'm aware that it was downloading every package, but my internet connection is not that slow, 10 hours are almost 2 GB with it, Ubuntu installed just take 2.5 GB, that means that .deb download packages are sensible less heavy.

Well, Ubuntu 7.10 was only recently released, so perhaps your local mirrors were overburdened. Also note that most of the downloading will occur at the 6% stage, so perhaps it was much closer to being finished at "13%" than the progressbar indicated. But yes, certainly, 10 hours to download Ubuntu 7.10 (roughly 700 MB) is quite a while.

---

### Post by LuisAugusto on 2007-10-27
> **tuxcantfly said:**
> Well, Ubuntu 7.10 was only recently released, so perhaps your local mirrors were overburdened. Also note that most of the downloading will occur at the 6% stage, so perhaps it was much closer to being finished at "13%" than the progressbar indicated. But yes, certainly, 10 hours to download Ubuntu 7.10 (roughly 700 MB) is quite a while.

Ok, thanks for th anwser :)

---

### Post by tuxcantfly on 2007-10-28
I've updated the UNetbootin builds for OpenSuse 10.3 to support Windows Vista as well. Usual download spot at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

---

### Post by tuxcantfly on 2008-01-03
I've released new UNetbootin builds for openSUSE that install the Factory (experimental, constantly under development) version.

Download location for the openSUSE-factory version is at [http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=256968](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=256968)

**openSUSE-Factory Instructions**

If installing openSUSE, after rebooting, ignore any error messages and select back if prompted for a CD, then go to the main menu, select the "Start Installation" option, choose "Network" as the source, choose "HTTP" as the protocol, and for the server, specify:

```
download.opensuse.org
```

and for the folder, if installing openSUSE Factory, specify:

```
distribution/SL-OSS-factory/inst-source/
```

Also, since openSUSE-Factory is an experimental distributions, and thus frequently changes, the UNetbootin builds for them have a slightly different behavior; they will initiate the download of the latest builds of its netboot initrd and kernel files from the official mirrors rather than bundling them in. (Which is why the filesize is now down to a couple of kilobytes rather than several megabytes)

---


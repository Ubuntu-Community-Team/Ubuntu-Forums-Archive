---
title: "Upgrade hassles"
date: 2006-06-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-06-18
I have been having a miserable time upgrading my Breezy-64 to Dapper-64.

I had an unused 20 GB on my hard disk, so I burned the 64-bit Dapper DVD and used it to install Dapper on it, creating a new 8 GB partition in the process. After I rebooted I was wandering around checking it out and suddenly I noticed all my files were in the new partition. Everything was there -- even the second emergency user account that I had created. How did this get into this new partition? Oh no! It must have installed itself over my original Breezy, and all my programs and hundreds of personal settings were gone!

I shut down and tried rebooting. Grub showed both versions, but both booted to Dapper and showed everything that had been on my Breezy hda2 partition. After about the third reboot effort the boot process announced that the filesystem had been mounted 30 times so it was forcing a fsck. I let it continue, and it found several broken inodes. I let it fix them. Afterwards I discovered that everything was back to normal. Booting to Dapper booted only to Dapper and none of my Breezy stuff was visible. Booting to Breezy still worked exactly as before. Whew!

So having gone through that mess I decided to use a rescue CD to copy everything from my Breezy hda2 partition to an external USB pocket drive, just to be safe. Having finished that, I proceeded to use the Update Manager to update the Breezy installation. Except that Update Manager announced that a lot of packages would not be updated, and if I wanted them updated to do sudo apt-get dist-upgrade. 

I decided to use the manual method instead of Upgrade Manager. I gave it sudo apt-get dist-upgrade, the terminal window scrolled by for 20 minutes (I get about 750-800 k/s) and finally finished the download. Then, shortly after it started the actual upgrade it stopped and said:

Configuration file `/etc/login.defs'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** login.defs (Y/I/N/O/D/Z) [default=N] ?

I told it D, since I had no idea what it was talking about. That spewed out a couple pages of additional incomprehensible stuff. At the bottom of the page it said END. When in a man page or something, the way to get out of that is Ctrl-z. So I did Ctrl-z, and then the terminal window said 

[1]+  Stopped                 sudo apt-get dist-upgrade

So then I decided I was going to have to start all over again from the start. (Grrrrr.) So I typed sudo apt-get dist-upgrade again, and got:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

So now I'm posting this here to bitch to whoever designed the user interface for the upgrade. Don't just say "END" at the bottom of a terminal window without also explaining to the user how to get out of it. You may find this difficult to believe, but I was not born knowing how to use Linux.

Now I guess I have to reboot and start all over again from the start. That is, if it will still boot having been half upgraded.

---

### Post by Kilz on 2006-06-18
Upgrading an older version is always a iffy situation. It may go ok, it may not. It all depends on how much customization you have done. I don't think I would do it personally. Better to start all over fresh imho.

---

### Post by John Jason Jordan on 2006-06-18
[QUOTE=Kilz]Upgrading an older version is always a iffy situation. It may go ok, it may not. It all depends on how much customization you have done. I don't think I would do it personally. Better to start all over fresh imho.[/QUOTE]
Well, now I am totally screwed. It won't even boot. There are so many errors it is hopeless.

I am using the other installation, the new one on the 8 GB partition. It sees the hda2 Breezy partition, so I dragged my Firefox bookmarks in to the new installation. At least I can find the forums.

The problem is, you have no idea how many user configurations I had in that Breezy installation. Someone once told me that program configuration files were in hidden . files in the users home directory. So I looked at my home folder in hda2 and there are some there. I dragged the OO.o folder to here, then launched Writer, and it came up as it did on Breezy. So now I wonder, if I just use the Dapper-64 DVD that I burned the other day to install a fresh version of Ubuntu-64 over the Breezy installation, will it wipe out the configuration files? If not, it may be the best solution. Then I could reinstall the programs, and they would launch with their old configuration files. That is, unless installing a program makes it overwrite the old configuration files with a new, blank one.

---


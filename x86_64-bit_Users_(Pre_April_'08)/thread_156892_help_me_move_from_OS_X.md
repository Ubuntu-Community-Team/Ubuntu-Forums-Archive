---
title: "help me move from OS X"
date: 2006-04-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by davidmaxwaterman on 2006-04-08
Hi,

I'm close to making the switch. Help me.

Tell me what I'll miss.

I have two Macs; a Powerbook G4/800 DVI and a Mac Mini; both running OS X 10.4.5.
I think I'll switch my Powerbook first, then I'll have the Mini to fall back on when/if I miss something.

I have booted the Live CD and things seem to work ok. Not sure about :

Bluetooth -> sync/sms with Sony t68i
Firewire -> disk drive, ipod, dvcam, cf card reader
usb -> ipod (wife's)
dvd player -> region free dvd playing
airport base station -> configuration/airtunes
airport express -> configuration
DVI/svideo -> HP 2335L/TV

I am worried about missing the use of these applications :

address book SMS via my t68i
imovie -> mainly for dvcam
idvd -> simple dvd production
final cut pro 3 -> don't use it much
dvd studio pro 2 -> don't use it much
itunes -> ipods, airport express, podcasts
airfoil -> airport express
handbrake -> ipod
mac the ripper -> ipod
photoshop -> photo adjustment
realplayer -> listening to bbc radio2
graphic converter -> browsing/converting photos
chinese language input -> my wife is chinese and we live in china
existing mac filesystems -> some data on firewire drives with hfs+

Do these have reasonably functional Linux alternatives?

I have a spare 30GB firewire drive - I'd love to boot my tiBook or mini to ubuntu off it. Has anyone done it successfully/easily?

Max.

---

### Post by 3rdalbum on 2006-04-08
You can load an iPod using the free gtkPod program, available through a simple download. I don't know whether it'll work through Firewire... perhaps only USB.

Is Mac the Ripper a CD-ripping program? If so, then you can download Grip and that will convert CDs to MP3.

The GIMP is an okay Photoshop replacement, unless you need to work with CMYK files. It also can convert graphics.

RealPlayer is a bit of a patchy proposition... it might work for you, but it certainly doesn't work for me.

No idea about Chinese language input, but Ubuntu can definately display Chinese characters out-of-the-box.

Existing Mac filesystems can be mounted as long as you add a couple of simple details to the fstab file.

Some of the other things you mention are programs I don't know, so I couldn't tell you whether there are alternatives. I don't think you'll be satisfied with video editing on Linux.

I would advise you to partition your hard disk and dual-boot until you can find good replacements for everything you want to do.

---

### Post by davygravy on 2006-04-08
I'd second that suggestion to remain dual-boot.

After tinkering for several years w/ YellowDogLinux, and now really liking Ubuntu much more, I can say that I nevertheless absolutely need some of what OS X has to offer, for work and for home.

But, Ubuntu and Linux have their appealing sides.  It is getting steadily better and better.

Just my $.02.

davygravy

---

### Post by davidmaxwaterman on 2006-04-08
> **3rdalbum]You can load an iPod using the free gtkPod program, available through a simple download. I don't know whether it'll work through Firewire... perhaps only USB.
[/QUOTE]

Re firewire - the website makes it sound like it should work (the first ipods are supported and they only came with firewire) said:**
> 
Is Mac the Ripper a CD-ripping program? If so, then you can download Grip and that will convert CDs to MP3.


Yes. Though it removes region codes and macrovision too.

> 
The GIMP is an okay Photoshop replacement, unless you need to work with CMYK files. It also can convert graphics.


I use GIMP fairly often, so I should be ok with that - though I wonder about printer support.

> 
RealPlayer is a bit of a patchy proposition... it might work for you, but it certainly doesn't work for me.


I had it working a while ago on FC4, so I think it should be ok. Interesting that it doesn't work for you :(

> 
No idea about Chinese language input, but Ubuntu can definately display Chinese characters out-of-the-box.


That's good.

> 
Existing Mac filesystems can be mounted as long as you add a couple of simple details to the fstab file.


Good to know :) I wasn't expecting to be able to make that work.

> 
Some of the other things you mention are programs I don't know, so I couldn't tell you whether there are alternatives. I don't think you'll be satisfied with video editing on Linux.


Hrm. Maybe I'll keep OS X on my mini just for that.

> 
I would advise you to partition your hard disk and dual-boot until you can find good replacements for everything you want to do.

How can I do that without reinstalling OS X?

Max.

---

### Post by stmiller on 2006-04-08
If you turn off journaling on your OS X drive with the disk utility (hold down option, or shift- something like that while in disk utility, and choose file>disable journaling) you can resize the partition without destroying data. Search on the gentoo PPC forums for more help on this.

---

### Post by jdp on 2006-04-08
Or just read the on going thread we have [right here on ubuntuforums.org](http://ubuntuforums.org/showthread.php?t=89960) about resizing HFS+ partitions from the Ubuntu Installer CD.  Note that the LiveCD doesn't have the parted software on it, just the Installer CD.  Gparted doesn't work for this.

---

### Post by dpny on 2006-04-08
[QUOTE=stmiller]If you turn off journaling on your OS X drive with the disk utility (hold down option, or shift- something like that while in disk utility, and choose file>disable journaling) you can resize the partition without destroying data. Search on the gentoo PPC forums for more help on this.[/QUOTE]

Or you can type:
```
sudo diskutil disableJournal /
```

in the Terminal.

---

### Post by davidmaxwaterman on 2006-04-09
[QUOTE=jdp]Or just read the on going thread we have [right here on ubuntuforums.org](http://ubuntuforums.org/showthread.php?t=89960) about resizing HFS+ partitions from the Ubuntu Installer CD.  Note that the LiveCD doesn't have the parted software on it, just the Installer CD.  Gparted doesn't work for this.[/QUOTE]

Well, I tried the instructions on that thread.

I made a mistake in parted. I tried to resize to 30GB, but it said the closest was 20GB - I mistakenly thought this figure was the new partition (I got ahead of myself), instead of the smaller size of the old partition, so I said, 'OK'; but my data on that partition was more than 20GB in size.

I figured I was hosed, so I started from scratch and whiped the disk.

I had made some form of backup, so I'm not particularly worried.

I then did an update.

Now I'm trying to put 'easy ubuuntu' on it, but it doesn't seem to work.

I checked almost everything, then clicked 'Install' - it did some stuff, but nothing seems to work. I don't have 'Realplayer' anywhere (it appears in 'Add programs', but it is 'uninstallable' - trying to add the 'multiverse', as it suggests, fails).

Any ideas?

Max.

---

### Post by 3rdalbum on 2006-04-11
I think RealPlayer 8 for x86 Linux is in repositories, but not for PPC.

You'll need to go to [https://player.helixcommunity.org/2005/downloads/]("https://player.helixcommunity.org/2005/downloads/") and download the RealPlayer 10 PPC installer. Unfortunately, on my computer, it freezes when you try to play RealPlayer files.

Have you enabled the Universe repository as well? Do that from within Synaptic, because I don't think the Add Applications program really works :-)

---

### Post by shawnhcorey on 2006-04-11
[QUOTE=davidmaxwaterman]I checked almost everything, then clicked 'Install' - it did some stuff, but nothing seems to work. I don't have 'Realplayer' anywhere (it appears in 'Add programs', but it is 'uninstallable' - trying to add the 'multiverse', as it suggests, fails).

Any ideas?

Max.[/QUOTE]

Yes, you must edit the /etc/apt/sources.list to get 'Add programs' to work.

  sudo gedit /etc/apt/sources.list

Note that sometimes sudo and gedit don't play well together. You may have to repeat the command.

When you look at the file, you will notice that everything is commented out. Uncomment the packages you want access to. If you don't know which, uncomment 'main', 'main restricted', and 'universe'.

Launch `System -> Administration -> Synpatic Package Manager` and click on the Reload. You should see oogles and oogles of packages. Do a search for RealPlayer.

shc

PS: My adventures with my Powerbook G4 are at [https://wiki.ubuntu.com/Shawnhcorey](https://wiki.ubuntu.com/Shawnhcorey)

---

### Post by hotani on 2006-04-12
I'm making the same switch soon, but going with new hardware (AMD 64 x2).

One thing I noticed in the comments above is MacTheRipper is not for CDs but for DVD ripping. I know there is an alternative on Linux but haven't gotten that far in my exploration yet.

As for the iPod, that I have messed with quite a bit. I have a windows formatted 20GB iPod and am using it on my work PC. gtkpod works well for adding/editing songs and working with all playlists, rhythmbox works well for seeing the playlists on the pod and playing them, but will not see smart playlists. Plus rhythmbox seems to be read-only not just on the ipod but on the filesystem as well. I have yet to edit tag info on a music file, I think that is an upcoming feature though.

[Here is a good table](http://www.linuxrsp.ru/win-lin-soft/table-eng.html) of equivalents - although it lists Windows applications as the starting point, it is still a good reference for us Mac folks wanting to use Linux.

---


---
title: "Getting KDE 4.2 back to defaults?"
date: 2009-05-13
forum: x86 64-bit Users
---

### Post by dh003i on 2009-05-13
How do I get back to default settings with KDE 4.1 under Kubuntu 9.04? 

Things are really not working well all over. Upon boot, I get a "audio device disconnected" message (non-sense, I haven't opened the case). The digital clock has disappeared; I had to reassemble the task-bar, but still don't see iconified apps like Amarok or Konversation when the window is closed.

When I log into KDE, and plug in my Cowon D2, the cursor starts jittering (also, now, my D2 shows no music files in it, despite me transferring files to it from my comp!). 

Now, upon logging in, I can't even do anything...all I see is this minimized window saying "audio device disconnected".

Huh? This all happened after I disconnected my Cowon D2 in the middle of transferring files (but it's supposed to be able to be disconnected, I believe). Not sure if that's relevant. 

(all partitions are Ext4, don't know if that matters). 

Anyways, I just want things back to the default.

---

### Post by pixel :-) on 2009-05-13
you edited in /etc ? or just user level config changes? these are located in .kde folder, rename it, it will recreate .kde folder with all the defaults. You lose everything, conqueror bookmarks rss feeds, ect, emails for kmail, but you can dig them up from your old .kde

files with "." at the begining, are headen.

If it extend out side of .kde creat a new user and salvage your stuff from the old home.

about ext4, its performance at the expense of security. #-o At this stage of its development anyway.

> Problems can arise if the system crashes before the actual write occurs. In this situation, users of ext3 have come to expect that the disk will hold either the old version or the new version of the file following the crash. However, the ext4 code in the Linux kernel version 2.6.28 will often clear the contents of the file before the crash, but never write the new version, thus losing the contents of the file entirely.

i'm guessing that D2 acts as a mounted hardrive. It may tell you that he transfered the files, but internaly the system tries to delay actually doing stuff on the disk in order to increase performence. Its physicaly safe to remove the plug, you will not damage it, but you have to unmount it in order to force it to finish his job. ext3 does the same, it just make sure that theres always at least one copy on disk.

---

### Post by dh003i on 2009-05-13
Thank you very much; I'll give that a try and report back.

In the meantime, I wonder why everything got so screwed up.

---

### Post by xebian on 2009-05-13
Get rid of the folder .kde in your home directory, and restart.):P

---

### Post by Ericyzfr1 on 2009-05-13
> **xebian said:**
> Get rid of the folder .kde in your home directory, and restart.):P

How does it work in Gnome?

---

### Post by dh003i on 2009-05-14
pixel, xebian, 

Thanks for the tip, but something is still wrong. I have my default KDE bar back, but I still can't open programs.

If I try to open Firefox or any other window, it just stays as a minimized bar and I can't see it on the screen, even if I click "maximize" on it's instance in the task-bar. 

Any ideas?

---

### Post by pixel :-) on 2009-05-14
You did all i told you? You created a new user? We don't read minds, what did you did?

can you lunch a terminal?
run inside something, like firefox, and send us back the out put, in the terminal.

try command

killall kwin ; kwin

ctrl+alt+F1 gives you a emergency terminal? it can't run gui applications, but you can do stuff with text mode tools.

install gnome, as a temporary measure.

sudo apt-get install gnome-core

---

### Post by dh003i on 2009-05-16
pixel,

Thanks, I went back and followed your original suggestion; I added a new user, moved my data to that user's folder, deleted the old one. (and then used the appropriate usermod flags to change the new users name back to he old one). 

That fixes most problems. However, there are still some issues...sometimes programs open, but don't display in windows, only the taskbar (can't see them on my primary CRT). Also, sometimes I get tearing when scrolling (could this be related to my radeonhd driver? If I switch to plain ati/radeon, will I have to change anything in my xorg.conf other than the Driver option?). 

Also, from the **Software Updates - KDE Control Module" window, which showed up on the [b]Update Notifier** icon in the system panel, when I click on **Apply all available updates**, it tells me:

```
You don't have the necessary privileges to perform this action.
```

I just used "sudo apt-get update ; sudo apt-get upgrade" instead, but still got an error (and why isn't there any hint as to what I should do to fix it in the window?). Error:

```

$ sudo apt-get update
...
$ sudo apt-get upgrade
...
Setting up mesa-utils (7.4-0ubuntu3.1) ...
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
                                                    <unknown program name>(9713)/ KStartupInfo::createNewStartupId: creating:  "davidjheinrich-desktop;1242453277;153076;9713_TIME0" : "unnamed app"
                                                                                                                                                                                                    Setting up libical0 (0.43-2ubuntu1) ...
kbuildsycoca4 running...
                        Error: "/var/tmp/kdecache-davidjheinrichPeGt0d" is owned by uid 1001 instead of uid 0.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

Oh yea, and when I right click in Firefox on a web-page, he popup menu is way above the cursor. 

My **xorg.conf** file

```
Section "Device"
	Identifier	"ATI Radeon HD4670"
	Driver		"radeonhd"
	Option		"DRI" "on"
	Option		"AccelMethod" "EXA"
	Option		"monitor-DVI-I_1/digital" "Viewsonic VP2290B"
	Option		"monitor-DVI-I_2/analog" "Sony GDM-F520"
EndSection

Section "Monitor"
	Identifier	"Sony GDM-F520"
	VendorName	"Sony"
	ModelName	"GDM-F520"
	HorizSync	30-137
	VertRefresh	48-170
	DisplaySize	388 291
	Option		"PreferredMode" "2048x1536_73"
	Modeline	"2048x1536_73"	329.11  2048 2208 2432 2816  1536 1537 1540 1601  -HSync +Vsync
EndSection


Section "Monitor"
	Identifier	"Viewsonic VP2290B"
	VendorName	"Viewsonic"
	ModelName	"VP2290b"
	HorizSync	22-118
	VertRefresh	9-64
	DisplaySize	478.1 298.8
	Option		"PreferredMode" "3840x2400_13"
	Option		"RightOf" "Sony GDM-F520"
	# Option		"Enable" "false"
	Modeline	"3040x2400_13"	148.00 3840 3944 4328 4816 2400 2401 2404 2418
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Sony GDM-F520"
	Monitor		"Viewsonic VP2290B"
	Device		"ATI Radeon HD4670"
	DefaultDepth	24
	SubSection "Display"
	  Depth		24
	  Virtual	5888 2400
	EndSubSection
EndSection

Section "DRI"
	Mode		0666
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection
```

My **/var/log/Xorg.0.log**:

```
Section "Device"
	Identifier	"ATI Radeon HD4670"
	Driver		"radeonhd"
	Option		"DRI" "on"
	Option		"AccelMethod" "EXA"
	Option		"monitor-DVI-I_1/digital" "Viewsonic VP2290B"
	Option		"monitor-DVI-I_2/analog" "Sony GDM-F520"
EndSection

Section "Monitor"
	Identifier	"Sony GDM-F520"
	VendorName	"Sony"
	ModelName	"GDM-F520"
	HorizSync	30-137
	VertRefresh	48-170
	DisplaySize	388 291
	Option		"PreferredMode" "2048x1536_73"
	Modeline	"2048x1536_73"	329.11  2048 2208 2432 2816  1536 1537 1540 1601  -HSync +Vsync
EndSection


Section "Monitor"
	Identifier	"Viewsonic VP2290B"
	VendorName	"Viewsonic"
	ModelName	"VP2290b"
	HorizSync	22-118
	VertRefresh	9-64
	DisplaySize	478.1 298.8
	Option		"PreferredMode" "3840x2400_13"
	Option		"RightOf" "Sony GDM-F520"
	# Option		"Enable" "false"
	Modeline	"3040x2400_13"	148.00 3840 3944 4328 4816 2400 2401 2404 2418
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Sony GDM-F520"
	Monitor		"Viewsonic VP2290B"
	Device		"ATI Radeon HD4670"
	DefaultDepth	24
	SubSection "Display"
	  Depth		24
	  Virtual	5888 2400
	EndSubSection
EndSection

Section "DRI"
	Mode		0666
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection
```

---


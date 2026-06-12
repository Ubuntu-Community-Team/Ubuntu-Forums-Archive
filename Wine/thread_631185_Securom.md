---
title: "Securom"
date: 2007-12-04
forum: Wine
---

### Post by WierdKid on 2007-12-04
I'm trying to install Tomb Raider Aniversery, but everytime I try to run the installer I get an error from SecuRom. Everything I've found around forums said that this shouldn't be an issue in wine. But yet, here I am, typing on a forum not playing a game.

I'm running .9.50 Wine, I have Wine set to recognize where the CD is as a CD drive. Still I get nothing.

```
fixme:process:IsWow64Process (0xffffffff 0x221ad34) stub!
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x221a520,0x00000004,0x221a51c) Unknown information class
fixme:process:IsWow64Process (0xffffffff 0x221a85c) stub!
fixme:process:IsWow64Process (0xffffffff 0x221a85c) stub!
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x221940c): Stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x2219290,0x00000000), stub!
```

Thats what the console thinks I need to know.

---

### Post by cogadh on 2007-12-04
Copy protection in Wine is not 100% complete, but most SecuRom protected games should work if you have Wine configured correctly. You already have Wine set up with a CD drive correctly, but you may also need to create a symbolic link to your CD-ROM drive's /dev entry in Wine's dosdevices directory before it will work. Assuming your CD drive is "D:" in Wine and that it is located at /dev/hdc in Linux:
```
ln -s /dev/hdc ~/.wine/dosdevices/d\:\:
```
Obviously change the /dev path and drive letter to match you actual configuration.

If doing that doesn't make the copy protection work, then you will probably need to use a cracked executable to run the game. **Do not ask where to get one or how to use one on these forums.** Cracked .exe's are often used for software piracy purposes and the discussion of the how's and why's of cracks on these forums is strongly discouraged.

EDIT - According to the most recent test data for the game on AppDB, a crack was required to run the game. However that test was done using Wine 0.9.43, which had significantly less complete copy protection support than 0.9.50:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=8139](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8139)

---

### Post by WierdKid on 2007-12-04
I tried that, making sure to change the code to fit my set up. Still no effect, Console output is the same, and same result in the WINE window itself.

Even if a crack were to be found, it wouldn't help me now as I still can't install the game. I'm gonna keep searching for some answers, I really want to play this game.

---

### Post by phenest on 2007-12-30
Have you found an answer to this? I'm using Wine 0.9.51.

---

### Post by WierdKid on 2007-12-30
No such luck at anytime.

---

### Post by phenest on 2007-12-30
Ok. I found a cracked exe known as a NoDVD crack which enables you to play the game without the need to insert the disc in the drive. This helped were it not for 2 other problems which arose:

1 - If I set the resolution to anything less than maximum (1920x1200x50Hz in my case), the game plays unbearably slow,
2 - When I try to start the game, the level loads and then the whole thing just quits on me.


As someone new to Wine, what is the difference between just clicking an exe, and using the terminal - prefixing the exe with wine, i.e. wine tra.exe?

---

### Post by YokoZar on 2007-12-31
Could you retest with 0.9.52 please?  There were some problems with Securom and GCC versions, so I switched 0.9.52 to compile with a GCC version known to work.

---

### Post by phenest on 2008-01-01
I tried 0.9.52 with the same results.

To install, make sure you cd to the cdrom directory, i.e:
> cd /media/cdrom0
...and then...
> wine setup.exe
This will install the game. To get round the Securom problem, you will need the NoDVD cracked exe I mentioned.

---

### Post by phenest on 2008-01-01
Must've been the lack of a reboot or something. It now works fine in all resolutions  (apart from the fact I have to disable the water effects), but I still have to select the resolution with each start of the game (the cracked exe maybe?).

---

### Post by pPrdrm on 2008-01-26
It seems that running some apps with wine after you've cd to the directory that this app is located is very crucial. Yet it's not known by many people (I've found it after hours of goggle search). Even though I don't quite get it why giving the complete path to app is not working, I think that this information must be widely made known.

---

### Post by A M on 2012-01-20
What follows was done in Debian/wheezy, using wine 1.0,
but should work everywhere.

We suppose that the user is called 'joe'

-) check permissions of joe
 # id joe
  uid=118(joe) gid=128(joe)  groups=128(joe),
   24(cdrom),25(floppy),29(audio),44(video)

 the 'cdrom' groups is for reading cdrom device, the
  'video' is for accessing videohw (at least with nvidia
  drivers), 'floppy' is for removable devices 
  (nowadays, USB drives), etc etc

 if any is missing,
 # sudo adduser joe thatgroup
 and then logout and login again (no need to reboot)

-) make sure that ~/.wine/dosdevices contains two links, e.g
 lrwxrwxrwx 1 joe joe 12 gen 20 07:07 d: -> /media/cdrom
 lrwxrwxrwx 1 joe joe 10 gen 19 23:33 d:: -> /dev/cdrom

-) run 'winecfg' , select 'Drive', select d:, 
  select 'Show Advanced' and select type "CDROM"
  (and not "local hard disk"); then 'Apply" and "OK"

-) make sure that /etc/fstab contains an entry such as

  /dev/cdrom	/media/cdrom	auto	defaults,user	0	0

  so that some internal trickery of wine knows that
  the two are associated, and also 'joe' can
  mount/umount the device on /media/cdrom

-) make sure that the cdrom device is there, and that it
  is readable by people in 'cdrom' group

 # ls -l /dev/cdrom
 lrwxrwxrwx 1 root root 3 gen 20 07:14 /dev/cdrom -> sr0
 # ls -lL /dev/cdrom
 brw-rw---T 1 root cdrom 11, 0 gen 20 07:14 /dev/cdrom

-) insert a cdrom , and check that it is mounted on
   /media/cdrom  using the command 'mount'
   if it is mounted somewhere else, use
  # umount /dev/cdrom 
  and when it is not mounted,
  # mount /media/cdrom

-) check that wine can find the cdrom 
 # wine eject



finally, mount your cdrom game, and issue
 # wine 'd:\thegame.exe'

---

### Post by Rubi1200 on 2012-01-20
Thanks for sharing with us but this is a very old thread. In future, start your own thread so that the most recent information is available to all.

Thread closed.

Reason: necromancy

---


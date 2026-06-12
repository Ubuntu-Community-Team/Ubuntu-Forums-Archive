---
title: ":( Windows Vista won't work after I dual-booted."
date: 2008-06-22
forum: x86 64-bit Users
---

### Post by CrumbledCookies on 2008-06-22
Hi, I have just recently installed Ubuntu and when I tried to boot from my Windows Vista, it gives me "booting from c:\windows, invalid something." Oh yea, and my C: drive is named to "102.5 GB Media." I've tried renaming it back to C:, renaming windows folder, and everything I could think of. I have my windows installation files, so if I could, just reinstall Windows from Ubuntu. Please help someone. I miss Vista. :(

---

### Post by AndyCee on 2008-06-22
Heya Cookies.

If you have important files or documents on your windows partition, DO NOT reinstall windows until you've backed them up.

Just to clarify:

1) When the computer boots do you have a menu with Ubuntu and Vista options.

2) When you select the vista option you get an error.

3) When you boot into Ubuntu, windows appears as 102.5 GB Media.

Point three is normal. It's supposed to happen, as Ubuntu doesn't recognise the partition as "Windows", but as an ntfs partition (or disk).

For more info, can you open a terminal, type the following and paste your output here:

```
cat /boot/grub/menu.lst
```

Don't panic.

---

### Post by wdaniels on 2008-06-22
> **CrumbledCookies said:**
> it gives me "booting from c:\windows, invalid something."

The *something* is the important bit! (it's probably BOOT.INI)

> **CrumbledCookies said:**
> my C: drive is named to "102.5 GB Media."

That's just a name that Ubuntu gives it, same as Windows calls it "C" - in neither case does it have anything to do with the actual disk label, you don't have to worry about that, it's not relevant.

> **CrumbledCookies said:**
> I've tried renaming it back to C:, renaming windows folder, and everything I could think of.

No, no, no!! Don't do that :D Windows will never boot if you start renaming it's folders! Put it all back how it was :D :D :D

> **CrumbledCookies said:**
> I have my windows installation files, so if I could, just reinstall Windows from Ubuntu.

That's not how things work, if you have an installation CD for Windows, you boot that directly. Microsoft does not make a Linux installer.

Probably you need to run "fixboot" from the Windows recovery console thing, but hopefully somebody else can tell you more specifically what to do since I haven't installed Windows myself in years...

> **CrumbledCookies said:**
> I miss Vista. :(

...no comment...:lolflag:

---

### Post by CrumbledCookies on 2008-06-22
Yes I get a menu to boot from, but Vista recognized as an "other OS." Whenever I try to boot from it, it just gives an error and goes to a black screen. I was panicking when I found this out, but I am confident that this problem can be solved. :)


And yes, it is BOOT.ini. I just don't get it, I can't run the recovery, because I can't find it at startup.

---

### Post by AndyCee on 2008-06-22
I think we need the error. Can you write it down and post it?

---

### Post by CrumbledCookies on 2008-06-22
Here's the error: "Invalid Boot.ini file : Booting from c:\windows\." Then it goes to black screen and I have to reboot.

Oh, and it also classifies Windows Vista as "WindowsNT/2000/XP."

Also, I have a files named "Boot.ini.saved" and "Boot.BAK." Are they backup copies? I found them in my "102.5 GB Media" folder/drive.

---

### Post by AndyCee on 2008-06-22
I think this may be what you're looking for.

[http://ubuntuforums.org/showthread.php?p=5184182](http://ubuntuforums.org/showthread.php?p=5184182)

If I haven't emphasized it enough, back up important stuff before changing boot settings.

---

### Post by CrumbledCookies on 2008-06-22
I do not have the disk. I purchased it online. I don't have a 4 GB DVD that I can make an .iso and burn to it. But if I tried this, would it work? How would I make it start from the setup.exe? How can I format my hard drive?

---

### Post by AndyCee on 2008-06-22
Can you please post your grub file? And explain which options work (the actual menu is right down the bottom of the file.)

I fear you'll have to wait for someone more experienced, especially when it comes to reformatting and partitioning.

You don't have the Vista install DVD - where are the windows installation files? Are they installed on a seperate partition?

---

### Post by CrumbledCookies on 2008-06-22
What is a grub file? My Vista files are on my hard drive. I still have Vista installed, but it won't let me boot it.

---

### Post by tgrimley on 2008-06-22
grub is this:

> **AndyCee said:**
> 

For more info, can you open a terminal, type the following and paste your output here:

```
cat /boot/grub/menu.lst
```

Don't panic.

---

### Post by Sakrimo on 2008-06-22
it shouldn't classify Windows Vista as Windows XP/NT/2000 or whatever you posted, this is an extra..

Below this there should also be Windows Vista/Longhorn(loader).


My Windows XP/NT/2000 option didn't load either, i don't know why it's there, because i don't have them installed, removed them from my grub menu to give me on Windows Vista and Hardy Heron.

---

### Post by CrumbledCookies on 2008-06-22
Will someone answer? Oh yea, I'm getting a 4 GB DVD tommorow, so, can anyone point out an iso maker so I can burn it to a disc? How will I assign it to run setup.exe?

---

### Post by AndyCee on 2008-06-23
> **CrumbledCookies said:**
> Will someone answer? Oh yea, I'm getting a 4 GB DVD tommorow, so, can anyone point out an iso maker so I can burn it to a disc? How will I assign it to run setup.exe?

As i'm not sure which OS you're working from:

From windows, a good iso maker/burner is "iso recorder" at [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

From ubuntu, you should be able to right-click the file and "write to disk".

But to boot into anything outside Ubuntu, the option is in the bios menu or boot menu. When the machine starts and splashes the manufacturer's name (Dell, Compaq, Sony etc), in that short time there will be text somewhere that says "F12 for boot menu" or "F8 for setup". You can't run an executable (*.exe) natively from within Ubuntu.


Note: I DON'T KNOW WHAT THE FOLLOWING WILL DO
Your edited post says you found "boot.ini.saved" . If someone knowledgable backs me up - copying that to "boot.ini" in the same directory could work. Or it could prevent vista from booting.

---

### Post by CrumbledCookies on 2008-06-23
So if I just burn the files, and I select boot from cd, how will it know to run setup.exe?

---

### Post by tgrimley on 2008-06-23
if you're burning a vista ISO you don't need to worry about it running setup.exe

just let it boot from the cd and it'll run the installer

---

### Post by CrumbledCookies on 2008-06-23
I don't think I can make an ISO on Ubuntu, but if I just burn the three files: boot.wim, install.wim, and X13-49120.exe, will it boot from X13-49120.exe? That's what sets up the Vista setup.exe.

Nevermind, I made an ISO of the three files. But X13-49120.exe is what extracts files. It extracts setup.exe for example. Should I go ahead and extract then right the files? If I boot from the disk, how will it know to boot from the .exe? How could I format my Hard Drive so I can have a fresh, clean copy? Thank you guys a lot, we are close to finding a solution. :)

Wait, I forgot that I can't run .exe from Ubuntu. But, can I run X13-49120.exe from the booted disk? And then it extracts and runs setup.exe?

---

### Post by WeEatVista on 2008-06-23
I know this isn't much help, but this also happened to me. In the end, I finally just gave up on vista and now I am 100% ubuntu. I just wanted to put my two cents in :)

-We Eat Vista

---

### Post by jocko on 2008-06-23
> **CrumbledCookies said:**
> I don't think I can make an ISO on Ubuntu, but if I just burn the three files: boot.wim, install.wim, and X13-49120.exe, will it boot from X13-49120.exe? That's what sets up the Vista setup.exe.

Nevermind, I made an ISO of the three files. But X13-49120.exe is what extracts files. It extracts setup.exe for example. Should I go ahead and extract then right the files? If I boot from the disk, how will it know to boot from the .exe? How could I format my Hard Drive so I can have a fresh, clean copy? Thank you guys a lot, we are close to finding a solution. :)

Wait, I forgot that I can't run .exe from Ubuntu. But, can I run X13-49120.exe from the booted disk? And then it extracts and runs setup.exe?

I'm not sure I understand what you are trying to do here?
Do you think you can make a vista install cd from three loose files you have on your harddrive?
That's probably not possible. The only way to make a bootable vista cd is by burning an iso which is a direct copy of a real vista install cd (and as you don't own a vista install cd, that means you would need to download an illegal, pirated copy from somewhere. That's probably not something we should support on these forums).

To fix your problem, you need to give more information.
Your problem is probably the usual thing that goes wrong when grub is installed; It's not set up properly for booting windows, probably because it looks for the boot.ini on the wrong partition. Or maybe it looks for a boot.ini, when it really should look for some other file?
I'm not even sure vista use the same boot loader as XP, so maybe the problem is that grub looks for the wrong type of boot loader?
So unless you have messed things up by starting to make random changes in the windows partition (the one windows calls c:\), you should fix grub, not windows.

You need to do what AndyCee have asked of you several times, post your grub configuration file here so that we can see what's wrong with it:
```
cat /boot/grub/menu.lst
```We also need to know how your harddrive is partitioned:
```
sudo fdisk -l
```

---

### Post by CrumbledCookies on 2008-06-24
Dangit, I formatted my Hard Drive and installed XP, after I made an iso of the three files. Unluckily, it didn't write install.wim to the disc, now I will never have vista and I gave away $400 freaking dollars! :( Microsoft can't help me, I'm doomed. The download links that Microsuck gave me don't work, I don't know what I'm going to do. I really miss Vista now. :(

---

### Post by tgrimley on 2008-06-24
follow this guide under xp:

[http://hubpages.com/hub/Windows_Vista_Full_Direct_Download](http://hubpages.com/hub/Windows_Vista_Full_Direct_Download)

---


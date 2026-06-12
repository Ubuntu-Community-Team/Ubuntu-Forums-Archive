---
title: "Can I edit my Windows registry with Wine?"
date: 2008-10-22
forum: Wine
---

### Post by kahlil88 on 2008-10-22
I'm trying to fix a system that was corrupted by a virus. I'd like to know how to edit the registry using a Live CD with Wine installed, if that's even possible.

---

### Post by YokoZar on 2008-10-22
I don't think anyone's ever tried this before.  Importing the Windows registry into Wine won't work, and neither will setting Wine to use your windows drive as it's C:\ drive (this will in fact break the Windows installation completely)

---

### Post by marshalium on 2008-10-23
> **kahlil88 said:**
> I'm trying to fix a system that was corrupted by a virus. I'd like to know how to edit the registry using a Live CD with Wine installed, if that's even possible.

This linux boot cd looks like what you want:

[http://home.eunet.no/pnordahl/ntpasswd/](http://home.eunet.no/pnordahl/ntpasswd/)

---

### Post by prematurebaby on 2008-10-23
There actually is a registry editor in wine. I found it before. I'll tell you how to get there in a second.

---

### Post by prematurebaby on 2008-10-23
Ok browse the C: drive and go into the windows folder. Then click regedit.exe . Hope that was helpful. I'm not sure about putting wine on a live CD though. You can try though.

---

### Post by marshalium on 2008-10-23
> **prematurebaby said:**
> Ok browse the C: drive and go into the windows folder. Then click regedit.exe . Hope that was helpful. I'm not sure about putting wine on a live CD though. You can try though.

I don't think wine's regedit is compatible with regular windows.

---

### Post by oedipuss on 2008-10-23
I find it surprising that such a tool has not yet emerged .. Imagine how easier it would be to clean a malware infected system from a separate incompatible (to the malware) environment, such as a linux live cd or installation. 
Wine can't use its own registry editor to tweak a normal windows registry but what about some other tool?
Or are there technical difficulties in the way?

---

### Post by flav0rl3ss on 2008-11-19
I'm looking all over for a tool to do this as well, viewing and exporting a current windows installation's registry is good enough for me (I'm sure this is in some way possible, while modifying a registry could lead to corrupting it, a read-only style of working with it would be wonderful in so many ways)

I am wondering why there isn't something out that can do this by now (that I can find).  I'm, of course, not the biggest wiz, and am having trouble finding a way to do this alone :)

---

### Post by flav0rl3ss on 2008-11-20
Alright, after a little bit of work I found an easy way to do this...(I hafta say I don't feel to brilliant that I didn't think of it sooner) I am personally not going to modify my registry, but I do believe it's possible.

I simply downloaded an old program i used.. to repair registries from a dual booting windows machine.

[http://www.soft411.com/company/MiTeC/MiTeC-Windows-Registry-File-Viewer.htm](http://www.soft411.com/company/MiTeC/MiTeC-Windows-Registry-File-Viewer.htm)

and ran it with wine

from there you can open standalone windows registry hives in the windows\system32\config directory 


I hope this may help someone else out there.

---

### Post by pqrs295 on 2008-11-20
Up to 70% Off, Hurry Sale Ends SoonAustralian Real Sheepskin Boots**[color=#c76200]Uggretailsale.com[/color]**Authentic ugg boots, crafted from 100% natural Australian merino sheepskin leather.**[color=#c76200]Uggretailsale.com[/color]****[color=#c76200][/color]**100% Genuine AustralianUgg BootsPay by Paypal, Non-tax, Hurry!**[color=#c76200]Uggretailsale.com[/color]**

---

### Post by SpawnHappyJake on 2011-04-17
&#65279;Hey guys. I know this an old thread, but do you know what else is old? Not having a GUI by which to edit the Windows registry from Linux. I'm not blaming Linux or anything for being inadequate (no one can rightfully demand that Linux be equipped with such a tool), and I'm very thankful for what they have given the public, but I think many of you will agree with me that there is a need here.

If you don't want to read all this, and just want the workaround, skip to the end.

Why is this a need? Well, it sure would help if I had a CD or thumb drive that I could just boot any computer with, and proceed to edit the Windows registry of the computer I booted off of, for recovery purposes. And, of course, we all want to be able to this for free - legally free. How many operating systems do you know of that are capable of booting off a thumb drive (or something else portable and insertable without opening the case), capable of being portable from system to system regardless of hardware, is free, has a GUI, and is able to run programs that can be used for recovery purposes? Of these that you could think of, which one would you prefer to work in? Probably Linux. If not, it probably is Linux, and you don't realize it. Having a registry editor that we can point at any collection of hive files and also works in Linux is the obvious solution here - but we want a GUI - or at least I do.

Flav0rl3ss, I'm sorry to say that the MiTeC Registry Viewer only VIEWS registry hives, and does not do editing. I got really excited when it worked flawlessly in WINE 1.3.17, but it was heartbreaking to find that it only views. I found out the hard way.

There seems to be 5 requirements here:
#1. Be able to load a hive of one's choosing, not just the hive it finds first.
#2. Be Free. (If we didn't care about free, then this thread would be closer to pointless - or should I say needless - hehehe - because you could just boot into Windows and edit the registry. Yes you can install XP to a USB drive, and yes there is a portability "hack" you can do in the registry to make it not care about differing hardware, see [www.ngine.de](www.ngine.de).)
#3. Work in WINE, or goodness forbid, natively in Linux.
#4. Have a GUI.
#5. Be able to read AND write to the registry.

I've known about the chntpw registry editor for, I think over 2 years now, but just today discovered that there is a version that can be installed into Linux, in fact, it's in the Ubuntu default repository, so you can "sudo apt-get" it. This is a CLI tool. It has no GUI. Before, I thought it was only available as it's own independent operating system that you booted off a CD or thumb drive. This bugged me in my attempts to make a multi-bootable thumb drive that included it as a tool because the darn thing (ok, I actually love it) has not one, but TWO initial ramdisks, and GRUB2 does not support the loading of more than one initial ram disk to a kernel, the loopback-iso-GRUB2 method didn't work, and also, I succeeded in merging the two images into one (I think), but GRUB2 still didn't boot it, and sadly, I had issues with syslinux and GRUB2 co-existing, though I think I could do it now. But now I can just have a thumb drive bootable into Linux, and have it in there!

Another issue with the "independent" (its own OS) form was that it had the worst possible interface (ok, not worst possible, but pretty bad). I can put up with a CLI when I'm desperate, but this was heck. Let's say you want to edit something in HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run . First you had to tell it to go into registry editor mode, then load the hive, which is all well and good, but you couldn't just do "edit [path] to [whatever you wanted the value to be]". You first had to cd to Software. Then cd to Microsoft. Then cd to Windows. Then cd to CurrentVersion. Then cd to Run. Yep, it was bad. What if you wanted to delete a key? Oh boy. You had to delete everything in that key before you could delete it. If the key contained keys that contained keys... I think you can see where this is going.

The "dependent" one, if you will, doesn't seem to have such cding issues. However, still no GUI. It also has an "rdel" feature that recursively deletes keys, meaning you don't have to do the super annoying delete ls delete ls delete ls like before. That feature wasn't there last time I used chntpw (which was in the "independent" version). I have a feeling that there simply have been newer versions since last time I tried it, and the new version is probably implemented in the "independent" version by now too, so it too probably now has rdel and deep cding. But it still doesn't reload your last line with an up arrow key. I misspell paths ior get quotes ior slashes wrong a lot, and I want to be able to go back and tweak it instead of writing out that big, long path again. Am I picky or what?

Editing the Windows registry from Linux is actually something I have researched before. Unfortunately, when I right-click on the Windows regedit and tell it to run in Wine, it seems to bring up the same regedit that typing "wine regedit" at terminal brings up. Either way, I have no option of loading a hive. I certainly don't have a file menu when I click on HKEY_USERS or HKEY_LOCAL_MACHINE keys ([http://technet.microsoft.com/en-us/library/cc759303(WS.10).aspx](http://technet.microsoft.com/en-us/library/cc759303(WS.10).aspx)). I can import or export a text file containing keys, but not a hive. It just loads the WINE registry, and that's your option. You can have a Model-T in any color you want as long as that color is black.

I found PC Regedit quite a while ago (at least a year), but it straight-up wouldn't boot. [http://www.pcregedit.com/](http://www.pcregedit.com/) . If I remember right, it didn't want to boot off a thumb drive no matter what sorcery I threw at it either. Of course, I tried burning the iso to a CD too (though I avoid CDs whenever possible and use a thumb drive). It is free, and supposedly has a GUI and lets you pick the hive files and is bootable as its own thing and everything...but it wouldn't boot. That puts quite the damper on it.

The bootable AVG tool supposedly has a registry editor as well, but I couldn't get it to work. It just didn't go. Like, nothing. It booted into it's thing, but the option to edit the registry was a no-go.

So I spent a couple hours trying to find a 3rd party registry tool that would work through WINE. Here's the ones I found and tried in one determined sitting ](*,)(maybe the last one or two was a second setting, but here we go):

Regalyzer: It ran, and it has the option to load the hive of choice, but errored when I told it to load a hive. I saw that the volume containing the hive files was mounted with root being the owner, so I edited fstab to mount the volume with me owning it (the person running WINE), and it still errored. I copied the config folder to my home folder and it still errored.

Reg: Ran, but no option to load hive of choice. It only opened the WINE registry.

RegistrarLite: Editing hives from a location of choice seems only to be offered in the Pro version (costs money).

Vilma Reg Explore: Straight-up didn't open.

Registry Commander: No option to load hive of choice, only loaded WINE registry.

CrackSoft Reg Explore: Straight-up didn't open.

RegmagiK: Staight-up didn't open.

Salamander Whatever It's Called: Looks free, but's not.

Small Registry Editor: Straight-up didn't open.

RegSeeker: Not actually an editor. It's just searcher/ cleaner.

Ntpwedit.exe: This seemed most promising because I read that it is a GUI implementation of chntpw. Sadly it only implements the OTHER feature of chntpw, not it's registry editing feature.

MiTeC Registry Viewer: OMIGOSH!! OMIGOSH!! It actually loaded in Wine AND has an option to load whatever hive I want to AND it's free AND it ACTUALLY succeeded in loading the hive of choice!! OMIGOSH!...oh. It only views. It doesn't edit. Poop. :-({|=

Yes, it's OK to laugh. :lolflag:In fact, I would appreciate it if someone did. It's an excellent way of coping; I've found.

:idea:My recommendation: Use MiTeC Registry Viewer in WINE 1.3.17 (or higher, provided it still works) side-by-side with the "dependent" chntpw (obtained by "sudo apt-get install chntpw" in terminal, or through Synaptic package manager. Terminal is actually quicker and easier, believe it or not). Copy the config folder somewhere, have MiTeC Registry Viewer pointed at the copy, and have chntpw open in terminal pointed at the original. You can search and find the paths/ names of wanted (as in bounty-on-head, not as in "desired") registry keys in MiTeC, then do the dirty work in chntpw. You can copy and paste even. Shift-Ctrl-V to paste into terminal, and Shift-Ctrl-C to copy selection from terminal. Don't forget Ctrl-Alt-T to open terminal ;) . Pasting what you have copied from terminal into something other than a terminal is Ctrl-V as normal (without the Shift). So you can copy the key name/path from MiTeC into terminal where you are in chntpw. WINE 1.3.17 lets your WINE clipboard be one with your Linux clipboard; it didn't used to be that way. You had to paste in WINE notepad, save, open in gedit and copy - or something absurd like that.

:KSFAT NOTE IN ALL-CAPS. CHNTPW IS CAPS-SENSITIVE, AS IS TERMINAL.:KS

Post-Post (hehehe, see technically it's not post-script because there's no signature, and it conveniently makes a pseudo-pun. No, not a sudo-pun.): Maybe use Kregedit instead of MiTeC in WINE because Kregedit runs natively in Linux and you could skip WINE. Then again, maybe MiTeC is so much better that it's worth it, I don't know. You still can't write with either.

---

### Post by SpawnHappyJake on 2011-04-17
Hey, sorry guys. Forum rules says we're not supposed to use acronyms.
Here's some I used:

GUI = Graphical User Interface. (there's buttons instead of all typing. Think Windows instead of DOS - Disk Operating System). Includes graphical aids like buttons and/or menus/ and/or dropdowns and/or trees, etc. A two-dimensional area with interactable subareas (technically it COULD be 3-D).

CLI = Command Line Interface. No buttons or anything graphical. All typing.

ls = Command line command for LiSting what's in the current directory (folder or registry key, the current path). Type "ls" then enter.

iso ~ intentional double meaning: It means both the "International Standardization Organization" and the Greek work "iso" which means "same," since that is the goal of the organization. The ISO 9660 standard is a filesystem for optical discs, so images of optical discs compliant to this standard are often called isos. Note: not all CD images can be rightfully called an iso, because only some CDs comply to this standard. Example: you can't make a true iso of an audio CD. You can dump it and name the image file *.iso, but it won't be an iso.


cd = change directory or compact disc (as in optical), depending on context

WINE = Wine Is Not an Emulator

chntpw = CHange NT PassWord

AVG = Anti-Virus by Gritsoft

OS = Operating System
 
sudo = Super User DO (from what I've heard)

I don't think we have to be THAT picky, but I wanted to clear the air, especially for my first post.

---

### Post by Mr Stoozer on 2011-04-17
You could use imagex to capture the Windows image. You could then mount it and service it, all offline (and use the image to test in a Virtual Machine before redeploying). Whether this is possible whilst using a LiveCD, i cannot tell.

---

### Post by SpawnHappyJake on 2011-04-17
[SIZE=2][FONT=Times]> **Mr Stoozer said:**
> You could use Imagex to capture the Windows image. You could then mount it and service it, all offline (and use the image to test in a Virtual Machine before redeploying). Whether this is possible whilst using a LiveCD, i cannot tell.[/FONT][/SIZE]
  
  [SIZE=2][FONT=Times]There's stuff that has to be known about that option. First, Windows usually is picky about hardware, unlike Linux. If I have Linux installed to a thumb drive, I can boot darn near any computer off that thumb drive - even a MacBook with a little sorcery. If I installed WinXP to a thumb drive and tried to boot off the thumb drive on a computer different hardware-wise from the one I used to install WinXP onto the thumb drive, then it will complain about the hardware difference because it is not configured for the other hardware - unless you do the "portability hack" (see [http://forums.ngine.de/viewtopic.php?f=4&t=3202](http://forums.ngine.de/viewtopic.php?f=4&t=3202) and [http://forums.ngine.de/viewtopic.php?f=4&t=3132](http://forums.ngine.de/viewtopic.php?f=4&t=3132) , though the person is wrong when he says Linux installs itself every time because I have actually INSTALLED Linux to a thumb drive, and it can boot off any computer. Notice this is different than making it bootable into the installer).[/FONT][/SIZE]
  [SIZE=2][FONT=Times]So if you image a Windows drive and mount it in a virtual machine, there will be different hardware, and you will first need to tweak the registry before it will boot in the virtual machine.[/FONT][/SIZE]
  [SIZE=2][FONT=Times]Second, servicing the image from within a virtual machine is probably only worth the hard drive space, resources, and time if you are going to do things other than simple registry editing. You could just copy the %systemroot%\config folder, edit the copy, then paste back over...as opposed to copying the entire hard drive or partition, tweaking it to work with the emulated environment, then proceeding to take up the resources necessary to emulate an entire machine (in an already limited "Live" environment). However, it would be nice to see if everything works first, and that gets me excited that idea...good job sir. But why not do something like Plop's vhd booter, eh? [http://www.plop.at/en/vhdloader.html](http://www.plop.at/en/vhdloader.html) . Then you are only running 1.1 operating systems instead of 2, or however that works out. Now THAT'S some SERIOUS sorcery![/FONT][/SIZE]
  [SIZE=2][FONT=Times]Just have a multi-bootable thumb drive with the Plop VHD booter as an option, and off you go![/FONT][/SIZE]
  [SIZE=2][FONT=Times]Or you can boot the raw image with something like this: [http://reboot.pro/10107/](http://reboot.pro/10107/) .[/FONT][/SIZE]
  [SIZE=2][FONT=Times]LiveCD? No. LiveThumbDrive. Come on. ;) Either way, yes, you could make a LiveCD with VirtualBox, chntpw, WINE 1.3.17, and the MiTeC Registry Viewer all installed already in the live environment. There's probably a way to increase allotted temporary filesystem space as well during the creation of the disc (which you might need). [/FONT][/SIZE]
  [SIZE=2][FONT=Times]You could mount a plain raw image in Linux with "sudo mount - o loop," but I don't think you can for any other format of image.[/FONT][/SIZE]
  [SIZE=2][FONT=Times]However, this Imagex sounds like a rather proprietary, "smart" ,"cooked" (it ain't raw no more, and certainly ain't mooin') image that needs a special program to make sense of it. You need cooked images for hard drives or else they'd get to big, unless you could somehow mount and edit an image while constantly keeping it in a tar.bz2. I doubt VirtualBox will be able to make sense of this Imagex format. With raw images, there's nothing that needs to be made sense of, they are 1:1 copies of the original (unless the firmware lied). So no, Linux can't mount the Imagex images, unless there is a tool for doing so that I don't know of.[/FONT][/SIZE]
  [SIZE=2][FONT=Times]Making vhd images is one option. The Plop VHD Loader as well as VirtualBox could boot that image once you've done the portability hack.[/FONT][/SIZE]
  [SIZE=2][FONT=Times]Making a raw img image is another option. This can be booted with the [http://reboot.pro/10107/](http://reboot.pro/10107/) technique, and IS mountable with Linux's "sudo mount -o loop". The image won't be bootable unless it is continuous (the file itself is not fragmented on the disk). The big downer here is that the image must be able to fit in the RAM and still have enough left to do other things (like run the operating system). So if you have a 40 GB XP install...not happening. Test in a Virtual Machine.[/FONT][/SIZE]
  [SIZE=2][FONT=Times]Then again, you don't have to test at all. You can just edit the disk first, and ask questions later. If it still doesn't work, what's new? You can use the same method to eventually fix it, or do a repair install. Or switch to Linux ;) .[/FONT][/SIZE]
  [SIZE=2][FONT=Times]An idea I've had in my head for a long time was, "Why can't a share a REAL partition to VirtualBox? Then I could have a hybrid between a 'dual boot scenario' and a 'virtualization scenario'." But no one seems to be doing this. This would be optimal in this situation. Just boot into a LiveCD (or thumb drive) environment with VirtualBox, point it at the partition, and boot it to see if our editings bore good fruit.[/FONT][/SIZE]

---

### Post by SpawnHappyJake on 2011-04-17
[http://openreged.sourceforge.net/](http://openreged.sourceforge.net/)
OpenRegEd doesn't exist yet, but it will be the solution. It is an open source GUI implementation of chntpw. Get that sucker compiled for your Linux, and you're golden.

---


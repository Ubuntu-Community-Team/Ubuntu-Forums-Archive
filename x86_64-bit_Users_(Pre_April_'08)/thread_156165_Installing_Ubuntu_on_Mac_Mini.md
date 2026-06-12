---
title: "Installing Ubuntu on Mac Mini?"
date: 2006-04-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sushi on 2006-04-06
I have few questions. Few are Mac Mini specific, and few are about Linux-PPC in general. Like the title suggests,I'm thinking of installing Ubuntu on my Mac Mini (1.25Ghz G4). Now, how well does Mini work with Linux? Does suspending work? What about the hardware in general? The Live-CD does seem to work, but the resolution is screwed up.

Now, as to PPC in general: what would I be giving up if I moved to Linux on PPC? I know that Flash would not work (mostly), but what about media-codecs? I find it rather weird that we can use Windows-codecs with linux on x86, but we can't use Mac OS-codecs on PPC....

Maybe it would be easier to just sell the PPC-Mini, and maybe get a Intel-Mini instead :)?

---

### Post by Ubuntuud on 2006-04-06
I believe that installing on an intel-mini is very hard...

---

### Post by mail_order_mini on 2006-04-06
I've got a mac mini and am having trouble with Ubuntu. It won't boot after installation, though the live cd worked fine for me too.

---

### Post by wannabelinuxconvert on 2006-04-07
What version of ubuntu are you using !?

I have installed both Breezy and the Dapper Flight 6 releases on my Mac Mini and everything works 100%

How are you installing !?

What I did was to create two partitions on my Mini's drive, one Mac OS Journaled and left one as free space. I then installed OS X as normal on the Mac partition. Then I rebooted into the breezy/dapper installation, just hit enter for regular installation, (*although I have tried **server** and that worked fine too!*) when the partition editor starts up selected use largest continous free space and then finish the install.

Everything works fine, and I have done this quite a few times now.

I have a 1.42ghz PPC Mac Mini with 1gb Memory.

Mic

---

### Post by mail_order_mini on 2006-04-07
Aww mate, that sucks. I've got the same except I haven't upgraded the ram yet. I'm trying to  install 5.10 and can't get past the first boot.

Edit: Check out my thread  [here]("http://ubuntuforums.org/showthread.php?t=155386") for more info...

---

### Post by glatzor on 2006-05-01
I installed dapper on my mac mini (G4) and I am confrated with the following shortcomings:

- NetworkManager doesn't work with Airport/Wireless
- Cannot control the sound volume
- Suspend doesn't work

Not tested:
- Firewire

---

### Post by apanloco on 2006-05-05
I just installed Dapper Drake Flight6 on my Mac Mini, after trying out both Fedora Core 5 and Ubuntu Breezy. I just say WOW everything just works.

SOUND:
Sound did work at some times in Fedora Core, but not automatically. It worked in Breezy but the VolumeIcon in gnome always showed Muted, but it wasn't. In Dapper it just works.

PRINTING:
Tried in Fedora Core, and had som issues adding the printer. It worked, but not as good as in Dapper. MMMmmmm Dapper...

CODECS:
Well. I havn't quite figured out yet why I can watch flash-things in Mac OS X but not in Linux. I have pondered on this for a week, maybe someone can enlighten me? I used EasyUbuntu and got quite a few things working, but not enough for being satisfied really... I have an assortement of small clips, mostly wma, and one wma worked, and I don't know why it did :)

VIDEO:
Using the opensource ati driver. Seems like there is no binary ATI driver for PPC. *sod, sod*

/D

---

### Post by 3rdalbum on 2006-05-05
[QUOTE=apanloco]

CODECS:
Well. I havn't quite figured out yet why I can watch flash-things in Mac OS X but not in Linux. I have pondered on this for a week, maybe someone can enlighten me?[/QUOTE]

For the same reason that there is no proprietry ATI driver for PPC Linux, there is no version of Flash for PPC Linux. Macromedia haven't compiled it for PPC Linux, and nobody has any idea why not. They've obviously got Macs there, otherwise they wouldn't have been able to make Flash for OS X!

[QUOTE=apanloco]
I have an assortement of small clips, mostly wma, and one wma worked, and I don't know why it did :)
[/QUOTE]

I even managed to get a WMV working on Linux-PPC. Nautilus generated a thumbnail for it and Totem played it! But I'm thinking now that it must've actually been an AVI or something. It was that video of some guy completing Super Mario 64 in 21 minutes.

---


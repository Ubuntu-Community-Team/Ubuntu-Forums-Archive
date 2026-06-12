---
title: "can't setup dual boot (XP and Linux)"
date: 2006-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by rupsyco on 2006-04-20
Dear all,

installed Ubuntu 64... already had winXP... when trying to install Grub on the MBR I get failure to boot... tried in the ntfs partition.. screwd up the XP boot... at the end I'm booting XP normally and to startup Linux I use a floppy....

I suspect my bios does recognize a different MBR and blocks the bootstrap. (My previous 64 with lilo used to message and beep me before going ahead)

Anybody got Ideas?

Thank you

---

### Post by gpeck157 on 2006-04-20
[QUOTE=rupsyco]Dear all,

installed Ubuntu 64... already had winXP... when trying to install Grub on the MBR I get failure to boot... tried in the ntfs partition.. screwd up the XP boot... at the end I'm booting XP normally and to startup Linux I use a floppy....

I suspect my bios does recognize a different MBR and blocks the bootstrap. (My previous 64 with lilo used to message and beep me before going ahead)

Anybody got Ideas?

Thank you[/QUOTE]

This link might help.
[http://ubuntuforums.org/showthread.php?t=76652&highlight=Arnieboy](http://ubuntuforums.org/showthread.php?t=76652&highlight=Arnieboy)
Glen

---

### Post by evergreen on 2006-04-22
[>here<]("http://video.google.com/videoplay?docid=-6104490811311898236&q")

---

### Post by new2ub on 2006-04-26
I have the following 64 bit OSs installed and working on the same SATA hard disk : WinXP-64, Ubuntu 5.10, Gentoo-64 SUSE 10-64,
Fedora fc4-64 and Kanotix-64. All boot and work okay with LILO.
[I][SIZE="1"]If you can get ahold of a 64 bit rescue CD like Gentoo-64-minimal or Fedora-64 Rescue all you have to do is mount Ubuntu, chroot to it then run "liloconf". Next run "lilo -t" to test if there is no critical errors  like "FATAL" appears. If there isnt  then run "lilo" (without options).
Reboot then loose the floopy. Sorry I cant help you with GRUB.[/SIZE][/I]

---

### Post by new2ub on 2006-04-27
WHOOPS ! My apologies. Liloconf found on Ubuntu (hoary) not breezy .
](*,)

---

### Post by rupsyco on 2006-05-02
i don't even know what difference there is between all this Hoary, Breezy? So how do I get lilo and how do I understand which I installed?

---


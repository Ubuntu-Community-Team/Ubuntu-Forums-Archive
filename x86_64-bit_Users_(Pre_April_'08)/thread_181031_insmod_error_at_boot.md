---
title: "insmod error at boot"
date: 2006-05-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by amklinux on 2006-05-23
I have a G4-400, and I'm getting an error during boot process. The error message is something like that: 

insmod error: cannot read 'lib/modules/2.6.12-10-powerpc/kernel/drivers/video/console/bitblit.ko: directory or file not found
insmod error: cannot read 'lib/modules/2.6.12-10-powerpc/kernel/drivers/video/console/font.ko: directory or file not found
insmod error: cannot read 'lib/modules/2.6.12-10-powerpc/kernel/drivers/video/console/tileblit.ko: directory or file not found
insmod error: cannot read 'lib/modules/2.6.12-10-powerpc/kernel/drivers/video/console/fbcon.ko: directory or file not found

...and several other similar messages with changing file names. I checked the files and they really doesn't exist. But the boot process continues, and I can use the machine. However, I would like to know what is causing this and if there is some effect. Thanks for any help.

---

### Post by Ptero-4 on 2006-05-23
Those messages come b/c the kernel is trying to load some kernel modules that aren't in your HD. The ones you showed are for Matrox videocards.

---

### Post by amklinux on 2006-05-24
Well, that's really strange. My video card is an ATI Rage 128 Pro! How could I remove these messages? Thanks for your reply.

---

### Post by RavenOfOdin on 2006-05-24
[QUOTE=Ptero-4]Those messages come b/c the kernel is trying to load some kernel modules that aren't in your HD. The ones you showed are for Matrox videocards.[/QUOTE]

I'm getting the messages related to bitblit and fbcon too, but they go more along the lines of "unknown symbol in module", "invalid module format", "exports duplicate symbol (owned by kernel)"

I also get those messages as related to cfbimgblt, cfbfillrect, cfbcopyarea and softcursor.

I'm using a PC with 128MB ATI Radeon 9200, over a built-in S3 ProSavage DDR.

Hopefully this isn't an architecture-specific issue.

---

### Post by RavenOfOdin on 2006-05-27
And its not. Enabling Matrox G200/G400 support worked. Yay.

---


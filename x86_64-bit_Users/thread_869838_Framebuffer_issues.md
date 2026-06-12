---
title: "Framebuffer issues"
date: 2008-07-25
forum: x86 64-bit Users
---

### Post by dave_chimaera on 2008-07-25
Little bit of background info first. 

I'm running Ubuntu 64-bit on a Dell XPS M1530 in an encrypted LVM as per the instructions [Here]("http://https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto") with a couple of minor modifications, specifically:
[LIST]
[*]grub and /boot are on a USB memory key (so memory key in = boot to grub and linux, no mem key = whatever happens to be installed in the first partition of the HDD (currently Vista)
[*]/etc/crypttab references a keyfile so only prompted for the LVM password once
[/LIST]

In addition to this I have modified /boot/grub/menu.1st to include the appropriate boot option to allow the trackpad to work properly. 

So I've got most things working how I want them, but one thing is irritating me - my laptop has a widescreen 1650x1080 display so the aspect ratio of the boot screen is wrong. It's a minor problem, but now that I've sorted the major problems it's irritating me :). Anyway, I've folowed the instructions in post #22 of [this thread]("http://ubuntuforums.org/showthread.php?t=258484&page=3") and not had much success - the hwinf command returns the expected list of vesa modes and does include the suitable one for the panel (1650x1080 at 24-bit - I *think* it was 0x0369 but I can't remember - I'm posting from work atm) and I've appended this to the boot options in /boot/grub/menu.lst but it doesn't work - instead the image is compressed the other way (tall and thin as opposed to short and fat). 

I've tried a few other widescreen resolutions and colour depths from the hwinfo output and none of them work, some are the same as the above example, some are off center and also in the wrong aspect ratio and so on. 

Help, please!

---


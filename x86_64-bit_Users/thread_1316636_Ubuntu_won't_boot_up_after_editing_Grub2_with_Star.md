---
title: "Ubuntu won't boot up after editing Grub2 with Start-up Manager!!"
date: 2009-11-06
forum: x86 64-bit Users
---

### Post by Harold.Gcia on 2009-11-06
I installed Start-up Manager to change settings in Grub2. I changed the seconds to auto boot from 10s to 20s, and Ubuntu would load up fine. After that, I changed the resolution of the display it was originally 640x480, but I forgot to what resolution I changed it to. I changed the resolution of the splash image too. The boot up menu shows up, But the seconds don't show up and when I hit enter to boot up into Ubuntu it only shows a blank screen and Ubuntu doesn't boot up.

I have a dual boot system with vista, and vista boots up fine. I need help with this, I don't know what to do.

---

### Post by dvlchd3 on 2009-11-06
I had this exact same issue.  Luckily I didn't move completely to 9.10.  I just restored legacy GRUB, and am still using 9.04.  I was disappointed in the new additions with GRUB 2 and GDM anyway.  Until there has been more done with both of these new features, I believe I'm staying away from Karmic...

However, if someone has a fix, I'd certainly love to see it!  Perhaps it will give me a little more knowledge into the workings of the new GRUB and gdm!

---

### Post by Harold.Gcia on 2009-11-06
Is there a way to restore Grub2 to the default settings using the live cd? I have searched google and the forums, but I can't find anything on this or any other fix for this problem.

---

### Post by bedtime_with_the_bear on 2009-11-06
> **Harold.Gcia said:**
> Is there a way to restore Grub2 to the default settings using the live cd? I have searched google and the forums, but I can't find anything on this or any other fix for this problem.

sudo grub-mkconfig will generate a new grub.cfg and display it on screen, but will NOT overwrite your existing - you'll have to do that yourself.

---

### Post by Harold.Gcia on 2009-11-06
> **bedtime_with_the_bear said:**
> sudo grub-mkconfig will generate a new grub.cfg and display it on screen, but will NOT overwrite your existing - you'll have to do that yourself.
Can I do that if Ubuntu won't boot up? When I try to boot it up, it only shows a blank screen and nothing changes.

In the boot up menu, I get the option to boot up on Ubuntu or Vista. Then at the bottom it says.

[Use the up and down keys to select which entry is highlighted. Press enter to boot the selected os, 'e' to edit the commands before booting or 'c' for a command line.]

I click 'c' and when I do what you suggested it says [error: unknown command 'sudo']

When I click 'e' it says

recordfail=1
if [ -n ${have_grubenv} ] ; then save_env recordfail; fi set quiet=1
insmod ext2
set root=(hdo, 5)
Search --no-floppy --fs-uuid --set 51963d98-cfa1-4648-ac2d-093205097ecd
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=51963d98-cfa1-4648-ac2d-093205097ecd ro \
 splash quiet vga=795 quiet splash
initrd /boot/initrd. img-2.6.31-14-generic

Then at the bottom it says:

Minimum Emacs-like screen editing is supported. TAB lists
completions. Press Ctrl-x to boot, Ctrl-c for a command line
or ESC to return menu.

I really don't know what to do. I'm new to Ubuntu and Linux, I intstalled Ubuntu 3 days ago. So I will really apriciate any help you guys can give me.

---

### Post by sadahalli on 2009-11-06
Try this link..- See the section for restoring GRUB from Live CD

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by hkkea on 2009-11-07
i guess the link given by #6 above is for GRUB 1, for how to recover GRUB 2 should read this:

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")

---

### Post by Harold.Gcia on 2009-11-09
> **hkkea said:**
> i guess the link given by #6 above is for GRUB 1, for how to recover GRUB 2 should read this:

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")
I tried doing the instruction on the link, but I couldn't get it fixed. So I just removed Ubuntu and installed it again. Its working fine now. But I'm not going to mess with Start-up Manager again.

---


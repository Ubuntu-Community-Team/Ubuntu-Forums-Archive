---
title: "[SOLVED] Boot Splash disappeared"
date: 2008-06-09
forum: x86 64-bit Users
---

### Post by cowanh00 on 2008-06-09
Since I modified my partitions (my new home partition was too small) the splash screen when booting has disappeared. After the grub I get the loading screen where the bar bounces from side to side and then it changes to the scrolling text. It boots into Hardy no problem anyway but it is slightly annoying to see the text.

The shutdown loading bar shows no problem.

---

### Post by editrix on 2008-06-09
I think I have the same problem, except after installing Hardy I *never* saw a splash screen, and I get absolutely nothing while the machine's booting up. I'd really like to see all that scrolling text. Sometimes there's important information there, like if a piece of hardware fails.

---

### Post by John Jason Jordan on 2008-06-09
> **cowanh00 said:**
> Since I modified my partitions (my new home partition was too small) the splash screen when booting has disappeared. After the grub I get the loading screen where the bar bounces from side to side and then it changes to the scrolling text. It boots into Hardy no problem anyway but it is slightly annoying to see the text.
The shutdown loading bar shows no problem.
You may have a problem with the /boot/grub/menu.lst file.

CAUTION: Make a backup of your menu.lst file before editing it, lest you render your computer unbootable. You can always restore the backup using a live CD if necessary.

Here is a section of my menu.lst file:

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=afba6df9-befb-4643-a209-841c2476a989 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

This is the first boot option that will appear in the grub boot menu options. Note the "quiet splash" at the end of the third line. If that is missing in your file, add it.

Another note: In case your editing of the boot menu options renders your computer unbootable, when the grub boot menu comes up you can edit things manually at that point (hit Esc). Any changes you make at that point will not persevere to the next boot, so to make the changes permanent you have to edit the menu.lst file.

---

### Post by John Jason Jordan on 2008-06-09
> **editrix said:**
> I think I have the same problem, except after installing Hardy I *never* saw a splash screen, and I get absolutely nothing while the machine's booting up. I'd really like to see all that scrolling text. Sometimes there's important information there, like if a piece of hardware fails.
This is a recurring problem with Ubuntu. The upgrade to Hardy fixed a lot of problems that people were having before, but there are still occasional people reporting issues with the splash screen. The problem is that the splash screen has to display before the video driver loads, and sometimes it doesn't properly detect the proper resolution for your screen.

The fix is simple once you figure it out. Rather than repeat everything here, just search the forums for "usplash." That should turn up multiple threads where the various fixes are discussed.

---

### Post by philinux on 2008-06-09
If you want a gui then install and run startupmanager.

---

### Post by cowanh00 on 2008-06-10
> **John Jason Jordan said:**
> You may have a problem with the /boot/grub/menu.lst file.

CAUTION: Make a backup of your menu.lst file before editing it, lest you render your computer unbootable. You can always restore the backup using a live CD if necessary.

Here is a section of my menu.lst file:

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=afba6df9-befb-4643-a209-841c2476a989 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

This is the first boot option that will appear in the grub boot menu options. Note the "quiet splash" at the end of the third line. If that is missing in your file, add it.

Another note: In case your editing of the boot menu options renders your computer unbootable, when the grub boot menu comes up you can edit things manually at that point (hit Esc). Any changes you make at that point will not persevere to the next boot, so to make the changes permanent you have to edit the menu.lst file.

Thanks for the reply. I checked this file and I do indeed have 'quite splash' at the end of all 3 kernels I have installed. I've also installed Startup Manager and the show splash is ticked.

---

### Post by MeURi on 2008-06-10
Since you installed startupmanager, check that it tells you your exact screen resolution (if you are using a widescreen monitor, choose a resolution that is lower or equal to your vertical screen size)

Or, if you prefer a more 'manual way', you could check [this post](http://ubuntuforums.org/showpost.php?p=1987055&postcount=9) and see if it solves your problems (actually the post is about off-center bootsplash, but since it tells you to reconfigure usplash, it could be useful ;-))

---

### Post by bpl07 on 2008-06-10
[Fix on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990")

Basically, when you changed your swap partition, it didn't get updated in all the files it needed to be changed in.  Follow the 6 steps to sync your swap location and it should start working again.  The fix worked for me.

---

### Post by bpl07 on 2008-06-10
Another thing to check is your usplash.conf file at /etc/usplash.conf

Make sure the resolution matches your screen resolution.  You can check what resolution your framebuffer is capable of by running the command:
> sudo hwinfo --framebuffer
You need to have hwinfo installed to run this obviously.  The framebuffer is what your bios uses to load the splash before it's loaded the actual video drivers.  My screen size is 1280x800 but I had to set mine to 1024x768 because that was the limit of my framebuffer.  Hope this helps.

---

### Post by cowanh00 on 2008-06-10
> **bpl07 said:**
> [Fix on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990")

Basically, when you changed your swap partition, it didn't get updated in all the files it needed to be changed in.  Follow the 6 steps to sync your swap location and it should start working again.  The fix worked for me.

Perfect! Thank you sir! Yes indeed after I changed my swap partition I had to change the UUID in two places. I had changed it in one (due to my swap not loading on boot) but not the other!

Thanks again! :guitar:

---

### Post by RCC2k7 on 2008-06-12
I have this problem - same reason. After restoring a disk image my partitions got renumbered, my swap partition stopped working and usplash changed to the arcane text-based boot.

So, I fixed my /boot/grub/menu.lst and /etc/fstab files so my system boots and my swap partition works. However, I'm still stuck with usplash doing its ping pong thing then being replaced with the text-based boot. I tried the workaround mentioned in the Launchpad, but there is one problem, I'm not given a UUID for my swap partition!

```

roberto@rcc-desktop:~$ sudo blkid
[sudo] password for roberto: 
/dev/sda1: UUID="F6EC0E1CEC0DD82F" LABEL="XP PRO" TYPE="ntfs" 
/dev/sda2: UUID="3406E12F06E0F332" LABEL="Vista" TYPE="ntfs" 
/dev/sda5: UUID="7db22148-ec99-41d7-9dfe-f090c54e30aa" TYPE="ext3" 
**/dev/sda6: TYPE="swap"** 
/dev/sda7: UUID="F6C40E79C40E3BFD" LABEL="Intercambio" TYPE="ntfs" 
roberto@rcc-desktop:~$

```

By the way, unless the system is failing to boot, I don't see the point of a text-based boot. In a normal boot sequence everything happens so fast you don't even have time to read that stuff anyway.

---

### Post by Stunts on 2008-07-14
The fix from launchpad did solve my issue!
Thanks!
Now as for RCC2k7, maybe there is a way to set your own UUID on the swap partition? Or at least set it...

---


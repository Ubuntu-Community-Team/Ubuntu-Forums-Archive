---
title: "Opensuse upgrade broke grub. Boot-Info attached."
date: 2018-03-24
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Steve Goodey on 2018-03-24
Hello, sorry to bother you with an opensuse problem but I tried on a forum there but with no luck. Thanks for any help.

Boot-Info [http://paste.ubuntu.com/p/BVPB75MKF5/]("http://paste.ubuntu.com/p/BVPB75MKF5/")

I have /dev/sda1 with my existing home partition.

/dev/sdb1 Boot Grub
/dev/sdb2 swap
/dev/sdb3 btrfs / partition where the operating system is.

I had a working Opensuse Leap 42.2 working ok but as EOL I tried an update to 42.3 which broke things.

I tried Boot-Repair but got an error message 
Please enable a repository containing the [grub-efi-amd64-signed] packages in the software sources of openSUSE 42.3 (sdb3)

With nothing in the dvd drive I get missing OS, with the opensuse leap 42.3 dvd in and trying boot from hard disk I get error not a valid root device.
Trying rescue system get error file '/boot/x86_64/loader/linux' not found, same with boot linux system

---

### Post by jeremy31 on 2018-03-24
*Thread moved to **openSUSE and SUSE Linux Enterprise**.*

---

### Post by yancek on 2018-03-24
You have an EFI system which shows entries for OpenSuse so have you done what was suggested by boot repair:

> Please do not forget to make your BIOS boot on sdb1/efi/.../grub*.efi file!

You should be able to do that in the BIOS on boot with boot options for whatever hardware you are using.  These options vary between manufacturers.  Your grub.cfg file shows the updated version of Opensuse 42.3.

---

### Post by Steve Goodey on 2018-03-24
Thanks for your reply and apologies for not putting post in correct place.

All now sorted, thanks.

---

### Post by Steve Goodey on 2018-03-24
Added (Solved) to title.

---


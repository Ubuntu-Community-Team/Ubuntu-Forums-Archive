---
title: "ubuntu 8.04 fresh install crashes at boot time while loading usbHID"
date: 2008-06-11
forum: x86 64-bit Users
---

### Post by gsanroma on 2008-06-11
I have a Dell Inspiron 530 desktop computer with core 2 duo processor E6550.
I have installed 64 bits Ubuntu 8.04 correctly from live CD.
When doing normal boot the first time, system hangs while showing ubuntu logo and the orange bar moving one side to another.
In order to see what happens exactly I tried to boot in recovery mode and the system hangs immediately after displaying:

/build/buildd/linux-2.6.24/drivers/HID/usbHID/HID-Core.c: v2.6: USB HID Core Driver

Afterwards, the system remains indefinitely in this state while showing periodically further messages as:

[48.752700] ata3.00: qc timeout (cmd 0x27)
ata3.00: failed to read native max address (err_mask= 0x4)
ata3: failed to recover some devices, retrying in 5 secs

The system does not bring up any shell.

I tried to disable USB from bios and the system boots correctly (but mouse and keyboard don't work, obviously).

Maybe one solution could be to boot with the liveCD and do a chroot into the root directory of the fresh installed partition and finally replace the kernel by another version.
Any ideas? 

Thanks,

Gerard

---

### Post by evanphilip on 2008-09-04
This is a USB-SATA race codition. The solution is to force the SATA driver to load before the USB driver via a script. Follow the steps given below:

1.In the terminal, type the following command to create a script
$ [FONT="Courier New"]**gksudo gedit /usr/share/initramfs-tools/scripts/init-top/load_ata_piix**[/FONT]

2.Paste the following script (copied from Dell wiki)
[FONT="Courier New"]#!/bin/sh
PREREQ=""
prereqs()
{
    echo "$PREREQ"
}
case $1 in
# get pre-requisites
prereqs)
    prereqs
    exit 0
    ;;
esac
modprobe -Qb ata_piix
 [/FONT]
3.Use the following command to make the script executable
$ [FONT="Courier New"]**sudo chmod +x /usr/share/initramfs-tools/scripts/init-top/load_ata_piix**[/FONT]

4.Execute the script by typing
$ [FONT="Courier New"]**sudo /usr/share/initramfs-tools/scripts/init-top/load_ata_piix**
[/FONT]
5.Now rebuild initrd using
$ [FONT="Courier New"]**sudo update-initramfs -u -k all**
[/FONT]

I encountered the same problem with my Dell Vostro 200 and I saw your unsolved question while looking for a solution. I found the above solution from *[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang)* and *[http://johnbokma.com/mexit/2008/08/05/fixing-the-vostro-hang-issue.html](http://johnbokma.com/mexit/2008/08/05/fixing-the-vostro-hang-issue.html)*. My computer has been working fine ever since.

---


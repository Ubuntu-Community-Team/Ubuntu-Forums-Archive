---
title: "Trouble launching Synaptic"
date: 2009-01-31
forum: x86 64-bit Users
---

### Post by mobs2000ontheweb on 2009-01-31
Hello, 

I installed ubuntu 64. 
I really like it, but i encounter the following problem when I try launching Synaptic. Here's the message I get : 
"
[COLOR="DarkOrange"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/COLOR]
"
Synaptic refuses to start.
So I run "sudo dpkg --configure -a", but then I encounter this problem : 
"
[COLOR="DarkOrange"]mike@genius-music:~$ sudo dpkg --configure -a
[sudo] password for mike:
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.22-14-rt (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
[COLOR="Red"]/usr/sbin/mkinitramfs: 13: getopt: not found[/COLOR]
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-rt
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-rt (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.22-14-rt:
 linux-ubuntu-modules-2.6.22-14-rt depends on linux-image-2.6.22-14-rt; however:
  Package linux-image-2.6.22-14-rt is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.22-14-rt (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-rt
dpkg: subprocess post-installation script returned error exit status 1[/COLOR]
"

Does any enlightened soul here know how to solve this issue ? 

Respect, 

michael.

---

### Post by mobs2000ontheweb on 2009-01-31
PS : 
I tried the solution to this thread : [http://ubuntuforums.org/showthread.php?t=550085]("http://ubuntuforums.org/showthread.php?t=550085")

namely, running : 

Code:

 sudo dpkg -i --force-all /var/cache/apt/archives/ udev_113-0ubuntu14_i386.deb

Code:

sudo apt-get install util-linux



but Synaptic is still not working !

Ubuntunian light appreciated, 

thank You very much, 

michael.

---

### Post by mobs2000ontheweb on 2009-01-31
PPS : After that, I upgraded Ubuntu and it is now working !

---

### Post by ATSC on 2009-04-02
A bit late to the party but I thought I'll add my step-by step solution for this problem anyway. It solves your problem without having to upgrade.

This happened to me as the update manager updated something and the pc crashed, resulting in a broken "util-linux"-package. The file "getopt" was missing.

For this recipe you need:

- a spare harddrive
- a USB-Stick (or any other removable drive)
- a Ubuntu live-cd (with the same Ubuntu version as your current one)

It goes like this:

1.: remove current HDD, install other HDD

2.: install new OS from live-cd onto spare HDD

3.: once that is working ok (ie, it booted!) copy the file /usr/bin/getopt onto a removable drive

4.: remove the spare HD and reinstall the original HDD

5.: launch into the livecd

6.: within the livecd, copy the file from the removable drive back to the location /usr/bin/ on the original hdd

7.: reboot and see whats happened


Addendum: You could do the copy back to the original hdd while it's running, as binaries aren't locked like they are in windows, but doing the writeback with the livecd is safer. Once you have done the copy back, you may have to reset the permissions on that file. it's  sudo chmod 755 /usr/bin/getopt. I have found that when moving things with a usb stick, sometimes the permissions don't move properly. especially if the usb stick is formatted FAT32. In my case I noticed later that another file ("getopt-long") from the same directory was missing. I've replaced that one, too.


Hope it helps. :)

---


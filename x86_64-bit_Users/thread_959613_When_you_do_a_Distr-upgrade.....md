---
title: "When you do a Distr-upgrade...."
date: 2008-10-26
forum: x86 64-bit Users
---

### Post by binskipy2u on 2008-10-26
will it keep system wide tweaks you may've done?
such as swappiness, hard drive tuning, boot speedup tweaks, etc etc..??

and does anyone know if the boot/system/hd/ misc speed tweaks for hardy "WILL" work for Intrepid too?

or is the underlying system , being linux, pretty much the same and the same system tweaks will work?

thanks

---

### Post by Kilz on 2008-10-26
In my experience, no, and usually its the customization and tweaks that make upgrades fail or cause head aches. Thats why a clean install is a good idea to someone having a bad upgrade experience.

---

### Post by binskipy2u on 2008-10-26
will these tweaks that i've used for hardy work for intrepid..
**********
Description
You want your Ubuntu desktop to be more responsive? It will take less than a half hour to perform all these tweaks. These tweaks will make your system faster and more responsive without a doubt. Read on to perform the tweaks and enjoy your faster system.

From what I understand these tweaks will work with all forms of Linux. They are not Ubunut Specific. I have only tried them on Ubuntu though, so if you use them on other Linux Distro’s you do at your own risk.

Speed up your File System

About
Ubuntu Linux, unless you have set it up otherwise, uses the EXT3 system by default. It’s a pretty good system. There are 3 journaling methods for EXT3 system.

    * Journal Data Writeback
    * Journal Data Ordered
    * Journal Data

By default Ubuntu chooses “journal data ordered”. In data=ordered mode, ext3 only officially journals metadata, but it logically groups metadata and data blocks into a single unit called a transaction. When it’s time to write the new metadata out to disk, the associated data blocks are written first. data=ordered mode effectively solves the corruption problem found in data=writeback mode and most other journaled filesystems, and it does so without requiring full data journaling. In general, data=ordered ext3 filesystems perform slightly slower than data=writeback filesystems, but significantly faster than their full data journaling counterparts.

To speed it up, we are going to change it to the data=writeback system.

Tweak

    * Open your Grub boot menu.

   1. sudo nano -w /boot/grub/menu.lst

    * Look for the ”Defoptions” and ”Altoptions” and make them look like the entry below.

   1. # defoptions=quiet splash rootflags=data=writeback
   2. # altoptions=(recovery mode) single rootflags=data=writeback

    * You need to update your Grub since you have altered it.

   1. sudo update-grub

    * Now we are going to edit the Fstab because it will be expecting these options.

   1. sudo nano -w /etc/fstab

    * Now you are going to want to add the ”(data=writeback and noatime=0)” flags to your hard drive. It might be a little confusing because of the new naming system. Look for the ”(,errors=remount-ro)” and add it afterwards to make it look like our example.

   1. defaults,errors=remount-ro,data=writeback,noatime 0

    * Now you tell your system to use them both.

   1. sudo tune2fs -o journal_data_writeback /dev/''yourdrive''

And you’re done.

Concurrent Booting

About
Concurrent booting allows Ubuntu to take advantage of dual-core processors, as well as processors that hyperthread or multithread or what ever the different companies call it now.
Tweak

    * These settings are located in your /etc/init.d/rc file. Lets open it up.

   1. sudo gedit /etc/init.d/rc

    * Look through the file and you will find ”CONCURRENCY=none”. You want to change it to:

   1. CONCURRENCY=shell

And you’re done.

Swapping

About
Swappiness takes a value between 0 and 100 to change the balance between swapping applications and freeing cache. At 100, the kernel will always prefer to find inactive pages and swap them out; in other cases, whether a swapout occurs depends on how much application memory is in use and how poorly the cache is doing at finding and releasing inactive items.

The default swappiness is 60. A value of 0 gives something close to the old behavior where applications that wanted memory could shrink the cache to a tiny fraction of RAM. For laptops which would prefer to let their disk spin down, a value of 20 or less is recommended.

Tweak

    * First we have to gain access to your /etc/sysctl.conf file.

   1. sudo gedit /etc/sysctl.conf

    * Just scroll to the bottom of the page and add the tag listed below. The number you want depends on how much ram you have and what you do with your system. Please read the about above this to make your decision. I have mine set to 0 on a dual core laptop with 1 gig of ram and have seen no issues and a good performance gain.

   1. vm.swappiness=0

And you’re done.

Broadband Internet

About
These are various tweaks taken from various places. Here is an article that explains them all if you would like to read it in depth.

Tweak

    * You have to open your /etc/sysctl.conf file back up again.

   1. sudo gedit /etc/sysctl.conf

    * Then again, scroll to the bottom and just add these lines to it.

   1. net.core.rmem_default = 524288
   2. net.core.rmem_max = 524288
   3. net.core.wmem_default = 524288
   4. net.core.wmem_max = 524288
   5. net.ipv4.tcp_wmem = 4096 87380 524288
   6. net.ipv4.tcp_rmem = 4096 87380 524288
   7. net.ipv4.tcp_mem = 524288 524288 524288
   8. net.ipv4.tcp_rfc1337 = 1
   9. net.ipv4.ip_no_pmtu_disc = 0
  10. net.ipv4.tcp_sack = 1
  11. net.ipv4.tcp_fack = 1
  12. net.ipv4.tcp_window_scaling = 1
  13. net.ipv4.tcp_timestamps = 1
  14. net.ipv4.tcp_ecn = 0
  15. net.ipv4.route.flush = 1

    * You have to reset your sysctl for these to take effect.

   1. sudo sysctl -p

And you’re done.

IPv6

About
IPv6 is an internet protocol. Most of your software uses IPv4 though and it causes conflicts.

Tweak

    * We are going to create a file. Paste this into a terminal.

   1. sudo gedit /etc/modprobe.d/bad_list

    * Then paste this into the file and save and exit the file.

   1. alias net-pf-10 off

And you’re done.

Boot Profile

About
You have just made a lot of changes to your system. Re profiling your boot will reorganize it and make it faster on boots afterwards.

Tweak

    * Reboot your PC.

    * When you come to your grub list, hit escape to see your grub menu.

    * Edit the topmost line and add the word below to the end of it.

   1. profile

    * Then just reboot the system.

And you’re done.

Free More Memory

About
We’re going to free up more RAM by disabling some virtual consoles that use up memory even though most people never use them. To do that, we need to edit the inittab file in the /etc directory.

Tweak

    * Open your inittab file.

   1. sudo gedit /etc/inittab

    * Scroll down until you find the six lines that begin with:

   1. 1:2345:respawn:/sbin/getty 38400 tty1

    * Comment out the last four lines by adding the hash or “#” symbol in front of them
    * Save the file.

And you’re done.

Make OpenOffice Faster

About
To make OpenOffice snappier, you can adjust the way it uses memory.

Tweak

    * Launch the OpenOffice word processor.
    * Go to the Tools menu and select Options.
    * Select “Memory” on the left panel.
    * On the right side of the panel, reduce the number of Undo steps to a figure lower than 100. I suggest 30 or 20 steps, just to be safe. I don’t think I’ll have to undo more than that many commands.
    * Under graphics cache, set “Use for OpenOffice.org” to 128 MB, memory per object to 20MB, and set the number of objects under “Cache for inserted objects” at 20.

And you’re done.

Get Faster Menus

About
You can make menus more responsive by telling Ubuntu to zero-delay them.

Tweak

    * Open a new document in gedit and past this line into it:

   1. gtk-menu-popup-delay = 0

    * Save the file in your home directory (/home/your-user-name) under this name:

   1. .gtkrc-2.0

Now you are done and you can enjoy your faster Ubuntu System.
****************

they've made a HUGE difference from my default install... what do you (or anyone reading this) think?

---

### Post by Sef on 2008-10-28
>  		will these tweaks that i've used for hardy work for intrepid..

Impossible to say unless someone has the exact same hardware specs and set up as you.

---


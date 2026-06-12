---
title: "[SOLVED] /dev/md0 does not exist"
date: 2007-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by PaulRSte on 2007-08-02
**This post is related to the Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/128313](https://bugs.launchpad.net/bugs/128313) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				System is based on an ASUS M2NPV-VM board with a 2GHz dual core Athlon 64 and two 500GB SATA Deskstars and running 64-bit Feisty and Mythtv.  I have attempted to convert this to RAID1 after installation following the procedure as outlined at [http://www.debian-administration.org/articles/238](http://www.debian-administration.org/articles/238).  As outlined in the bug report, the process worked to the point of loading on software raid with just partitions from sdb in the array.  Since I added the partitions from sda to complete the mirror the system fails to load from raid and gives the following EM:-

check root = bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT: /dev/md0 does not exist. dropping to a shell

After a long pause it eventually drops into the busybox

Device md0 never becomes available but all partitions on both sda and sdb are detected ok.

I can only access the array by loading from the LiveCD and then doing

sudo apt-get install mdadm

and specifying "all" partitions in the auto config.  Both raid devices are then available.

Can anyone help please?

---

### Post by Midahed on 2007-08-02
Not sure I can really help - I'm very new to Linux myself.  However, I did spend about a week getting raid 1 working on Feisty 7.04 workstation  just recently.  In case it helps you, my struggles are documented here [http://ubuntuforums.org/showthread.php?t=504463](http://ubuntuforums.org/showthread.php?t=504463) :)

Presumably if you can boot off your 'half-raid' on sdb you are managing to load the raid-related modules at boot time - so there isn't a problem with your initrd.

How does your motherboard work in terms of boot devices?  Having installed sda is it now attempting to boot from that drive rather than sdb (which was working before sda became available)?

I think I'd be looking into how the boot process has been affected by the introduction of sda.  I'd also be checking UUIDs in mdadm.conf - that was an area that tripped me up when I was getting it working on my system.

Hope this helps.

Mike

---

### Post by PaulRSte on 2007-08-03
Thanks for the response Midahed.  I saw this a while ago and couldn't see anything that was too much different to what I had already done but I had a full day to have a go at it today.

I haven't been able to boot from the array at all since I added the second half of the array mirror, I've only been able to boot from the live cd and by installing mdadm into this, gaining full access to the raid array.

The problem at this point has been that the installed software was at kernel 2.6.20-16 and the live cd at 2.6.20-15.  I am thus unable to load on the version of kernel that I really need.

There were a couple of items in KingJohn's article "Convert Root System to Bootable Software RAID1" - adding

md
raid1

to /etc/modules and /etc/mkinitrd/modules.  I did both of these but was still unable to create a new initrd.

It then dawned on me the second time through that when I installed mdadm after rebooting from the live cd again, after the auto configure, it creates a new initrd using "update-initramfs".  OK, so this is at 2.6.20-15 but it should have all the modules it needs.

I mounted /dev/md0 on /mnt, renamed the existing generic initrd, and copied the new one across.  I then edited /boot/grub/menu.lst to load the new image and /etc/fstab to remove UUID references from the root and /home partitions and rebooted.

Unbelievably, it actually loaded so thanks very much for concentrating my mind in that direction.  Only one problem now - how do I get back to 2.6.20-16?

---

### Post by Midahed on 2007-08-03
Good.  I've found so many times myself that it helps to outline a problem and just have someone else look at it from a different perspective - even if it's a complete newbie like me :)

So if I've understood you correctly, you now have a working raid1 system but an initrd/kernal that's not based on the latest and greatest? 

I'm so new to this environment that I have no idea how kernel updates are released or installed!  I'm sat here awaiting the announcement of the next kernel update with interest and some trepidation!  It seems to be something that causes problems, especially in raid environments, so I'll be doing a major backup before installing one of those! :)

I'm guessing here, but you still have a copy of 2.6.20-16 on your hard drive, albeit without the raid modules?  I'm not that familiar with the initramfs-tools package - I just learnt enough to be able to rebuild my initrd successfully, but now that you have a working system can't you run update-initramfs against the original  2.6.20-16 files or can it only ever work against the _running_ kernel?

Alternatively, if you were to download a new copy of the live CD, would you expect that to reflect the latest ( 2.6.20-16) kernel?

Just some random thoughts....

Mike

---

### Post by PaulRSte on 2007-08-04
Mike

Starting at the 2nd paragraph:-

Yes, you understood correctly :)

Kernel updates are issued just like anything else, via the apt-get interface or by accepting the updates available when you log in.  It's an interesting point as to how it works in a raid environment but perhaps consideration of how it works anyway is worthwhile.

What I'm getting at is how does update-initramfs work?  Does it use the version of Kernel that you are loaded on or does it use the latest version of Kernel on the system.  If it was the former then you would have to reboot onto the new kernel before running update-initramfs; but you wouldn't be able to boot on the new kernel because you hadn't yet created the new initrd file by running update-initramfs.  It therefore has to be the latter so I think your suggestion of just running this on my system should work.  I'll try this and let you know - will be Monday now I think.

Regarding downloading a new copy of the live cd, I suspect that this hasn't been updated as the update process to 2.6.20-16 was almost transparent.  As a matter of interest was your live cd at -15 and what version are you at now? (uname -r).

Cheers - Paul

---

### Post by Midahed on 2007-08-04
Hi Paul,

I just had a look at man update-initramfs and learnt something!  The -k switch allows selection of the image to use - the default behaviour is to use the latest version.

Presumably as you now have a working raid1 system based on -15, you should be able to force a kernel update via Synaptic or update manager?  You should then be able to boot-up via the menu.lst options and select the old kernel, run update-initramfs against the new kernel, tweak the content of menu.lst and reboot into your new initrd and kernel.

Sounds easy, doesn't it.  I'll leave it to you to do the testing, though! :)

To what extent, I wonder, does initrd have to 'match' the kernel?  It is, after all, just an intermediate step in the boot process.  Hopefully in the case of most updates, the new kernel will not be so different as to render the existing initrd unusable.  If that's the case, the new kernel arrives, the system is re-booted to load it, the existing initrd still works so the system boots off the raid normally.  At that point a really smart update process would rebuild initrd to get it completely in line with the new kernel, but I suspect we may have to manually run update-initramfs to achieve this.

Either way, as I said earlier, I'll be doing some serious backups before the next kernel update in installed!

On that subject, having looked through my notes, my system _was_ originally built on -15 and was updated to -16 _before_ I switched to the raid1 environment.  I'd removed all the earlier kernel references from menu.lst and had forgotten about them until now.  The uname -r command confirms that I'm currently on -16.  My installation CD is therefore probably the same as yours, i.e. -15

I'll be really interested to know how you get on - it will effectively tell us how we'll have to address all the kernel updates in the future.

Hope this makes sense (but it probably doesn't!).

**[EDIT]**  Having re-read my post I think I'd stick with the suggested procedure in paragraph 2.  In retrospect it sounds much safer to me.  It may be very risky to assume that an existing initrd will just happen to work with a later kernel.  It might work, but equally it might not.  And, of course, if it's the latter you'd then have to resort to the live CD or SystemRescueCD to get the system running again. :(

Mike

---

### Post by PaulRSte on 2007-08-06
Mike

Thanks once again for the pointers.  I just ran 

> root@PVR-1:~# update-initramfs -k 2.6.20-16-generic -c -t 

 as I already had the latest Kernel on board.  The previous version of the file was created using the initrd tools so I wasn't worried about losing this.  The system now boots ok on 2.6.20-16.

Also I had put a "sleep 10" into /usr/share/initramfs-tools/init which was getting round the problem with the raid not being assembled in time, so the mount=break is no longer required and the system boots without intervention.

I then remembered that I had seen that there was a fix to this problem anyway (I didn't think this relevant at the time as I wasn't getting that far anyway) so have commented the "sleep 10" line out as well and the system still boots ok.

I can now get on with the serious stuff :popcorn:

Thanks again.

Paul

---

### Post by Midahed on 2007-08-06
Good - all sorted out, and the bonus is that I feel far less nervous about the next kernel upgrade :)

I didn't know that the race condition problem with the raid not being ready had been fixed - I subscribed to the mailing list on launchpad for that bug but haven't seen anything... :confused:.  

Anyway, if that's the case, that's good - I'll be able to take the break=mount and quiet=n entries out of my menu.lst file.

Mike

---


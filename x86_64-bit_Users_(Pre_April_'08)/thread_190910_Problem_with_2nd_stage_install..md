---
title: "Problem with 2nd stage install."
date: 2006-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by ebeyer on 2006-06-06
OK.

So now I'm trying to install breezy on my iMac G3/233.  I think I asked it to erase the whole hard drive, an 80 Gb I installed several months ago.  The installer created two partitions and installed the operating system without any errors.  It popped out the installation CD and reset the iMac.

On reset, I get the yaboot greeting (Welcome, version 1.3.13 ...) and press ENTER.  It says:

Please wait, loading kernel.... (long wait)
/pci@800000000/mac-io@10/ide@200000/disk@0:3,/boot/vmlinux: Input/output error
boot:

Anything I put at this point comes back with "loading kernel" and then nothing.

Where did I mess up?

More to the point, what can I do about it?

Again, advance thanks for any guidance.

EB

Addendum:

My partitions are currently configured thus:

IDE1 master    (hda)   - 80.0GB ST380013A
#1        32.3 kb                  Apple
#2        1.0 MB        boot     Untitled
#3       79.7 GB       ext3      Untitled         /media/untitled
#4     282.3 MB        swap    swap             swap

I don't know if this matters.

---

### Post by ebeyer on 2006-06-07
I tried installing and completely erasing the hard drive.  The stage 1 installation seemed successful, as before, with no errors.  The system resets itself, placing me ultimately in front of the 'boot:' prompt.  If I hit enter, 'Linux' or 'old' I get "input/output error".  If I try again, the system stops responding.

Am I doing something wrong?  Is this install salvageable?

I can boot up into breezy live, but the OS there cannot access any of the new partitions I have created.  The disk utility seems unable to enable the partitions either.  So it seems as though I won't be able to change any of my configuration files or do anything useful with the system I just installed.

Any guidance at all will truly be appreciated.

---

### Post by ebeyer on 2006-06-07
So now I've tried installing with Debian (netinst) disk and am having the same problem.  There's a one line blurb on the YDL site ([http://www.terrasoftsolutions.com/support/hardware/breakdown/index.php?hw_cat_id=5](http://www.terrasoftsolutions.com/support/hardware/breakdown/index.php?hw_cat_id=5)) which mentions having to have a 100 Mb partition before the / partition to get the system to boot.  I tried to do just that but ran into the same problem.

---

### Post by ebeyer on 2006-06-07
So I think I solved the problem.  With help from YDL and Debian, as it happens.

Debian has this netboot installer that gets me to the 2nd stage of the install much faster.

This gave me the opportunity to play around with partition settings more easily.  What I ultimately wound up doing was creating two partitions - (1) NewWorld boot partition (100.0 Mb) (2) Another random ext3 partition (100.0 Mb) with mount point set to /boot , my main partition - an ext3 - (~76 Gb) with mount point set to / and a swap partition.  The installer also makes an Apple bootstrap partition at the very beginning automatically.  I didn't mess with that.

Anyway, it went on to the second stage with no problem.  

I'm a total newbie, so I'm not sure how to make this issue and its solution generally known aside from making this post.  

Again, any advice is truly appreciated.

EB

---


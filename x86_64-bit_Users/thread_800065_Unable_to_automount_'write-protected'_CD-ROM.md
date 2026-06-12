---
title: "Unable to automount 'write-protected' CD-ROM"
date: 2008-05-19
forum: x86 64-bit Users
---

### Post by Bataille23 on 2008-05-19
Details:
mount: block device /dev/scd0 is write-protected, mounting read-only mount: wrong fs type, bad option, bad superblock on /dev/scd0, missing codepage or helper program, or other error

dmesg | tail gives me the following:

[ 1722.319704] hfs: can't find a HFS filesystem on dev sr0.
[ 1746.493085] cdrom: sr0: mrw address space DMA selected
[ 1748.726152] hfs: unable to set blocksize to 512
[ 1748.726160] hfs: can't find a HFS filesystem on dev sr0.
[ 1957.212796] cdrom: sr0: mrw address space DMA selected
[ 1959.887697] hfs: unable to set blocksize to 512
[ 1959.887706] hfs: can't find a HFS filesystem on dev sr0.
[ 2068.038049] cdrom: sr0: mrw address space DMA selected
[ 2070.324921] hfs: unable to set blocksize to 512
[ 2070.324930] hfs: can't find a HFS filesystem on dev sr0.

I have no problem with CD-R/RW or DVD-R/RW discs, and I typically don't have problems with other out-of-the-box CDs/DVDs, etc.  
Also, when I try to mount it with Gmount-iso, I get this back: 

'You are not supposed to show G_IO_ERROR_FAILED_HANDLED in the UI'

Any help would be very, VERY appreciated!  If there's any additional info I can provide, please let me know!

Thanks!

---

### Post by Bataille23 on 2008-05-19
Just solved!  Sort of...turns out it was a Macintosh-only CD. :-S   Now the search for a Mac emulator begins.  I hope you get a good laugh out of this, because I am weeping.

---


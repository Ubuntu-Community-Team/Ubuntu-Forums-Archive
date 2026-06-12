---
title: "reiserfstune -l"
date: 2007-07-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by OldAlgis on 2007-07-11
Hi,

I want to label some existing partitions with reiserfs.  The tool for that is reiserfstune with -l to switch to label change or addition.  The man pages tell me that:
>  Note: At the time of writing the relocated journal was implemented for a special release of ReiserFS, and was not expected to be put into the mainstream kernel until approximately Linux 2.5. This means that if you have the stock kernel you must apply a special patch. Without this patch the kernel will refuse to mount the newly modified file system. 
Of course, the kernel is now 2.3.20.XX for kbuntu 7.04, which I use.  Currently on my new amd64 box ubuntu/kubuntu is the only Linux OS that functions flawlessly (Most of my Linux experience was with openSUSE until my switch to amd64).

Can someone tell me - warn or assure me - that the Note in the man pages is out of date for current kernel?  It would be rather disastrous if I could not mount my data or OS partitions, both of which are with reiserfs.

Alternatively, where can I find this "special patch" for reiserfs?  There is no indication in the man as to what is the name of the patch, if any.

I would be most grateful for any suggestions and thank you in anticipation.

---

### Post by dabl on 2007-07-11
Did you find reiserfstune in the repositories (i.e. with Synaptic or Adept)?  If so, it certainly should be safe to use on your system (that's what the repos are for, after all!).  :)

---

### Post by OldAlgis on 2007-07-11
>  dabl wrote:  Re: reiserfstune -l 
Did you find reiserfstune in the repositories (i.e. with Synaptic or Adept)? If so, it certainly should be safe to use on your system (that's what the repos are for, after all!).

I did not specifically install it - it was there with the basic system. Following your suggestion, I had a look at Adept and found one package with reiserfs - "reiserfsprogs". The description says that "This package contains utilities to create, check, resize, and debug ReiserFS filesystems", so it seems to cover part of reiserfstune capabilities.  

I think I will first test it on an empty partitions - give it a label and then mount it by label.  

Good suggestion, dabl - thank you!

---

### Post by OldAlgis on 2007-07-13
Just to close it - I did try reiserfstune -l <label> /dev/xxx.  It works OK. The warning in the man pages is obsolete and should be removed - it serves no good purpose, other than to distract users.

This closing note is simply for those who may be distracted by the obsolete note about the reserfstune. It seems to work fine with kernel 2.6.20-15.

---


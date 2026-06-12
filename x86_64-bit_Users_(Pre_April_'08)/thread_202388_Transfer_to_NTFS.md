---
title: "Transfer to NTFS?"
date: 2006-06-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Steve S. on 2006-06-23
Not sure where to post this one so, mod's, if you want to move me, please do so.

I am trying to set up a computer for my brother.  It is a dual boot, two seperate hard drives, each formatted for the maximum size, one XP and the other Ubuntu.  

I set up the dual boot because he uses a fricking Sony sonicwave mp3 player that will do nothing without the software in XP.

Here is the scenario: he has mp3 files on the Ubuntu drive, and we want them in the XP drive.  Here is the question: is there a way to transfer the files to the XP drive from the Linux drive on a regular basis so that he can put these files onto his mp3 player?  I heard something about an experimental NTFS deal...something like that?

Please help.  Still putting the computer together and he doesn't know about it yet, so I can do anything with the drives or whatever that I need to.

What does everyone recomend?

---

### Post by x64Jimbo on 2006-06-23
You heard experimental like "cutting edge," but in this case, the NTFS write support is experimental like "I designed a nuclear reactor out of paper clips. Let's test it!"
Three words:
DON'T DO IT
It's extremely likely that you'll fubar the entire filesystem.
I recommend making your Linux filesystems ext3 and then using this program in windows to access your Linux filesystems:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by jeepsnlinux on 2006-06-23
NTFS write support for Linux is there, but sketchy at best (AFAIK).  Last I heard write support on NTFS only allowed for the modification of present files, not the creation of new.  Someone correct me if I'm wrong...

The best idea is to use a FAT partition to share between the two.  Both OS's have great support for FAT, and the only downside is the max file size of ~2 GB (if that's a problem for you).  I've had this type of setup for close to a year now and it works great.  --> 160Gb HD, split into 20 GB NTFS for XP, 10 GB ext3 for Linux /, 10 GB FAT for /share, and the rest ext3 for /home.  This is just my preferred setup, others may suggest something different (partition sizes can be changed to whatever you want).

The next best thing about this setup is that Open Source apps that run on both Windows and Linux can be setup to share the same config folders, i.e., Firefox, Thunderbird, Gaim, etc...this way you always have the same bookmarks, etc.

EDIT:  The above suggestion would also work well.  I knew ext2(3) support for Windows existed, but wasn't sure how far along it was.

---

### Post by Steve S. on 2006-06-23
Oh, yeah...both ideas are great, and I'll check out each.  Thanks for the quick responses!

Couple of questions:
1. I already have the os's set up.  How can I add another fat partition after the fact?
2. How do I know what type of filesystem I have in Linux?  If it's ext2, then can/how do I change it?

---

### Post by Kilz on 2006-06-23
[QUOTE=x64Jimbo]You heard experimental like "cutting edge," but in this case, the NTFS write support is experimental like "I designed a nuclear reactor out of paper clips. Let's test it!"
Three words:
DON'T DO IT
[/QUOTE]
OMG that was one of the most funny things I have read in a long time. "I designed a nuclear reactor out of paper clips. Let's test it!" lol in still laughing.

---

### Post by jeepsnlinux on 2006-06-23
[QUOTE=Steve S.]

2. How do I know what type of filesystem I have in Linux?  If it's ext2, then can/how do I change it?[/QUOTE]

Type:
```
cat /etc/fstab
```

Look for the line that has only a single /  under <mount point>.  This indicates your root partition for linux.  The next column, <type>, will tell you what type of fs it is.

I've never had to/desired to change an fs in Linux, so I can't answer that one.  The same goes for resizing/adding.

---

### Post by Steve S. on 2006-06-23
[QUOTE=x64Jimbo]You heard experimental like "cutting edge," but in this case, the NTFS write support is experimental like "I designed a nuclear reactor out of paper clips. Let's test it!"
Three words:
DON'T DO IT
It's extremely likely that you'll fubar the entire filesystem.
I recommend making your Linux filesystems ext3 and then using this program in windows to access your Linux filesystems:
[http://www.fs-driver.org/](http://www.fs-driver.org/)[/QUOTE]

> Type:
Code:

cat /etc/fstab

Thanks, all.  I checked it out: it's ext3.  That's good, yeah?  I try this fs-driver thing and see what we got goin' all.  Thanks again for the quick replys.

---

### Post by Steve S. on 2006-06-23
Wow...very straightforward...very simple.  Worked perfectly!  Thanks all!

---

### Post by Steve S. on 2006-12-01
Well, this thread has been dead for many months, but I'm afraid that I have to rejuvinate it.

It has been working great, but Winbloze, as it does, decided that it wasn't going to work suddenly.  Now, whenever I (from Windoze) click on the Linux drive that I want (the ext.3 drive) it says, "This drive is not formatted.  Would you like to format it now?"  All I can think is, "NO!!  I don't want to format it you @#$W@#$ Windows drive!!"

I reran the Ext.2 exe file after redownloading it (just to be sure) to no avail.

Any advise?

---

### Post by blitze on 2006-12-01
Don't know what the issue with NTFS is under Linux.  I'm using the NTFS-3G driver and it has been nothing but stable for me.  Been transfering videos from ext3 to ntfs and back with no problems what so ever.

Don't get to paranoid like some here.  If you are worried then backup your data before using your ntfs partition under Linux.

---

### Post by RAOF on 2006-12-01
Yeah, just in case anyone else comes in and sees that:

NTFS support on linux **used** to be flacky.  A couple of years ago, the read/write driver would regularly kill NTFS partitions.

That driver is **no more**.  The new NTFS drivers (both the kernel and NTFS-3g drivers) were rewritten **from scratch** and there have, as of now, been **no reports** of them killing data.  The new drivers either **write safely** or will not write if there's a chance that they'll break something.  The current NTFS support is **almost** totally safe.

---

### Post by Steve S. on 2006-12-02
> **blitze said:**
> Don't know what the issue with NTFS is under Linux.  I'm using the NTFS-3G driver and it has been nothing but stable for me.  Been transfering videos from ext3 to ntfs and back with no problems what so ever.

Don't get to paranoid like some here.  If you are worried then backup your data before using your ntfs partition under Linux.

I have a dual boot.  In Ubuntu, I can read my Windoze drive just fine (not write).  I am open to suggestions, perhaps on how to write to this drive if I can't get Winbloze to read my Ubuntu drive.

I have been able to do read my Linux drive from Windows up to this point, but it suddenly failed.

Please advise.

---

### Post by Aega on 2006-12-05
> **Steve S. said:**
> I have a dual boot.  In Ubuntu, I can read my Windoze drive just fine (not write).  I am open to suggestions, perhaps on how to write to this drive if I can't get Winbloze to read my Ubuntu drive.

I have been able to do read my Linux drive from Windows up to this point, but it suddenly failed.

Please advise.

Did you try using the fs-driver program to unmount and remount your linux partition in windows? Perhaps to another drive letter? I had a problem once where it suddenly decided to mount the wrong partition of my linux drive (so it attempted to mount my swap partition instead of my actual linux partition). So I guess just make sure you're mounting the right partition.

Also, don't be afraid to try ntfs-3g ([http://www.ntfs-3g.org/]("http://www.ntfs-3g.org/")). I've been using it for about a month now and it's working really well. There are a couple of minor bugs in it for extreme cases, but I understand they're working on them. (One in particular I encountered was when I had forgotten to set the locale and files that had filenames with accents on vowels were not showing up).

---

### Post by Steve S. on 2006-12-05
> **Aega said:**
> Did you try using the fs-driver program to unmount and remount your linux partition in windows? Perhaps to another drive letter? I had a problem once where it suddenly decided to mount the wrong partition of my linux drive (so it attempted to mount my swap partition instead of my actual linux partition). So I guess just make sure you're mounting the right partition.

Also, don't be afraid to try ntfs-3g ([http://www.ntfs-3g.org/]("http://www.ntfs-3g.org/")). I've been using it for about a month now and it's working really well. There are a couple of minor bugs in it for extreme cases, but I understand they're working on them. (One in particular I encountered was when I had forgotten to set the locale and files that had filenames with accents on vowels were not showing up).

I did remount it, but didn't use a different letter, and it wasn't the swap.  But I may try it again...takes all of 15 seconds or something.

May try the other if that doesn't go.  Thanks!

---

### Post by Steve S. on 2006-12-14
Upgraded to Edgy, it works again...perfectly.

I'll take it!

---


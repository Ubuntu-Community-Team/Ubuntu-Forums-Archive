---
title: "[SOLVED] mkfs.ext3 -m 0 but still missing harddrive space"
date: 2008-03-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Don Giovanni on 2008-03-01
I've tried looking around, but I haven't been able to find an answer to this.

I recently removed an NTFS partition from one of my external drives and switched over to ext3 (as there are drivers for allowing both OSX and Windows to read ext3).
After deleting partitions I used this command to setup my drive with one big ext3 partition:

sudo mkfs.ext3 -m 0 -L eSata -M eSata /dev/sdc

From the Ubuntu desktop if I pull up the drives properties it says the total capacity is 458.5GB.  If i format the same drive with NTFS or ReiserFS it will show a total capacity of 465.7GB (which is what I would expect).

I am already using -m 0 so there shouldn't be reserved space for root.  Where is the other 7.2GB of drive space going?

---

### Post by kidders on 2008-03-02
Hi there,

The "missing" space could be going a number of places. One possibility that occurs to me is your filesystem journal. I don't use Ext3 very much, but I managed to dig up a 100GiB filesystem to take a look at. It's journal was using about 0.15% of the  available storage space. I have no idea if it's reasonable for yours to take up 10 times that much room ... all mke2fs's man page says about the subject is that, by default, it creates "an  appropriately sized journal (given the size of the filesystem)". At the very least though, I'd say your journal accounts for *some* of the space not being used for storage. I'd be surprised if yours and mine differed by a factor of 10, but the only way to be sure is to check, I suppose.

There are other places for space to go, but this post would get very long if I went through them all!

In any case, even if you do manage to identify exactly where every last byte of the unusable space is going, I can't say it matters very much. Taking the mkfs command you used as an example...

Depending on your settings, the command assumes an average file size of about 2 4kiB blocks, giving you enough inodes to store about 65 million files. Even assuming you only store a tenth that many (ie you've allocated 10 times more inodes than you really need), and only half of those miss the block boundary a few bytes, the amount of disk space you'll have lost by the time the filesystem fills up will be nearly double the few gigs you're chasing now. Once you start taking things like fragmentation into account, that number gets even bigger.

Anyhow, the point is not to worry too much. Different filesystems do their housekeeping in different ways, but the amount of space you actually get to use in the end is always far smaller than what you started with.

By the way, just for future reference, this post is in the wrong forum. It's generally a good idea to post threads where they belong ... you'll tend to get faster (and better) responses that way.

---

### Post by Don Giovanni on 2008-03-02
hey thanks for the reply, although I didn't think it had anything to do with me being in 64bit, I posted here anyways.

From what your saying it sounds like their isn't much more I can do with ext3 to optimize my disk usage and the value of useable storage space when formated as NTFS/ReiserFS, although appearing larger might end up being about the same due to other factors?  Up until more recently I had never given file systems that much consideration.

I guess I'll just leave it as is. Thanks for the info.

---

### Post by kidders on 2008-03-03
No problem. :-)

For most people, performance is the priority, more so than space usage efficiency. They're almost always competing concerns though ... improving one very often trades off against the other. My tendency is usually to waste space, where doing so results in a performance gain.

Anyhow, in answer to your question regarding NTFS vs ReiserFS vs Ext3, it's very difficult to give specific recommendations without knowing more about what you want to do with your filesystem. For example, ReiserFS is by far the most storage-efficient of the three, but only for specific applications, where file sizes tend to be quite small, and at the cost of performance and compatibility with certain things (eg bootloaders). NTFS is usually a bad choice, given its propensity for wild fragmentation, lack of support for unix style permissions management, and a poor support on non-MS operating systems. Of the three, Ext3 probably performs best in RAID environments, but has a number of long-term disadvantages in areas like maintenance.

Those are just a few of the pros & cons of the three filesystem types you mentioned, to give you an idea. My advice would be to...
[LIST]
[*]Decide on your priorities ... eg speed vs recoverability vs efficiency vs reliability.
[*]Think about what will be on the filesystem ... eg very large media files, millions of tiny emails, etc. What you plan to do (eg more reading than writing, lots of deletion & creation of files) is also important.
[*]In many cases, people find that what they're looking for plays to the strengths of a particular filesystem. For instance, XFS supports absolutely gargantuan files, but performs poorly when creating & destroying large numbers of files, like might happen in /tmp or /usr/src.[/LIST]Many people find Ext3 just fine though. It's very old, very reliable, and a good general-purpose choice, with plenty of tweakability.

---

### Post by Don Giovanni on 2008-03-03
I had spent a good number of hours trying to read up on file systems, a lot of what I found was conflicting opinions (different needs as you say).  I ended up picking EXT3 for this external (eSata/USB) drive because I occasionally have to bring it to another location and transfer large amounts of data to WinXP and MacOSX boxes.

I was seeing issues with NTFS (as expected) and EXT3 seems to be the best supported for recovery tools and also readability, with use of third party drivers, on WinXP (as ext2) and MacOSX.  So I'll stick with it until I see reliable XFS support in OSX.

Thanks again.

---

### Post by kidders on 2008-03-04
Sounds good.

One other possibility is HFS+, which has native OSX support, and works well with Windows (via third pary software) & Linux too. There's nothing wrong with choosing Ext3, but I thought I'd mention HFS+ anyway.

---


---
title: "[SOLVED] When Hardy comes out..."
date: 2008-02-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by timzak on 2008-02-29
I currently have 64 bit Gutsy and a separate /home partition.  When Hardy comes out, can I install the 64 bit version to root, preserve my home, and have all my installed 64 bit apps work automatically?  Or will there need to be some tweaking or reinstalling of apps?

Just trying to prepare...

Thanks.

---

### Post by kaens on 2008-02-29
I would think that should work fine, at least in theory, but I wouldn't be surprised if you had to do some tweaking.

Then again, I'm not on the Hardy development team or anything, so I don't really know.

---

### Post by ajgreeny on 2008-02-29
You can certainly do most of what you are suggesting;  that's the major advantage of a separate /home partition.  However, any applications you've added to Gutsy, over and above the ones that come on the original CD installation disk, will have to be downloaded and installed again.  All or most of the configuration files will be in your /home partition so you shouldn't need to do too much tweaking, though a change of version of some applications may mean the configs are either not compatible or simply need complete updating etc.

---

### Post by gfg on 2008-02-29
If I understand your question correctly you simply want to update from gutsy to hardy? If that is what you want to do, then yes that is quite feasible. When hardy is released, you can update to it from the update manager. You will then keep all your apps, and can chose if you want to keep some of your old config files. There may occur some problems if you use this method, and thus it's always wise to wait a while before upgrading, and see other's experiences, before you upgrade.

---

### Post by timzak on 2008-02-29
Yes, I'd like to upgrade from Gutsy to Hardy.  However, I was thinking of installing on top of Gutsy manually, instead of Update Manager.  It doesn't seem like that much more work to just do a full reinstall, though.  My only real concerns with a reinstall from scratch is for VirtualBox.  I have some critical financial docs in a virtual OS and I'm not sure how VirtualBox will handle the upgrade.

So what's my best option?

1) Upgrade Manager

2) Manually install over existing install w/o reformatting my partitions

3) reformat and reinstall everything from scratch

---

### Post by Kilz on 2008-02-29
> **timzak said:**
> Yes, I'd like to upgrade from Gutsy to Hardy.  However, I was thinking of installing on top of Gutsy manually, instead of Update Manager.  It doesn't seem like that much more work to just do a full reinstall, though.  My only real concerns with a reinstall from scratch is for VirtualBox.  I have some critical financial docs in a virtual OS and I'm not sure how VirtualBox will handle the upgrade.

So what's my best option?

1) Upgrade Manager

2) Manually install over existing install w/o reformatting my partitions

3) reformat and reinstall everything from scratch


4) Clean install to a new partition keeping old one in place while you setup and transfer needed files.

Also, Backup, backup, backup anything you cant afford to loose.  Problems and mistakes can wipe out everything. Those that backup just in case can breath easily.
You might also want to wait a week after release to make sure any major issues that could lead to loss of data are found and fixed.

---

### Post by timzak on 2008-02-29
Thanks, Kilz.

I use Clonezilla to image my entire hdd (swap, /root and /home partitions), so I've got the backup covered.  Sometimes I just feel more satisfied with a clean, fresh install.  Especially with an LTS version, which I'm likely to keep for a couple of years, I want to start off as clean as possible.

I guess I just answered my own question!  I'll have to prepare ahead of time by backing up critical things, writing down installed apps, etc. (in addition to my imaged backup which would just serve to get me back where I was if the new install goes haywire).

Thanks everyone for your feedback.

---


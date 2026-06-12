---
title: "Backup - best method"
date: 2009-08-06
forum: x86 64-bit Users
---

### Post by niw_uk1964 on 2009-08-06
Right...to save me from myself, which is the best way of backing up my Ubuntu installation and data?

I know Rsync is a backup tool, but is this the recommended tool and what front end/gui should I be using with it? I have a Windows server that I want to keep my media collection in sync with.

TIA.

---

### Post by dlmarti on 2009-08-06
The best answer is don't.

Backup the /etc and /home, rely on the distribution for the rest.

Linux is not like Windows, its very easy to restore.

For backing up /etc and /home I use two tools:
1. "tar"  yeah I know its old, but its extremely robust and tolerant of moving around to different OS'es and machines.  "tar" will take care of most of your files, the stuff that isn't life or death.  Just put the tar-files onto different drives and different machines.

2. For the critical stuff, I use svn (in addition to the normal tar files).  I keep a local copy of the svn repository and do the day to day stuff to a different machine.  If you don't have a different machine, at least use different drives.

---

### Post by Clancy_s on 2009-08-06
There's no official recommendation.  I back up /home and /home/data (I made a seperate partition for data) to an external hard drive using grysnc as a graphical front end for rsync.

---

### Post by ShadowTek on 2009-08-07
> **niw_uk1964 said:**
> 
I know Rsync is a backup tool, but is this the recommended tool and what front end/gui should I be using with it? I have a Windows server that I want to keep my media collection in sync with.

Rsync is simple enough that there is no need for a front end.

For example:
```
rsync -n -av --delete --log-file=/home/user/Desktop/$(date +%Y%m%d)_rsync.log /media/SourceDisk/DirName /media/DestinationDisk/DirName
```I always use the "-n" option first, which does a dry run and prints to the log what it would have done otherwise. Remove that option to do it for real.

You have to be careful with the "--delete" option. It will remove any file on the distination disk that are not on the source disk, which is what you would want it to do if you deleted something from source and expect it to be removed from the destination as well. But it is *very important" to make sure that you don't confuse the source and the destination, or you would end up with a disaster. That is one reason I always do a dry run first.

---

### Post by mtinman on 2009-08-07
> **niw_uk1964 said:**
> Right...to save me from myself, which is the best way of backing up my Ubuntu installation and data?

I know Rsync is a backup tool, but is this the recommended tool and what front end/gui should I be using with it? I have a Windows server that I want to keep my media collection in sync with.

TIA.

TIA:

There is no "best way of backing up" an Ubuntu installation & data. It is a matter of personal choice. I personally use a Linux dedicated backup file server via ssh on my LAN, and use sbackup on my Linux client machines. 

sbackup is a gui which uses rsync & rdiff to allow for many different backup configurations, and is fairly simple to use.

At the very least, You will have to install ssh on your Windows server in order to make this work for you, and sbackup on the Linux client(s).

You may also want to consider using Samba instead, since your server is a Windows machine...

---

### Post by rudihawk on 2009-08-08
Personally I use Grsync -its really helpful! :)

---

### Post by Tanker Bob on 2009-08-08
As others have said, there's no need to back up your installation, only your data. You can recreate your installation by using:

```
dpkg --get-selections > ~/restore-install
```

This creates a record of all your package installations from repositories in the file restore-install in your /home directory. Backup your /home partition using Synkron, which is available in the repositories. To restore your system configuration, type:

```
sudo dpkg --set-selections < restore-install && sudo apt-get dselect-upgrade
```

You'll have to reinstall any programs that you manually installed before from outside the repository yourself. Then restore your data and settings from /home.

The best way to preserve your data and settings is to put your /home on a separate partition. That way, you can upgrade your system on the root partition as often as you like and keep your data and settings preserved. I started that way several years ago and have never had an issue in successive upgrades and full installations. I'm also pretty fond of Synckron as an additional safety measure for my data.

Hope this helps.

---

### Post by vegmunky on 2009-08-08
I just wrote [a related blog post]("http://thinkycrow.blogspot.com/2009/08/mozy-vs-spideroak.html") on this issue yesterday.  In the blog I discussed synchronizing between Windows and Ubuntu.  Not mentioned in the blog is that I'm synchronizing about 100GB of music files.

---

### Post by Padrig Leamhnach on 2009-08-08
I just downloaded the SpiderOak software, after reading about it in your blog, vegmunky. Seems to be working great so far. It's the first backup solution I've found that works with Ubuntu and Windows at the same time, and the software seems very nice.

---

### Post by mtinman on 2009-08-09
Also, you may want to try unison, it looks like something that may work for you...

---

### Post by guneza on 2009-08-09
Depending on your needs, there is an overlay to rsync called rdiff-backup which works great. We use it at the office, and I use it at home to perform local and remote backup. The great thing about rdiff-backup is that it relies on a file structure. 

Read more about rdiff-backup here: [http://rdiff-backup.nongnu.org/](http://rdiff-backup.nongnu.org/)

---


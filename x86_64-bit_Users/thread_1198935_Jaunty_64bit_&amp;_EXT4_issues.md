---
title: "Jaunty 64bit &amp; EXT4 issues"
date: 2009-06-28
forum: x86 64-bit Users
---

### Post by kami84gr on 2009-06-28
Greetings to everyone,
 
Just a small feedback since I'm new to these forums...
 
I've started using ubuntu 3 years ago and stayed with it for a whole year... after that I've switched to Fedora and then to Arch Linux and tried each one for a year also. I'm now finally back with Ubuntu and I've decided to stay for good this time since that is the distro for me.
 
Now to the main subject...
 
I'm running Jaunty 64bit with all of my partitions using the EXT4 file system.
As a file system it worked like a charm with ubuntu and it is quite faster than ext3 UNTIL I 've tried to copy a huge file (64 gigabytes) from an internal SATA2 disk to another one, both running with ext4.
 
The system was almost unusable and both disks where runniing like crazy but the transfer rate was crawling to death.
 
After explicitly killing the necessary processes (that was the only option) I've tried to copy a much smaller file around 4 gigabytes. Same result. I thought ok and then tried to start downloading a big torrent file (around 20 gb) and I had the exact same results.
 
That was quite a new behaviour of my system and I ended up believing that it was Jaunty to blame since I haven't had any problems with large files on my old ubuntu installation using ext3, and neither in my other 2 distros (fedora, and arch) which where using the new ext4 fs.
 
After a lot of testing with different mount options in fstab. I realised that the problem was infact with the kernel 2.6.28.xx version that ubuntu is running (both arch and fedora are running on 2.6.29.xx).
 
I wasn't very fond of the idea to install a newer kernel on my Jaunty to try it with (I've abandoned Arch because I got tired of such acrobatics). So after a LOT of searching I've found a way to remedy the problem (most of it at least).
 
The way to fix the issue is to mount all of your ext4 partitions with the **noatime** option and change the method the fs writes data from "**ordered**" to "**writeback**".
 
After that my system has been working great ...but not perfect...but I can live with a few problems with large torrent files until the karmic Coala reaches the beta level and see if they have fixed the issue.
 
**BE AWARE** that by doing all of the above it it possible to corrupt or lose your data in case of a sudden system termination (power cut , reseting the pc by pressing the reset button , etc.)
 
Basically you are making your ext4 fs to behave like an xfs fs as far as data integrity is concerned. (please don't rant on me... I know that this is an awful comparison).
 
I hope I've helped a little about that issue with ext4 and please forgive any language mistakes of mine because english is not my mother tongue.
 
Best Regards!:D
 
 
P.S. A nice guide for the actions I've mentioned above is this one. It is for the ext3 fs but applies for the ex4 as well....again...use with caution!!!
 
[http://ubuntuforums.org/showthread.php?t=107856](http://ubuntuforums.org/showthread.php?t=107856)

---

### Post by Arup on 2009-06-28
I have been running ext 4 on both Phenom and dual quad core machines, on the Phenom, I see this issue but not on the Intel.

---

### Post by kami84gr on 2009-06-30
> **Arup said:**
> I have been running ext 4 on both Phenom and dual quad core machines, on the Phenom, I see this issue but not on the Intel.

My pc has an Intel processor also but I do have that problem unfortunately, which as I said before I don't have it with Fedora and Arch on the same system.
So Im guessing it is a Distro specific problem and not a cpu one.

It is quite strange though that in your case the problem appears on different cpus.

Anyone else who has the same problems with large files and ext4 on Jaunty?

---

### Post by timzak on 2009-06-30
When I first installed Jaunty 64-bit I chose EXT4.  The main issue I noticed was with Firefox grinding the hard disk when I first opened it, and with Liferea grinding the hard disk like crazy with each feed I selected.  I did a search and found some known issue related to this (I can't recall now off the top of my head...xulrunner?)  My installation was new enough that I just reformatted and reinstalled with EXT3.  I'll probably revisit EXT4 in Karmic, but won't hesitate to switch back to EXT3 if I encounter any more problems.

---

### Post by krazykritter on 2009-07-01
I made a backup of Home before installing Kubuntu 64-bit and then copied the files over from an external USB drive once installed. At first the file transfer didn't take up a huge chunk of the processing power but as the transfer went on it became worse, as has been described. My install is on a laptop with an Intel Core 2 Duo T7100 1.8GHz with 4GB RAM. Looking at the way the machine behaves the other processes of the machine don't appear to be hindered as much as the video processing.

My video card is NVIDIA GeForce 8400M GT which has 256MB on-board.

---

### Post by kami84gr on 2009-07-06
I'm currently in the process of replicating the problem with as many scenarios that I can. I will post it as a bug once I have all the necessary data to back it up with ;)

---


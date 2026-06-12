---
title: "movieplayer youtube vids and mountpoints"
date: 2009-10-29
forum: x86 64-bit Users
---

### Post by ubuntubrian on 2009-10-29
I am running Karmic on my Toshiba Satellite-I love it! (Finally dumped the WUBI install and Windoze completely)
This isn't a big issue but when I search for youtube vids with Totem movieplayer I get some searching and then this error that has me totally baffled:

"ubuntu movieplayer Automount failed:mountpoint for org.gtk.vfs.mountpoint.http already running"

I don't know what it means or how to fix it!

Help?

---

### Post by mrmememe on 2009-11-01
I have the same problem on my fresh install of Ubuntu 9.10 Netbook Remix. I am unable to play any youtube videos in Totem due to this error. Anyone any ideas?

---

### Post by ubuntubrian on 2009-11-01
I found that quitting and restarting Totem didn't help but if I force quit it (or kill it) then the videos load up. they do not, however, play due to an ffmpeg bug: [https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/459423?comments=all](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/459423?comments=all)

Apparently ffmpeg can't play compressed swf files (did it ever, are these something new?) It's an upstream bug requiring a fix.

On the other mountpoint issue, I noticed a message when booting that refers to mountpoint problems but I haven't caught it yet as it goes by too quickly! Must be a Karmic bug

---

### Post by ubuntubrian on 2009-11-01
I rebooted and took a picture of the screen when I get the message. It is the first message that pops up:

"One or more of the mounts listed in /etc/fstab cannot be mounted:
/:waiting for /dev/disk/by-uuid/ea915446-2b36-4ba1-bcf6-ac766107fd58
/tmp:waiting for (null)
Press ESC to enter a recovery shell"

then the boot resumes normally.

So again, killing totem solves the mountpoint issue, don't ask me why, but I get the Gstreamer error about libraries that is apparently an ffmpeg problem.

---

### Post by ubuntubrian on 2009-11-01
After some checking it looks like the mountpoint issue is common with Karmic. there are many threads:

[http://ubuntuforums.org/showthread.php?p=8207267](http://ubuntuforums.org/showthread.php?p=8207267)
[http://swiss.ubuntuforums.org/showthread.php?t=1306009](http://swiss.ubuntuforums.org/showthread.php?t=1306009)

Seems the workaround involves editing grub or fstab which i am not about to do as my install boots fine after getting the message. Maybe it won't later but until there is an actual fix I'm sticking with this setup for now. I can watch the vids on youtube.

---


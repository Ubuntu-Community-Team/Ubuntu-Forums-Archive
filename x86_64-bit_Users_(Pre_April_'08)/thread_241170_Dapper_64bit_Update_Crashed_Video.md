---
title: "Dapper 64bit Update Crashed Video"
date: 2006-08-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by najames on 2006-08-21
Anyone else have a video crash after running updates today?   There were only a few packages installed, but I think one was related to Xorg.  I kind blindly took a quick glance, updated, rebooted and no longer have any working video.  I reran the setup and it seemed to find the Nvidia 6600 fine, I set resolutions, and all looked ok, but there still is no video.

Any ideas? 

The PC has been running Dapper fine for a couple months.  Tonight I installed Thunderbird, copied over email and addresses and was ready to have my wife start using it, rebooted and BOOM.

---

### Post by lenin on 2006-08-22
This happened to me as well. I don't know the details of the problem but I fixed it by going back to an older version of the xserver-xorg-core package.

Hope it helps.

---

### Post by sanzaborn33 on 2006-08-22
I also just did a fresh install of 6.06.1 LTS Dapper AMD64 and after the 3 new updates, one of which was the updated Xorg files, my system failed to boot the X-server upon reboot. That was a nice start to a fresh install! Working on a fix here. Probably have to go back to old X-server or something...

---

### Post by scatyb on 2006-08-22
the exact same thing happened to me.  I don't think I'm going to run any updates until it gets fixed.

---

### Post by Kilz on 2006-08-22
[Here is the solution.]("http://www.ubuntuforums.org/showthread.php?t=241254")

---

### Post by najames on 2006-08-22
Thanks for the link Kilz!!!  Just like my late great aunt would've said, "come on over here so I can give you a big hug and a smooch".  I'm puckering right now.

I was dreading the thought of loosing my single system drive, 4 disk raid5, and VMServer testbox.  I better wander over and thank the poster of the fix too!!

---


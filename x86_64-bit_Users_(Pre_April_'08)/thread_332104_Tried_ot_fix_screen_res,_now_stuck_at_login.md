---
title: "Tried ot fix screen res, now stuck at login"
date: 2007-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by The Iron Curtain on 2007-01-05
Hello,

I just built a computer and Installed Ubuntu 6.10 for AMD64. When I tried to change the screen resolution, the only options were 800x600 and 640x480. I prefer something larger than that. Here are my specs:
monitor:  AOC 9 GLrs 19 inch CRT Monitor
Graphics: ATI Radeon Xpress 200 (it's integrated into the northbridge)

So, I tried to install the drivers [from here]("https://help.ubuntu.com/community/RadeonDriver#head-8fa9267d9fa7b892fa1c394d49f4e645e197a797"), and I followed all the directions (except the part about wacom since I couldn't find it (and it said it was for cleaning up anyway). I edited the config file in Gedit (and backed up the old one), saved and restarted X. I then checked it as [per the instructions]("https://help.ubuntu.com/community/RadeonDriver#head-8fa9267d9fa7b892fa1c394d49f4e645e197a797") and here's what I got (I don't have access to my computer, so I'm telling you what I remember):
```
$ glxinfo | grep vendor
it was SGI. I checked and that was good.

$ glxinfo | grep "direct rendering"
No. It said that the open driver couldn't work.
```

Well, I did some searching and I found that HorizSync and VertRefresh weren't declared. As per [this post]("http://ubuntuforums.org/showthread.php?t=11337&p=632803"), I googled my monitor, found[ this site]("http://www0.shopping.com/xPF-Aoc-9-GLrs-19-in~r-1~CLT-INTR~RFR-www.google.com") that had this info:
```
 Synchronization Range - Vertical  	 50 - 150 Hz
Synchronization Range - Horizontal 	30 - 95 kHz
```

I changed the config file to say :
```
HorizSync 30-95 
VertRefresh 50-150
```

Then I restarted X. The login screen came up in a fine resolution. I logged in and, lo and behold, after loading, I was kicked back to the login screen. I tried several times and even restarted. 

Can you help?

Thanks!

---

### Post by The Iron Curtain on 2007-01-05
Uh...Wow. After I typed that whole this out on my laptop. I decided to try once more to login. it worked! I guess it just needed to me time. Maybe ghosts were haunting it :p

Anyway, I hope this problem doesn't happen again.

---

### Post by dannyboy79 on 2007-01-05
read what the error log states and post the results here. normally /var/log/Xorg.0.log. also take a look at your latest /home/username/.xsession-errors file. i have read many posts on the ati 200M graphics chip and all have been not good about it's support. have you gogled it? and followed the many different threads on getting it working? well, I did a quick search within this forum and found this: [http://www.ubuntuforums.org/showthread.php?t=326301&highlight=ATI+Radeon+Xpress+200](http://www.ubuntuforums.org/showthread.php?t=326301&highlight=ATI+Radeon+Xpress+200)

should do it for ya

---


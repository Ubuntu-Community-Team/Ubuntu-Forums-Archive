---
title: "MapleStory v62"
date: 2018-07-14
forum: Wine
---

### Post by johncintron on 2018-07-14
Hi all.

I've been trying to accomplish one thing for almost two weeks now and I feel like I've exhausted all options. This is the roadblock I'm facing: [https://ubuntuforums.org/showthread.php?t=1386675](https://ubuntuforums.org/showthread.php?t=1386675)

I've tried everything in that thread, along with the instructions here [http://forum.ragezone.com/f922/maplestory-v62-linux-wine-896880/](http://forum.ragezone.com/f922/maplestory-v62-linux-wine-896880/) and here [https://forum.maplelegends.com/index.php?threads/playing-maple-legends-on-a-linux-box-the-guide.5400/](https://forum.maplelegends.com/index.php?threads/playing-maple-legends-on-a-linux-box-the-guide.5400/) and here [https://mapleroyals.com/forum/threads/how-to-play-mapleroyals-in-linux-using-wine.22254/](https://mapleroyals.com/forum/threads/how-to-play-mapleroyals-in-linux-using-wine.22254/) These guides are pretty much identical, but with some small deviations.

I've even gone so far as to create a Windows 7 virtual machine where I confirm that MapleStory works and brute-forced pulled dlls from that VM image onto my Linux box. Thus far I've tried combinations of ws2_32.dll, ws2help.dll, and msdia90.dll. I had a strong suspicion of msdia90.dll because I essentially diffed the VM's filesystem before and after I installed VMWare Tools on it, without which MapleStory won't run.

For reference, I've tried this on all combinations of Arch, Debian Stretch, Ubuntu 18.04 using Wine 1.1.36, 1.4, and 3.12.

The error that I'm consistently getting is ```
Microsoft Visual C++ Runtime Library Runtime Error! abnormal program termination
```

Is there anybody else who has attempted this?

---


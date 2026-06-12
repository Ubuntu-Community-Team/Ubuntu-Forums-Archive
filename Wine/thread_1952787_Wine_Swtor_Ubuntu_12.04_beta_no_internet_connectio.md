---
title: "Wine Swtor Ubuntu 12.04 beta no internet connection ?"
date: 2012-04-05
forum: Wine
---

### Post by Nemesis2012 on 2012-04-05
i Found out was it was executing "echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope" Fixed it ty Christian 

[http://appdb.winehq.org/commentview....ThreadId=75939]("http://appdb.winehq.org/commentview.php?iAppId=11123&iVersionId=20882&iThreadId=75939")

in Ubuntu 12.04 beta it's not letting wine use my network has any one found a way around it? it Works just fine on ubuntu 11.10 11.04 and arch the Launcher opens i put in my pass word and hit login and it hangs i let it go for up to 15mins



```
  
File info: launcher.exe size=2527400, created=3/5/2012 20:12:37, accessed=4/4/2012 23:33:35, written=3/5/2012 20:12:37 
2012-04-04 22:37:23 INFO   -----------------------------(300)----------------------------- 
2012-04-04 22:37:23 INFO   SpecsHash=1592394536.1330505159 
2012-04-04 22:54:25 INFO   User presses exit - E:(false,Error Text) NE:(false,Network error. Check your internet connection) 
2012-04-04 22:54:25 INFO   Closed launcher

```

---

### Post by Nemesis2012 on 2012-04-06
i tryed to edit the /etc/hosts and Wicd [http://wiki.winehq.org/FAQ#head-f000601e2d4ad173587b19c8d2f097d6dfba8cbe](http://wiki.winehq.org/FAQ#head-f000601e2d4ad173587b19c8d2f097d6dfba8cbe) i'm going to keep trying intel i find a way to get it working

---

### Post by Nemesis2012 on 2012-04-13
Deleted

---


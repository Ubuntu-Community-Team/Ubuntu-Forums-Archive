---
title: "[Wine 2.8] - Trouble running a exe from path."
date: 2017-05-13
forum: Wine
---

### Post by MasterNetra on 2017-05-13
Trying to get a exe to run from path and the app (game actually) fails to launch (tries and fails), but if I cd to directory and run the exe it launches fine which is odd. I'm trying to get it right so I can launch from a .desktop, but I dunno wth is going on with it.

Tried Running
```
 wine /home/<CENSORED>/.wine/drive_c/Program\ Files/Monster\ Girl\ Quest\ -\ NG+/mon_que_ng+.exe 
```

But is fine in terminal when I do:
```
 cd /home/<CENSORED>/.wine/drive_c/Program\ Files/Monster\ Girl\ Quest\ -\ NG+/ 
```
```
 wine mon_que_ng+.exe 
```

Though in both scenarios I get this error showing up regardless, I dunno if it's worth noting but here it is anyway:
```
 fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub 
```

---


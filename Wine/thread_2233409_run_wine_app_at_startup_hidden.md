---
title: "run wine app at startup hidden"
date: 2014-07-08
forum: Wine
---

### Post by cmcanulty on 2014-07-08
I run 16 computers at our local library and need some help. I can do remote support using this app in wine 

[http://www.aeroadmin.com/en/index.html]("http://www.aeroadmin.com/en/index.html")

 it works fine in wine and I have instructions on how to run it hidden in windows (so users aren't distracted by the interface). That is for win 7 our librarians use. All our public computers run xubuntu 14.04 64 bit. I need the aeroadmin to run at startup and hidden. So I may need 2 commands one to have aeroadmin.exe run with wine at every startup, and one to make it run hidden. Otherwise at start the public sees the aeroadmin app window right on the desktop. I am attaching 2 screenshots -1 showing how I want it to look and 2 showing desktop with aeroadmin visable. Aeroadmin isn't installed in wine it just runs by double clicking the exe file.

[http://www.aeroadmin.com/en/index.html]("http://www.aeroadmin.com/en/index.html")

 I would also like to add a shortcut for it to the panel 0 and whisker menu but since it isn't an install can't figure out how to do that.  It seems identical to teamviewer but it is free for the library use and team viewer is only free for personal use ( I talked to both companies to find that out). Thanks I sure hope this is doable as I really like the app.

---

### Post by slooksterpsv on 2014-07-10
To have it run on login/startup, if they login with the same username and password (separate would require a different way of doing so) you can go to: System Settings (The light-switch icon in Whisker) -> Session and Startup -> Application Autostart, just point to it and have it as an autostart item.
You can add a launcher and add whatever apps you want to it, even custom ones, you would just have to point to the location of your app.

---


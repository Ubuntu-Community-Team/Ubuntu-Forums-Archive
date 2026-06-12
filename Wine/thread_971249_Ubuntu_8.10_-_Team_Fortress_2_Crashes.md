---
title: "Ubuntu 8.10 - Team Fortress 2 Crashes"
date: 2008-11-04
forum: Wine
---

### Post by nzrock95 on 2008-11-04
Hello everyone.

I was on Ubuntu 8.04 for a while, and after sorting out a few problems (DirectX, ATI, Tahoma font, etc), I had Team Fortress 2 running great. Well, I recently upgraded to Ubuntu 8.10 and...well...problems. Everything works great...I can startup the game, change settings, join a server, and even play. But after 10-15 minutes of play, Team Fortress 2 freezes up, and I am forced to hard restart. I had it working under 8.04, so I have added "-dxlevel 81" and all of that stuff. I am using Wine 1.1.6.

Any ideas?

---

### Post by nzrock95 on 2008-11-07
...anyone having the same issue?

---

### Post by Clemens1212 on 2008-11-17
yes me here i have video: 
[http://www.youtube.com/watch?v=htG27Sv4wUo](http://www.youtube.com/watch?v=htG27Sv4wUo)

---

### Post by Dark9204 on 2008-11-18
Try to run it in wine stable 1.0.1

---

### Post by tespio on 2008-12-21
Here's a solution...

Go to your TF2 folder (C:/program files/steam/steamapps/[accountname]/team fortress 2/tf)

Delete the textwindow_temp.html file

Create a plain text document

Name it textwindow_temp.html (the same name as the one you deleted)

Make that file read only

This problem happens because gecko can't handle the process of being redirected to another page. The textwindow_temp.html file is where tf2 saves that page so you can view it quickly. By making a new empty one and making it read only TF2 will be forced to display the empty file.

---

### Post by tespio on 2008-12-26
Another fix:

Try disabling the in-game steam community interface

setting>In Game> uncheck "Enable steam community interface..."

---

### Post by illmatic on 2009-03-16
I got exactly the same Problem.
and its not fixed with the 2 options.
I'm running on wine 1.17

---

### Post by hikaricore on 2009-03-16
Make a new thread.
Give more detail.

Posts like this with no info whatsoever get ignored.

---


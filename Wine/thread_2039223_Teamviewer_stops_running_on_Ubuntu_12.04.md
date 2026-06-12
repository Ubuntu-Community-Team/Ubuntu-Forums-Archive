---
title: "Teamviewer stops running on Ubuntu 12.04"
date: 2012-08-08
forum: Wine
---

### Post by digitalvaldosta on 2012-08-08
Recently we installed Ubuntu 12.04 Server on a server here at my work. Everything works great. However, Teamviewer (which runs in WINE) will stop working when we are remotely connected after random amounts of time. If we are not on site then we are SOL and have to drive out and physically start the program again. :confused:

The server is not going offline in anyway (I have tested that extensively). I will be sending this to teamviewer support as well. 

Just Reaching Out to the Community

Josh at [digitvaldosta]("http://digitalvaldosta.com") dot com

---

### Post by Sachin Sharma on 2012-08-08
U do know that  Teamviewer exists for Ubuntu also in .DEB form.
WINE is known to have stability issues.

---

### Post by digitalvaldosta on 2012-08-13
That is what I used, directly from the teamviewer website. This installer actually runs a variant of wine with the windows version of teamviewer. 

I have also attempted [this]("http://ubuntuforums.org/showthread.php?t=1471247") to get it to start without manually doing so. Still not working without manually starting the program.

Any other ideas to get this to start automatically or possibly another Remote Access program that works without a hitch, would be great.

Thanks

---

### Post by PaulEdwards on 2012-08-17
openssh-server & vino (Ubuntu's built-in VNC remote desktop server) work for me as long as the firewall rules are set.

---


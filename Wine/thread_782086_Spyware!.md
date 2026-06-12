---
title: "Spyware?!"
date: 2008-05-04
forum: Wine
---

### Post by Charlie708 on 2008-05-04
When I started up my computer the other, I found it strange that an applet wanted access to my keychain.  I just installed a bunch of software, so I granted it access.  About twenty minutes later, I started getting pop ups, about three at a time.  I have been running Linux for two years, and never got anything like this, so I restarted.  When the keychain access request came up again, I tracked down the 'nm-applet'.  It was some spyware planted in my /bin directory, and it was using wine to call in pop ups!  I removed it quickly, and the pop ups and applet have not reappeared.  What can be done to stop this kind of breach?

---

### Post by Catalyst2Death on 2008-05-04
Only install software from trusted sources?

I doubt this came out of the official repositories...

---

### Post by cogadh on 2008-05-04
If it was using Wine to run, then it is likely something you installed with Wine. I'd take a look at what you've been using Wine for and try to be a little more slective with what you install.

---

### Post by Charlie708 on 2008-05-04
The only thing I used with wine at that point was Guitar Pro 5.  Shortly after the incident I started using ePSXe, and have had no problems since.  Can this be picked up surfing the web?

---

### Post by jrusso2 on 2008-05-05
I am wondering how it got into /bin sinc this requires privlidge escalation to access?

Your not using WINE as root are you?

---

### Post by Charlie708 on 2008-05-06
I have used root before, but not under wine.  I did a lot of work trying to figure out ad-hoc networks, and would stay logged in with sudo -i.

---


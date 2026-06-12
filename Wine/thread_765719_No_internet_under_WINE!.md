---
title: "No internet under WINE!"
date: 2008-04-24
forum: Wine
---

### Post by kevin11951 on 2008-04-24
i installed wine from here (Ubuntu 8.04 64 bit):
[http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)

everything works, but programs it it cant reach the internet. I just dont understand. (i tried to post this in beginner talk but it wouldn't let me, it said i didn't have permissions?)

---

### Post by kevin11951 on 2008-04-24
oh cmon! not even a click!

---

### Post by diablo75 on 2008-04-24
If you're going to install Wine, download it from the official website, and not some third-party site.  Sometimes they distribute out-of-date versions of Wine with their installers.

[www.winehq.org](www.winehq.org)

Also, there is a Ubuntu Wine Forum available.  You should post Wine related questions there, instead of here.

---

### Post by kevin11951 on 2008-04-24
> **diablo75 said:**
> If you're going to install Wine, download it from the official website, and not some third-party site.  Sometimes they distribute out-of-date versions of Wine with their installers.

[www.winehq.org](www.winehq.org)

Also, there is a Ubuntu Wine Forum available.  You should post Wine related questions there, instead of here.

this was from the wine hq site, go to wine's site, and click on ubuntu.

---

### Post by FuturePilot on 2008-04-24
> **diablo75 said:**
> If you're going to install Wine, download it from the official website, and not some third-party site.  Sometimes they distribute out-of-date versions of Wine with their installers.

[www.winehq.org](www.winehq.org)

Also, there is a Ubuntu Wine Forum available.  You should post Wine related questions there, instead of here.

That's not a third party site. That is the repository for Ubuntu. It links back to the Wine site.
Look here
[http://winehq.org/site/download-deb]("http://winehq.org/site/download-deb")

---

### Post by diablo75 on 2008-04-24
Meh, the thread should have been moved a long time ago...

---

### Post by jrusso2 on 2008-04-24
Does this happen with all apps or just one?  Have you tried others? It maybe that program doesn't work well under wine.

---

### Post by Killer-Bob on 2008-04-25
I've got the same problem.
After installing ubuntu 8.04 64bit, wine and firefox 2.0.0.14, 
firefox does not get connected to the internet.
In 7.10 that was no problem at all.
Hope you can help us, thanks,
killer-bob

---

### Post by Killer-Bob on 2008-04-25
Hey, I noticed that firefox is able to open websites, when using the IP instead of the URL.
So there seems to be a problem with the DNS.
Who knows how to fix that?
Killer-Bob

Edit:
Ok, I've found a solution on
[http://ramblingfoo.blogspot.com/2008/01/networking-in-wine-on-amd64.html](http://ramblingfoo.blogspot.com/2008/01/networking-in-wine-on-amd64.html)
referring to:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=430845](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=430845)

You simply have to install "lib32nss-mdns" or uninstall "libnss-mdns" 
(don't know if this works, i used the first option :) )

Hope this helps you too!
Killer-Bob

---

### Post by kevin11951 on 2008-04-25
> **Killer-Bob said:**
> Hey, I noticed that firefox is able to open websites, when using the IP instead of the URL.
So there seems to be a problem with the DNS.
Who knows how to fix that?
Killer-Bob

Edit:
Ok, I've found a solution on
[http://ramblingfoo.blogspot.com/2008/01/networking-in-wine-on-amd64.html](http://ramblingfoo.blogspot.com/2008/01/networking-in-wine-on-amd64.html)
referring to:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=430845](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=430845)

You simply have to install "lib32nss-mdns" or uninstall "libnss-mdns" 
(don't know if this works, i used the first option :) )

Hope this helps you too!
Killer-Bob

That totally worked! first option.

---

### Post by K.Mandla on 2008-04-25
Moved to Wine subforum.

---

### Post by andrebrait on 2008-04-27
vote for sticky

---


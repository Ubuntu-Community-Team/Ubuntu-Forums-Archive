---
title: "Pandora One issue"
date: 2009-11-01
forum: x86 64-bit Users
---

### Post by The_Cavester on 2009-11-01
Hello
I have installed 9.10 amd64 on my Toshiba Satellite A215 and all seems to be working great.
I installed Pandora One applet and that went good, but now every time I try to start
the Pandora my Tosh comes back and asks me the following...

You are trying to connect to an unverified server internal-tuner.pandora.com. (on port 443).

Do you trust this server, and want to go ahead with connection?

It gives me the option of allowing this connection only once or deny.
If I allow, then the app runs fine till next time I start the app again.
Then it asks me again.
Has any one else having the same issue?
What do I need to do so the Pandora will just start when I want it to.
Thank-you for any help

---

### Post by pheedback on 2009-11-03
I have this error on 9.10 32 bit. I did not have the problem in 9.04. I have looked for a fix, but I have not found one. It isn't much of a pain to allow each time, but I know it would be good to not have to allow each time.

---

### Post by fewyun on 2009-11-03
I had this issue on 9.04 amd64, and it continues on 9.10. I assume it is a Pandora error.. but I would still like to know how to fix it.

---

### Post by fatalerr on 2009-11-06
I'm experiencing the same thing.  

The real oddity is that [https://internal-tuner.pandora.com](https://internal-tuner.pandora.com) appears to have a valid SSL cert.  This may be a problem with how Adobe Air validates the cert .. I know that Air somewhat relies on flash working properly which, at least for me, has been sketchy on my 64-bit install.

---

### Post by mvalenti on 2009-11-06
I had that issue on my machine as well, 64 bit. It went away after I removed all flash plugins and reinstalled them. Could be the case here... BTW I am running 9.04, and the latest firfox 3.5.The problem happened with the earlier version of firefox, I did the erase and reinstall of the flash prior to upgrading to the newer firefox.


-Mark

---

### Post by The_Cavester on 2009-11-06
I am glad that I'm not alone on this one.
I have tried the fix from mvalenti but no luck.
I have some idea where to look now.
Thanks to all
I'll keep you all post on any fixes that I find.[http://ubuntuforums.org/images/smilies/smiley-faces-80.gif](http://ubuntuforums.org/images/smilies/smiley-faces-80.gif)

---

### Post by mvalenti on 2009-11-09
How did you go about uninstalling your flash?

---

### Post by mvalenti on 2009-11-09
To be sure we don't have any other old flash libs let's cleanup the folders where it usually resides:
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

---

### Post by mvalenti on 2009-11-09
Did you see this also?

[http://ubuntuforums.org/showthread.php?t=1259102&highlight=flash+player](http://ubuntuforums.org/showthread.php?t=1259102&highlight=flash+player)

-Mark

---


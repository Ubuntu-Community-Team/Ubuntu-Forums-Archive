---
title: "samba no longer work after updating"
date: 2008-01-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by wadragunov on 2008-01-13
Wednesday I installed updates for 7.04.  Samba had an update as well.  Since then, I can no longer connect to anything using samba.  I've searched the forums for suggestions to try and so far nothing has worked.  I have tried reinstalling samba, editing the config, starting and stopping samba manually to try to get some response.  the samba version is 3.0.24-2ubuntu1.5.  any help  would be great

wadragunov

---

### Post by fjgaude on 2008-01-13
Do you have your samba password installed:

```
sudo smbpasswd -a yourname
```

Not sure if updating removes it or not.

---

### Post by wadragunov on 2008-01-13
i tried and no luck.  thing is everything was working right up to the update.  i was listening to music from my nslug, stopped and closed rythmbox, then proceeded to update.  i didn't notice a problem until friday when i could no longer play music.  that's when i noticed samba was not working.  

wadragunov

---

### Post by freddyp on 2008-01-13
And did you enable the samba password with - 

sudo smbpasswd -L -e yourname

---

### Post by wadragunov on 2008-01-13
Ok, tried that with no luck.

---

### Post by fjgaude on 2008-01-13
Seems you could have done something "bad" to cause this to happen. Can you think of anything you haven't told us?

In Gnome it is so easy to use System/Administration/Shared Folders to have Samba, SMB work. No need to do anything else, except enter your smbpasswd like you have done.

Just thought of something else. Do you have the Samba Server installed? I vaguely remember that Gutsy doesn't install it at install.

---

### Post by wadragunov on 2008-01-13
No, I can't think of anything else.  I stopped and closed rythmbox.  Then ran the update manager.  When I next went to use samba, it could not connect to anything.  I'm using Feisty Fawn 7.04.

---

### Post by freddyp on 2008-01-13
My try a total uninstall of Samba, reboot, and then reinstall using this excellent guide at -- 
[URL="http://www.europe.eclipse.co.uk/Ubun...in-network.htm"]
http://www.europe.eclipse.co.uk/Ubun...in-network.htm[/URL]

---

### Post by wadragunov on 2008-01-13
I get a 404 on that link.  I'll see about forcing a complete uninstall, then reinstall.

---

### Post by freddyp on 2008-01-13
My apologies, the link got shortened during the cut-and-paste.  Try this one --

[http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm](http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm)

You might need to copy and paste into your browser.  I didn't insert a link just in case that was the problem last time.

---

### Post by wadragunov on 2008-01-13
That's close to what I do every time I install ubuntu.  I've tried removing and readding the shares.I just don't know.  I'll keep trying until I figure something out

---

### Post by wadragunov on 2008-01-16
I've tried everything I can think of besides attempting to remove libsmb, samba-common and smbclient as they want to remove a whole lot more,

---


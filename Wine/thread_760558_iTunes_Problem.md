---
title: "iTunes Problem"
date: 2008-04-20
forum: Wine
---

### Post by coolkid5 on 2008-04-20
I tried downloading the latest version of iTunes off Apple's website, but when I run it, it says, "This iTunes installer requires that your computer is running Windows XP or Windows Vista."  Is there something I'm supposed to do to fool iTunes into thinking I'm running windows?

---

### Post by edm1 on 2008-04-20
I wouldnt have though it would work very well under wine. Have you looked [here]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347") for help. Is there something you specifically need itunes for? There's plenty of linux native alternatives.

---

### Post by coolkid5 on 2008-04-20
No, I was just testing it out to see if it would work.  I found out the problem, I needed to change my OS in winecfg to XP, it was set to Windows 2000.

---

### Post by coolkid5 on 2008-04-20
Nevermind, it still doesn't work, it freezes up on the install when it is "Registering iTunes automation server."  Any idea's?

---

### Post by wizardofyendor on 2008-04-20
[http://wine-review.blogspot.com/2007/10/itunes-73-on-linux-with-wine.html](http://wine-review.blogspot.com/2007/10/itunes-73-on-linux-with-wine.html)

---

### Post by coolkid5 on 2008-04-20
Sorry, I forgot to say I was trying iTunes 7.6, the link there is for 7.3.  It does mention that sometimes it will freeze, and that you should just run it again, however I have run the setup multiple times and it always freezes in the same spot.

---

### Post by cookies on 2008-04-20
> **coolkid5 said:**
> Sorry, I forgot to say I was trying iTunes 7.6, the link there is for 7.3.  It does mention that sometimes it will freeze, and that you should just run it again, however I have run the setup multiple times and it always freezes in the same spot.

I had this error. You have to get Quick Time seperatley:
[http://www.apple.com/support/downloads/quicktime72forwindows.html](http://www.apple.com/support/downloads/quicktime72forwindows.html)

Then run the installer again. (Preferrebly in a new .wine folder). Let the installer run. It will still hang on the Automation Server bit. Let it hang for a while (3 or 4 minutes), then kill it with the force kill app. (press alt f2 then type xkill and click on the installer with the cursor). Then press alt f2 again and type:

wine "C:\Program Files\iTunes\iTunes.exe"

It will take a long time to start (up to one or two minutes)

Playback is skippy when you try to do anything other than have iTunes open. (Unless you have tons of RAM and a fast CPU.

---

### Post by coolkid5 on 2008-04-20
Thanks for the response, I gave up because I like Amarok better and I was just testing to see how iTunes was working under wine.  Perhaps the this thread will help other people who really need to get iTunes working.

---


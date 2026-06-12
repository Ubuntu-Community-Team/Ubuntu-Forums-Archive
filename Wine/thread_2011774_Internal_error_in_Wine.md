---
title: "Internal error in Wine?"
date: 2012-06-27
forum: Wine
---

### Post by Butthead on 2012-06-27
Hi,

Anybody else getting the "Internal error" and "There is no Windows program configured to open this type of file" error messages when attempting to run Wine after today's Update Manager upgrade to Wine 1.5.7?

Could it be also related to the Wine mono install (that crapped out on me) that I attempted to do yesterday when Upgrade Manager upgraded to Wine version 1.5.6 (why are there so many Wine upgrades coming down the pike lately? :confused: ). 

BTW - this is referring to the Wine 1.5.7 upgrade on Kubuntu 12.04 x64 that happened today.

I read this thread (and it sounds plausable as a fix), but I don't have synaptic installed (can't see any red exclamation points :mrgreen: ). 

[http://ubuntuforums.org/showthread.php?t=1993455]("http://ubuntuforums.org/showthread.php?t=1993455")

Thanks for any help and suggestions with this!  Jonesin' to play a round of Unreal Tourney again.  :guitar:

---

### Post by sogood007 on 2012-06-28
I have the same problem. I ended up go to /var/cache/apt/archives to rollback to one version down. 


cd /var/cache/apt/archives  
sudo dpkg -i *2~pulse18*

after that thing work again.

---

### Post by gioloi on 2012-06-28
I have the same issue with wine 1.5.7 on Kubuntu 12.04 64bit. 
Note that launching wine applications from terminal works instead... 
The error happens (at least to me) only when using launchers from menu (Kickoff or KRunner)
So for now I'm launching from terminal (yes.. it's a bit annoying) waiting for the issue to be fixed.
Or you can try to rollback as suggested by sogood007

---

### Post by gioloi on 2012-06-28
> **gioloi said:**
>  waiting for the issue to be fixed.

we should report a bug?

---

### Post by texpat on 2012-06-28
Same issue here.

Any solutions in sight other than rolling back to a previous version? Not that that'd be much of a hassle, either, though..

---

### Post by Butthead on 2012-06-28
I personally couldn't launch Wine applications in terminal either. :confused:

Today's Wine upgrade seems to have fixed things again.  I hope it stays working though. :neutral:

---

### Post by texpat on 2012-06-29
Well, my Xubuntu just downloaded and installed a presumably patched, new version of Wine and everything works fine again.

Big, massive kudos, guys. Thank you for producing awesome software for free!

---

### Post by dino99 on 2012-06-29
don't forget bugs, also for free :)

---

### Post by texpat on 2012-06-29
> **dino99 said:**
> don't forget bugs, also for free :)

Better free than paid-for, though ;-)

---

### Post by cwwilson721 on 2012-06-29
Note how fast the issue was fixed. Try getting it that fast with Windows Pay=Per_Bug software. There's still issues from Windows 95 that haven't been resolved

---

### Post by texpat on 2012-06-29
> **cwwilson721 said:**
> Note how fast the issue was fixed. Try getting it that fast with Windows Pay=Per_Bug software. There's still issues from Windows 95 that haven't been resolved

Yep, I totally agree. This bug was found and a fix was deployed within a day. That's pretty cool.

Also note that this is the development version of Wine 1.5.7 vs the stable version 1.4.1.

---


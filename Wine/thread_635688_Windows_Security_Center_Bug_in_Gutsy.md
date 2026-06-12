---
title: "Windows Security Center Bug in Gutsy?"
date: 2007-12-09
forum: Wine
---

### Post by Dscottmc7 on 2007-12-09
I have Ubuntu 7.10, i386 on HP 64-bit.
Suddenly I have three successive pop-up screens that tell me I have a serious "TrojanDownloader.NX" infection and "click here to remove," and all the rest of the BS.  It appears to be a legitimate Windows Security Center window...and IF I click on it, it goes to WINE and a blank screen.  I'll post a .JPG of the 3 screens.  Anybody have an idea what this is...or how to get rid of it?  Thanks!
Scott

---

### Post by hikaricore on 2007-12-09
What exactly have you been running via WINE?
You can't really be affected by ***dows viruses in Linux.

I can only imagine at worst someone is playing an elaborate joke on you.

---

### Post by Dscottmc7 on 2007-12-09
I'd buy the joke, but they keep coming up and look to capture data and send.  I don't know how to get the !@#RQWE% things off there.  Any Ideas?  I'd appreciate it.  Maybe a small charge of black powder?
Thanks, Scotrt

---

### Post by hikaricore on 2007-12-09
Does this happen randomly or upon logging in?

If it's on login check your System/Prefs/Session for anything that looks like it's running WINE.
If it's randomly either it's a [cronjob]("http://help.ubuntu.com/community/CronHowto") or someone is accessing your system remotely via ssh or telnet if you have those services.

Do you have friends or flatmates that use your system and or helped you setup Ubuntu?

I'd start asking questions and poking around in that case, as well as checking logs:

gedit /var/log/auth.log
gedit /var/log/auth.log.0

Look for anything dealing with SSH like the following:

> Dec  8 20:52:01 localhost sshd[15478]: Accepted password for hikaricore from 192.168.1.89 port 53450 ssh2

As well as gdm logins when you know you weren't around (my example is kdm but you get the point):

> Dec  8 20:45:57 localhost kdm: :0[5351]: pam_unix(kdm:session): session opened for user hikaricore by (uid=0)

Hope this helps.

--Aaron

---

### Post by Dscottmc7 on 2007-12-09

Thanks, Aaron,
Had to run last night, sorry.  The three sequential screens come up on a relatively timed basis, (frequency) not random.  I'm the only user and I'm not running WINE, except original setup.
You're right on.  It's a cronjob, (didn't even know what that was), and a doozy, and not even stored in the crontab.  Runs from remote.  I'm a real noobee but I'll run this to ground and report. Thanks, Aaron
Scott

---

### Post by Dscottmc7 on 2007-12-10
Thanks, Aaron and everyone.
Just to close this out, it WAS a cronjob, but how it was created is absolutely a mystery!  I took Aaron's advice and simply "sudo gedit crontab -e" and deleted the sole entry.  Voila!
Can't tell if I see visions of Rod Serling floating around or hear sounds of "Deliverance" wafting through my pea brain.  Thanks troops.

---


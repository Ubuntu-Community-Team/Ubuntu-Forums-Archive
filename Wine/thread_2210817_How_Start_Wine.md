---
title: "How Start Wine?"
date: 2014-03-12
forum: Wine
---

### Post by spock3 on 2014-03-12
Installed Wine as part of a Navicat 11 package installation onto Ubuntu 12.04 desktop.

Everything worked fine until I exited Navicat which also automatically closed out Wine.


Embarassed to say I've searched the menu & disk directory, [COLOR=#b22222][U][I][B]but am unable to figure out
how to restart Wine?[/B][/I][/U][/COLOR]

Once I get any response, I surely will peg it to my start menu.

Can anyone suggest the best approach to starting Wine again either thru the desktop gui
or cmd line?

Thanks

---

### Post by QIII on 2014-03-13
You don't exactly run Wine like that.

Try opening the Dash and typing the name of your application.  If it shows, just click it.  Many apps will just have a launcher when you install them.

Otherwise, you should be able to start it from the terminal like so (if I remember correctly):

```
$ wine "C:\Program Files\*appname*\*appname.exe*"       


```

---

### Post by spock3 on 2014-03-13
Thanks, it appears Wine doesn't yet have any association with the navicat exe file.

---

### Post by spock3 on 2014-03-13
I've been reading thru the WineHQ.org doc & wiki attempting different calls, but not yet been successful.

Is there an Ubuntu cmd to use to review my log calls for this applic yesterday to determine what I'm needing to properly
invoke Navicat?

---

### Post by monkeybrain20122 on 2014-03-13
Just navigate to the .exe file and click it should work.

---

### Post by spock3 on 2014-03-13
Clicking on the .exe doesn't work, I've tried using the Winefile utility too with the same effect.

I'll completely uninstall Wine & Navicat and start over.

---

### Post by spock3 on 2014-03-13
Ok, the deinstall/reinstall from the Navicat downloadable fixed the problem at least for Navicat.

The download archive includes its own copy of Wine & a config file.

Will keep this thread open a bit longer as I need to test installing another application into the Wine environment.

---

### Post by spock3 on 2014-03-13
Btw, for information purposes for any others to avoid the frustration & time waste, Navicat doesn't disclose in their download page
that their "Linux" version really is just their WinXP package with Wine, configured to support Navicat.  Clicking on the navicat.exe
won't work, one must click on their custom [COLOR=#ff0000]***start_navicat***[/COLOR] shell script.

---

### Post by spock3 on 2014-03-13
FYI, why this is relevant?

With WinXP security patch update elimination in April 2014, more users with legacy XP applics are more apt to migrate to Linux vs scrapping everything to upgrade to Win7/8/9.

I'm documenting this those users as well as for my own needs as the 1st of several PC's I will migrate to Linux Ubuntu & it's hardware dependent variants.

Thanks all for your help, it's been refreshing the level of support from the Ubuntu community.

---


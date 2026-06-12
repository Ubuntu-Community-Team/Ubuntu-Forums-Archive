---
title: "Ubuntu 8.10 64Bit and Firefox 3"
date: 2008-11-03
forum: x86 64-bit Users
---

### Post by Jkatz on 2008-11-03
I've looked through a lot of posts but I haven;t found and answer yet so I figured I'd ask.. 

I did an upgrade from 8.04 LTS to 8.10 and everything when as smooth as it could... a few apps had to be reloaded because of dependancies but no big deal. However when I went to use Firefox that was loaded with the upgrade strange things started to happen. when I try to go from my homepage of MSN, firefox seems to hang for a few mins , the screen goes to a grayed out screen and it stops responding.. then if I leave it for about a 1 min or so it comes back to normal. I'm not sure if is a glitch in the software or is it a result of not doing a clean install.
Has anyone come across this issue yet , if so and there is a fix for it please send me the link...

I've run the system from the CD live version and it seems to work ok

My system consists of:

PCChips MB
AMD 64 X2 3800 processor
1 Gb memory
Nvidia 6100 On-board graphics

---

### Post by scragar on 2008-11-03
Try seeing if it's a plugin/whatever by renaming(for a little while anyway) your firefox settings file:
```
mv ~/.mozilla/firefox ~/.mozilla/firefox_
```
Test, then restore when you know if that's the problem:
```
rm -rf ~/.mozilla/firefox
mv ~/.mozilla/firefox_ ~/.mozilla/firefox
```

---

### Post by WijbrandSchaap on 2008-11-04
> **scragar said:**
> Try seeing if it's a plugin/whatever by renaming(for a little while anyway) your firefox settings file:
```
mv ~/.mozilla/firefox ~/.mozilla/firefox_
```Test, then restore when you know if that's the problem:
```
rm -rf ~/.mozilla/firefox
mv ~/.mozilla/firefox_ ~/.mozilla/firefox
```

I have the same problem with FF3 freezing for a minute, after opening a new page. Tried with a clean ~/.mozilla/firefox, but nothing changed. Also, Flash is no longer working. Have to keep switching to Google Chrome on Wine to watch Youtube.  Is there an easy solution?

---

### Post by TryHarder on 2008-11-04
I had the same problem. Try to reinstall nspluginwrapper and flashplugin-nonfree manually. Check this topic for more info: [http://ubuntuforums.org/showthread.php?t=970383](http://ubuntuforums.org/showthread.php?t=970383)

---

### Post by WijbrandSchaap on 2008-11-04
> **TryHarder said:**
> I had the same problem. Try to reinstall nspluginwrapper and flashplugin-nonfree manually. Check this topic for more info: [http://ubuntuforums.org/showthread.php?t=970383](http://ubuntuforums.org/showthread.php?t=970383)

The miracle happened: it seems to work. Thanks a lot. I can ditch Google Chrome, now. :p

---

### Post by TryHarder on 2008-11-04
I'm always glad to help. If you think that you solved your trouble - mark this thread as SOLVED in Thread tools.

---

### Post by WijbrandSchaap on 2008-11-04
> **TryHarder said:**
> I'm always glad to help. If you think that you solved your trouble - mark this thread as SOLVED in Thread tools.
That option is not available in my thread tools. Have only: subscribe, print and email.  Someone else might want to do that, then?:confused:

---

### Post by TryHarder on 2008-11-04
Oh... Sorry, its not your topic. Jkatz should do this when he'll solve this issue for him.

---


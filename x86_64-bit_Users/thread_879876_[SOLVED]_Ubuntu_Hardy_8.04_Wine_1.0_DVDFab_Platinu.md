---
title: "[SOLVED] Ubuntu Hardy 8.04 Wine 1.0 DVDFab Platinum 5.0.7.6"
date: 2008-08-04
forum: x86 64-bit Users
---

### Post by ddales on 2008-08-04
Hi all,

I have a purchased and legally licensed copy of DVDFab Platinum 5.0.7.6 running on an XP box.  What I would like to do is transfer this App to my Linux box and run it under Wine.

**Problem:**  Under Wine, I cannot install my key.

**Done so far:**  

Copied the XP directory structure for DVDFab and tried it out under Wine.  Result:  DVDFab thinks it's the Demo version because I can't install the key or Registry Keys are missing.

Tried installing directly under Wine.  Although it does install, same result, can't enter the key.

Tried searching out all the Registry Keys from my XP box in order to duplcate them under Wine.  Forget it, there are way way too many.

This is not a permissions problem either.

Any suggestions would be greatly appreciated!

**Hint:** Please don't suggest other Apps that run natively under Linux.  I've tried them, don't like them.  Additionally, please don't lecture about copyright protection.

---

### Post by BLTicklemonster on 2008-08-04
I had a problem getting some of the new dvds I bought to work in ubuntu, so I was using dvdfab in wine. Turns out there's a simple fix. 

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

pay special attention to libdvdcss2. If you have it, remove it, and get the medibuntu repositories, and install it from there.

--PART 4/5, DVD PLAYBACK/RIPPING/BURNING--


DVD PLAYBACK


Note: I recommend disabling the CD/DVD-ROM source before completing this section, as you will receive numerous prompts if you need to run the "install-css.sh" command. If you're not sure whether it's disabled or not, follow the instructions in the preparation section of Part 1 for your particular Ubuntu variant.

For the best DVD playback in Ubuntu, including menu support, install the following packages:

sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc

You can also use the Xine engine in Ubuntu (default engine in Kubuntu and Xubuntu) for video/DVD playback. This can be done without having to change the backend of Totem - just install an alternative GNOME frontend for Xine called Gxine (this is optional, VLC will do just fine):

sudo apt-get install gxine libxine1-ffmpeg

Now you can test a DVD with VLC, Kaffeine, Gxine or whatever your favourite media player is. Enable deinterlacing (VLC > Video > Deinterlacing > Blend) if playback is choppy or if you notice artifacts.

Note: Those of you still having DVD playback issues after installing the above packages should try the solutions in the troubleshooting section, which you can find at the end of this how-to.


(oops, just noticed your hint there at the end. I'll leave this in case you change your mind)

---

### Post by ddales on 2008-08-08
Thanks for the tips but the actual problem is that I can't use my registered copy of DVDFab because it won't accept the registration key under wine.  It runs just fine under wine but only in the Demo Mode.

I would like to be able to use my registered DVDFab under wine so that I can finally get rid of the last instance of Windows running in my house.

---

### Post by roberine on 2008-08-08
I just downloaded the latest version of DVDFab from their website
and installed it with the latest wine available (1.1.2).
When I run it it'll come with a screen where I can choose
to run the application or register my version and enter
my registration key.
As your DVDFab version is the latest it could be that youre
version of Wine is outdated. To allways get the latest version
of Wine on your machine follow this here:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

HerbY

---

### Post by BLTicklemonster on 2008-08-08
Well heck, install virtualbox, then install xp on it, then install dvdfab in it.

---

### Post by ddales on 2008-08-08
Not meaning to be rude, but I'm already using DVDFab under a Win XP VMware Guest.

The question was, how to install the registration key under Wine/Ubuntu.

Thanks for nothin

---

### Post by BLTicklemonster on 2008-08-09
Rather than go tit for tat with you on this, let just keep trying, and share this:

```
Hello,

I can confirm that the bug is fixed when I compiled wine with "./configure
CC=/usr/bin/gcc-4.1".  The previously entered registration code is
automatically and correctly read and the program starts in full registered
mode.

pK.
```


from 


[http://bugs.winehq.org/show_bug.cgi?id=13114](http://bugs.winehq.org/show_bug.cgi?id=13114)

Looks like it might solve your problem.


When people try to help, try not to be sarcastic to them. We don't do this for any other reason but because we want to try to help.

(if this works, you owe me a pizza :) )

---

### Post by ddales on 2008-08-18
I'm not trying to be sarcastic.  It's just that I don't like compiling software.  I try to use the repository versions always.  I'll uninstall the repository version and try installing Wine from source with your suggestion.

Sorry for the late answer, I was on vacation.

---

### Post by BLTicklemonster on 2008-08-18
Well, it's the best I could find, I hope it works out for you! Let us know how it turns out, please.

Vacation, eh? I wondered where you got off to. Didn't send us a postcard, either, I see. *strikes ddales off Christmas list*

:) good luck, I know how frustrating this can all be. Hopefully this will get it all working right for you.

---

### Post by Kilz on 2008-08-18
DVDfab is listed in the W[ine Application Database]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=11565") and lists the registration issue. Wine does not guarantee that you can run every windows application without issue.

If you want to back up DVD's you might try k9copy, its in the repositories.

---

### Post by jgme on 2009-01-18
Is there any way to remove the SOLVED from the headline, I keep falling for it when I search for a DVDFab fix. The link up above to the wine bugs does not solve the problem, it still does not accept a key. Therefore this problem is not solved :cry: Thanks.

---


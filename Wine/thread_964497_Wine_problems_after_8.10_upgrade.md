---
title: "Wine problems after 8.10 upgrade"
date: 2008-10-30
forum: Wine
---

### Post by sirdouglas on 2008-10-30
Alright, so it seems like I find another problem after every Ubuntu upgrade.  Wine was working quite well for me, but since the upgrade to 8.10, every program I try open with Wine doesn't work.  I click on an .exe file and the bottom of my laptop screen will simply flash, and that's it.  This happens consistently with every .exe file.  Has anyone else experienced a similar problem?  Is there an easy solution?

Thanks!

Doug

---

### Post by david_kt on 2008-10-31
> **sirdouglas said:**
> Alright, so it seems like I find another problem after every Ubuntu upgrade.  Wine was working quite well for me, but since the upgrade to 8.10, every program I try open with Wine doesn't work.  I click on an .exe file and the bottom of my laptop screen will simply flash, and that's it.  This happens consistently with every .exe file.  Has anyone else experienced a similar problem?  Is there an easy solution?

Thanks!

Doug

Open terminal:

```
sudo dpkg-reconfigure -phigh wine
```

and try exe file again.

DK

---

### Post by Laibcoms on 2008-10-31
Have you tried testing using a Desktop?  I'm not sure, but on my end it is working fine.

Ubuntu 8.10 64-bit
Wine 1.1.7

---

### Post by Dark9204 on 2008-10-31
You will need to reinstall wine

---

### Post by Mistrblank on 2008-10-31
Wine (and many other Linux programs) are picky about the environments they run in.  You should probably go to Package Manager and have wine reinstalled or revert to a backup of your system from before the update.

---

### Post by yahs on 2008-10-31
My problem is that card games that worked with hardy and intrepid beta, now give an error message. Example "An error occurred while loading the archive. End-of-central-directory signature not found.  Either this file is not a zipfile, or it constitutes one disk of a multi-part archive. In the latter case the central directory and zipfile comment will be found on the last disk(s) of this archive.
note:  /home/sk/Desktop/Bridge/bridge.exe may be a plain executable, not an archive"

This is an exe file not a zip file.

Running wine 1.7 which works perfectly on my Hardy set up, works on my Intrepid beta release but not on 8.10. Tried removing and re installing wine but no joy.

---

### Post by sirdouglas on 2008-10-31
Alright, I tried "sudo dpkg-reconfigure -phigh wine" and even reinstalling, but the same problem consists.  I don't have Linux on my desktop so am unable to experiment with that.  Any other ideas?  I guess I can always bump back to an older version but would really prefer to continue with 8.10.  Thanks everyone,

Doug

---

### Post by david_kt on 2008-10-31
> **sirdouglas said:**
> Alright, I tried "sudo dpkg-reconfigure -phigh wine" and even reinstalling, but the same problem consists.  I don't have Linux on my desktop so am unable to experiment with that.  Any other ideas?  I guess I can always bump back to an older version but would really prefer to continue with 8.10.  Thanks everyone,

Doug

Right click on any of you exe file, choose properties. And then clcik "open with" tab. Click add and choose custome command. Type wine and add. Click on radio button of wine, and click ok.
I write this on xp and I do not have intrepid as well, so, you might need to adjust the above instruction but I think you got the idea of what I mean in case the above steps are not so accurate.

Now try double click on exe file again.

DK

---

### Post by sirdouglas on 2008-11-01
Weird, I didn't do anything, and now it works.  Right on.  Thanks guys!

Doug

---


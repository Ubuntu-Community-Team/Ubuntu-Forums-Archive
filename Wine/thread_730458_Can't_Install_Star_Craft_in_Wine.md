---
title: "Can't Install Star Craft in Wine"
date: 2008-03-20
forum: Wine
---

### Post by eeefresh on 2008-03-20
I'm trying to install a copy of Starcraft on my latop.  It's a Dell Inspiron,  running Ubuntu 7.10, and all drives, sound, video, settings, etc. seem to be working correctly.

However, when I try to install StarCraft using [these instructions]("http://joshhighland.com/blog/2008/02/26/starcraft-in-ubuntu-yes-drink-the-wine/"), I get an error.  When I get to the part where you run    ```
wine setup.exe
```

Terminal spits out this message:

```
Warning: the specified Windows directory L"C:\\windows" is not accessible.
Warning: the specified System directory L"C:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/media/cdrom0', starting in the Windows directory.
Warning: the specified Windows directory L"C:\\windows" is not accessible.
Warning: the specified System directory L"C:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
wine: could not load L"C:\\windows\\system32\\setup.exe": Module not found
err:wineboot:main Cannot set the dir to L"C:\\windows" (2)
```

I have no idea what this means.  Any ideas?

---

### Post by NightwishFan on 2008-03-20
Did you autodetect your drives in the wine configuration?

---

### Post by eeefresh on 2008-03-21
Yes.  When I click the drives tab it tells me I do not have a C: drive.  When I click autodetect, it shows my C: drive as the root folder (/) and my CD-ROM is drive F.

I am sure this is something really simple that I am overlooking...

---

### Post by eeefresh on 2008-03-21
I have also tried right-clicking on the setup.exe file on the CD and selecting "open with Wine emulator," but nothing happens when I do that.

---

### Post by eeefresh on 2008-03-21
Well I just tried opening the setup.exe file with wine again and received something new.  This time it gave me this:

The filename "setup.exe" indicates that this file is of type "exe document". The contents of the file indicate that the file is of type "DOS/Windows executable". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "DOS/Windows executable", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.

---

### Post by NightwishFan on 2008-03-21
I just tried. Starcraft works perfect for me. I put it in, and configure wine generically. Then i:
```
cd /media/cdrom0/
wine setup.exe
```

---

### Post by eeefresh on 2008-03-21
I just tried it again, and it still gives me the same message.

Maybe its a wine issue and not necessarily a Starcraft issue.  When you say you configured it generically, what exactly did you do?

---

### Post by NightwishFan on 2008-03-21
I installed it from the repos. Then I set it up as Windows Xp. Made it a 1024x768 virtual desktop. Autoconfigured drives, and the sound. Then it works perfectly.

---

### Post by eeefresh on 2008-03-21
Fixed it!  I guess wine didn't install correctly or something...I uninstalled it, deleted the .wine folder on my home directory, then reinstalled everything.  It worked the second time around!

---

### Post by NightwishFan on 2008-03-21
Nice :guitar:

It is fast in wine but a bit hard to play on a tournament level because the fast boxing is odd.

---

### Post by eeefresh on 2008-03-21
Here's another question: Is there a way to make it full screen?  My laptop is set to 1280x800, and the wine box is very hard to see.

I suppose I could just change my screen resolution, but I have this weird issue right now where I have to restart my session for screen resolution changes to take effect.  I don't think that's how it supposed to be, but that's what its doing...

---

### Post by NightwishFan on 2008-03-21
I think if you do not have a virtual desktop starcraft will run fullscreen.

---


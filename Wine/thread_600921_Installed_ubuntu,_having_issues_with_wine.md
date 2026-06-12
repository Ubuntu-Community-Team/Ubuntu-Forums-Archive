---
title: "Installed ubuntu, having issues with wine"
date: 2007-11-02
forum: Wine
---

### Post by highstead on 2007-11-02
I'm not completly new to linux, i've been using it for a few years, but decided i wanted to replace windows on my home computer.  I enjoy screwing around on linux for the most part but at the moment i'm utterly frustrated.

The goal has been to get starcraft to run, but i won't plague you with that question yet.  I can't install drivers for my video card (assuming i have to), i check the registry and the entir direct3d folder under wine is missing.  I try to install directx9 knowing that 10 is vista exclusive and that fails too.  

If you can point me to any other thread i'll hapily read up on it, or i'll post somewhere else. but please i'd like some help on this, the wine installing guides don't seem to tell me much of anything in the departments i'm looking in.

Thanks in advance.

---

### Post by highstead on 2007-11-02
wrong forum?

---

### Post by Iceni on 2007-11-02
If I remember correctly starcraft uses directx5, so I belive you don't actually need direct3d...

---

### Post by highstead on 2007-11-02
You would be correct, but the registry seems bare by comparison to the examples i see on winehq.  Did i skip a installation step?  was there something i was supposed to run ahead of time, or after installation completed to saturate the wine registry?

---

### Post by cogadh on 2007-11-02
If you are referring to what is on the Wine [Useful Registry Keys](http://wiki.winehq.org/UsefulRegistryKeys) page, all of those keys need to be manually created if you are going to use them, but not all of them are needed (in fact most of them are not). The Wine registry itself is much less cluttered than a normal Windows one, so don't expect to find the mess you would normally find in Windows.

Windows drivers are not needed nor would they work in Wine anyway. Wine translates any calls that would normally be made to the driver and sends them to OpenGL and the X server on its own.

Also, do not install DirectX in Wine, it will break your fake Windows directory. Wine already has its own implementation of DX9 and installing the real DirectX will replace it with native Windows libraries that do not work correctly.

You might want to click on the "Stuff I've learned about Wine" link in my sig. Its a basic Wine usage document that will help get you started really using Wine.

---

### Post by highstead on 2007-11-03
Alright that clarifies a few things, Is there no '.reg' area to aquire the keys so that this isn't done by hand with the potential for human error?  Similiarly, if i enter these by hand and they are correct there needs to be no back end software beyond wine to process it?

The reason i'm concerned is that even in non gui intensive programs (eg: starcraft map editor) my framerate doesn't exceed 10.

---

### Post by aoanla on 2007-11-03
Hrm.

Can you tell us something about your system and specs? What graphics card and processor do you have? Which graphics card drivers are you using (did you turn on drivers in the Restricted Driver manager?).
What version of /wine/ are you using?

Wine will be a little slower than using Windows directly, but it shouldn't be that slow - however, there may be other reasons why it is being iffy. For example, I happen to know that certain efficiency improvements in the 2d rendering *don't work* with the current ATI fglrx driver (with some versions of wine), as it doesn't provide the relevant features.

---

### Post by highstead on 2007-11-03
Nvidia 8800GTS   - ( using the latest restricted drivers )
4gb ram
AMD 64bit X2 5200+   - (not running 64bit ubuntu, wasn't sure if there was enough people behind it).
wine-0.9.48

I've been playing around with the direct3d keys and see some performance increase, but its still quite bad.

---

### Post by cogadh on 2007-11-03
> **highstead said:**
> Alright that clarifies a few things, Is there no '.reg' area to aquire the keys so that this isn't done by hand with the potential for human error?  Similiarly, if i enter these by hand and they are correct there needs to be no back end software beyond wine to process it?

The reason i'm concerned is that even in non gui intensive programs (eg: starcraft map editor) my framerate doesn't exceed 10.
I'm afraid that the potential for human error when entering registry edits in Wine is the same as the potential involved in making registry edits in Windows. The difference is, if you screw up Wine, then all you have to do is delete the .wine directory from your home folder and rebuild a new one. If you screw up the registry in Windows, your machine might not boot.

I'm not sure I understand your second question. Wine reads the registry upon initiation of the wineserver, similar to Windows reading from the registry on boot. It just reads it as it is, no additional processing is required. As long as you have made valid entries in regedit, it will read and use what you entered.

As for your framerate issue, which registry entries have you already made in an effort to correct it?

---

### Post by highstead on 2007-11-04
Sorry for the late response, i'd thought i'd replied but apparently not.  The framerate is no longer an issue, and your help was much appreciated.

the question was wether or not winehq had a 'import'able registry for the 'nice to have keys'.  I ended up adding most of the 3d/2d rendering keys, and now the framrate is better.

For some odd reason though, if i mount a iso, and have reffered wine to that iso to be the path it doesn't recogize it as the drive.  I've gone through the registry and made sure that nothing points to anywhere else, and have installed everything from that point.  But that is another problem i suppose.

---

### Post by cogadh on 2007-11-04
Have you set up the ISO mount point as a CD-ROM drive on the "Drives" tab in winecfg?

---

### Post by reagentz on 2007-11-04
I would suggest looking into getting the newest 0.9.48 WINE and install WINE-Doors to compliment it. If there's any .dll files needed to execute the program in this case Starcraft under WINE, WINE-Doors will do that for you.

I'll break out my old Starcraft/Broodwars CDs tonight and try it out myself and see if it works.

---

### Post by cogadh on 2007-11-04
Its been a while since I messed with Wine-Doors, but I don't think it actually takes care of DLL overrides for you, since the DLLs required often have MS licensing restrictions on them. On top of that, it is still beta software (only one minor rev beyond an initial alpha release) and still very buggy.

That being said, it is a very promising looking application and as long as it continues to develop as it has so far, it will be a very useful Wine tool someday. There are few things it already does pretty well, such as installing Steam or WoW, but there are other things that can screw up a Wine drive horribly, like when it tries to install DirectX.

---


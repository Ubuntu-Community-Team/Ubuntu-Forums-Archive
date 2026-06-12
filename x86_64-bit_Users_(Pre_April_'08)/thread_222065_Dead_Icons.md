---
title: "Dead Icons"
date: 2006-07-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by kayoti on 2006-07-24
Not sure what caused this, but I noticed last night that some of my programs are missing their icons on the main panel.  Specifically Firefox and Azureus.  I followed the post about Missing Thunderbird Icon, but it did not help.  

[IMG]http://img424.imageshack.us/img424/1185/iconspo0.png[/IMG] [imageshack]

Any ideas, let me know ;)  Thanks!
Kyle

---

### Post by kayoti on 2006-07-24
...Just thought about a possibility.  I am running Ubuntu64, but my Firefox and Java are 32 bit apps running under the 32 bit kernel ([http://www.ubuntuforums.org/showthread.php?p=1174435)](http://www.ubuntuforums.org/showthread.php?p=1174435)).  Would this cause these programs to not have a icon on the panel?

-Kyle

---

### Post by Kilz on 2006-07-24
> **kayoti said:**
> ...Just thought about a possibility.  I am running Ubuntu64, but my Firefox and Java are 32 bit apps running under the 32 bit kernel ([http://www.ubuntuforums.org/showthread.php?p=1174435)](http://www.ubuntuforums.org/showthread.php?p=1174435)).  Would this cause these programs to not have a icon on the panel?

-Kyle

That would be correct in that the reason you are getting the no icons in the taskbar is becasue they are running under linux32. But they are not running under a 32bit kernel, the kernel is 64bit but running in 32bit compatibility mode.

---

### Post by kayoti on 2006-07-24
That makes sense.  I really did not understand how the 32bit apps were able to run.

Well, is there a workaround that will allow the icons to show up that anybody knows about?

-Kyle

---

### Post by jamesford on 2006-07-24
not sure about azureus but for me changing the firefox32 launcher to /usr/local/firefox32/firefox helped

im running 64 bit java for azureus btw, and 32 bit for firefox, maybe u could install 64 bit java in addition to the 32 bit one like i did and have only firefox use 32 bit java and the rest including azureus using 64 bit java. i seem to recall that the 64 bit java needs to be isntalled first tho, ah i dont know, i forgot it was all so messy

---

### Post by kayoti on 2006-07-24
Hmm, I already have the launcher to run /usr/local/firefox32/firefox.  I'll try installing the java64 to see if that resolves the Azureus problem though.

Thanks
Kyle

---

### Post by kayoti on 2006-07-24
> **kayoti said:**
> I'll try installing the java64 to see if that resolves the Azureus problem though.
It looks like java 64bit is already installed.  Does it need to be connected to Azureus some how?

---

### Post by Kilz on 2006-07-24
> **jamesford said:**
> not sure about azureus but for me changing the firefox32 launcher to /usr/local/firefox32/firefox helped



If you change the launcher to that location. It bypasses the /usr/local/bin/firefox32 launch script. In doing so you will mess up how applications like the archiver look if you open a downloaded archive automaticly The widgets will be missing and look like squares.

---

### Post by jamesford on 2006-07-24
sudo update-alternatives --config java
should do it, there u select the default one, and i repsume azureus uses the default one. i think the one called smt with sun java 1.4 is the 32 bit one and 1.5 is the 64 bit one

---

### Post by jamesford on 2006-07-24
kilz not for me, using the desktop icon the script made gave me no firefox icons (like in the screenshot in the first post) changing it like i described solves that prob and there are no other probs, for me at least

---

### Post by Kilz on 2006-07-24
> **jamesford said:**
> kilz not for me, using the desktop icon the script made gave me no firefox icons (like in the screenshot in the first post) changing it like i described solves that prob and there are no other probs, for me at least

[Here is a copy of my install script]("http://tghc.org/files/Firefox32-flash-java.tar.gz") Click on it and instead of "Save to Disk" Click the other option "Open with" use the /usr/bin/file-roller. Dose the file roller look normal?

---

### Post by jamesford on 2006-07-24
sure does, looks the same as with epiphany, ffox64 and swiftfox

---


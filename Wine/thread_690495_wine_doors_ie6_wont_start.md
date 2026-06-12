---
title: "wine doors ie6 wont start"
date: 2008-02-07
forum: Wine
---

### Post by SyCo123 on 2008-02-07
I've tried ies4linux which runs but is all messed up. (ref my post a couple of days ago, which at this time has no response.)
[http://ubuntuforums.org/showthread.php?t=688449](http://ubuntuforums.org/showthread.php?t=688449)

So I tried wine-doors in my linux VM on my vista work box before my linux only laptop. Ie6 is in my Applications menu but clicking the menu listing results in nothing happening, so I tried running it from the  command line, and am getting this error

```
simon@simon-vbox:~/.wine/drive_c/Program Files/Internet Explorer$ ./iexplore.exe 
err:module:import_dll Library shdocvw.dll (which is needed by L"c:\\windows\\system32\\iexplore.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\iexplore.exe" failed, status c0000135
```

Any ideas? I need to test my CSS layouts at home in at least ie6 and using a VM is a hassle.

---

### Post by frlgrb on 2008-02-15
I'm having the same problem. I installed Wine-Doors and it went smoothly. simple apps like Notepad.exe are running well. My first serious app attempt was Quicktime (big mistake) and I learned very quickly that it can be a real pain. It runs very poorly and isn't recommended. I was just trying and playing to see what the Wine experience was like. IE is something I need, however, as I have some vendor-delivered apps that need IE for the user interface. A Windows install of Firefox often does the job but my experiment involves running things in a Windows shop from a Linux client. No problem if I use shortcuts like VM-Ware Windows boxes and RDP sessions. But I won't learn anything that way. I used the Wine-Doors interface to install IE6 on my Gutsy Ubuntu. It seemed to install properly but when I launch IE from the Gnome desktop nothing seems to happen. If I launch from a terminal then I get the same error message that shows the launch failure as noted in this thread. So far I think Wine is neat but apps on Wine need some serious tweaking. Oh well - I'll keep working and post any positive results.

---

### Post by stevejesus on 2008-02-15
hmmm...  If I remember right, wine-doors just installs ies4linux...  Or at least it used to.

---

### Post by garyedwardjohnston on 2008-04-28
Not much help but Wine HQ says it's still a no-go for IE.

Wine Doors is still very much beta/underdeveloped too.

Try browser shots if all you need to do is see sites in different browsers.

[http://browsershots.org/](http://browsershots.org/)

:)

---

### Post by skysurfer2 on 2008-05-03
I had the same problem initially as stated above, installed Wine-Doors from .deb download from the wine-doors.org site on Ubuntu Hardy 8.04, ran the IE6 installer, but it would not start.

Then I installed from SVN (Subversion) as outlined on this page:

[http://www.wine-doors.org/wordpress/?page_id=4](http://www.wine-doors.org/wordpress/?page_id=4)

When I attempted to run Wine-Doors from the Applications menu, it told me it could not launch the menu item, but from the command line if I typed wine-doors it started up normally. 

From the GUI I saw that my non-working IE6 installation was still listed in the 'installed applications' category, so I uninstalled it, then re-installed it.

From the Ubuntu menu, Applications -> Internet, IE6 was listed. I launched it without errors.

I then went back to my menu editor and found that the Wine-Doors application was attempting to launch out of my home directory. I searched my drive, found it at /usr/bin/wine-doors, and changed the menu item appropriately to point towards the correct launch directory.

I have Flash working IE6, but I'm experiencing some strange re-paint effects when going to sites such as YouTube. The videos play fine, but the page seems to want to either reload or repaint the entire screen for each Flash object that it encounters.

---


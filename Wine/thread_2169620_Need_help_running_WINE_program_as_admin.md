---
title: "Need help running WINE program as admin"
date: 2013-08-22
forum: Wine
---

### Post by videogamesandepicness on 2013-08-22
I need to patch Supreme Commander Forged Alliance but i get :error:unable to find version 3596. I found out that to get it to work if i were a windows user that i would have to right click the patcher and run it as admin. Of course you cant do that in ubuntu so i was wondering if there is any identicle way i could run the program as admin. Thanks! :) (by the way im leaving for vacation for a weak starting saterday. feel free to post suggestions while im gone but i will still be online before then :) )

---

### Post by newbie-user on 2013-08-23
sudo wine [name of executable]

---

### Post by videogamesandepicness on 2013-08-23
The file was file:///home/oem/Desktop/supcom_fa_patch_1.5.3596_to_1.5.3599.exe  and i did what you said but i got wine: /home/oem/.wine is not owned by you. ?

---

### Post by lah7 on 2013-08-28
> **newbie-user said:**
> sudo wine [name of executable]
[COLOR=#ff0000]**Never run Wine as root!**[/COLOR] That's strongly [COLOR=#b22222]not recommended [/COLOR]for various reasons (and doesn't fix this problem)
The problem is to do with Windows' administrative features, not Linux's.

**I found this from WineHQ:** [http://www.winehq.org/pipermail/wine-users/2005-September/018921.html](http://www.winehq.org/pipermail/wine-users/2005-September/018921.html)

> [COLOR=#000000]The 'solution' is to tell the application that it's being installed [/COLOR][COLOR=#000000]under Win98 (assuming that the program is willing to install under [/COLOR][COLOR=#000000]Win98), rather than 2K.[/COLOR]

It's because of how Windows NT-based installations work, they have permissions and different user account types, which didn't exist with Windows 9K. You can change the setting in **Winecfg** to mimic Windows 98 permission's behaviour -- full control.

**It's also documented in the WineHQ FAQ: **[http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014](http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014)
> **7.12. Should I run Wine as root?**

[FONT=verdana][COLOR=#000000][IMG]http://wiki.winehq.org/wiki/winehq/img/alert.png[/IMG] ***NEVER run Wine as root!*** Doing so gives Windows programs (and viruses) full access to your computer and every piece of media attached to it. Running with sudo also has these same risks but with the added bonus of breaking the permissions on your ~/.wine folder in the process. If you have run Wine with sudo you need to fix the permission errors as described in the next question, and then run [winecfg]("http://wiki.winehq.org/winecfg") to set Wine up again. You should always run Wine as the normal user you use to login.[/COLOR]

[COLOR=#000000]As far as Windows programs are concerned, you are running with administrator privileges. If an application complains about a lack of administrator privileges, file a bug; running Wine as root probably won't help.[/COLOR][/FONT]

---


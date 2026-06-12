---
title: "Boot failiure after installing nvidia driver 180"
date: 2009-07-21
forum: x86 64-bit Users
---

### Post by HolyDiver024 on 2009-07-21
hey guys, 
 
let me begin by saying i'm an absolute noob and have tried hard to research this myself but to no success. I'm an advanced windows and mac user but this (linux) is a whole new realm of challenge and excitement for me. I'm currently dual booting with vista 64 bit and have 2 nvida 8800 gtx cards in SLI, with 8 gigs of ram. Everything runs fine except when i update the drivers to 180, after it prompts me to reboot and it will just give me some "D.O.S-like" screen and ask me for my user name and password, In other words the G.U.I or, GNOME (ubuntu) as i think the linux community refers to it as, will not boot. The only thing i know how to do to get back to square one is to re-install 9.04 which is quite sad, frustrating, and time-consuming.  I know you guys know a much better way than this. Now i've been reading and trying to do things that others have posted in the past but when i type these commands i just get a blank command line under the command i typed in. Is there some possible way anyone can help me. I've read others with my same problems and see they resolved the issue but i can't seem to pull it off. anyone willing to help a noob like me? i'd greatly appreciate any links or references or step-by-step instructions.
 
I'm eventually looking to switch ubuntu to my primary OS as i get better with ubuntu and linux in general..... plz help :confused::confused:
 
-Eric

---

### Post by litspliff on 2009-07-21
you may have to start fresh if you did some unknown damage at the CLI.





don't install the 3rd party driver until you run all of your updates in the update manager.

after updates, activate the driver under system-admin-hardware drivers.

press ctrl+alt+F1 to get a terminal on T1

username....password to login


NOW THE COMMANDS:

sudo -i      (when prompted, enter password)

nvidia-xconfig

/etc/init.d/gdm restart

wait for a minute or two, you should see your mouse cursor, but a little bit small because you are in a higher resolution.

 if nothing happens, ctrl+alt+F7 should take you into X (GUI server), running Gnome (default ubuntu GUI)


if you want, you can practice this on a live session...it works exactly the same.

---

### Post by dagrump on 2009-07-21
Otay, nothing like jumping into the deep end. Just search for SLI & nvidia, maybe add GUI, you should find the info you need. In this forum.
If all else fails look for "GUI doesn't load after installing nvidia drivers" or a close thread name. I try to explain how I was told to do it in that thread. Good luck, & say goodbye TTY1.

---


---
title: "Cannot Install NoteTab Pro on Trusty Tahr with Wine"
date: 2014-12-07
forum: Wine
---

### Post by goggins on 2014-12-07
I just installed wine. after many "file not found" errors using "open with wine" on an old NoteTab 6.2 package, I downloaded a brand new copy of NoteTab 7.2, changed to my downloads directory, executed  "wine NoteTab_Full_Setup_720.exe" and got the following --

ag@Spot:~/Downloads$ wine NoteTab_Full_Setup_720.exe
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:wineboot:main Cannot set the dir to L"C:\\windows" (2)
err:wineboot:ProcessRunKeys Error running cmd L"C:\\windows\\system32\\winemenubuilder.exe -a -r" (2)
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
fixme:service:scmdatabase_autostart_services Auto-start service L"MountMgr" failed to start: 2
fixme:service:scmdatabase_autostart_services Auto-start service L"PlugPlay" failed to start: 2
wine: cannot find L"unix\\home\\ag\\Downloads\\NoteTab_Full_Setup_720.exe"

How should I proceed?

Also: How do I kill those smileys and how did they get there?

---

### Post by tgalati4 on 2014-12-08
I use *zim* for notes.  Perhaps consider migrating your notes to a native, linux solution?

Notetab 7.1 should load under 12.04 using WINE:  [https://appdb.winehq.org/objectManager.php?sClass=version&iId=28805](https://appdb.winehq.org/objectManager.php?sClass=version&iId=28805)

As far as installing, I would expand the executable using a Windows machine and copy the entire installation directory to a USB stick.  Then transfer the installation directory to a local directory on your linux machine.  Then run the setup.exe in WINE.  It could be problem with creating directories needed for installation.

What is the killer feature that NoteTab has that *zim* doesn't?

The smileys are emoticons (emotional icons) that are parsed from all of the slashes and colons.  This forum runs on vBulletin which is a social forum platform, and not really designed for technical use.  Just i:-|gno:-|re and press on.:-|

---

### Post by goggins on 2014-12-08
I obtained a solution for this from the wine forum. I had placed a copy of my old /.wine directory in my new machine in the hopes of shortcutting things and that was the problem. Once I deleted /.wine and ran the install commands again it worked fine. This should be marked as closed now.

---

### Post by goggins on 2014-12-08
I have no knowledge of or experience with zim, but have been using NoteTab Pro for 20 years or so. I use it more as a nestable, hot linkable flat file database generator than as a pure editor. For example, my "misc" file is pretty much blank, but has maybe 40 headings, each of which is a very comprehensive database or file on its own and which are clickable from the sidebar in which they show up. Many of those are, in turn, linked to others via embedded links. I also have a ton of legacy files in it. 

I found that I could disable smileys somewhere, and did so for that message. Thanks for the information.

---


---
title: "Need for Speed High Stakes issue with WINE"
date: 2011-09-16
forum: Wine
---

### Post by NowTheWorld on 2011-09-16
Hey everyone. Kris here :)

Alright. I got an issue installing NFS 4 HS with WINE.
I open SETUP.EXE with WINE, and it asks me to choose my language. I select OK with English and it loads the "Preparing to Install, Please Wait" screen. It gets to 100%, then a window saying "This game must be installed off the CD!" shows up. I don't understand why I'm having this issue, I'm opening the SETUP.EXE file from the CD. If anyone can point me in the right direction, PLEASE do so. I planned on having this installed tonight or this weekend, seeing as how I have class all week. Thanks in advance guys!

PVT Mackey
Oklahoma Army National Guard

---

### Post by NowTheWorld on 2011-09-16
Alright. Got it installed, thank goodness. :) Missed the Drive E:/ CDROM thing in WINE configuration. Alright. So. My current problem is starting it up. I double click on the icon and it says "The program nfshsgame.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience" and then at the bottom it says "This can be caused by a problem in the program or a deficiency in Wine. You may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application" then "If this problem is not present under Windows and has not been reported yet, you can report it at http://bugs.winehq.org" 

So I click on "Close", then a window saying "Need For Speed files corrupted; Please reinstall" comes up. I installed everything via [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4101](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4101) (installation guide). 

If anyone can help me, I'd highly appreciate it.

PVT Mackey
Oklahoma Army National Guard

---

### Post by maul9999 on 2011-09-17
> **NowTheWorld said:**
> Alright. Got it installed, thank goodness. :) Missed the Drive E:/ CDROM thing in WINE configuration. Alright. So. My current problem is starting it up. I double click on the icon and it says "The program nfshsgame.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience" and then at the bottom it says "This can be caused by a problem in the program or a deficiency in Wine. You may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application" then "If this problem is not present under Windows and has not been reported yet, you can report it at http://bugs.winehq.org" 

So I click on "Close", then a window saying "Need For Speed files corrupted; Please reinstall" comes up. I installed everything via [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4101](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4101) (installation guide). 

If anyone can help me, I'd highly appreciate it.

PVT Mackey
Oklahoma Army National Guard


I have same problem. that's tough.  But i was able to start video game by add drive in configure.  Here how i do that.  Go to Configure Wine then Drives tab.  You see missing CDROM drive on list?  that is why wine can't found drive at all and that is why you need to add.  Here how i add it.  click Add.. then choose any letter you want (HINT: You might want to add before you install program and video game)  click ok.  Click Show Advanced then change Type from autodetect to CDROM.  Now click Browse and go to media (HINT: It should be Path "/media/(game title)/"  Then there, you should be able to start it up.  

Let me know if any help.

---

### Post by NowTheWorld on 2011-09-18
Appreciate it. Will def give it a shot when  my new laptop gets in. This one's messing up, so I'm going to swap my hard drive over to the new one :) I think my motherboards on the fritz

---

### Post by maul9999 on 2011-09-18
> **NowTheWorld said:**
> Appreciate it. Will def give it a shot when  my new laptop gets in. This one's messing up, so I'm going to swap my hard drive over to the new one :) I think my motherboards on the fritz

What kind laptop?

---

### Post by NowTheWorld on 2011-09-28
HP Pavilion DV6000 laptop xD. Okay. So I got it to come up, fixed the DirectX files. It starts loading, then a message saying "The program NFSHS.ICD has encountered a serious problem and needs to close. We are sorry for the inconvenience." comes up. This is all that I believe I have to fix. Any ideas?

Thanks,
PVT. Kris Mackey,
Oklahoma Army National Guard

---

### Post by maul9999 on 2011-09-29
> **NowTheWorld said:**
> HP Pavilion DV6000 laptop xD. Okay. So I got it to come up, fixed the DirectX files. It starts loading, then a message saying "The program NFSHS.ICD has encountered a serious problem and needs to close. We are sorry for the inconvenience." comes up. This is all that I believe I have to fix. Any ideas?

Thanks,
PVT. Kris Mackey,
Oklahoma Army National Guard

HP?  The Intel Video card in CPU?  What kind CPU do you have?

---

### Post by NowTheWorld on 2011-09-29
Centrino Duo. I'd like some help with the game, not trying to advertise

Thanks,
PVT. Mackey
Oklahoma Army National Guard

---

### Post by fatriff on 2011-10-20
I take it you installed the proprietary graphics drivers? Most games won't start if they aren't installed.

One thing I used to do when I couldn't get a game working was install the full directx package. Try installing the game using playonlinux.

---


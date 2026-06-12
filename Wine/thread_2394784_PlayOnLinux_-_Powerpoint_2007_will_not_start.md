---
title: "PlayOnLinux - Powerpoint 2007 will not start"
date: 2018-06-21
forum: Wine
---

### Post by gdesilva on 2018-06-21
Hello,

I installed MS Office 2007 (Word, Excel and Ppt) on Ubuntu Studio 18.04 using wine 32 bit architecture. No problems with using Winword and Excel but Powerpoint fails to start. Debug shows the following


[06/21/18 21:44:22] - Running wine- WINWORD.EXE (Working directory : /home/gdes/.PlayOnLinux/wineprefix/MSOffice2007/drive_c/Program Files/Microsoft Office/Office12)
[06/21/18 21:49:58] - Running wine- POWERPNT.EXE (Working directory : /home/gdes/.PlayOnLinux/wineprefix/MSOffice2007/drive_c/Program Files/Microsoft Office/Office12)
[06/21/18 21:50:00] - Running wine- POWERPNT.EXE (Working directory : /home/gdes/.PlayOnLinux/wineprefix/MSOffice2007/drive_c/Program Files/Microsoft Office/Office12)
002e:err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
002e:err:ole:CoGetClassObject no class object {c1ee01f2-b3b6-4a6a-9ddd-e988c088ec82} could be created for context 0x1

Had no problems what so ever with running Powerpoint from POL in Ubuntu Studio 16.04.

Any suggestions will be greatly appreciated.

---

### Post by gdesilva on 2018-06-22
Here are the steps taken to fix the issue.

1. Highlight Powerpoint app on PlayOnLinux
2. Select configure on top menu bar
3. Click on Wine tab
4. Click configure wine - wine config screen appears
5. Select Libraries and add 'riched20.dll' and apply

Now I can start powerpoint from POL.

Thanks to the post by cipricus in [https://askubuntu.com/questions/155809/can-wine-support-office-2007#258717](https://askubuntu.com/questions/155809/can-wine-support-office-2007#258717)

---


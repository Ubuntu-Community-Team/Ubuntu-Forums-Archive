---
title: "How to start native Linux app from a Windows app running in wine?"
date: 2017-06-19
forum: Wine
---

### Post by etsnyman on 2017-06-19
I have need of a Windows application (there is no Linux version). It works perfectly under Wine on the latest Ubuntu.

  However, under some circumstances, one needs to open a text editor  and edit certain text files from within this Windows application. It  opens the Wine Notepad application, no problem at all.

  However, I would much rather need to use Gedit (or another native and more powerful text editor).

  How can I edit the command (currently "C:\windows\Notepad.exe") in  the Windows application to invoke/run a native Linux application like  Gedit?
[I]
[FONT=courier new][COLOR=#800000]start /unix /usr/bin/gedit[/COLOR][/FONT][/I] does nor work, nor does [I][FONT=courier new][COLOR=#800000]start /unix "/usr/bin/gedit"[/COLOR][/FONT]
[/I]
Thank you very much in advance.
  
(Running Wine 1.8.7 on Ubuntu 17.04)

---

### Post by monkeybrain20122 on 2017-06-19
I can be wrong, but I don't think it will work, just like it won't work if you try to start a Linux application in a Windows environment. First off the path wouldn't be recognized by your Win app. Remember your Win app lives in a simulated Windows environment so the Linux path has to mapped to a Windows path somehow and then the Linux app itself would not be runnable. Finally even if you can make it work somehow it is probably a security risk.

---

### Post by yoshii on 2017-07-18
Try using the freeware "NotePad++" for Windows; it runs via wine pretty well and has lots of nice features.

---

### Post by sccman on 2017-07-18
You change the default program for .txt files. Make sure you make a copy before you edit and save it:

[https://askubuntu.com/questions/90214/how-to-set-default-program](https://askubuntu.com/questions/90214/how-to-set-default-program)

---

### Post by yoshii on 2017-07-22
If I remember correctly, the info is at WineHQ, yet the info is so old and outdated it might not work.  But ask there, and they will probably get you the correct answer.

---

### Post by Bucky Ball on 2017-07-22
Ever thought about using Virtualbox and installing Win as a virtual machine? That way you'll be able to use both OSs at the same time. You'll have Windows in, well, a window, just like another program, and you can access Ubuntu just as you normally would, then open the Windows virtual machine to use Windows and its apps.

Just a thought. Good luck. ;)

---


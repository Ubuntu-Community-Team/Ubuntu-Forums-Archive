---
title: "how to execute a .exe file!?"
date: 2011-09-20
forum: Wine
---

### Post by geekhush on 2011-09-20
hi, i am using ubuntu 11.4 and i am new to it.... and i usd to us windows b4 i startd with ubuntu...i v installed ubuntu via wubi... so i v some softwares (windows native) thats .exe programs which i would like to install  on ubuntu..so i go to properties and then permissions to make it executable to run it through wubi..but when i try to chang anything in th permission tab ..it doesn't happen..i mark it as executable and within a sec it gets unmarked... and also the softwares i am using are fr softwares not those pirated ones..anybodies got any clue on this prob.?? 
any help really really appreciated :)
thanks

---

### Post by rollinsmoke on 2011-09-20
do some looking into wine and vitalization its your best hope of running windows programs on Linux


I personaly use virturalbox ose but system stats have to up there to run smoothly wine is the typical solution for slower pcs

---

### Post by Elfy on 2011-09-20
It's not a problem as such :)

You need windows to run .exe's not linux, however you might find that what you want to use runs with Wine. 

Not everything will, not everything will run perfectly.

There's a database you can search to see of what you want has had chance previously.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

moved to wine

---

### Post by Riothamus on 2011-09-20
Ubuntu is its own operating system, separate from Windows. You can't run Windows programs on it without running an emulator.

What kind of program is it? If it's a DOS program you want to run you can install DOSBox. If it's for Windows, you can use Wine, the Windows emulator.

If the program you want to run is like a game or a word processor, it should run fine. But if it's like a command-line utility, it won't work, or won't be worth the effort.

---

### Post by WinterMadness on 2011-09-20
> **Riothamus said:**
> Ubuntu is its own operating system, separate from Windows. You can't run Windows programs on it without running an emulator.

What kind of program is it? If it's a DOS program you want to run you can install DOSBox. If it's for Windows, you can use Wine, the Windows emulator.

If the program you want to run is like a game or a word processor, it should run fine. But if it's like a command-line utility, it won't work, or won't be worth the effort.

Wine is not an emulator. But I agree, its worth trying

---

### Post by geekhush on 2011-09-20
hi. thanks all for your reply.... ok i want to run games through WINE on ubuntu....now the problem is  i am not able to change the permission of any file... be it a game's .exe file or anything... its like i go to properties>permission and mark "make it executable" and a sec later its unmarked.. this is what i am not able to come over with..anyone if u cud tell me how to do it... thanks :)

---

### Post by Mark Phelps on 2011-09-20
The ability to run Games (Windows, that is) in Linux also depends critically on the DirectX support provided by your video driver.  For example, if your drive only supports up to DirectX v9, and the game expects D11, it's not going to work in Wine, no matter what you do.

So, if you know the make and model video card, post that back here.  If you don't, open a terminal and enter "lspci" and look for the line containing "VGA" -- and post THAT back here.

Even if you do have a supporting driver, Games often do not work well in Wine.  You should really check the first link that forestpixie posted for the particular games you want to run.

---

### Post by geekhush on 2011-09-23
hi, well i did as u said and my video card controller's make and model is-- VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE].... but like, okay i amy b competely sounding like a IDtenT but, when i tried to  change the permission of the game file (cod modern warfare.exe) which i had installed on windows..i cant do it..its keeps on undoing the changes i make... did i do something in a wrong way...?? neways thanks a lot for your help :)

---

### Post by peterbmetcalf on 2013-04-30
> **rollinsmoke said:**
> do some looking into wine and vitalization its your best hope of running windows programs on Linux


I personaly use virturalbox ose but system stats have to up there to run smoothly wine is the typical solution for slower pcs

But how does one execute WINE on the linux/ubuntu system?? I can download programs, but they appear as files to be extracted or each file visually read. Nothing like Windows where I merely hit the "run" button which appeared after hitting "open file."

Thanks.
Peter

---

### Post by Thee on 2013-04-30
You should be able to just double-click the exe file to run the Windows app you like, once you have WINE installed.

---

### Post by oldos2er on 2013-04-30
Old thread closed.

---


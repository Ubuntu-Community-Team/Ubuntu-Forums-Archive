---
title: "Playonlinux crash and no install metatrade 4"
date: 2015-11-14
forum: Wine
---

### Post by ioo2 on 2015-11-14
today have reinstall ubuntu 14.04 lts 32 bit , i have upgrade it to the new 15.10 but the internet connection was orrible, so i come back to 14.04 
the problem is with play on linux , i installed it from software center and i looking for metatrade 4 : start install wine 1.7.35 mono geko dowlod the mt4. exe setup and then report that the installation is abort and play on linux crash . i'm not expert so i can't give more info about it .
during the installation of play on linux in the and it report that tha package:   corefont.... ( i don't remeber )  was corrupt and so it was no installed and need to be reinstall.
i choose the bootom replace it now but nothing happen .

thant's my problem with play on linux 

thanks if you have some solution

---

### Post by howefield on 2015-11-14
Thread moved to the "*Wine*" forum for better chance of support.

---

### Post by ioo2 on 2015-11-15
ok i sovede it:

before i take a look this link :  [https://appdb.winehq.org/objectManager.php?sClass=version&iId=19984&sAllBugs](https://appdb.winehq.org/objectManager.php?sClass=version&iId=19984&sAllBugs) where  there are some info about the best version of wine that support metatrade:
[ATTACH=CONFIG]265584[/ATTACH] the best version is 15.9.

so i open play on linux and go on cofigure and open it:

[ATTACH=CONFIG]265585[/ATTACH][ATTACH=CONFIG]265586[/ATTACH]

Now my version is 1.5.9  but before was 1.7.35 to change it, you have to click on    +   

looking for the version of wine 1.5.9 here and add it clicking on  >  i removed the last version using < and the result was that:

[ATTACH=CONFIG]265587[/ATTACH]

now the last thing is go here and click on : execute a  .exe file and looking for metatrede exe setup file

[ATTACH=CONFIG]265588[/ATTACH]

in the folder home / play on linux / metatrade / drive c or dos device / program file   you can found the metatrade installatin folder 

the metatrade need two ddl the mfc40 and mfc42

IN ANOTHER GUIDE THE WRITER TELL TO PUT THIS TWO DDL AND RENAME IT WITH UPPER CASE , so i put the ddl in the window folder /system 32 and call them MFC40.DLL and MFC42.DLL. ([http://originaldll.com/file/mfc40.dll/1480.html](http://originaldll.com/file/mfc40.dll/1480.html) and   but you can looking for it on internet also)

Now is Sunday so i have to wait Monday to take a look if everything is ok . For now the installation is going.

---


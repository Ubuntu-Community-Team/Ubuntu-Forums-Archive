---
title: "WINE wont work with halo"
date: 2012-01-15
forum: Wine
---

### Post by Linux1999 on 2012-01-15
Whenever I try to use halo:combat evolved in WINE through playonlinux it starts up installs well then comes with the start up screen and closes again. When I look in a terminal it says "Wine cannot find c:/Windows/system32/dxdiag.exe" and it says "wine cannot find c:/Windows/system32/plugplay.exe" and i checked in the folder and they are both there in system 32 and im just not sure what to do.

---

### Post by grahammechanical on 2012-01-15
I use Wine to run one Windows application but not Halo, So, I am just guessing.

Wine follows the Windows convention when installing programs which is to create a folder named after the program in a folder called Program files. So, it is in c:/Program Files/program name/ that I find the exe file for my windows program.

I suggest that you look for these two exe files in somewhere like c:/Program Files/Halo and copy them into c:/Windows/system32/ because that is where Wine expects to find them for some reason.

It is just a guess. I had to do something similar when I first tried to run my particular Windows program through Wine. Certain files where not in their expected places.

Regards.

---

### Post by howefield on 2012-01-15
Thread moved to the "*Wine*" forum.

---

### Post by Mark Phelps on 2012-01-16
The link below is to the WineHQ compatibility page for "halo":

[http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true")

If you're running the version indicated for Vista, then you are out of luck.  It's rated gargage -- meaning it's not going to work, no matter what you do.

---


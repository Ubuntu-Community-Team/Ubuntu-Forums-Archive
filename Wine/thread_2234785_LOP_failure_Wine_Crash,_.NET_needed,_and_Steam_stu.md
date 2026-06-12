---
title: "LOP failure: Wine Crash, .NET needed, and Steam stuck"
date: 2014-07-16
forum: Wine
---

### Post by abdullaaldilaijan on 2014-07-16
Hello, This is my first time posting here. I really need help.
I'm trying to install a game (Magicka) and I'm always facing three problems every time I retry installing the game.
First the installer installs Wine (1.5.20) and extract it. Then I choose installing the Magicka steam version.
1st problem:
the next step is installing .NET Framework 2.0, which appears for half a second, which is followed by the error message in the installer:
[COLOR=#333333][FONT=Arial]Error in POL_Wine[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]Wine seems to have crashed[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]If your program is running, just ignore this message[/FONT][/COLOR]
I press next and continue. I don't know if I should take this error seriously.

2nd problem:
installer starts installing many items: XNA 3.1, .NET Framework 2.0, .NET Framework 2.0 SP1, .NET Framework 2.0 SP2, .NET Framework 3.0 ..etc
at one point, a new box appears with the message:
[COLOR=#333333][FONT=Arial]You must first install Microsoft .NET Framwork 2.0SP1 before installing or reparing this product[/FONT][/COLOR]
I press OK, and the program continues.

3rd problem:
eventually the installer finishes, and displays a normal message saying:
[COLOR=#333333][FONT=Arial]When Magicka download by steam finished,[/FONT][/COLOR][COLOR=#333333][FONT=Arial]Do NOT click on Play.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]Close completely the Steam interface,[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]so that the installation script can continue[/FONT][/COLOR]
which is fine. I press next. and Steam starts updating in a new window.
The window for update then becomes stuck on updating steam at a certain point (eg 19,232 of 119,323 KB) which continues for hours.

Other problems:
In some of the hundred times I restarted the process, a couple of times the process stopped completely. This happened to two files, Steam.exe and Update.exe. The message:
The program [choose from above].exe has encountered a serious problem and needs to close. We are sorry for the inconvenience.

---

### Post by Mark Phelps on 2014-07-17
The WineHQ page for this games talks about installing .Net v3.5 and using winetricks: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=22627]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=22627")

---


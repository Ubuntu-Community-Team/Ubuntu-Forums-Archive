---
title: "problem installing dotnet30"
date: 2014-07-19
forum: Wine
---

### Post by abdullaaldilaijan on 2014-07-19
[COLOR=#333333][FONT=MavenPro]Hello
[/FONT][/COLOR][COLOR=#333333][FONT=MavenPro]I'm trying to install the game Magicka thorugh steam.
 I installed most of the required libraries with wine 1.7.8. Then I switched to wine 1.5.18 to install other libraries: dotnet30 and dotnet35. I'm using PlayOnLinux 4.2.4 on Ubuntu 14.04.[/FONT][/COLOR][COLOR=#333333][FONT=MavenPro]The first time I installed dotnet30, it was smooth and error free.

 The other times (also this error appears when installing dotnet35, since dotnet35 installs it in the process) I get a report error window, then a window notifying me about the error. It says:[/FONT][/COLOR][COLOR=#333333][FONT=MavenPro]"The Program ServiceModelReg.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience"
[/FONT][/COLOR][COLOR=#333333][FONT=MavenPro]I copied the output of this process from the terminal. It is very long, take a look: [Installing dotnet30 using PoL]("http://pastebin.com/aGiA2k4D")

[/FONT][/COLOR][COLOR=#333333][FONT=MavenPro]When I tried to to install dotnet35, of course I get the same messages as before, but also, a message pops up saying:
 [/FONT][/COLOR][COLOR=#333333][FONT=MavenPro]"You must first install .NET Framework 2.0SP1 before installing or reparing this product"
[/FONT][/COLOR][COLOR=#333333][FONT=MavenPro]I don't understand how this happens, since .NET Framework 2.0SP1 installs in the dotnet30 process before it gets the error, and also in the dotnet35 process.

[/FONT][/COLOR][COLOR=#333333][FONT=MavenPro]For additional testings, I tried installing dotnet30 using winetricks, and got the following results in terminal: [Installing dotnet30 using winetricks]("http://pastebin.com/skZHJ43e")

[/FONT][/COLOR][COLOR=#333333][FONT=MavenPro]Any help is appreciated :-)

[/FONT][/COLOR][COLOR=#333333][FONT=MavenPro]Edit: Although I used wine version 1.5.18 in PoL, winetricks probably uses wine 1.7.22 (if that makes any difference) and maybe doesn't install prereqs like dotnet20,dotnet20sp1,dotnet20sp2 like PoL does.[/FONT][/COLOR]

---


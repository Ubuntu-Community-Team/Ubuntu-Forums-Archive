---
title: "Autocad 2006????"
date: 2008-01-27
forum: Wine
---

### Post by jrharvey on 2008-01-27
I wanted to try and install autocad 2006 and this it the log file where it failed. Any sugguestions?

[1/27/2008 13:30:43] === Installation started on jrharvey-deskto by jrharvey ===

[1/27/2008 13:30:47] [Info] Windows Installer upgrade is not required

[1/27/2008 13:30:47]   System Version = 3.1.4000.2435

[1/27/2008 13:30:47] Installation skipped: MSI Runtime 3.0

[1/27/2008 13:30:47] [Info] .NET Framework Runtime upgrade is not required

[1/27/2008 13:30:47]   System Version = 1.1.4322.573

[1/27/2008 13:30:47] Installation skipped: .NET Framework Runtime 1.1

[1/27/2008 13:30:47] Installation started: .NET Framework Runtime 1.1 SP1

[1/27/2008 13:30:47]   Command = "F:\Bin\AcadFEUI\support\dotnetfx\NDP1.1sp1-KB867460-X86.exe" /I /Q

[1/27/2008 13:30:50] [Error: 1603] ERROR_INSTALL_FAILURE
[1/27/2008 13:30:50] Installation failed: .NET Framework Runtime 1.1 SP1

[1/27/2008 13:30:50] Installation aborted

[1/27/2008 13:30:54] === Installation ended ===

---

### Post by ario on 2008-03-31
Thanks for your try in the world of Wine.
As a matter of fact all of us have problems with Autocad 2002 and above.
It is just about something like AutoCad Installer wants to install special version of .Net Freamwork and when it fails to install (I don't know why!) It seems that autocad wont install in linux anymore. Also same problems with other products of AutoDesk. Someone must go to they office and tell them we like it in Linux rather than every body install MS Windows just to use AutoCAD.
Also you may take a look at [http://appdb.winehq.org]("http://appdb.winehq.org")

---

### Post by epsolon77 on 2008-09-08
I have been reading on some other forums about what seems to be a similar issue.  It seems Autocad requires Microsoft's .NET framework 1.1 with service pack 1.  I have been able to get .net 1.1 to install fine under wine.  SP1 seems to be a little trickier.  I am sorry I do not have a solution yet, but I hope this helps get you closer to your answer.

---

### Post by qwertymn on 2008-09-09
For the trial of autocad 2006 the following works jsut fine:

1. Start with clean ~/.wine

2. Do 'wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks) && sh winetricks msxml3 dotnet20'

(Though Autocad2006 claims it needs .net 1.1, you get a crash updating a hotfix in the installer; so don't install .net 1.1, but do .net 2.0, that is enough to make the installer happy)

3. Run the app

I would guess that should be enough to get the retail version running as well
See [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by martin.laf on 2008-10-09
I would probably sound ignorant but firstly, what is "clean ~/.wine" ?
And how to install 2.0 instead of 1.1 ?   where does it come at the time of installation ?
I am a real beginer but a very patient and persistent trier...  we want to convert this architect office into ubuntu... but a lot of people have to be convinced... thanks

---

### Post by martin.laf on 2008-10-09
Thanks, this trick works well for intallation but it does not work further for me.  I can't start the software.  It ask me to register, i download some gecko and thats it.  I cant register my product.  If i want to run unregister, it does not run and no error mentionned, it just shut down.  Perhaps once it showed some fatal error...
Any advice?
thank you

---

### Post by martin.laf on 2008-10-09
The Error code is : 
fatal error: unhandled access violation reading 0x0000 exception at 7c17d38ch
Does anybody knows what is it about ?

---

### Post by CovenStine on 2009-10-19
What about tapping in to an existing installation that's working on a windows partition of a dual-boot machine?

---

### Post by sandy8 on 2009-10-20
[COLOR=Black]Hi [/COLOR][COLOR=Black][Jrharvey.]("http://ubuntuforums.org/member.php?u=371101")
You need to install Autocad 2006 on your Linux machine instead you can use Linux based cad software. Autocad is Windows, Mac OS based software. Autocad Linux is not that much effactive and popular yet. So, better go for Linux based cad software.
[/COLOR]

---


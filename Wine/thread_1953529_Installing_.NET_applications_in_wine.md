---
title: "Installing .NET applications in wine"
date: 2012-04-06
forum: Wine
---

### Post by Dmelnet on 2012-04-06
Hi!
I'm trying to install scientific software in my Ubuntu 11.04 using wine 1.4-rc6. The first missage I got when trying to do so was that I had to install the windows version of mono or something like that. I installed mono for windows successfully but it didn't work. Finally I installed  the Microsoft .NET Framework version 2.0 using the command "winetricks dotnet20". It seems the problem is solved for one of the programs I had to install and I can use it without problems but I got a new error when trying to install the other program. I think I'm going crazy! I need some help.
 
I type:
[INDENT] wine Setup.Exe
[/INDENT]And it says:

[INDENT]fixme:storage:create_storagefile Storage share mode not implemented.
err:msi:ITERATE_Actions Execution halted, action L"VSDCA_VsdLaunchConditions" returned 1603
[/INDENT]is this error related to .NET? what can I do? the program is called MyIQ5. Tell me if I can provide you more useful details.

Thank you in advance.

---

### Post by dino99 on 2012-04-09
use the latest wine, 1.4rc6 is outdated, now its 1.5.1

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

better to rename or delete your actual .wine folder and create a fresh one with 1.5.1

then follow winetricks & winehq database about .net, look at winehq forum too as some workaround are discussed.

---

### Post by sportfreak2020 on 2012-05-03
in the folder that you are running the application from .. is there a file that is similar to NAMEOFAPP.exe.config or something like that .. if so, rename it to a diff or a .bk file and try running the app again .. 

its always recommended to cd into the directory and then run the command 

wine APP.exe 

hope it helps !!!

---


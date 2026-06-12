---
title: "Arg im frustrated!!!!!!!!!!"
date: 2008-11-27
forum: Wine
---

### Post by mut4nt on 2008-11-27
:frown: Im trying to install NullDC. 
I double click on the exe to install, nothing 
happens so I open terminal cd to the directory 
and run wine on it

vv
```

snesticle@r00t:~$ cd drive_c/Program Files/
bash: cd: drive_c/Program: No such file or directory
snesticle@r00t:~$ cd drive_c/Program Files/
bash: cd: drive_c/Program: No such file or directory
snesticle@r00t:~$ cd Desktop
snesticle@r00t:~/Desktop$ cd nullDC_100b1_6
snesticle@r00t:~/Desktop/nullDC_100b1_6$ wine nullDC_100b1_6
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\snesticle\\Desktop\\nullDC_100b1_6\\nullDC_100b1_6.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\snesticle\\Desktop\\nullDC_100b1_6\\nullDC_100b1_6.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\snesticle\\Desktop\\nullDC_100b1_6\\nullDC_100b1_6.exe" failed, status c0000135

```


I searched the first error, Microsoft.VC80.CRT
and found out this is some bug in ubuntu?
(Im running Xubuntu) HELP MEH PALEASE!

---

### Post by cogadh on 2008-11-27
First off, to change directories to a directory with a space in the name, you either have to enclose the path in quotes or put an escape character before the space:
```
cd ".wine/drive_c/Program Files"
OR
cd .wine/drive_c/Program\ Files
```
As for your specific problem, the error message you got explains it all. The installatiion is looking for a DLL file that is not part of Wine by default, i.e. MSVCP80.dll. You can get that by getting [winetricks](http://wiki.winehq.org/winetricks) and using it to install Visual C++ Runtime 2005. After doing that, try running the install again and see what happens.

---

### Post by gettinoriginal on 2008-11-27
Everything that i have installed via wine, I do not double click the .exe file, but right click it, choose "open with wine program loader" and it installs without difficulty.  Double clicking usually tries to use the "archive manager" which of course does not recognize .exe

---

### Post by mut4nt on 2008-11-27
thanks for the replies, I did try right clicking and opening with wine but same thing happened. Anyways i googled away and found this and it worked! hope this will help someone else.

[http://forums.ngemu.com/nulldc-discussion/88553-nulldc-wine.html](http://forums.ngemu.com/nulldc-discussion/88553-nulldc-wine.html)

---


---
title: "What DLLs to install in winetricks?"
date: 2012-04-10
forum: Wine
---

### Post by ch3at3r on 2012-04-10
I have Wine 1.4 and i have to install some DLLs via winetricks but don+t know what..
I want to play FIFA99, but trying to install I get the following error:
"Program error" 
"The program winevdm,exe has encountered an serious problem and needs to close." 
Thanks.

---

### Post by cogadh on 2012-04-10
We need much more detail to give you any kind of meaningful advice. Run the install from the terminal and post the output here, it may indicate exactly what you might need. However, it should be noted that FIFA 99 has a "bronze" rating from Wine's Application Database, meaning the last time it was tested, it barely worked anyway.

---

### Post by Drowz0r on 2012-04-11
> **ch3at3r said:**
> I have Wine 1.4 and i have to install some DLLs via winetricks but don+t know what..
I want to play FIFA99, but trying to install I get the following error:
"Program error" 
"The program winevdm,exe has encountered an serious problem and needs to close." 
Thanks.

Try running it through PlayOnLinux instead. It might be on there. If not, try doing it through steam.

---

### Post by ch3at3r on 2012-04-14
> **cogadh said:**
> We need much more detail to give you any kind of meaningful advice. Run the install from the terminal and post the output here, it may indicate exactly what you might need. However, it should be noted that FIFA 99 has a "bronze" rating from Wine's Application Database, meaning the last time it was tested, it barely worked anyway.

Here is what it shows after trying to install the game via terminal:
wine: Unhandled page fault on read access to 0xffffffff at address 0x11df:0x000032cc (thread 0029), starting debugger...
fixme:dbghelp:addr_to_linear Failed to linearize address d00d:800 (mode 0)
fixme:dbghelp:addr_to_linear Failed to linearize address d00d:6636 (mode 0)
fixme:dbghelp:addr_to_linear Failed to linearize address d00d:660e (mode 0)

---

### Post by cogadh on 2012-04-15
An unhandled page fault should produce much more info than that. There should be some kind of error dump following those messages. Are you sure that is the entire terminal output?

---

### Post by ch3at3r on 2012-04-15
> **cogadh said:**
> An unhandled page fault should produce much more info than that. There should be some kind of error dump following those messages. Are you sure that is the entire terminal output?

Yes. Thats all.. And yes after that follows that error I told in my first post:
"Program error" 
"The program winevdm,exe has encountered an serious problem and needs to close."

---

### Post by ch3at3r on 2012-04-17
> **cogadh said:**
> An unhandled page fault should produce much more info than that. There should be some kind of error dump following those messages. Are you sure that is the entire terminal output?

Now I tested again getting following info:
-------------------------------------------------------------------------------------------------------
root@username:/media/FIFAPCCD# wine AUTORUN.EXE
wine: Unhandled page fault on read access to 0xffffffff at address 0x11df:0x000032cc (thread 0029), starting debugger...
-------------------------------------------------------------------------------------------------------

And after that pops out box(Wine debugger) saying:
------------------------------------------------------------------------------------------------------- 
[SIZE=4]Program error[/SIZE]
[COLOR=Black]
[/COLOR][SIZE=2][COLOR=Black]"The program winevdm.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience.[/COLOR][/SIZE]

This can be caused by a problem in the program or a deficiency in Wine. You may want to check the _[COLOR=Blue]Application Database[/COLOR]_ for tips about running this application."

-------------------------------------------------------------------------------------------------------

Then I hitted "Close" and got following new lines in terminal:
-------------------------------------------------------------------------------------------------------
fixme:dbghelp:addr_to_linear Failed to linearize address d00d:800 (mode 0)
fixme:dbghelp:addr_to_linear Failed to linearize address d00d:6636 (mode 0)
fixme:dbghelp:addr_to_linear Failed to linearize address d00d:660e (mode 0)
-------------------------------------------------------------------------------------------------------

Hope this gives info you need.

---

### Post by cogadh on 2012-04-18
Unfortunately, no, that is a stunningly uninformative error. However, I do have a suggestion: don't use autorun.exe, find the actual installer (probably called "setup.exe") and run that instead. The autorun should just be launching that installer anyway and since it appears that autorun is having the issue, just eliminate it from the process and skip right to the target. If you have trouble finding the installer, find the autorun.ini file on the disk and open it with a text editor. That is the instruction autorun is supposed to follow, so it should tell you exactly where the setup executable is and what it is named.

---

### Post by ch3at3r on 2012-04-19
> **cogadh said:**
> Unfortunately, no, that is a stunningly uninformative error. However, I do have a suggestion: don't use autorun.exe, find the actual installer (probably called "setup.exe") and run that instead. The autorun should just be launching that installer anyway and since it appears that autorun is having the issue, just eliminate it from the process and skip right to the target. If you have trouble finding the installer, find the autorun.ini file on the disk and open it with a text editor. That is the instruction autorun is supposed to follow, so it should tell you exactly where the setup executable is and what it is named.

It works now! 
Giving same kind of Program error, but it anyway works! ;)
Thanks to you!!

---


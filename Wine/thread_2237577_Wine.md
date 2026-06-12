---
title: "Wine"
date: 2014-08-02
forum: Wine
---

### Post by jwn-2 on 2014-08-02
Ubuntu 14.04

I have  installed Wine, but how on earth do you now install or run windows  software with it. I have tried Control/Install new software, I tried  running the install file (as well as some old stand allone DOS  programmes for a test (which still run perfectly well in Win7)), but  abolutely nothing happens. I have tried double-clicking the file, I have  tried right-click/open with Wine, I have tried opening it directly from  Ubuntu, as well as with the Wine explorer. I have checked that the  ownershiop is Me, and that the executable-flag is set. Absolutely no  luck. What on earth am I doing wrong???

---

### Post by monkeybrain20122 on 2014-08-02
Just click the .exe file like you would in Windows. Now of course not all Windows programs work in  Wine, but if you are installing PDF-Xchange viewer (from your other thread) it should work.

If not, open a terminal and type
```
wine /path/to/exe/file
```
and post the error messages.

Where /path/to/exe/file is the path to the .exe file, for example, if foo.exe sits in Downloads, it would be Downloads/foo.exe (note the capital D)

---

### Post by howefield on 2014-08-02
Thread moved to the "*Wine*" forum.

---

### Post by Dennis N on 2014-08-02
You should do some reading about Wine. Here is the user guide:

[http://www.winehq.org/documentation](http://www.winehq.org/documentation) on which click on "Wine User Guide" link - See Chapter 1, Quick Start.

---

### Post by jwn-2 on 2014-08-03
Thanks Dennis N, that link is useful.

However I still can't run any Windows software.

When I try to run the pdf-exchange viewer installer from a terminal, I get the following output:

fixme:wininet:query_global_option INTERNET_OPTION_CONNECTED_STATE: semi-stub
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 5000
fixme:exec:SHELL_execute flags ignored: 0x00004100
jonnie@jonnie-N150P-N210P-N220P:~$ fixme:exec:SHELL_execute flags ignored: 0x00004100
fixme:exec:SHELL_execute flags ignored: 0x00004100
fixme:exec:SHELL_execute flags ignored: 0x00004100
fixme:exec:SHELL_execute flags ignored: 0x00004100
fixme:exec:SHELL_execute flags ignored: 0x00004100

(the last line just seems to repeat forever)

I have also tried to run another stand alone program from the terminal, and then I get the following:

winevdm: Cannot start DOS application Z:\home\jonnie\Temp\VRAMY.EXE
         because the DOS memory range is unavailable.
         You should install DOSBox.

Help please!

---

### Post by mastablasta on 2014-08-04
to run wine you can run it by right clicking on it and then select run/open with wine.in your case it looks like it wasn't internet connection. could that be possible? you need to read instructions for oyur application on wine application database.

another way to use wine is through graphical interface named Playonlinux. they offer some scripts for more common applications and games to help you with install. sometimes these scripts make it a lot easier other times they are not so good.

as for dos program you need to install dosbox, run it and then install in it. dosbox is a DOS emulator. you need to read at least a couple of how tos e.g : [http://www.dosbox.com/wiki/Basic_Setup_and_Installation_of_DosBox](http://www.dosbox.com/wiki/Basic_Setup_and_Installation_of_DosBox)
to know how to work it since it is a CLI only interface and has a few features original DOS didn't have (screenshots, screen videos...). but basically what you need to do is mount the folder where you program is (for example you mount it as C:\  )and then you go to it and run your install.


if you want a GUI interface for installs and such... you can try DBGL, but I think it still needs oracle java to be installed (java can be installed via PPA): [http://members.quicknet.nl/blankendaalr/dbgl/](http://members.quicknet.nl/blankendaalr/dbgl/)

---

### Post by jwn-2 on 2014-08-07
I have at last got Wine (and some Windows apps) running with the help of a friend. Don't ask me what he has done, its beyond my comprehension. Thanks for your help guys. I am not sure if I should mark this one as solved? This did not really solve my problem.

---

### Post by mastablasta on 2014-08-08
I avoid wine on Linux PC if possible. there are  usually good alternatives to windows apps. the only issue are windows games where I have to use wine. :P

So yes, Linux is not windows. And windows specific apps are not made to run on Linux, so best to avoid them and forget about them.

ReactOS on the other hand....

---


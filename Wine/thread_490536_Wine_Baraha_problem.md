---
title: "Wine: Baraha problem"
date: 2007-07-02
forum: Wine
---

### Post by pvravi on 2007-07-02
Hi,

I'm trying to run this program called baraha ([www.baraha.com](www.baraha.com)) on wine 0.9.40 on Fiesty.

The latest version v7.0 fails to install with a "Unable to add font resource" or some such error. I can live with the previous version (0.6), and I installed that.

The program GUI comes up, and just freezes there. Mouse pointer is lost over the window, and that cannot be used either. I tend to kill it from the command line (from the terminal I started it).

This is the console output running the program creates:

```
fixme:shdocvw:PersistStreamInit_InitNew (0x17c4d0)
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
fixme:shdocvw:OleObject_DoVerb stub for -3
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x17c4d0)
fixme:shdocvw:OleObject_Close (0x17c4d0)->(1)
fixme:wininet:InternetGetConnectedState always returning LAN connection.

```

Anybody help, please? Has anyone successfully run this program under Wine? There appear to be some success stories, but it is unclear.

thanks
pvravi

---

### Post by chaanakya_chiraag on 2010-01-02
I know this is after quite a while, but anyway...
First of all, Baraha 8.0 works flawlessly in the latest WINE in Karmic (9.10).  However there is one caveat: most of the time the menubar does not appear :(  However, since most of the functions are on the toolbar below the main menubar, it's ok.

---

### Post by Exodist on 2010-01-02
You would prob be able to get more help with this in General Help. :)

---

### Post by ibuclaw on 2010-01-02
Moved to WINE

edit - didn't notice the original date of this thread.

July 2nd, 2007 

Closing, if you think this issue affects you, start a new thread [here]("http://ubuntuforums.org/newthread.php?do=newthread&f=313").

Regards
Iain

---


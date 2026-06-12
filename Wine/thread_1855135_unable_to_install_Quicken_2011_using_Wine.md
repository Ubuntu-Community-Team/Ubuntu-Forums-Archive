---
title: "unable to install Quicken 2011 using Wine"
date: 2011-10-05
forum: Wine
---

### Post by sasjzl on 2011-10-05
Hi all,

I am unable not able to install Quicken 2011 Premier Release R 8(20.1.8.6) using Wine
1.3.29-0ubuntu1~ppa1~natty1 (wine1.3).  I followed these directions:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=22198](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22198)

and did not have any problems with the winetricks commands or anything else.
All appeared to go smoothly.  It made all the correct entries for Quicken but they do not work.  Tell me if I did the code icons correctly.

It extracts fine and gets past the 'agree' deal but after a couple of windows it stops with the message:

Program Error
The program qw.exe has encountered a serious problem and needs to close.  We are sorry.....

I ran it from the terminal and here is the end of my log.  I got some hits on the error message that were related to Quicken but they were very different issues.  I am brand new to Ubuntu and I love it but would really like to be able to use Quicken on it.  It appears that alot of other folks are.  
```

ogram Files\\QUICKENWinet\\common\\system", (null), (nil)): stub
fixme:imagehlp:BindImageEx (0, "C:\\Program Files\\QUICKENW\\xsell.dll", "C:\\windows\\system32\\", (null), (nil)): stub
fixme:winspool:OpenPrinterW PRINTER_DEFAULTS ignored => (null),(nil),0x000f000c
err:setupapi:do_file_copyW Unsupported style(s) 0x284
fixme:winspool:OpenPrinterW PRINTER_DEFAULTS ignored => (null),(nil),0x000f000c
err:module:import_dll Library msvcm90.dll (which is needed by L"C:\\Program Files\\QUICKENW\\qwutilnet.dll") not found
err:module:import_dll Library qwutilnet.dll (which is needed by L"C:\\Program Files\\QUICKENW\\QWUTIL.dll") not found
wine: Unhandled exception 0xc06d007e at address 0x7b839d72 (thread 0046), starting debugger...
err:module:import_dll Library msvcm90.dll (which is needed by L"C:\\Program Files\\QUICKENW\\qwutilnet.dll") not found
err:module:import_dll Library qwutilnet.dll (which is needed by L"C:\\Program Files\\QUICKENW\\QWUTIL.dll") not found
wine: Unhandled exception 0xc06d007e at address 0x7b839d72 (thread 0045), starting debugger...

```

Any help would be much appreciated.

Thanks very much,
Jim Lee

---


---
title: "office 2007 installation crashes (wine 1.1.8)"
date: 2008-11-20
forum: Wine
---

### Post by ehudros on 2008-11-20
Hi everyone,
On Ubuntu 8.10 with Wine 1.1.8 I can't get Office 2007 setup to start (it crashes immediately).

In the setup log it shows the following:

----------------------------------------------------
PERF: TickCount=7068 Name=OBootStrapper::Run Description=Begin function

Operating System version: 5.1.2600 Service Pack 2. Platform ID: 2

Running on a 32-bit operating system.

Command line: "Z:\home\noa\Desktop\office\setup.exe"

No command line arguments given

Verify file signature in "Z:\home\noa\Desktop\office\setup.exe"

Using setup controller dll at [Z:\home\noa\Desktop\office\Enterprise.WW\OSETUP.DLL].

Opening log file C:\windows\temp\SetupExe(2008112000462816).log.

=========================================================================

...
Searching for updated versions of resource files under the 'updates' folder [Z:\home\noa\Desktop\office\updates].

Found [0] resource files under the update folder.

Searching for default versions of resource files under the folder [Z:\home\noa\Desktop\office].

Resource File Manager : Found (CultureTag=en-US) resource file at [Z:\home\noa\Desktop\office\Office.en-us\OSETUPUI.DLL].

Found [1] resource files under the default folder.

Resource File Manager : Current user's LCID is [1033].

Resource File Manager : Selecting resource file (File=Z:\home\noa\Desktop\office\Office.en-us\OSETUPUI.DLL) for CultureTag [en-US].

Running in [InstallExecutionMode]. Run from TEMP folder at [C:\windows\temp\Setup00000016].

Loaded resource file [C:\windows\temp\Setup00000016\OSETUPUI.DLL] (CultureTag=en-US).

Loaded Dll : Z:\home\noa\Desktop\office\Enterprise.WW\OSETUP.DLL.

Catalyst version is : 12.0.4518.1014

JobExecutionMode is InstallExecutionMode.

Error: Failed to set image property image ID: 405 Type: UnexpectedError.

Catalyst execution finished: 11/20/2008 00:46:29. Return code: 30088. Exception caught: UnexpectedError.

PERF: TickCount=13693 Name=RunSetup Description=End function

=========================================================================

Any thoughts? What am I doing wrong? Should I use winetricks to install .net 2.0 etc.?

Thanks!

---

### Post by gjoellee on 2008-11-20
Wine 1.1.8 is a development version...the latest stable version is WINE 1.0.1 try using that version....

---

### Post by rukie on 2008-11-26
I have the same problem
Ubuntu 8.10
wine version 1.0.1 though
I also have crossover office and it gives the same exact error



I HAD it installed successfully before but I accidentally deleted by .wine directory, and can't reinstall it now.

---

### Post by Joemomma69 on 2009-01-04
Exact same issue ... tried 1.0.1 and 1.1.12 as well.

Anyone figured this out yet?

Thanks!

---


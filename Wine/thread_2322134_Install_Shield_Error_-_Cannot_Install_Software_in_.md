---
title: "Install Shield Error - Cannot Install Software in Wine"
date: 2016-04-26
forum: Wine
---

### Post by wagb278 on 2016-04-26
Running Ubuntu-MATE 16.04 and trying to install Ancestral Quest 14 in Wine-1.6.2. When running the application install EXE file I result with the Error: 1621 Failed to verify signature of isscript.msi.  I suspect something is wrong with Ubuntu-MATE 16.04 because this install has worked on all previous Ubuntu (most recently Ubuntu-MATE 15.10) and Linux Mint versions - never had this .msi file error before.  Could there be some certificate missing in Ubuntu 16.04?  I don't pretend to understand any of this I just know the Ancestral Quest Windows application ran fine under other distributions. 

One thing I did differently this time I installed PlayOnLinux (which includes Wine) and before I have only installed basic Wine.  Could that have anything to do with it?  - _EDIT_: I removed and reinstalled Wine three times using different install methods (PlayOnLinux, PPA method, and Ubuntu Software Center) all methods gave the same result. The application would not install giving the same Install Shield error. 

If I can help provide any information please ask.  I really need this (Ancestral Quest) to run in Linux - it's the only Windows app I need, and like I said I have never had any problems before. 

**EDIT**: I solved this by copying the ~/.wine folder from my Ubuntu 15.10 partition to the Ubuntu 16.04 partition (after saving what was there for safety).  Then the App's installation file (Install Shield wizard) would run.  The .wine folder on Ubuntu 15.10 included the Install Shield files where as the one on Ubuntu 16.04 did not.  I selected to perform the Repair action in the wizard and because my files on both distributions match - after the repair the application was installed and ran as desired.  Thank my foresight for maintaining multiple disk partitions of Linux distributions. 

Thanks

---

### Post by sweldon001 on 2016-05-12
you need to run on terminal wine winetricks  then follow image then prompt to install msi and mfc component as well as directx items .. 
Here main GUI for start of istall of this above mentioned  [https://www.therepopulation.com/wiki/lib/exe/fetch.php/repop_linux_008.png](https://www.therepopulation.com/wiki/lib/exe/fetch.php/repop_linux_008.png)

---


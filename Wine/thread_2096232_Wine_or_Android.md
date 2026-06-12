---
title: "Wine or Android"
date: 2012-12-19
forum: Wine
---

### Post by Cyber72 on 2012-12-19
I will be using some software which is compatible with Windows 7 and 8 and an Android version is promised soon (it is to run a Janty Mid which won't mean anything to you unless you are a vaper - smoker turned nicotine inhaler). 

I have never used Wine.  Does it bring any vulnerability to Windows viruses and malware? If it does I may well install a second linux OS just for wine and dual boot, so advise please if there is a Linux known to work  particularly well with Wine & Windows. Sorry but I'm alergic to Microsoft.

Would I be better using the Android version - I haven't a touch screen.

---

### Post by Cyber72 on 2012-12-19
I should have said I have Ubuntu 12.10.

---

### Post by Lila7714 on 2012-12-24
With wine you don't have to worry about windows viruses and malware. You really don't need a second Linux OS.

As I am unaware of that particular software I can't say if the android version would be better. Whatever works and is more convenient.

---

### Post by haqking on 2012-12-24
> **Lila7714 said:**
> With wine you don't have to worry about windows viruses and malware. You really don't need a second Linux OS.
.

[http://wiki.winehq.org/FAQ#head-3cb8f054b33a63be30f98a1b6225d74e305a0459](http://wiki.winehq.org/FAQ#head-3cb8f054b33a63be30f98a1b6225d74e305a0459)

> **11.1. Wine is malware-compatible**

 Just because Wine runs on a non-Windows OS doesn't mean you're protected from viruses, trojans, and other forms of malware. 
There are several things you can do to protect yourself: 

[LIST]
[*]Never run executables from sites you don't trust. [Infections have already happened.]("http://www.winehq.org/pipermail/wine-devel/2007-January/053719.html") 
[*]In web browsers and mail clients, be suspicious of links to URLs you don't understand and trust. 
[*]Never run any application (including Wine applications) as root (see [above]("http://wiki.winehq.org/FAQ#run_as_root")). 
[*]Use a virus scanner, e.g. [ClamAV]("http://www.clamav.org") is a free virus scanner you might consider using if you are worried about an infection; see also [Ubuntu's notes on how to use ClamAV]("https://help.ubuntu.com/community/ClamAV"). No virus scanner is 100% effective, though. 
[*]Consider  removing the default Wine Z: drive, which maps to the unix root  directory. This is only a weak defense, but it might help against some  attacks. The downside to this is you **won't be able to run  Windows applications that aren't reachable from a Wine drive (like C: or  D:). This includes inability to install wine-gecko (see [bug 19873]("http://bugs.winehq.org/show_bug.cgi?id=19873")).**  A workaround is to copy/move/symlink downloaded installers to ~/.wine/drive_c before you can run them. 
[*]If you're running applications that you suspect to be infected, run them as their own Linux user or in a virtual machine (the [ZeroWine]("http://wiki.winehq.org/ZeroWine") malware analyzer works this way). 
[/LIST]


---

### Post by N00b-un-2 on 2012-12-24
There is no way to currently run Android apps on Linux, at least not in any way that has acceptable performance (the AVD manager that comes with the SDK).  The Android emulator suffers from terrible performance.

As far as Windows security issues on WINE, yes.  It is perfectly possible to get a WINE installation infected with Windows malware, however these issues are specific to WINE, meaning that a Windows virus infecting Windows software on WINE is incapable of affecting the function of your Linux system in any way.  Fixing the issue is as simple as uninstalling WINE and deleting the .wine directory from your /home.

You may want to look into VirtualBox or some other virtualization software.  I avoid using WINE whenever possible as I find it to be problematic, buggy and generally a poor substitute for an actual Windows system.  Especially if it's going to be running something that could potentially have serious negative health side effects such as your nicotine vapor inhaler.

---

### Post by haqking on 2012-12-24
> **N00b-un-2 said:**
> There is no way to currently run Android apps on Linux, at least not in any way that has acceptable performance (the AVD manager that comes with the SDK).  The Android emulator suffers from terrible performance.

As far as Windows security issues on WINE, yes.  It is perfectly possible to get a WINE installation infected with Windows malware, however these issues are specific to WINE, meaning that a Windows virus infecting Windows software on WINE is incapable of affecting the function of your Linux system in any way.  Fixing the issue is as simple as uninstalling WINE and deleting the .wine directory from your /home.

You may want to look into VirtualBox or some other virtualization software.  I avoid using WINE whenever possible as I find it to be problematic, buggy and generally a poor substitute for an actual Windows system.  Especially if it's going to be running something that could potentially have serious negative health side effects such as your nicotine vapor inhaler.

Windows malware affecting Windows software is of no issue to Linux - Correct.

However Windows malware can be written to target the Linux kernel with system calls if written for purpose using the wine interpreter.

The likelihood is rare, however it is something to be aware of and not dismissed.

not forgetting some people use and run WINE as root ;-)

---

### Post by Cyber72 on 2013-01-12
Many thanks

---


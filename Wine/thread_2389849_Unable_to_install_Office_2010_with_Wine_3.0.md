---
title: "Unable to install Office 2010 with Wine 3.0"
date: 2018-04-22
forum: Wine
---

### Post by redmage123 on 2018-04-22
Hello all, 

I have been trying to install Microsoft Office 2010 32 bit on my Ubuntu 17.10 system with Wine 3.0.  The problem is that the setup crashes midway through the installation.  
I had Microsoft Office installed on a previous installation using Ubuntu 14.10, but since then, I've had absolutely no luck in installing Office on any version of Ubuntu Linux
after that.  

The installation gives me an unhandled exception and prints out a large stack trace.  

I've also tried PlayOnLinux and I've tried different versions of Office (2013, 2016) but I have had absolutely no luck.  I can't understand why
I was able to install in 14.04 and the functionality has been broken ever since. 

Has anyone been able to successfully install Office 2010 on Ubuntu 17.x?  

thanks,

---

### Post by armrek on 2018-04-22
Have you tried to install it on  18.04?

This might be bad advice since I also have problems doing the same with Paint Shop Pro 8 on that Ubuntu version :-)

---

### Post by luizluca on 2018-05-26
I can use an installation from a previous Ubuntu (using playonlinux) but I cannot install a fresh one.
It crashes while installing SingleImageWW.msi and returns error code 1603

I'm doing:

apt install libwbclient0:i386
sudo systemctl start winbind
WINEPREFIX=~/.local/share/wineprefixes/Office2010 WINEARCH=win32 wineserver -k
rm -Rf ~/.local/share/wineprefixes/Office2010
WINEPREFIX=~/.local/share/wineprefixes/Office2010 WINEARCH=win32 winetricks corefonts dotnet20 msxml6
WINEPREFIX=~/.local/share/wineprefixes/Office2010 WINEARCH=win32 winetricks settings winxp
cd /media/$USER/OFFICE14/x86
WINEPREFIX=~/.local/share/wineprefixes/Office2010 WINEARCH=win32 wine setup.exe

You can monitor installation using:

tail -f  ~/.local/share/wineprefixes/Office2010/drive_c/users/*/Temp/SetupExe*.log

Someplaces says I need winbind 32bit (while I installed 64-bit one). However, there is too much dependencies to replace it. I will simply touch too much stuff

---


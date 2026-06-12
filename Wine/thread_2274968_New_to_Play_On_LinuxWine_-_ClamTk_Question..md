---
title: "New to Play On Linux/Wine - ClamTk Question."
date: 2015-04-23
forum: Wine
---

### Post by 77_GCSX on 2015-04-23
I just started messing around with Play On Linux/Wine. The ONLY MS program I have installed to use is IE8. Now, when I check my ClamTk scan history I come up with the following:

  	 	 	 	   /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/winsxs/x86_microsoft.windows.common-controls_6595b64144ccf1df_6.0.2600.2982_none_deadbeef/comctl32.dll: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/Microsoft.NET/Framework/v4.0.30319/mscorlib.dll: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/Microsoft.NET/Framework/v1.1.4322/mscorlib.dll: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/Microsoft.NET/Framework/v2.0.50727/mscorlib.dll: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/Installer/c29b.msi: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/Installer/204f.msi: PUA.Win32.Packer.Msvcpp FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/mono/mono-2.0/lib/mono/4.5/mscorlib.dll: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/mono/mono-2.0/lib/mono/4.5/monop.exe: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/mono/mono-2.0/lib/mono/4.0/mscorlib.dll: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/mono/mono-2.0/lib/mono/2.0/mscorlib.dll: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/mono/mono-2.0/lib/mono/2.0/monop.exe: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/mono/mono-2.0/lib/mono/gac/Novell.Directory.Ldap/2.0.0.0__0738eb9f132ed756/Novell.Directory.Ldap.dll: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/mono/mono-2.0/bin/libmono-2.0-x86_64.dll: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/mono/mono-2.0/bin/MonoPosixHelper-x86_64.dll: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/system32/xmllite.dll: PUA.Win32.Packer.Msvcpp FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/system32/shlwapi.dll: PUA.Win32.Packer.MsVisualCpp-2 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/system32/gecko/2.24/wine_gecko/gkmedias.dll: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/system32/msimtf.dll: PUA.Win32.Packer.MsVisualCpp-2 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/system32/wininet.dll: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/system32/clock.exe: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/system32/inetcpl.cpl: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/system32/browseui.dll: PUA.Win32.Packer.MsVisualCpp-2 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/system32/comctl32.dll: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/system32/msctf.dll: PUA.Win32.Packer.MsVisualCpp-2 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/system32/user32.dll: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/system32/riched20.dll: PUA.Win32.Packer.MsVisualCpp-2 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/system32/shdocvw.dll: PUA.Win32.Packer.MsVisualCpp-2 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/windows/ie8/spuninst/updspapi.dll: PUA.Win32.Packer.Msvcpp FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/users/paul1/Local Settings/Temporary Internet Files/Content.IE5/Y275SPOG/hkcu_internetexplorer[0]: PUA.Win32.Packer.Upx-48 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/users/paul1/Local Settings/Temporary Internet Files/Content.IE5/AQD82BB8/hkcu_internetexplorer[1]: PUA.Win32.Packer.Upx-48 FOUND 
 /home/paul1/.PlayOnLinux/wineprefix/InternetExplorer8/drive_c/users/paul1/Local Settings/Temporary Internet Files/Content.IE5/2ALIV8J1/hkcu_internetexplorer[1]: PUA.Win32.Packer.Upx-48 FOUND 
 /home/paul1/.PlayOnLinux/ressources/xmllite.dll: PUA.Win32.Packer.Msvcpp FOUND 
 /home/paul1/.PlayOnLinux/ressources/InstMsiW.exe: PUA.Win32.Packer.Armadillo-59 FOUND 
 /home/paul1/.PlayOnLinux/ressources/ie7-dlls.tar.bz2: PUA.Win32.Packer.Msvcpp FOUND 
 /home/paul1/.PlayOnLinux/ressources/IE8-WindowsXP-x86-ENU.exe: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/ressources/msxml3/msxml3.msi: PUA.Win32.Packer.Msvcpp FOUND 
 /home/paul1/.PlayOnLinux/wine/gecko/wine_gecko-2.24-x86.msi: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wine/linux-x86/1.7.22/lib/wine/fakedlls/clock.exe: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wine/linux-x86/1.7.22/lib/wine/fakedlls/comctl32.dll: PUA.Win32.Packer.PrivateExeProte-7 FOUND 
 /home/paul1/.PlayOnLinux/wine/linux-x86/1.7.22/lib/wine/fakedlls/user32.dll: PUA.Win32.Packer.PrivateExeProte-7 FOUND

_**Is this NORMAL for ALL of this to be considered a Threat? Or did I some how mess things up and installed something REALLY bad?**_


I am using Ubuntu 14.04 LTS 64 Bit

Thanks in advance,
Paul

---

### Post by Mark Phelps on 2015-04-24
Sorry, but if it is your intent to use IE through Wine for any serious work, be prepared to be frustrated to no end!  The WineHQ web page shows that most of the ratings for IE versions are among the worst you can have (Bronze) -- which makes using IE essentially a waste of your time: [https://appdb.winehq.org/objectManager.php?sClass=application&iId=25]("https://appdb.winehq.org/objectManager.php?sClass=application&iId=25")

---

### Post by 77_GCSX on 2015-04-24
Nothing real important - Just trying to see if I can get it to work so my daughter could continue to play Roblox. 

No great loss if it doesn't work out..

Thanks!

---


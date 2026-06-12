---
title: "trying to install MS Office Starter 2010 on wine"
date: 2015-02-14
forum: Wine
---

### Post by timeofday on 2015-02-14
Microsoft Office Starter 2010 is a free reduced-functionality version of Office 2010 from MS, intended mainly for reading Word docs etc. but with some editing functions thrown in.  I'm trying to install it in a fresh 32-bit wineprefix that I've loaded (using winetricks) with .NET 4.5, Direct X 9, and relevant fonts and dlls.  (I have Xubuntu 14.04.1). When I run the Office Starter 2010 installer from the terminal, I get:

```
fixme:wer:WerSetFlags (2) stub!
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:process:SetProcessShutdownParameters (00000380, 00000000): partial stub.
fixme:advapi:EventRegister {8736922d-e8b2-47eb-8564-23e77e728cf3}, 0x2e037798, 0x2e10b280, 0x2e10b278
fixme:ntdll:NtQueryInformationToken QueryInformationToken( ..., TokenElevation, ...) semi-stub
fixme:imm:ImmDisableIME (41): stub
fixme:dwmapi:DwmIsCompositionEnabled 0x93e518
fixme:nls:CompareStringEx semi-stub behavor for flag(s) 0x10000000
fixme:nls:CompareStringEx semi-stub behavor for flag(s) 0x10000000
fixme:nls:CompareStringEx semi-stub behavor for flag(s) 0x10000000
fixme:nls:CompareStringEx semi-stub behavor for flag(s) 0x10000000
fixme:nls:CompareStringEx semi-stub behavor for flag(s) 0x10000000
fixme:nls:CompareStringEx semi-stub behavor for flag(s) 0x10000000
fixme:nls:CompareStringEx semi-stub behavor for flag(s) 0x10000000
fixme:nls:CompareStringEx semi-stub behavor for flag(s) 0x10000000
fixme:nls:CompareStringEx semi-stub behavor for flag(s) 0x10000000
fixme:bcrypt:BCryptOpenAlgorithmProvider 0x32e650, L"\d30c\0013\d2ac\0013\333b\3a31(", (null), 00000000 - stub
fixme:service:QueryServiceConfig2W Level 6 not implemented
fixme:service:QueryServiceConfig2W Level 6 not implemented
fixme:service:QueryServiceConfig2W Level 6 not implemented
fixme:service:QueryServiceConfig2W Level 6 not implemented
fixme:service:QueryServiceConfig2W Level 6 not implemented
fixme:ntdll:NtQueryInformationToken QueryInformationToken( ..., TokenElevation, ...) semi-stub


```

And the MS GUI installer stops with this message: "A file required to set up Microsoft Office Starter 2010 is corrupted. Try running Setup again. If the problem continues, contact your computer manufacturer for support." (Of course if I run the Office Starter 2010 Setup again, I get the same result.)

I only see "fixme"s, no huge errors. So what's going wrong here?

---

### Post by ian-weisser on 2015-02-14
'fixme' looks like a huge error to me. "Hey, this doesn't work, and I know it"
Unless you want to do a lot of coding and replace those stubs with real functions, I suspect your software is as-yet incompatible with Wine.

---

### Post by pfeiffep on 2015-02-15
> **timeofday said:**
> Microsoft Office Starter 2010 is a free reduced-functionality version of Office 2010 from MS, intended mainly for reading Word docs etc. but with some editing functions thrown in.  I'm trying to install it in a fresh 32-bit wineprefix that I've loaded (using winetricks) with .NET 4.5, Direct X 9, and relevant fonts and dlls.  (I have Xubuntu 14.04.1). When I run the Office Starter 2010 installer from the terminal, I get:

And the MS GUI installer stops with this message: "A file required to set up Microsoft Office Starter 2010 is corrupted. Try running Setup again. If the problem continues, contact your computer manufacturer for support." (Of course if I run the Office Starter 2010 Setup again, I get the same result.)

I only see "fixme"s, no huge errors. So what's going wrong here?I respectfully suggest that you try to use Libre Office - I've found that it reads and writes most MS Office file formats.

---

### Post by timeofday on 2015-02-16
@pfeiffep:
Yes, I use LibreOffice and love it. It serves me for 99% of all I do.  But I have a home office and deal extensively with Word docs and there's the rare time that LibreOffice doesn't correctly render the Word doc.  Thus my desire to have a free MS reader.

@ian-weisser
Oh well, I guess you're right.  I have one other possible approach to try.  Apparently, if Office Starter 2010 is installed on a Windows computer, one can make a "portable" version of the application.  That would allow me to avoid the MS installer, and perhaps the portable version itself would run in Wine.  I have no Windows computers in my house, so I'll have to bug a friend.  :)

---

### Post by Mark Phelps on 2015-02-16
Sorry this is an OLD link, but it's the only one I had that explains how to install MS Office 2010: [http://ubuntuforums.org/showthread.php?t=1885051]("http://ubuntuforums.org/showthread.php?t=1885051")

---

### Post by SeijiSensei on 2015-02-16
One alternative if you only need to view Word documents rather than edit them is the [stand-alone Word viewer]("http://support.microsoft.com/kb/891090").  I don't know how well it runs in Wine, but you could give that a shot.

---

### Post by timeofday on 2015-02-17
@SeijiSensei:  Thanks for the tip -- so I just installed the standalone Word viewer on Wine and it works, although one .docx file I have looks kinda weird in it somehow. So time will tell.  I think I'm also going to try installing the latest 4.4 version of LibreOffice (I currently have 4.2.7.2), which supposedly has improved .docx rendering.

---

### Post by bashiergui on 2015-02-17
Another option is to install Windows in a virtual machine and put the word viewer in there. I haven't found a linux word processor that converts MS documents consistently enough for my tastes.

---

### Post by mastablasta on 2015-02-19
really...

It says here: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=17336](https://appdb.winehq.org/objectManager.php?sClass=version&iId=17336)

> **Make sure all dependencies of Wine are installed on your system, including winbind.     **

Install Office 2010 to a clean wineprefix--no winetricks or other tweaks, and no other applications installed. Do not change the Windows version in winecfg; it should remain at the default setting of XP. 


and here is what you did:

> **timeofday said:**
> Microsoft Office Starter 2010 is a free reduced-functionality version of Office 2010 from MS, intended mainly for reading Word docs etc. but with some editing functions thrown in.  I'm trying to install it in a fresh 32-bit wineprefix that I've loaded [COLOR=#FF0000][SIZE=4]**(using winetricks) **[/SIZE][/COLOR]with .NET 4.5, Direct X 9, and relevant fonts and dlls.  (I have Xubuntu 14.04.1). When I run the Office Starter 2010 installer from the terminal, I get:



I wouldn't know about this starter version for sure, but I know 2010 works. not perfectly, but it works.

---

### Post by Fincer on 2015-02-19
The following method has always worked with MS Office 2010 programs (even Visio & Project Professional):

```
WINEPREFIX=$HOME/.wine_msoffice/ WINEARCH=win32 winetricks dotnet20 comctl32 ie6 msls31 msxml3 msxml6 pngfilt riched20 riched30 vcrun2005
```

and then run your Office starter setup:

```
WINEPREFIX=$HOME/.wine_msoffice/ wine *pathtomyofficesetup.exe*
```

As far as I can tell by experience, MS Office 2010 installer is extremely sensitive about the stuff you have inside your prefix, so use only a clean prefix. Your current prefix has already garbage inside, so delete it completely and do a fresh start. :)

I hope this helps.

Regards,
Fincer

---


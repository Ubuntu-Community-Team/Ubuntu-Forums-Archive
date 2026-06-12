---
title: "Ies4linux is Not Work in Kubuntu 64-bit"
date: 2008-01-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Darll on 2008-01-27
I Install Kubuntu 64-bit on my computer

and i can't make iexplore work, i success to install the 34-bit version, but it's not work, i can see only the icons but i can't go to any page.
that what i get:
```
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias -120, std (d/m/y): 5/10/2008, dlt (d/m/y): 28/03/2008
err:shell:ReadCabinetState Initializing shell cabinet settings
fixme:shell:DllGetClassObject failed for CLSID=
        {53bd6b4e-3780-4693-afc3-7161c2f3ee9c} (MruLongList)
err:rebar:REBAR_WindowProc unknown msg 200b wp=00000000 lp=71180f00
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:shell:NTSHChangeNotifyRegister (0x10034,0x00008003,0x00008000,0x0000c074,0x00000001,0x34dbec):semi stub.
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x10034, wParam=0x00000000, size.cx=1280, size.cy=32000 stub!
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_Unkwn464 hwnd=0x10038 wParam 00000001 lParam 00000000
fixme:dpa:DPA_LoadStream phDpa=0x34d628 loadProc=0x8aba1c pStream=0x148230 lParam=141858
fixme:dpa:DPA_LoadStream dwSize=0 dwData2=0 dwItems=0
fixme:dpa:DPA_LoadStream new hDpa=0x141800, errorcode=80004005
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x1004e, wParam=0x00000000, size.cx=1280, size.cy=1020 stub!
fixme:shell:NTSHChangeNotifyRegister (0x1004e,0x00008003,0x0c02b7ff,0x0000c074,0x00000001,0x34dc2c):semi stub.
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias -120, std (d/m/y): 5/10/2008, dlt (d/m/y): 28/03/2008
fixme:shell:DllGetClassObject failed for CLSID=
        {871c5380-42a0-1069-a2ea-08002b30309d} (Internet Explorer)
fixme:shell:NTSHChangeNotifyRegister (0x10028,0x00008003,0x0003f5f4,0x00000410,0x00000001,0x34ea88):semi stub.
fixme:shell:SignalFileOpen (0x00000000):stub.
fixme:shell:DllGetClassObject failed for CLSID=
        {871c5380-42a0-1069-a2ea-08002b30309d} (Internet Explorer)
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x34bc78)
fixme:shell:DllGetClassObject failed for CLSID=
        {871c5380-42a0-1069-a2ea-08002b30309d} (Internet Explorer)
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!

```
And that the window i get
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=57786&stc=1&d=1201456799[/IMG]

Can i fix it? :confused:

Thank you :)

---

### Post by Darll on 2008-01-27
someone?

---

### Post by kyleabaker on 2008-01-27
@Darll
This is apparently a problem with newer versions of Wine. There is a fix here..
[http://ubuntuforums.org/showthread.php?t=670662](http://ubuntuforums.org/showthread.php?t=670662)

---


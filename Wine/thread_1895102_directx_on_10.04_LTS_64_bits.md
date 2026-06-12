---
title: "directx on 10.04 LTS 64 bits"
date: 2011-12-14
forum: Wine
---

### Post by p.cuica on 2011-12-14
hi guys!

I have Ubuntu 10.04 LTS 64 bits and I've tried to install directx using winetricks and this was the result:
```

pazevedo@pazevedo-laptop:~$ sh winetricks directx9
Executing w_do_call directx9
Executing load_directx9
Executing mkdir -p /home/pazevedo/.cache/winetricks/directx9
Downloading [http://download.microsoft.com/download/E/E/1/EE17FF74-6C45-4575-9CF4-7FC2597ACD18/directx_feb2010_redist.exe](http://download.microsoft.com/download/E/E/1/EE17FF74-6C45-4575-9CF4-7FC2597ACD18/directx_feb2010_redist.exe) to /home/pazevedo/.cache/winetricks/directx9
--2011-12-14 08:22:06--  [http://download.microsoft.com/download/E/E/1/EE17FF74-6C45-4575-9CF4-7FC2597ACD18/directx_feb2010_redist.exe](http://download.microsoft.com/download/E/E/1/EE17FF74-6C45-4575-9CF4-7FC2597ACD18/directx_feb2010_redist.exe)
Connecting to 10.159.32.155:8080... connected.
Proxy request sent, awaiting response... 200 OK
Length: 109072752 (104M) [application/octet-stream]
Saving to: `directx_feb2010_redist.exe'

100%[======================================>] 109,072,752 82.3K/s   in 13m 59s 

2011-12-14 08:36:06 (127 KB/s) - `directx_feb2010_redist.exe' saved [109072752/109072752]

------------------------------------------------------
You probably shouldn't be using this.  d3dx9 or, better, d3dx9_36 usually suffice.
------------------------------------------------------
Setting Windows version to winxp
Executing winetricks_early_wine regedit C:\windows\Temp\_directx9\set-winver.reg
Executing wine directx_feb2010_redist.exe /t:C:\windows\Temp\_directx9
fixme:advapi:DecryptFileA "C:\\windows\\Temp\\_directx9\\" 00000000
Using native override for following DLLs: d3dim d3drm d3dx8 d3dx9_24 d3dx9_25 d3dx9_26 d3dx9_27 d3dx9_28 d3dx9_29
Executing winetricks_early_wine regedit C:\windows\Temp\_directx9\override-dll.reg
Using native override for following DLLs: d3dx9_30 d3dx9_31 d3dx9_32 d3dx9_33 d3dx9_34 d3dx9_35 d3dx9_36 d3dx9_37
Executing winetricks_early_wine regedit C:\windows\Temp\_directx9\override-dll.reg
Using native override for following DLLs: d3dx9_38 d3dx9_39 d3dx9_40 d3dx9_41 d3dx9_42 d3dx9_43 d3dxof
Executing winetricks_early_wine regedit C:\windows\Temp\_directx9\override-dll.reg
Using native override for following DLLs: dciman32 ddrawex devenum dmband dmcompos dmime dmloader dmscript dmstyle
Executing winetricks_early_wine regedit C:\windows\Temp\_directx9\override-dll.reg
Using native override for following DLLs: dmsynth dmusic dmusic32 dnsapi dplay dplayx dpnaddr dpnet dpnhpast dpnlobby
Executing winetricks_early_wine regedit C:\windows\Temp\_directx9\override-dll.reg
Using native override for following DLLs: dswave dxdiagn msdmo qcap quartz streamci
Executing winetricks_early_wine regedit C:\windows\Temp\_directx9\override-dll.reg
Using native override for following DLLs: dxdiag.exe
Executing winetricks_early_wine regedit C:\windows\Temp\_directx9\override-dll.reg
Using builtin override for following DLLs: d3d8 d3d9 dinput dinput8 dsound
Executing winetricks_early_wine regedit C:\windows\Temp\_directx9\override-dll.reg
Executing wine C:\windows\Temp\_directx9\DXSETUP.exe
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
```

I've tried to execute the dxdiag.exe with wine but it doens't open.
any ideas?

many thanks!

---

### Post by Mark Phelps on 2011-12-14
So, why are you installing DirectX 9 when most of the new Windows games require DX 10 or better to work, and your video card driver has to support DX at that level or better, as well?

Not a Wine expert (Use Windows for Windows stuff, not Linux), so am requesting this thread be moved to the Wine section -- where you're likely to get better results.

---

### Post by Iowan on 2011-12-14
Moved to Wine.

---

### Post by negatorative on 2011-12-15
You do not install directx in wine. wine provides its own implementation, and using the native directx will just break your prefix. Supporting dlls, such as those found in the d3dx9 winetricks entry are fine though.

direct3d in wine also does not rely on your video card in the same way that it does in windows. through wine it just links back to opengl, so if your card adequately supports opengl then you're not going to have any issues. if it doesn't, then get a clue.

---


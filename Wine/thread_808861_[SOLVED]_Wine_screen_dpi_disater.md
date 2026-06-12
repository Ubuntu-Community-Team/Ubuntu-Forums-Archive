---
title: "[SOLVED] Wine screen dpi disater"
date: 2008-05-26
forum: Wine
---

### Post by SteveNorman on 2008-05-26
So im screwing around with wine,,,and in configure>graphics I slide the slider all the way to the right to see if it will make a game window larger. Now I cant  get the configure screen small enough to slide it back to the left. Is there a way to do it via the command line?

---

### Post by schtufbox on 2008-05-26
in your .wine folder you need to open system.reg file in a text editor like gedit ( MAKE SURE YOU MAKE A COPY OF THE FILE FIRST JUST IN CASE )
find the part below either by a search within the text editor or scrolling til you find it :
```

[System\\CurrentControlSet\\Hardware Profiles\\Current\\Software\\Fonts]

```

under that there should be a "LogPixels"  entry, edit it so it is the same as below:

```

[System\\CurrentControlSet\\Hardware Profiles\\Current\\Software\\Fonts]
"LogPixels"=dword:00000060

```

You want to make sure that the log pixels entry is as above, this will reset wine to use 96dpi for fonts.
Then save and run winecfg to check it worked.

The "00000060" is actualy in hex - 0x60 = 96.

---

### Post by SteveNorman on 2008-05-27
Im not seeing the file,,here is my ls -a results in wine[PHP]/usr/lib/wine$ ls -a
.                itss.dll.so          libusp10.def     rsabase.dll.so
..               jscript.dll.so       libuuid.a        rsaenh.dll.so
acledit.dll.so   kernel32.dll.so      libuxtheme.def   rundll32.exe.so
activeds.dll.so  keyboard.drv16       libvdmdbg.def    sane.ds.so
actxprxy.dll.so  krnl386.exe16        libversion.def   sccbase.dll.so
advapi32.dll.so  libactiveds.def      libwinecrt0.a    schannel.dll.so
advpack.dll.so   libadsiid.a          libwined3d.def   secedit.exe.so
amstream.dll.so  libadvapi32.def      libwinedos.def   secur32.dll.so
atl.dll.so       libadvpack.def       libwininet.def   security.dll.so
avicap32.dll.so  libatl.def           libwinmm.def     sensapi.dll.so
avifil32.dll.so  libavicap32.def      libwinnls32.def  serialui.dll.so
avifile.dll16    libavifil32.def      libwinscard.def  services.exe.so
browseui.dll.so  libcabinet.def       libwinspool.def  setupapi.dll.so
cabinet.dll.so   libcapi2032.def      libwintab32.def  setupx.dll16
capi2032.dll.so  libcards.def         libwintrust.def  sfc.dll.so
cards.dll.so     libcfgmgr32.def      libwldap32.def   sfc_os.dll.so
cfgmgr32.dll.so  libclusapi.def       libwnaspi32.def  shdoclc.dll.so
clock.exe.so     libcomctl32.def      libwow32.def     shdocvw.dll.so
clusapi.dll.so   libcomdlg32.def      libws2_32.def    shell32.dll.so
cmd.exe.so       libcompstui.def      libwsock32.def   shell.dll16
comcat.dll.so    libcredui.def        libwtsapi32.def  shfolder.dll.so
comctl32.dll.so  libcrtdll.def        localspl.dll.so  shlwapi.dll.so
comdlg32.dll.so  libcrypt32.def       localui.dll.so   slbcsp.dll.so
commdlg.dll16    libcryptdll.def      lz32.dll.so      slc.dll.so
comm.drv16       libcryptnet.def      lzexpand.dll16   snmpapi.dll.so
compobj.dll16    libctl3d32.def       mapi32.dll.so    softpub.dll.so
compstui.dll.so  libd3d8.def          mciavi32.dll.so  sound.drv16
control.exe.so   libd3d9.def          mcicda.dll.so    spoolss.dll.so
credui.dll.so    libd3dim.def         mciseq.dll.so    spoolsv.exe.so
crtdll.dll.so    libd3drm.def         mciwave.dll.so   start.exe.so
crypt32.dll.so   libd3dx8.def         midimap.dll.so   stdole2.tlb.so
cryptdlg.dll.so  libd3dx9.def         mlang.dll.so     stdole32.tlb.so
cryptdll.dll.so  libd3dxof.def        mmdevldr.vxd.so  sti.dll.so
cryptnet.dll.so  libdbghelp.def       mmsystem.dll16   storage.dll16
ctapi32.dll.so   libdciman32.def      monodebg.vxd.so  stress.dll16
ctl3d32.dll.so   libddraw.def         mountmgr.sys.so  svchost.exe.so
ctl3d.dll16      libdinput8.def       mouse.drv16      svrapi.dll.so
ctl3dv2.dll16    libdinput.def        mprapi.dll.so    sxs.dll.so
d3d10.dll.so     libdinput.def.a      mpr.dll.so       system.drv16
d3d8.dll.so      libdmusic32.def      msacm32.dll.so   tapi32.dll.so
d3d9.dll.so      libdnsapi.def        msacm32.drv.so   taskmgr.exe.so
d3dim.dll.so     libdplay.def         msacm.dll16      toolhelp.dll16
d3drm.dll.so     libdplayx.def        msadp32.acm.so   twain_32.dll.so
d3dx8.dll.so     libdpnet.def         mscat32.dll.so   twain.dll16
d3dx9_24.dll.so  libdsound.def        mscms.dll.so     typelib.dll16
d3dx9_25.dll.so  libdwmapi.def        mscoree.dll.so   unicows.dll.so
d3dx9_26.dll.so  libdxerr8.a          msdmo.dll.so     uninstaller.exe.so
d3dx9_27.dll.so  libdxerr9.a          msftedit.dll.so  url.dll.so
d3dx9_28.dll.so  libdxguid.a          msg711.acm.so    urlmon.dll.so
d3dx9_29.dll.so  libgdi32.def         mshtml.dll.so    user32.dll.so
d3dx9_30.dll.so  libgdiplus.def       mshtml.tlb.so    userenv.dll.so
d3dx9_31.dll.so  libglu32.def         msi.dll.so       user.exe16
d3dx9_32.dll.so  libhid.def           msiexec.exe.so   usp10.dll.so
d3dx9_33.dll.so  libhlink.def         msimg32.dll.so   uxtheme.dll.so
d3dx9_34.dll.so  libicmp.def          msimtf.dll.so    vdhcp.vxd.so
d3dx9_35.dll.so  libimagehlp.def      msisys.ocx.so    vdmdbg.dll.so
d3dx9_36.dll.so  libimm32.def         msnet32.dll.so   ver.dll16
d3dx9_37.dll.so  libinetcomm.def      msrle32.dll.so   version.dll.so
d3dxof.dll.so    libiphlpapi.def      mssip32.dll.so   vmm.vxd.so
dbghelp.dll.so   libkernel32.def      msvcirt.dll.so   vnbt.vxd.so
dciman32.dll.so  liblz32.def          msvcr71.dll.so   vnetbios.vxd.so
ddeml.dll16      libmapi32.def        msvcrt20.dll.so  vtdapi.vxd.so
ddraw.dll.so     libmlang.def         msvcrt40.dll.so  vwin32.vxd.so
ddrawex.dll.so   libmprapi.def        msvcrtd.dll.so   w32skrnl.dll.so
devenum.dll.so   libmpr.def           msvcrt.dll.so    w32sys.dll16
dinput8.dll.so   libmsacm32.def       msvfw32.dll.so   win32s16.dll16
dinput.dll.so    libmscms.def         msvidc32.dll.so  win87em.dll16
dispdib.dll16    libmsdmo.def         msvideo.dll16    winaspi.dll16
display.drv16    libmshtml.def        mswsock.dll.so   windebug.dll16
dmband.dll.so    libmsi.def           msxml3.dll.so    winealsa.drv.so
dmcompos.dll.so  libmsimg32.def       nddeapi.dll.so   wineaudioio.drv.so
dmime.dll.so     libmsvcr71.def       netapi32.dll.so  wineboot.exe.so
dmloader.dll.so  libmsvcrt20.def      net.exe.so       winebrowser.exe.so
dmscript.dll.so  libmsvcrt40.def      newdev.dll.so    winecfg.exe.so
dmstyle.dll.so   libmsvcrtd.def       notepad.exe.so   wineconsole.exe.so
dmsynth.dll.so   libmsvcrt.def        ntdll.dll.so     winecoreaudio.drv.so
dmusic32.dll.so  libmsvfw32.def       ntdsapi.dll.so   wined3d.dll.so
dmusic.dll.so    libmswsock.def       ntoskrnl.exe.so  winedbg.exe.so
dnsapi.dll.so    libnddeapi.def       ntprint.dll.so   winedevice.exe.so
dplay.dll.so     libnetapi32.def      objsel.dll.so    winedos.dll.so
dplayx.dll.so    libnewdev.def        odbc32.dll.so    wineesd.drv.so
dpnaddr.dll.so   libntdll.def         odbccp32.dll.so  winefile.exe.so
dpnet.dll.so     libntdsapi.def       ole2conv.dll16   winejack.drv.so
dpnhpast.dll.so  libntoskrnl.exe.def  ole2disp.dll16   winejoystick.drv.so
dpnlobby.dll.so  libodbc32.def        ole2.dll16       winemenubuilder.exe.so
dsound.dll.so    libodbccp32.def      ole2nls.dll16    winemine.exe.so
dssenh.dll.so    libole32.def         ole2prox.dll16   winemp3.acm.so
dswave.dll.so    liboleacc.def        ole2thk.dll16    winenas.drv.so
dwmapi.dll.so    liboleaut32.def      ole32.dll.so     wineoss.drv.so
dxdiagn.dll.so   libolecli32.def      oleacc.dll.so    winepath.exe.so
eject.exe.so     liboledlg.def        oleaut32.dll.so  wineps16.drv16
expand.exe.so    libolepro32.def      olecli32.dll.so  wineps.drv.so
explorer.exe.so  libolesvr32.def      olecli.dll16     winevdm.exe.so
faultrep.dll.so  libopengl32.def      oledlg.dll.so    winex11.drv.so
fusion.dll.so    libpdh.def           olepro32.dll.so  wing32.dll.so
gdi32.dll.so     libpowrprof.def      olesvr32.dll.so  wing.dll16
gdi.exe16        libpsapi.def         olesvr.dll16     winhelp.exe.so
gdiplus.dll.so   libquartz.def        olethk32.dll.so  winhttp.dll.so
glu32.dll.so     librasapi32.def      oleview.exe.so   wininet.dll.so
gphoto2.ds.so    libresutils.def      opengl32.dll.so  winmm.dll.so
gpkcsp.dll.so    libriched20.def      pdh.dll.so       winnls32.dll.so
hal.dll.so       librpcrt4.def        powrprof.dll.so  winnls.dll16
hhctrl.ocx.so    librsaenh.def        printui.dll.so   winoldap.mod16
hh.exe.so        libsecur32.def       progman.exe.so   winscard.dll.so
hid.dll.so       libsensapi.def       propsys.dll.so   winsock.dll16
hlink.dll.so     libserialui.def      psapi.dll.so     winspool.drv.so
hnetcfg.dll.so   libsetupapi.def      pstorec.dll.so   wintab32.dll.so
iccvid.dll.so    libsfc.def           qcap.dll.so      wintab.dll16
icinfo.exe.so    libsfc_os.def        qedit.dll.so     wintrust.dll.so
icmp.dll.so      libshdocvw.def       qmgr.dll.so      winver.exe.so
iexplore.exe.so  libshell32.def       qmgrprxy.dll.so  wldap32.dll.so
ifsmgr.vxd.so    libshfolder.def      quartz.dll.so    wmi.dll.so
imaadp32.acm.so  libshlwapi.def       query.dll.so     wnaspi32.dll.so
imagehlp.dll.so  libslc.def           rasapi16.dll16   wordpad.exe.so
imm32.dll.so     libsnmpapi.def       rasapi32.dll.so  wow32.dll.so
imm.dll16        libspoolss.def       regedit.exe.so   wprocs.dll16
inetcomm.dll.so  libsti.def           reg.exe.so       write.exe.so
infosoft.dll.so  libstrmiids.a        regsvr32.exe.so  ws2_32.dll.so
initpki.dll.so   libtapi32.def        resutils.dll.so  wsock32.dll.so
inkobj.dll.so    libunicows.def       riched20.dll.so  wtsapi32.dll.so
inseng.dll.so    liburl.def           riched32.dll.so  xcopy.exe.so
iphlpapi.dll.so  liburlmon.def        rpcrt4.dll.so
itircl.dll.so    libuser32.def        rpcss.exe.so
[/PHP]

---

### Post by schtufbox on 2008-05-27
.wine

as in /home/yourusernamehere/.wine

it's a hidden folder so either show hidden files in nautilus, or do it in the terminal

gedit /home/yourusernamehere/.wine/system.reg

---

### Post by SteveNorman on 2008-05-27
Gotcha thanks,,Ill post results tomorrow.

---

### Post by SteveNorman on 2008-05-27
got it back,,thank you very much!

---

### Post by reahjw6 on 2008-12-27
Its allways good to search for a solution.
Had the same problem and you guys saved my bacon.
Thanks to all.
Reah.

---


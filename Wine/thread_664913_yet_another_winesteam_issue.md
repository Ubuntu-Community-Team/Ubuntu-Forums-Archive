---
title: "yet another wine/steam issue"
date: 2008-01-11
forum: Wine
---

### Post by immerohnegott on 2008-01-11
well, just reinstalled ubuntu, went back to 32-bit because I was getting some issues with program compatibility and didn't feel much like haxoring half my apps to get them to play nice with the architecture.

ANYway., back to the point, I installed the latest wine .deb from their site and downloaded the steaminstall.msi. Install went fine, already had tahoma.ttf ready to go. When I go to run steam, however, the program appears to load as normal, but when it should pop up the games window or whatever, it crashes. This occurs right when the dialog pops up to install Wine Gecko, which, of course, disappears as well. I've tried installing gecko from source, but the ./configure script dies checking the mozilla gtk libs.

```
checking MOZ_GTK2_LIBS...   -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage -lpango-1.0 -lcairo -lX11 -lXfixes -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
configure: error: --enable-application=APP is required
```

also, when i try to run wine &steam from terminal, i get this 

 ```
wine Steam.exe
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:shdocvw:ViewObject_SetAdvise (0x107102d8)->(1 00000002 0x139d850)
fixme:shdocvw:PersistStreamInit_InitNew (0x107102d8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x107102d8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x107102d8)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0xefd0418)->(1 00000002 0x139d8b8)
fixme:shdocvw:PersistStreamInit_InitNew (0xefd0418)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xefd0418)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xefd0418)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x10a7c588)->(1 00000002 0x139f218)
fixme:shdocvw:PersistStreamInit_InitNew (0x10a7c588)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x10a7c588)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x10a7c588)->(ffffffff)
fixme:win:SetLayeredWindowAttributes (0x10098,0x00000000,0,2): stub!
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:dbghelp:fetch_thread_info Couldn't open thread 47 (87)

```

with the same effect on the steam gui.

any ideas?

>>>>>>>>>>>EDIT<<<<<<<<<<<<<<<<<<<

purged wine, reinstalled wine and installed steam via a copy of the old .exe installer i had lying around my backup disk. works ok now...still need to get CS:S tweaked to run just right.

---


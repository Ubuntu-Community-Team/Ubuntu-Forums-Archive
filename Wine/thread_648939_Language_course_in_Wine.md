---
title: "Language course in Wine"
date: 2007-12-24
forum: Wine
---

### Post by iopo on 2007-12-24
Hi!
there is a very last piece of software I need to run in Ubuntu before I can totally get rid of Windows: it's a french language course that costed me a furtune (it's from a company called "digital publishing").
I tried to run it with wine with no luck. When I start it from the command line I get this:

andrea@andrea-laptop:/cdrom$ wine isrf1.exe
fixme:mixer:ALSA_MixerInit No master control found on Intel ICH6 Modem, disabling mixer
fixme:htmlhelp:HtmlHelpW HH case HH_INITIALIZE not handled.
fixme:quartz:Parser_FindPin (0x1577a0)->(L"Input",0xa5fa20)
fixme:quartz:AMGetErrorTextA (80004001,0x1f609c8,512) stub
fixme:advapi:CheckTokenMembership ((nil) 0x16ad30 0x7bec256c) stub!

the file isrf1.exe is the one in the autostart of the cdrom. I tried to change windows version and sound driver but I was not alble to make it work.
Any help will be greately apreciated!
Thanks a lot

---

### Post by iopo on 2007-12-24
Hi,
I tried to solve the problem by myself. I couldn't find any thred/post describing the very same thing so I followed instructions I found here and there regarding similar problems. What I did is:

-configure wine to use the Jack audio driver
-go to ~/.wine/drive_c/windows/system32
-rename advapi32.dll advpack.dll ole32.dll oleaut32.dll quartz.dll to *.bak
-get the same files from a windows installation and put them in ~/.wine/drive_c/windows/system32
-open the wine configuration window. Under "libraries" select the same libraries mentioned above and set them to "native".

It is not working, but now I get a very diffrent message:

 ```
 andrea@andrea-laptop:~$ wine /cdrom/isrf1.exe
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:htmlhelp:HtmlHelpW HH case HH_INITIALIZE not handled.
fixme:reg:RegOpenUserClassesRoot (0xfc, 0x0, 0x2000000, 0xa5f7dc) semi-stub
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {e436ebb3-524f-11ce-9f53-0020af0ba770} 0xa5f7b0
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {e436ebb3-524f-11ce-9f53-0020af0ba770} 0xa5f75c
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {e436ebb3-524f-11ce-9f53-0020af0ba770} 0xa5f0d0
fixme:advapi:CheckTokenMembership ((nil) 0x15e0f8 0x7befe56c) stub!
```

please, this is really as far as I can go by myself. Now I need some help!
Thanks!

---

### Post by markharding557 on 2007-12-27
it is very likley you can run this on windows in virtualbox
this way you don't have to dual boot,you have the security of linux and you only have to run virtual windows when you need it

---


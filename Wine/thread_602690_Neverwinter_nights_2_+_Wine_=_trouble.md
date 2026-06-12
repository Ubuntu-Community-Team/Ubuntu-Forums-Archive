---
title: "Neverwinter nights 2 + Wine = trouble"
date: 2007-11-04
forum: Wine
---

### Post by silfer on 2007-11-04
Hi 
Is there anyone here who have a playable copy of Nwn2 (with wine)? i have used this guide :[http://appdb.winehq.org/appview.php?iVersionId=7772]("http://appdb.winehq.org/appview.php?iVersionId=7772")
I the installer is working, but when i try to start the game i get this message 
```
wine '/media/hdd5/Program Files/Atari/Neverwinter Nights 2/nwn2main.exe'
fixme:win:EnumDisplayDevicesW ((null),0,0xcdf664,0x00000000), stub!
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:dsound:DllCanUnloadNow (void): stub
``` 

I have made the registry that the guide mentioned
```

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"OffscreenRenderingMode"="fbo"
"UseGLSL"="enabled"
"VideoMemorySize"="256" 
```
as i understand it i am to place a key named Direct3d in thw wine key and make a multi string in it named DirectDrawRenderer

My gfx card is a ati radeon 1950pro (drivers with envy) and it works realy good
I use the latest source to compile wine
can someone please help me?

---

### Post by Ferrat on 2007-11-05
I'm currently  trying to get it to run with the latest update ect. 

```

wine: Call from 0x5e2968 to unimplemented function MSVCP80.dll.??0?$basic_istream@DU?$char_traits@D@std@@@std@@QAE@PAV?$basic_streambuf@DU?$char_traits@D@std@@@1@_N@Z, aborting
wine: Call from 0x5e2968 to unimplemented function MSVCP80.dll.??0?$basic_istream@DU?$char_traits@D@std@@@std@@QAE@PAV?$basic_streambuf@DU?$char_traits@D@std@@@1@_N@Z, aborting
fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpWithDataSegs

```

is where my tries die sofar, just repeating those three lines every minute or so, trying to work around that

---

### Post by silfer on 2007-11-05
how did you apply the patches? did you get the auto updater to work?

---

### Post by Ferrat on 2007-11-06
> **silfer said:**
> how did you apply the patches? did you get the auto updater to work?

I used manual patching 

I got it running but it's running software GLSL which makes it very very slow and if I use wine 0.9.45 or later I get the 3D model rendering problem since I have an ATi card

---

### Post by pandayanyan on 2008-04-03
I too am having a problem running Neverwinter Nights 2 under ubuntu 7.10 with wine. 
I installed everything according to the guide without a hitch and when i try to play it it gives me 3 or four errors about direct 3d and my video card then shuts down 

terminal seems to display the same thing over and over again 
this is what it says in terminal:

```
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32F
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3730068, L"dwDirectXVersionMajor", 0x187ec14)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3730068, L"dwDirectXVersionMinor", 0x187ec14)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3730068, L"szDirectXVersionLetter", 0x187ec14)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3730068, L"szDirectXVersionEnglish", 0x187ec14)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3730068, L"szDirectXVersionLongEnglish", 0x187ec14)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3730068, L"bDebug", 0x187ec14)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x3730048, L"DxDiag_SystemInfo", 0x3730068)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x3730048, L"DxDiag_SystemDevices", 0x34216a0)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x3730048, L"DxDiag_LogicalDisks", 0x1e0620)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x3a40110,L"ddraw.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szPath", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szName", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bExists", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szVersion", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szAttributes", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szLanguageEnglish", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeHigh", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeLow", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bBeta", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bDebug", 0x187e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x3a40110,L"dplayx.dll")
err:dplay:DPLAYX_ConstructData : unable to map static data into process memory space (487)
err:dplay:DPLAYX_ConstructData : unable to map static data into process memory space (487)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szPath", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szName", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bExists", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szVersion", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szAttributes", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szLanguageEnglish", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeHigh", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeLow", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bBeta", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bDebug", 0x187e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x3a40110,L"dpnet.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szPath", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szName", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bExists", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szVersion", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szAttributes", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szLanguageEnglish", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeHigh", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeLow", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bBeta", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bDebug", 0x187e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x3a40110,L"dinput.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szPath", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szName", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bExists", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szVersion", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szAttributes", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szLanguageEnglish", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeHigh", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeLow", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bBeta", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bDebug", 0x187e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x3a40110,L"dinput8.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szPath", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szName", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bExists", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szVersion", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szAttributes", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szLanguageEnglish", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeHigh", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeLow", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bBeta", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bDebug", 0x187e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x3a40110,L"dsound.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szPath", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szName", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bExists", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szVersion", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szAttributes", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szLanguageEnglish", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeHigh", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeLow", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bBeta", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bDebug", 0x187e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x3a40110,L"dswave.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szPath", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szName", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bExists", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szVersion", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szAttributes", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szLanguageEnglish", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeHigh", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeLow", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bBeta", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bDebug", 0x187e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x3a40110,L"d3d8.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szPath", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szName", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bExists", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szVersion", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szAttributes", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szLanguageEnglish", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeHigh", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeLow", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bBeta", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bDebug", 0x187e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x3a40110,L"d3d9.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szPath", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szName", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bExists", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szVersion", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szAttributes", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szLanguageEnglish", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeHigh", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeLow", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bBeta", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bDebug", 0x187e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x3a40110,L"dmband.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szPath", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szName", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bExists", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szVersion", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szAttributes", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szLanguageEnglish", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeHigh", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeLow", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bBeta", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bDebug", 0x187e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x3a40110,L"dmcompos.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szPath", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szName", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bExists", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szVersion", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szAttributes", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szLanguageEnglish", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeHigh", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeLow", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bBeta", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bDebug", 0x187e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x3a40110,L"dmime.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szPath", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szName", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bExists", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szVersion", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szAttributes", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szLanguageEnglish", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeHigh", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeLow", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bBeta", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bDebug", 0x187e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x3a40110,L"dmloader.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szPath", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szName", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bExists", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szVersion", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szAttributes", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szLanguageEnglish", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeHigh", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeLow", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bBeta", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bDebug", 0x187e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x3a40110,L"dmscript.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szPath", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szName", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bExists", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szVersion", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szAttributes", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szLanguageEnglish", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeHigh", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeLow", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bBeta", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bDebug", 0x187e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x3a40110,L"dmstyle.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szPath", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szName", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bExists", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szVersion", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szAttributes", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szLanguageEnglish", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeHigh", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeLow", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bBeta", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bDebug", 0x187e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x3a40110,L"dmsynth.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szPath", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szName", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bExists", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szVersion", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szAttributes", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szLanguageEnglish", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeHigh", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeLow", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bBeta", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bDebug", 0x187e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x3a40110,L"dmusic.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szPath", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szName", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bExists", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szVersion", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szAttributes", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szLanguageEnglish", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeHigh", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeLow", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bBeta", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bDebug", 0x187e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x3a40110,L"devenum.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szPath", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szName", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bExists", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szVersion", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szAttributes", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szLanguageEnglish", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeHigh", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeLow", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bBeta", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bDebug", 0x187e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x3a40110,L"quartz.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szPath", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szName", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bExists", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szVersion", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szAttributes", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"szLanguageEnglish", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeHigh", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"dwFileTimeLow", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bBeta", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x3a40110, L"bDebug", 0x187e464)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x3730048, L"DxDiag_DirectXFiles", 0x3a40110)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x3731490, L"0", 0x37314b0)
fixme:win:EnumDisplayDevicesW ((null),0,0x187e4e8,0x00000000), stub!
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37314b0, L"szDeviceName", 0x187ebe4)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37314b0, L"szDescription", 0x187ebd4)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37314b0, L"szDisplayMemoryLocalized", 0x187ec04)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37314b0, L"szDisplayMemoryEnglish", 0x187ebf4)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37314b0, L"dwWidth", 0x187ebc4)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37314b0, L"dwHeight", 0x187ebb4)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37314b0, L"dwBpp", 0x187eba4)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37314b0, L"szVendorId", 0x187eb94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37314b0, L"szDeviceId", 0x187eb84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37314b0, L"szKeyDeviceKey", 0x187eb74)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37314b0, L"szKeyDeviceID", 0x187eb64)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x3731638)->((nil),00000008)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x3730048, L"DxDiag_DisplayDevices", 0x3731490)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x3731670, L"DxDiag_SoundDevices", 0x3731690)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x3731670, L"DxDiag_SoundCaptureDevices", 0x37316f8)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x3730048, L"DxDiag_DirectSound", 0x3731670)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x3730048, L"DxDiag_DirectMusic", 0x37317b8)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x3730048, L"DxDiag_DirectInput", 0x3731820)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x3730048, L"DxDiag_DirectPlay", 0x3731888)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x3731930)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x3731930, 1, 0x3731948)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szCatName", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidCat", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e43c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidFilter", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwMerit", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwInputs", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwOutputs", 0x187e42c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x3731930, 1, 0x3731960)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szCatName", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidCat", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e43c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidFilter", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwMerit", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwInputs", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwOutputs", 0x187e42c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x3731930, 1, 0x3a50698)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szCatName", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidCat", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e43c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidFilter", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwMerit", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwInputs", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwOutputs", 0x187e42c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x3731930, 1, 0x3a50a88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szCatName", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidCat", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e43c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidFilter", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwMerit", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwInputs", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwOutputs", 0x187e42c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x3731930, 1, 0x3a51070)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szCatName", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidCat", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e43c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidFilter", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwMerit", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwInputs", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwOutputs", 0x187e42c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x3731930, 1, 0x3a51498)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szCatName", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidCat", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e43c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidFilter", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwMerit", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwInputs", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwOutputs", 0x187e42c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x3731930, 1, 0x3a518f0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szCatName", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidCat", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e43c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidFilter", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwMerit", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwInputs", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwOutputs", 0x187e42c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x3a50068)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x3a502c0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x3a50070)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x3a50070, 1, 0x3a521f0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szCatName", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidCat", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e43c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dsnoop:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidFilter", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwMerit", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwInputs", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwOutputs", 0x187e42c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x3a50038)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x3a50038, 1, 0x3a50050)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szCatName", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidCat", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e43c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Midi Through"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidFilter", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwMerit", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwInputs", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwOutputs", 0x187e42c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x3a50038)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x3a50038)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x3a50038, 1, 0x3a50068)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szCatName", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidCat", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e43c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"DirectSound: dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidFilter", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwMerit", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwInputs", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwOutputs", 0x187e42c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x3a50038, 1, 0x3a52a48)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szCatName", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidCat", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e43c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szClsidFilter", 0x187e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"szName", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwMerit", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwInputs", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x37318f0, L"dwOutputs", 0x187e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x3730048, L"DxDiag_DirectShowFilters", 0x37318f0)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x3730048, L"DxDiag_SystemInfo", 0x187e88c)
fixme:dxdiag:IDxDiagContainerImpl_GetProp (0x3730068, L"dwOSMajorVersion", 0x187e85c)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x3730048, L"DxDiag_DisplayDevices", 0x187ea78)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x3731490, L"0", 0x187ea74)
fixme:dxdiag:IDxDiagContainerImpl_GetProp (0x37314b0, L"szDeviceName", 0x187ea40)
fixme:dxdiag:IDxDiagContainerImpl_GetProp (0x37314b0, L"szDescription", 0x187ea40)
fixme:dxdiag:IDxDiagContainerImpl_GetProp (0x37314b0, L"szKeyDeviceID", 0x187ea40)
fixme:dxdiag:IDxDiagContainerImpl_GetProp (0x37314b0, L"szKeyDeviceKey", 0x187ea40)
fixme:dxdiag:IDxDiagContainerImpl_GetProp (0x37314b0, L"szManufacturer", 0x187ea40)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x3730048, L"DxDiag_DirectSound.DxDiag_SoundDevices", 0x187ea74)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x3730048, L"DxDiag_DirectSound.DxDiag_SoundCaptureDevices", 0x187ea74)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x3730048, L"DxDiag_DirectPlay", 0x187ea74)
fixme:dxdiag:IDxDiagContainerImpl_GetProp (0x3731888, L"szNetworkNotesLocalized", 0x187ea40)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x3730048, L"DxDiag_LogicalDisks", 0x187ea7c)
fixme:dsound:DllCanUnloadNow (void): stub
``` 

any help?:confused:

---

### Post by pandayanyan on 2008-04-05
anyone???:confused:

---

### Post by h4mx0r on 2008-04-06
I managed to get it to play before and got up to character creation then was stuck on something, eventually I got it to play but with random crashes. Anyway it seriously wasn't worth my money nwn1 pretty much same but with native client and better performance. I think this new engine they used is just buggy. you guy's try installing directx9 support and .net? Something about quartz.dll too I think (had that dll mess with 2 other games conquer online and civilization)

---

### Post by harvodan on 2008-06-18
You need to copy over the following dll files to your wine /drive_c/windows/system32/. devenum.dll, and dxdiagn.dll, and you need to set up dll overrides for them in winecfg under libraries. Then it should work no problem, aside from the minimap not showing up properly.

---

### Post by heatblazer on 2008-06-18
WOW! This works? What is your PC specs? I am just curious. Not like I am going to play that crap NWN2! It was a total disappointment but it is heavy game so it`s a good PC test especially under WINE :)

---

### Post by Ng Oon-Ee on 2008-08-14
Worked for me using the guide at the winedb apphq. Unplayable though, 3 fps! The Direct3D to OpenGL slows things down considerably, I can get playable 25-30 fps on Windows on this same machine.

Back to NWN, then =)

---

### Post by vanquishedangel on 2010-07-31
I got mine to work by using PlayOnLinux, cant get it updated it seems so far but it is very playable along with mask of the betrayer. A little rough to get it going but it was easy so far. 

Once PlayOnlinux is installed it is pretty explanatory, after nwn2 is installed it will be working, and then open PlayOnLinux from the application menu. Click on install button then click "install a .pol package or an unsupported application" at the bottom. Choose "manual install" and click next. Click forward on the next window and then highlight "edit an application already installed" click forward. Highlight "NWN2" and click forward. Don't check any boxes just click forward. Then browse to the disk when prompted

---


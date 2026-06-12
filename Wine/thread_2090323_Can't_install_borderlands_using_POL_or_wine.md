---
title: "Can't install borderlands using POL or wine"
date: 2012-12-01
forum: Wine
---

### Post by jccantele49 on 2012-12-01
Hello all, I'm using Ubuntu x64 12.10, and I'm currently unable to install Borderlands using playonlinux or wine.

When I try to install using the POL present, it gets to the very last step where the VC C++ 2008 installer tries to run, and it puts out this error:

Internal errors - Invalid parameters received

If I try using wine, I run this command:

```
WINEPREFIX=~/.wine/borderlands wine winecfg
```

but it freezes, with these results:

```
wine: created the configuration directory '/home/user/.wine/borderlands'
fixme:storage:create_storagefile Storage share mode not implemented.
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:iphlpapi:NotifyAddrChange (Handle 0xefe2f8, overlapped 0xefe310): stub
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:iphlpapi:NotifyAddrChange (Handle 0x101e8d0, overlapped 0x101e8dc): stub
wine: configuration in '/home/user/.wine/borderlands' has been updated.
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
```

---

### Post by Dlambert on 2012-12-01
Just some advice from the Wine APPDb:

> _**[SIZE=4]Index[/SIZE]**_
   
[LIST]
[*]Configure wine
[*]Install requirements for Borderlands to run
[*]Link ~.wine/borderlands/c_drive to another location (optional)
[*]Activate the game
[*]Install the game
[*]Patch it
[*]Patch wine with mouse cursor patch to run properly with   Borderlands
[*]Hack registry
[*]Play
[*]Troubleshoot
[/LIST]
[SIZE=4]_**Configure wine**_[/SIZE]   
  In order to have sound use the following options:
   WINEPREFIX=~/.wine/borderlands wine winecfg
   **Audio tab:**ALSA (emulation)  
   **Drives tab:** click on Auto-detect
   You don't need to install the Gecko engine.                                                                                                                                                                          

   _**[SIZE=4]Install requirements[/SIZE]**_
   You will need  "d3dx9" and "vcrun2005" and "vcrun2008" to run Borderlands
   So get winetricks and install all 3 properly                                                                                                                                                                                                                  

   wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)     
chmod +x ./winetricks*
   WINEPREFIX=~/.wine/borderlands ./winetricks           

   mark "**d3dx9**" and "**vcrun2005**" and "**vcrun2008**" so it will install all 3 properly
   WINEPREFIX=~/.wine/borderlands wineboot
   [SIZE=4]_**Link it**_[/SIZE] (optional)
   Link /.wine/borderlands/c_drive to /..../..... whatever                                                                                                                                                                                                         
if you don't want to install _7 GB_ in your home. (copy the c_drive folder to the new dest. and link to it)
   [U][B][SIZE=4]Activate the game (before install)                                                                                                                                                                                                                                                                                                                                                                                                                       
[/SIZE][/B][/U]
   Do the offline activation described here [http://www.2kgames.com/borderlands/activation/](http://www.2kgames.com/borderlands/activation/):                                                                                                                                                                                                        

        WINEPREFIX=~/.wine/borderlands wine Borderland-ManualReleaseDateCheck.exe                                                                                                                                                           
    
WINEPREFIX=~/.wine/borderlands wineboot
   [SIZE=4]_**Install the game:**_[/SIZE]     

   Install the game from ISO file (quicker than DVD):                                                                                                                                                                                                        
    
Mount ISO.                                                                                                                                                                                                        

   WINEPREFIX=~/.wine/borderlands wine /cdrom/Setup.exe
   **The installer wants to install vcrun2008 (Visual C++2008)  [COLOR=#ff0000][/COLOR][COLOR=#ff0000][/COLOR]**[COLOR=#ff0000][/COLOR][B]_don't_[COLOR=#ff0000] allow it[/COLOR] it will corrupt the vcrun2005 installation! Open [COLOR=#0003ff]htop[/COLOR] or [COLOR=#0003ff]top[/COLOR] and send *sigterm* to *"vrcrun_x86.exe*"                                                                                                                                                                                                                                       
      
After that the initialising of the installer is _freezing_[/B]** so open [COLOR=#0003ff]htop[/COLOR] or [COLOR=#0003ff]top[/COLOR] again and send *sigterm* to *"dxsetup.exe" *and/or "*amd/ati_setup.exe*"and install will continue**
   Be careful to terminate the process with the higher PID otherwise  install will crash. Usually the path is shown in htop and it says  something like "Requirements....."                                                                                                                                                                

   [SIZE=3]_**Run the game: **_[/SIZE]
   _You will notice that you **can't **move your mouse 360° in game but that's fine for now.                                       _
   Start the binary in the directory with all the other files in it and not the one in Binaries/Binaries.                                                                                                                                                                 

   WINEPREFIX=~/.wine/borderlands wine Borderlands.exe
   Just check if it is running.                                                                                                                                                                 

   _**[SIZE=4]Patch it[/SIZE]**_
   Download the patch for Borderlands and install it. Change dir to the extracted patch.                                                                                                                                            
   [COLOR=#ff0000]*Be sure that  [COLOR=#018700][HKEY_LOCAL_MACHINE\Software\Gearbox Software\Borderlands\InstallFolder][/COLOR] is pointing to the Borderlands folder and _not_ to [COLOR=#090b96]Borderlands/Binaries[/COLOR] or [COLOR=#090b96]Borderlands/Something[/COLOR]*[/COLOR]
   WINEPREFIX=~/.wine/borderlands wine Setup.exe
    Now you can install additional DLC if you want.     

   [SIZE=4]_**Patch wine with mouse cursor patch**_[/SIZE]
    Install the dependencies for wine (_**script works for Ubuntu only**_). If you don't use K/Ubuntu look here for 32 bit [http://wiki.winehq.org/Recommended_Packages](http://wiki.winehq.org/Recommended_Packages) and here for 64 bit dependencies [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)     

   wget [http://winezeug.googlecode.com/svn/trunk/install-wine-deps.sh](http://winezeug.googlecode.com/svn/trunk/install-wine-deps.sh)     
sudo sh install-wine-deps.sh
   If you use Debian you can do:
    apt-get build-dep wine                    

   Download the wine source and patch it then build it new and create a .deb package.                                              (Patch works for see top of page)                                                                                                                   

   wget [http://downloads.sourceforge.net/project/wine/Source/wine-1.1.34.tar.bz2](http://downloads.sourceforge.net/project/wine/Source/wine-1.1.34.tar.bz2)     
tar xjvf wine*.tar.bz2                                                                                                                                                                                                   
cd wine-*
   _For different wine  version you need different patches:_
   For wine  [SIZE=3]**1134 to 1142 **[/SIZE]with[SIZE=3][/SIZE]Xorg[SIZE=3]** 1.7.5 or earlier**[/SIZE] you need:
   wget [http://bugs.winehq.org/attachment.cgi?id=25097](http://bugs.winehq.org/attachment.cgi?id=25097) -O X.patch                                                                                                                                                                     
   Unfortunatelley it seems that the above patch is **broken** with wine **greater than 1142** and Xorg[SIZE=3]** 1.7.5 or earlier **[/SIZE]and the new X2 patch does [SIZE=3]**not **[/SIZE]work with Xorg 1.7.5[SIZE=3][/SIZE]so use an older wine version or a newer version of Xorg. _(Currently only Ubuntu patches the Xorg 1.7.6 Server with patches from  Xorg 1.8 wich make the X2 patch working)_[SIZE=3][/SIZE]
   For Xorg[SIZE=3]** 1.7.6 (ubuntu patched) **[/SIZE]you need the new X2 patch:
   This patch should work with wine 1143 to 131 but i only tested: 130 and 131
   wget [http://bugs.winehq.org/attachment.cgi?id=]("http://bugs.winehq.org/attachment.cgi?id=25097")29313 -O X.patch                                                                                                                                                                     
   Now apply the patch:                    

   #Download other patches you may want at this point                                                                                                                                                                                                   
patch -p1 < X.patch                                                                                                                                                                                                   
autoreconf                                                                                                                                                           
./configure                                                                                                                                                                                                   
make depend                                                                                                                                  
make -j 2                                                                                                                                                                                                   
checkinstall -D --install=no                                                                                               

    install with mwine if you like.[SIZE=4][/SIZE]
   [SIZE=4]_**Hack registry**_[/SIZE]     

    Run regedit                                    

   WINEPREFIX=~/.wine/borderlands wine regedit
    Browse to: **Current_user/Software/Wine/** and create** "DirectInput"                                                                                                                                                 **
   Create 2 _strings_:                                   
"**MouseWarpOverride**" value "**force-box**"                                                                                                                                                                                    
"**BoxPixels**" value "**5**"
   **_Now_** mouse will work.
   _**[SIZE=4]Play the game [/SIZE]**_     

    Have fun!!! 
   [SIZE=5]_**Troubleshoot **_[/SIZE]
   _**[SIZE=3]Compiling [/SIZE]**_     

   When you **_compile_** wine **34** on x64 it could happen that make stops with an error with winemp3                                                                                                                             

    make[2]: Entering directory  `/mnt/daten/src/wine-1.1.34/dlls/winemp3.acm'                                                                                                                                                                                              
gcc -m32 -c -I. -I. -I../../include -I../../include   -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing  -Wdeclaration-after-statement -Wstrict-prototypes -Wwrite-strings  -Wtype-limits -Wpointer-arith  -g -O2  -o mpegl3.o  mpegl3.c                                                                                                                                                               
../../tools/winegcc/winegcc -m32 -B../../tools/winebuild  --sysroot=../.. -shared ./winemp3.acm.spec    mpegl3.o        -o  winemp3.acm.so  -lwinmm -luser32 -lkernel32   ../../libs/port/libwine_port.a  -lmpg123                                                                                                                                                                                                       
mpegl3.o: In function  `MPEG3_Reset':                                                                                                                                                                                                                                   
/mnt/daten/src/wine-1.1.34/dlls/winemp3.acm/mpegl3.c:401:  undefined reference to  `mpg123_feedseek'                                                                                                                                                                    
collect2: ld returned 1 exit  status                                                                                                                                                                                                                                    
winegcc: gcc  failed                                                                                                                                                                                                                                                    
make[2]: *** [winemp3.acm.so] Error  2                                                                                                                                                                                                                                  
make[2]: Leaving directory  `/mnt/daten/src/wine-1.1.34/dlls/winemp3.acm'                                                                                                                                                                                               
make[1]: *** [winemp3.acm] Error  2                                                                                                                                                                                                                                     
make[1]: *** Waiting for unfinished jobs....                                                                                                                         

   This can be fixed by rename "**[COLOR=#0003ff]mpg123_feedseek[/COLOR]**" into "**[COLOR=#0003ff]mpg123_feedseek_64[/COLOR]**" in wine-1.1.34/dlls/winemp3.acm/*.c
    
   [SIZE=3]_**Game is slow**_[/SIZE]     

   If the _**game is**** slow**_ try:
   HCU | +-Software    |    +-Wine      |      +-Direct3D
And create string: "DirectDrawRenderer" with "opengl" 
This helps a bit to smooth the game but on my machine it is not much. 
_**Turn FPS smoothing off**_
 Try to change:
bSmoothFrameRate=True  in *WilllowEngine.ini* to False 
[SIZE=2]_**Lower Texture Detail: **_[/SIZE] 
   *WillowEngine.ini* Find: 
   [SIZE=3][SystemSettings][/SIZE]    Change **MaxLODSize** of: 
   [SIZE=2]TEXTUREGROUP_World=(MinLODSize=1,MaxLODSize=4096,LODBias=0) TEXTUREGROUP_WorldNormalMap=(MinLODSize=1,MaxLODSize=4096,LODBias=0) TEXTUREGROUP_WorldSpecular=(MinLODSize=1,MaxLODSize=4096,LODBias=0) TEXTUREGROUP_Character=(MinLODSize=1,MaxLODSize=4096,LODBias=0) TEXTUREGROUP_CharacterNormalMap=(MinLODSize=1,MaxLODSize=4096,LODBias=0) TEXTUREGROUP_CharacterSpecular=(MinLODSize=1,MaxLODSize=4096,LODBias=0) TEXTUREGROUP_Weapon=(MinLODSize=1,MaxLODSize=4096,LODBias=0) TEXTUREGROUP_WeaponNormalMap=(MinLODSize=1,MaxLODSize=4096,LODBias=0) TEXTUREGROUP_WeaponSpecular=(MinLODSize=1,MaxLODSize=4096,LODBias=0) TEXTUREGROUP_Vehicle=(MinLODSize=1,MaxLODSize=4096,LODBias=0) TEXTUREGROUP_VehicleNormalMap=(MinLODSize=1,MaxLODSize=4096,LODBias=0) TEXTUREGROUP_VehicleSpecular=(MinLODSize=1,MaxLODSize=4096,LODBias=0) TEXTUREGROUP_Cinematic=(MinLODSize=1,MaxLODSize=4096,LODBias=0) TEXTUREGROUP_Effects=(MinLODSize=1,MaxLODSize=4096,LODBias=0) TEXTUREGROUP_EffectsNotFiltered=(MinLODSize=1,MaxLODSize=4096,LODBias=0) TEXTUREGROUP_Skybox=(MinLODSize=1,MaxLODSize=4096,LODBias=0) TEXTUREGROUP_UI=(MinLODSize=1,MaxLODSize=4096,LODBias=0) TEXTUREGROUP_LightAndShadowMap=(MinLODSize=1,MaxLODSize=4096,LODBias=0) TEXTUREGROUP_RenderTarget=(MinLODSize=1,MaxLODSize=4096,LODBias=0)[/SIZE]    To any of: 2048,1024, 512 or 256 (Lower is faster) 
   [SIZE=3]_**Outline Shader is not rendered correctly.**_[/SIZE]     

   Disable it:
   *WillowEngine.ini* Find: 
   [SIZE=3][Engine.Engine][/SIZE]    Change: 
   [SIZE=3]D[/SIZE][SIZE=3]efaultPostProcessName=WillowEngineMaterials.WillowScenePostProcess[/SIZE]     To:
   DefaultPostProcessName=WillowEngineMaterials.WillowScenePostProcess_cinematic                                                                                          

[SIZE=2]You can experiment with disabling the other *PostProcessName options to see what effects they have.[/SIZE]        

**                  [IMG]http://appdb.winehq.org/images/blank.gif[/IMG]   

---

### Post by jccantele49 on 2012-12-01
Well, I got it to install by using system monitor to kill the VB c++ installer per the advice in appdb, but now i'm seeing new errors:

```
[12/01/12 22:49:27] - Running wine-1.5.18 Borderlands.exe (Working directory : /home/user/.PlayOnLinux/wineprefix/Borderlands/drive_c/Program Files (x86)/2K Games/Gearbox Software/Borderlands GOTY Edifixme:service:scmdatabase_autostart_services Auto-start service L"UserAccess7" failed to start: 2
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directoryfixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
err:wgl:has_opengl Failed to load libGL: libGL.so.1: cannot open shared object file: No such file or directory
err:wgl:has_opengl OpenGL support is disabled.
Direct3D9 is not available without OpenGL.
fixme:file:K32EnumPageFilesA (0x2870320, 0x39a6a24) stub
fixme:file:K32EnumPageFilesA (0x2870320, 0x3971340) stub
Direct3D9 is not available without OpenGL.
Direct3D9 is not available without OpenGL.
err:seh:setup_exception_record stack overflow 156 bytes in thread 0009 eip 7bc73119 esp 03111294 stack 0x3110000-0x3111000-0x39e0000
```

---

### Post by jccantele49 on 2012-12-02
I reinstalled my nvidia drivers.. the opengl errors have disappeared but now this...

```
[12/01/12 23:10:14] - Running wine-1.5.18 Borderlands.exe (Working directory : /home/user/.PlayOnLinux/wineprefix/Borderlands/drive_c/Program Files (x86)/2K Games/Gearbox Software/Borderlands GOTY Edifixme:service:scmdatabase_autostart_services Auto-start service L"UserAccess7" failed to start: 2
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
fixme:win:EnumDisplayDevicesW ((null),0,0x39cab14,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ca694,0x00000000), stub!
fixme:file:K32EnumPageFilesA (0x2870320, 0x39a6a24) stub
fixme:file:K32EnumPageFilesA (0x2870320, 0x3971340) stub
fixme:win:EnumDisplayDevicesW ((null),0,0x390b49c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x390b01c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x390b4a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x390b020,0x00000000), stub!
err:seh:setup_exception_record stack overflow 156 bytes in thread 0009 eip 7bc73119 esp 03111294 stack 0x3110000-0x3111000-0x39e0000
```

---

### Post by Dlambert on 2012-12-02
It sounds like bad install media for some reason, I cannot find a sinlge other person with similar errors.

---

### Post by jccantele49 on 2012-12-02
I got past that by switching to a different No-DVD patch, but now the game crashes if I try to change the resolution from 640 x 480. I tried manually setting it in the willowengine.ini file, and now the resolution I set appears as that resolution in game, but the resolution is actually displaying at 640 x 480.

The crash it gives reports a file not found error pointing to the exe file in program files (x86) etc. etc.

here are my new logs:

```
Running wine-1.3.26 Borderlands.exe (Working directory : /home/user/.PlayOnLinux/wineprefix/Borderlands/drive_c/Program Files (x86)/2K Games/Gearbox Software/Borderlands GOTY Edifixme:heap:HeapSetInformation 0x3524000 0 0x29ffd90 4
fixme:gameux:GameExplorerImpl_VerifyAccess (0x181030, L"C:\\Program Files (x86)\\2K Games\\Gearbox Software\\Borderlands GOTY Edition\\Binaries\\Borderlands.exe", 0x29ff4b4)
fixme:win:EnumDisplayDevicesW ((null),0,0x29fe1ac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x29ff660,0x00000000), stub!
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 8 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 8 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x193418,0x18bb58): stub
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1979c0,0x197908): stub
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
```

---

### Post by Dlambert on 2012-12-03
Is this pirated? Or does this game _NEED_ a no-cd patch?

---

### Post by jccantele49 on 2012-12-05
The game is not pirated. It uses securom and needs a no-dvd patch.

I was able to resolve the low resolution problem by changing the wine script to 1.5.18, but the performance is now awful (seems to be a problem with my Bumblebee/Optimus). I've created a separate thread about that.

---

### Post by Dlambert on 2012-12-05
> **jccantele49 said:**
> The game is not pirated. It uses securom and needs a no-dvd patch.

I was able to resolve the low resolution problem by changing the wine script to 1.5.18, but the performance is now awful (seems to be a problem with my Bumblebee/Optimus). I've created a separate thread about that.

Use manjaro Linux, it takes care of that for you! (Arch)

---


---
title: "Games loading, then just.. stopping"
date: 2008-05-18
forum: Wine
---

### Post by U83RMENSCH on 2008-05-18
little info: 

wine ( whatever the latest one over the packet manager is )
distro: ubuntu 8.01 + updates. 
graphics card : ATI HD 2900 XT 
drivers : fglrx 


 I've been using Ubuntu for a very short amount of time now, but in that short amount of time I've come to like it ( granted figureing somethings are are a pain ). Im a gamer ( obviously ), and I'd like to use ubuntu more often, however i cant seem to get my games to work. 

after installing wine I installed steam, that went smooth, no problems, the only thing that dosent seem to work in steam is IM. but thats ok. 

the problme arises when i try to run 3D. I boot up counter strike, I decided to start a listen server so as just to test it, and while hte screen is a little glitch, it seemed to load just find. I get in the map, see the message of the day and click ok. I then pick my team and my screen go's black, after a few seconds it closes to the desktop. 

Same goes for Call of duty 2. I can go though the menu's then when i load up a map. it closes to the desktop. 

oddly enough, when i play quake III ( though wine ) It works just fine. 

any ideas? 

oh and while im here, has any one fixed the flickering on some of the ATI cards/drivers.

---

### Post by Bad Boy Bubby on 2008-05-18
Hi

I am new to ubuntu but getting similar errors on counterstrike 1.6 it runs but after a few mins or secs it just crashes my box just freezes and I have to kill the power.  I have tried quiet a lot of things e.g. running window'd trying different wine version's tweaking the flgrx driver settings all did not work I have read that the ATI drivers are not yet working 100% and I think this is the problem. The flashing screen is caused by the settings in wine config something about letting the system control the wine window I think.  Anyways I have given up on running games under wine for now until better driver / wine support.

---

### Post by aoanla on 2008-05-18
Can you please try running Steam in a terminal and reporting the errors you get? 

You'll need to do something like:
cd .wine/drive_c/Program\ Files/Steam/
WINEDEBUG=-all wine steam.exe


There should be at least some lines starting with "err:. These are the most important ones, if they appear to happen around when the crash occurs.

It is possible that the issue you are having is down to your hardware rendering not working correctly (frankly, my computer can do Quake III in software mode, so it's not a good test of rendering working).

---

### Post by U83RMENSCH on 2008-05-18
steam isnt the problem because its doing it on all games. Im pretty sure its rendering it because I can get into a map on css, i can see teh map and people playing on, but when i go to pick a class it closes.

I'll try to run them through the terminal, but im not sure how, so it could take a while to figure it out :P



ok, i got half life 2 start up via terminal ( the game still crashes ). This one doesnt even get to load the menu screen. Other updates: Call of duty 2 single player will run, so rendering isnt an issue ( i should think ) i can get about 3 mins into the single player game, but once it asks if i want to keep the mouse movement how it is ( if you've played any FPS you know they almost always do that at some point ). then it drops to desktop. I can get into a counter strike source map and spectate, but once i try to pick a class, it crashes to desktop. so.. here is the termial outcome from running half life 2. 


```
ubermensch@link-linux:~$ wine "C:/Valve/Steam/steamapps/kacation_man/half-life 2/hl2.exe"
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21e154,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3413
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x7f0281b0) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x7f0281b0) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x7f0281b0) : stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x7f0281b0) Event query: Unimplemented, but pretending to be supported
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x7f0281b0) : stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x7f0281b0) Event query: Unimplemented, but pretending to be supported
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b2991c0) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x7f0281b0) : stub
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x7f0281b0) : stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x6b0e6b78) : pBox=0x7f21e344 stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x7f0281b0) Event query: Unimplemented, but pretending to be supported
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #3: "Fragment shader(s) linked, vertex shader(s) linked. \n "
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #6: "Fragment shader(s) linked, vertex shader(s) linked. \n "
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x7f0281b0) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x33921908) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x33a1b728) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x337c00c8) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x7f0281b0) : stub
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:avifile:AVIFileExit (): stub!
wine: Unhandled page fault on write access to 0x00000022 at address 0x7fb48a37 (thread 0060), starting debugger...
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Unhandled exception: page fault on write access to 0x00000022 in 32-bit code (0x7fb48a37).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7fb48a37 ESP:7f21e574 EBP:00000004 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00000000 EBX:75bf0070 ECX:7fb5a9d0 EDX:7fb567b8
 ESI:00000700 EDI:7fb5a9d0
Stack dump:
0x7f21e574:  00000090 7fb5a9d0 00000004 7f60fe1c
0x7f21e584:  7fb49d32 75bf0070 00000730 35120074
0x7f21e594:  7fb5a9d0 7f60fe1c 7fb4a084 35120074
0x7f21e5a4:  00000730 35120074 7fb5a9f0 7fb5a9d0
0x7f21e5b4:  7fb486ca 35120074 ffffffff 7f21e60c
0x7f21e5c4:  00000008 7f21ff08 00000000 100070bb
Backtrace:
0x7fb48a37: addw	$0xffff,0x22(%eax)
Modules:
Module	Address			Debug info	Name (155 modules)
PE	  400000-  41c000	Deferred        hl2
PE	10000000-1002e000	Deferred        launcher
PE	20000000-2064b000	Deferred        engine
PE	21100000-211ad000	Deferred        mss32_s
PE	22000000-2263d000	Deferred        server
PE	24000000-24388000	Deferred        client
PE	26000000-26126000	Deferred        vphysics
PE	26400000-26439000	Deferred        mssvoice.asi
PE	26f00000-26f2e000	Deferred        mssmp3.asi
PE	2a000000-2a09f000	Deferred        shaderapidx9
PE	2c000000-2c2d8000	Deferred        studiorender
PE	30000000-302e5000	Deferred        steam
PE	628c0000-628d9000	Deferred        parsifal
PE	682d0000-683e4000	Deferred        serverbrowser
PE	6a5a0000-6a5c1000	Deferred        cserhelper
ELF	6a5c6000-6a610000	Deferred        dbghelp<elf>
  \-PE	6a5d0000-6a610000	\               dbghelp
PE	6ba10000-6bbcd000	Deferred        gameui
ELF	6bfe6000-6c030000	Deferred        dsound<elf>
  \-PE	6bff0000-6c030000	\               dsound
PE	6c030000-6c094000	Deferred        mss32
PE	6c0a0000-6c0b0000	Deferred        vaudio_miles
ELF	6c1dc000-6c1f0000	Deferred        winejoystick<elf>
  \-PE	6c1e0000-6c1f0000	\               winejoystick
PE	6c620000-6c778000	Deferred        p2pvoice
PE	6c780000-6ca1f000	Deferred        p2pcore
PE	6ca20000-6ca4e000	Deferred        nattypeprobe
PE	6cb70000-6cde0000	Deferred        steamclient
ELF	6d0f2000-6d118000	Deferred        netapi32<elf>
  \-PE	6d100000-6d118000	\               netapi32
ELF	6d118000-6d180000	Deferred        crypt32<elf>
  \-PE	6d120000-6d180000	\               crypt32
ELF	6e1eb000-6e200000	Deferred        psapi<elf>
  \-PE	6e1f0000-6e200000	\               psapi
PE	6e200000-6e23f000	Deferred        tier0_s
ELF	6e349000-6e370000	Deferred        secur32<elf>
  \-PE	6e350000-6e370000	\               secur32
PE	6e650000-6e68d000	Deferred        vstdlib_s
PE	6e9f0000-6ea2f000	Deferred        stdshader_dx9
PE	6ea30000-6ea6f000	Deferred        stdshader_dx8
ELF	7b7f0000-7b7f3000	Deferred        libnss_mdns4_minimal.so.2
ELF	7b800000-7b92c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca5000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bca6000-7bcbd000	Deferred        mcicda<elf>
  \-PE	7bcb0000-7bcbd000	\               mcicda
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7cb63000-7db6e000	Deferred        fglrx_dri.so
ELF	7de79000-7def3000	Deferred        libgl.so.1
ELF	7defa000-7df00000	Deferred        libnss_dns.so.2
ELF	7e011000-7e01a000	Deferred        librt.so.1
ELF	7e01a000-7e11b000	Deferred        wined3d<elf>
  \-PE	7e030000-7e11b000	\               wined3d
ELF	7e11b000-7e14b000	Deferred        d3d9<elf>
  \-PE	7e120000-7e14b000	\               d3d9
ELF	7e14b000-7e16c000	Deferred        mpr<elf>
  \-PE	7e150000-7e16c000	\               mpr
ELF	7e16c000-7e1ba000	Deferred        wininet<elf>
  \-PE	7e180000-7e1ba000	\               wininet
ELF	7e1ba000-7e1d9000	Deferred        imm32<elf>
  \-PE	7e1c0000-7e1d9000	\               imm32
ELF	7e1d9000-7e27b000	Deferred        oleaut32<elf>
  \-PE	7e1f0000-7e27b000	\               oleaut32
ELF	7e27b000-7e28f000	Deferred        midimap<elf>
  \-PE	7e280000-7e28f000	\               midimap
ELF	7e28f000-7e2a6000	Deferred        msacm32<elf>
  \-PE	7e290000-7e2a6000	\               msacm32
ELF	7e2a6000-7e2e1000	Deferred        wineoss<elf>
  \-PE	7e2b0000-7e2e1000	\               wineoss
ELF	7e2e1000-7e309000	Deferred        msvfw32<elf>
  \-PE	7e2f0000-7e309000	\               msvfw32
ELF	7e309000-7e397000	Deferred        winmm<elf>
  \-PE	7e310000-7e397000	\               winmm
ELF	7e397000-7e3bd000	Deferred        msacm32<elf>
  \-PE	7e3a0000-7e3bd000	\               msacm32
ELF	7e3bd000-7e3f7000	Deferred        avifil32<elf>
  \-PE	7e3c0000-7e3f7000	\               avifil32
ELF	7e52c000-7e58c000	Deferred        rpcrt4<elf>
  \-PE	7e540000-7e58c000	\               rpcrt4
ELF	7e58c000-7e630000	Deferred        ole32<elf>
  \-PE	7e5a0000-7e630000	\               ole32
ELF	7e655000-7e687000	Deferred        uxtheme<elf>
  \-PE	7e660000-7e687000	\               uxtheme
ELF	7e687000-7e746000	Deferred        comctl32<elf>
  \-PE	7e690000-7e746000	\               comctl32
ELF	7e746000-7e850000	Deferred        shell32<elf>
  \-PE	7e760000-7e850000	\               shell32
ELF	7e850000-7e8a9000	Deferred        shlwapi<elf>
  \-PE	7e860000-7e8a9000	\               shlwapi
ELF	7e8a9000-7e8bd000	Deferred        lz32<elf>
  \-PE	7e8b0000-7e8bd000	\               lz32
ELF	7e8bd000-7e8d6000	Deferred        version<elf>
  \-PE	7e8c0000-7e8d6000	\               version
ELF	7e8d6000-7e8e9000	Deferred        libresolv.so.2
ELF	7e8f6000-7e914000	Deferred        iphlpapi<elf>
  \-PE	7e900000-7e914000	\               iphlpapi
ELF	7e914000-7e940000	Deferred        ws2_32<elf>
  \-PE	7e920000-7e940000	\               ws2_32
ELF	7e940000-7e95a000	Deferred        wsock32<elf>
  \-PE	7e950000-7e95a000	\               wsock32
ELF	7e95a000-7e963000	Deferred        libxcursor.so.1
ELF	7e963000-7e968000	Deferred        libxfixes.so.3
ELF	7e968000-7e96b000	Deferred        libxcomposite.so.1
ELF	7e96b000-7e971000	Deferred        libxrandr.so.2
ELF	7e971000-7e979000	Deferred        libxrender.so.1
ELF	7e979000-7e97c000	Deferred        libxinerama.so.1
ELF	7e97c000-7e981000	Deferred        libxdmcp.so.6
ELF	7e981000-7e999000	Deferred        libxcb.so.1
ELF	7e999000-7e99b000	Deferred        libxcb-xlib.so.0
ELF	7e99b000-7ea82000	Deferred        libx11.so.6
ELF	7ea82000-7ea90000	Deferred        libxext.so.6
ELF	7ea90000-7ea95000	Deferred        libxxf86vm.so.1
ELF	7ea95000-7eaad000	Deferred        libice.so.6
ELF	7eaad000-7eab5000	Deferred        libsm.so.6
ELF	7eab5000-7eac0000	Deferred        libgcc_s.so.1
ELF	7eac2000-7eb53000	Deferred        winex11<elf>
  \-PE	7ead0000-7eb53000	\               winex11
ELF	7eb6f000-7eb90000	Deferred        libexpat.so.1
ELF	7eb90000-7ebba000	Deferred        libfontconfig.so.1
ELF	7ebbb000-7ebbe000	Deferred        libxau.so.6
ELF	7ebc7000-7ebdc000	Deferred        libz.so.1
ELF	7ebdc000-7ec4c000	Deferred        libfreetype.so.6
ELF	7ec59000-7ecaa000	Deferred        advapi32<elf>
  \-PE	7ec70000-7ecaa000	\               advapi32
ELF	7ecaa000-7ed45000	Deferred        gdi32<elf>
  \-PE	7ecc0000-7ed45000	\               gdi32
ELF	7ed45000-7ee8b000	Deferred        user32<elf>
  \-PE	7ed60000-7ee8b000	\               user32
ELF	7efab000-7efb6000	Deferred        libnss_files.so.2
ELF	7efb6000-7efce000	Deferred        libnsl.so.1
ELF	7efce000-7eff3000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
PE	7f550000-7f584000	Deferred        tier0
PE	7f590000-7f5b0000	Deferred        vstdlib
PE	7f6c0000-7f6f6000	Deferred        filesystem_steam
PE	7f700000-7f715000	Deferred        valve_avi
PE	7f870000-7f948000	Deferred        datamodel
PE	7fa60000-7fa89000	Deferred        dmserializers
PE	7fa90000-7fb35000	Deferred        materialsystem
PE	7fb40000-7fb61000	Export          datacache
PE	7fc80000-7fd44000	Deferred        vguimatsurface
PE	7fd50000-7fdb7000	Deferred        vgui2
PE	7fdc0000-7fdef000	Deferred        soundemittersystem
PE	7fdf0000-7fe00000	Deferred        steam_api
PE	7ff10000-7ff38000	Deferred        stdshader_dbg
PE	7ff40000-7ff73000	Deferred        stdshader_dx6
PE	7ff80000-7ffa7000	Deferred        stdshader_dx7
PE	7ffb0000-7ffbe000	Deferred        unicode
ELF	b7d16000-b7d1f000	Deferred        libnss_compat.so.2
ELF	b7d20000-b7d24000	Deferred        libdl.so.2
ELF	b7d24000-b7e73000	Deferred        libc.so.6
ELF	b7e74000-b7e8c000	Deferred        libpthread.so.0
ELF	b7e99000-b7fae000	Deferred        libwine.so.1
ELF	b7fb0000-b7fcc000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	00000016    0
	0000000e    0
	0000000d    0
00000012 
	00000015    0
	00000014    0
	00000013    0
0000001b 
	00000011    1
	00000063    1
	0000004f    0
	0000004e    1
	0000004d    0
	0000004c    1
	0000004b    0
	0000004a    1
	00000049    0
	00000048    1
	00000042    0
	00000047    1
	00000041    0
	0000003c    1
	00000046    0
	00000045    0
	00000044    0
	00000043    0
	00000040    0
	0000003f    1
	0000003e    0
	0000003d    0
	0000003b    0
	0000003a    1
	00000038    0
	00000036    0
	00000035   15
	00000034   15
	00000031   15
	0000002f    0
	0000002d    0
	0000002c    0
	0000002b    0
	00000029    0
	00000028    1
	00000027    0
	00000026    0
	00000025    0
	00000024    0
	00000023    0
	00000022    0
	00000021    0
	00000020    0
	0000001c    0
0000001d 
	0000001f    0
	0000001e    0
0000005f (D) C:\Valve\Steam\steamapps\kacation_man\half-life 2\hl2.exe
	00000053    0
	00000066    0
	00000065    0
	00000064    0
	00000062    0
	00000061    2
	00000060    0 <==
Backtrace:
ubermensch@link-linux:~$ 


```


hope this helps you to help me. :P

also, im using **wine 0.9.59** , if that helps too

*am updateing to wineRC1*

---


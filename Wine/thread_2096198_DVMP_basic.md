---
title: "DVMP basic"
date: 2012-12-19
forum: Wine
---

### Post by crogargamel on 2012-12-19
Hi.
I have problem with software DVMP basic 
[http://www.dvmp.co.uk/dv-media-player.htm](http://www.dvmp.co.uk/dv-media-player.htm) 
 
(classic media player, but shows Time Code. That is important to me.) 

I try to install it on Ubuntu 10.04 with wine, Ubuntu 12.04 with wine and Mint Maya with wine 1.5.18 (also try 1.5.19 and no luck.
So, problem is when I try to open .avi file I get a massage "Could not set windowless renderer".
I post this also on wine forum but nobody know the answer. If is problem with some adjustments in wine I am willing to pay someone to help me to get this software work on Linux.

error log file when I try to open .avi file

err:ole:CoGetClassObject class {b87beb7b-8d29-423f-ae4d-6582c10175ac} not registered
err:ole:CoGetClassObject class {b87beb7b-8d29-423f-ae4d-6582c10175ac} not registered
err:ole:CoGetClassObject no class object {b87beb7b-8d29-423f-ae4d-6582c10175ac} could be created for context 0x3
fixme:win:EnumDisplayDevicesW ((null),0,0x32b3cc,0x00000000), stub!
fixme:quartz:VMR9FilterConfig_SetNumberOfStreams (0x1613b8/0x1611c0)->(1) stub
fixme:quartz:AMGetErrorTextW (80004001,0x32ba10,160) stub


link to wine forum

[http://forum.winehq.org/viewtopic.php?f=8&t=17855&sid=098095b8f86c97ebde82faf44024b208](http://forum.winehq.org/viewtopic.php?f=8&t=17855&sid=098095b8f86c97ebde82faf44024b208)

---

### Post by PITRider on 2012-12-27
Installation directmusic through winetricks should solve the problem with an error
fixme:quartz:AMGetErrorTextW (80004001,0x32ba10,160) stub

---

### Post by crogargamel on 2012-12-28
After installing directmusic new error appeared... :mad:

Window  "Unable to find suitable renderer"


fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x32ab1c,0x00000000), stub!
err:d3d:context_create Failed to set pixel format 60 on device context 0x50048.
err:d3d:context_choose_pixel_format Can't find a suitable iPixelFormat
err:d3d:context_create Failed to set pixel format 52 on device context 0x320065.
fixme:d3d:wined3d_get_format Can't find format WINED3DFMT_R24_UNORM_X8_TYPELESS (0x49) in the format lookup table
fixme:d3d:getDepthStencilBits Unsupported depth/stencil format WINED3DFMT_UNKNOWN.
err:d3d:context_create Failed to set pixel format 36 on device context 0x1006c.
err:d3d:context_create Failed to set pixel format 44 on device context 0x1006e.
err:d3d:context_choose_pixel_format Can't find a suitable iPixelFormat
err:d3d:context_create Failed to set pixel format 44 on device context 0x10070.
fixme:ole:CoCreateInstance no instance created for interface {56a86895-0ad4-11ce-b03a-0020af0ba770} of class {51b4abf3-748f-4e3b-a276-c828330e926a}, hres is 0x80040273
err:ole:CoGetClassObject class {b87beb7b-8d29-423f-ae4d-6582c10175ac} not registered
err:ole:CoGetClassObject class {b87beb7b-8d29-423f-ae4d-6582c10175ac} not registered
err:ole:CoGetClassObject no class object {b87beb7b-8d29-423f-ae4d-6582c10175ac} could be created for context 0x3


what now?

---

### Post by crogargamel on 2013-01-02
After install of wine update 1.5.20

error log
```


fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x33ab1c,0x00000000), stub!
err:d3d:context_create Failed to set pixel format 60 on device context 0x50048.
err:d3d:context_choose_pixel_format Can't find a suitable iPixelFormat
err:d3d:context_create Failed to set pixel format 52 on device context 0x3c0065.
fixme:d3d:wined3d_get_format Can't find format WINED3DFMT_R24_UNORM_X8_TYPELESS (0x49) in the format lookup table
fixme:d3d:getDepthStencilBits Unsupported depth/stencil format WINED3DFMT_UNKNOWN.
err:d3d:context_create Failed to set pixel format 36 on device context 0x1006c.
err:d3d:context_create Failed to set pixel format 44 on device context 0x1006e.
err:d3d:context_choose_pixel_format Can't find a suitable iPixelFormat
err:d3d:context_create Failed to set pixel format 44 on device context 0x10070.
fixme:ole:CoCreateInstance no instance created for interface {56a86895-0ad4-11ce-b03a-0020af0ba770} of class {51b4abf3-748f-4e3b-a276-c828330e926a}, hres is 0x80040273
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000001 not handled
fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x33a87c,0x00000000), stub!
fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x33a52c,0x00000000), stub!
fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x33a52c,0x00000000), stub!
fixme:ddraw:ddraw7_Initialize Ignoring guid {aeb2cdd4-6e41-43ea-941c-8361cc760781}.
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000001 not handled
fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x33afec,0x00000000), stub!
fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x33ac9c,0x00000000), stub!
fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x33ac9c,0x00000000), stub!
fixme:ddraw:ddraw7_Initialize Ignoring guid {aeb2cdd4-6e41-43ea-941c-8361cc760781}.
fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x33b17c,0x00000000), stub!
err:ddraw:ddraw7_QueryInterface (0x15edf8)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x174028): No interface found
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {da4e3da0-d07d-11d0-bd50-00a0c911ce86} could be created for context 0x1

(process:18152): GThread-WARNING **: GThread system no longer supports custom thread implementations.
fixme:gstreamer:GST_QueryInterface No interface for {8e1c39a1-de53-11cf-aa63-0080c744528d}!
fixme:gstreamer:GST_QueryInterface No interface for {f90a6130-b658-11d2-ae49-0000f8754b99}!
fixme:gstreamer:event_sink 0x7de10780 stub tag
fixme:gstreamer:event_sink 0x7de10800 stub tag
fixme:gstreamer:event_sink 0x7de107b0 stub tag
fixme:gstreamer:event_sink 0x7de10800 stub tag
fixme:gstreamer:GST_QueryInterface No interface for {f90a6130-b658-11d2-ae49-0000f8754b99}!
fixme:gstreamer:GST_QueryInterface No interface for {8e1c39a1-de53-11cf-aa63-0080c744528d}!
wine: Unhandled page fault on write access to 0x00000000 at address 0x2d1508a (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x02d1508a).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:02d1508a ESP:0033b828 EBP:0033b85c EFLAGS:00010206(  R- --  I   - -P- )
 EAX:00005088 EBX:00000000 ECX:02d1cb90 EDX:00000000
 ESI:0017cd68 EDI:02d1cb9c
Stack dump:
0x0033b828:  00005088 35555f7d 02d15128 355552f8
0x0033b838:  0033b854 0017cd68 0017ce20 00000000
0x0033b848:  001c95d8 030dc4ec 001c7d70 00000000
0x0033b858:  030dc4ec 0017cd88 35558b70 02d1cb9c
0x0033b868:  00000000 0017cdb0 0017cdbc 0017cd68
0x0033b878:  355581c9 0017cdb0 0017cdb0 0033b8c8
Backtrace:
=>0 0x02d1508a (0x0033b85c)
  1 0x35558b70 in quartz (+0x58b6f) (0x0017cd88)
  2 0x35555330 in quartz (+0x5532f) (0x35555340)
  3 0x3556e2b2 in quartz (+0x6e2b1) (0x3556e2a8)
  4 0x3042e920 (0x04246c83)
0x02d1508a: roll    $1,0x0(%edx)
Modules:
Module    Address            Debug info    Name (187 modules)
PE      400000-  45a000    Deferred        dvmp-basic
PE      7d0000-  7e7000    Deferred        mkzlib
PE     18e0000- 1903000    Deferred        devenum
PE     1a20000- 1a5f000    Deferred        lavaudio.ax
PE     1a60000- 2621000    Deferred        avcodec-lav-54
PE     2740000- 2865000    Deferred        lavvideo.ax
PE     2b80000- 2d15000    Deferred        vsfilter
PE     2f30000- 2fbc000    Deferred        splitter.ax
PE     2fc0000- 2fcc000    Deferred        mkunicode
PE     31f0000- 3237000    Deferred        vp7dec.ax
PE    10000000-10421000    Deferred        ffdshow.ax
PE    1c400000-1c418000    Deferred        l3codecx.ax
ELF    20000000-20038000    Deferred        d3d9<elf>
  \-PE    20010000-20038000    \               d3d9
ELF    20038000-2016a000    Deferred        wined3d<elf>
  \-PE    20050000-2016a000    \               wined3d
ELF    2016a000-204ce000    Deferred        r300_dri.so
ELF    204ce000-20748000    Deferred        libdricore.so
ELF    20748000-20772000    Deferred        libexpat.so.1
ELF    20773000-207dd000    Deferred        ddraw<elf>
  \-PE    20780000-207dd000    \               ddraw
ELF    207dd000-2081b000    Deferred        usp10<elf>
  \-PE    207e0000-2081b000    \               usp10
ELF    2081b000-20884000    Deferred        setupapi<elf>
  \-PE    20830000-20884000    \               setupapi
ELF    20884000-208ca000    Deferred        dinput<elf>
  \-PE    20890000-208ca000    \               dinput
ELF    208ca000-20901000    Deferred        winegstreamer<elf>
  \-PE    208d0000-20901000    \               winegstreamer
ELF    20901000-20950000    Deferred        libgobject-2.0.so.0
ELF    20950000-209b0000    Deferred        libgstbase-0.10.so.0
ELF    209b0000-209d3000    Deferred        libgstpbutils-0.10.so.0
ELF    209d3000-20a1d000    Deferred        libgstcoreelements.so
ELF    20a1d000-20a45000    Deferred        libgstavi.so
ELF    20a45000-20a56000    Deferred        libgstinterfaces-0.10.so.0
ELF    20a56000-20a77000    Deferred        libspeex.so.1
ELF    20a77000-20b35000    Deferred        libschroedinger-1.0.so.0
ELF    20b35000-20b4b000    Deferred        libva.so.1
ELF    20eee000-20ef2000    Deferred        libxdamage.so.1
ELF    287d7000-287de000    Deferred        libffi.so.6
ELF    29e1b000-29e1e000    Deferred        libgthread-2.0.so.0
ELF    2acbd000-2ad94000    Deferred        opengl32<elf>
  \-PE    2ace0000-2ad94000    \               opengl32
ELF    2d338000-2d374000    Deferred        libgstbluetooth.so
ELF    2df78000-2df8f000    Deferred        libgsttypefindfunctions.so
ELF    2f992000-2f9bd000    Deferred        libvorbis.so.0
ELF    2fd20000-2fd79000    Deferred        libgl.so.1
ELF    308fa000-30918000    Deferred        libgstdecodebin2.so
ELF    31632000-31789000    Deferred        libgio-2.0.so.0
ELF    32231000-3223e000    Deferred        libdrm.so.2
ELF    337aa000-337c2000    Deferred        libxcb-glx.so.0
ELF    34aab000-34b1f000    Deferred        wininet<elf>
  \-PE    34ab0000-34b1f000    \               wininet
PE    35500000-35708000    Export          quartz
ELF    35ae4000-35bcc000    Deferred        libgstreamer-0.10.so.0
ELF    36bd7000-36bfd000    Deferred        mpr<elf>
  \-PE    36be0000-36bfd000    \               mpr
ELF    37236000-37253000    Deferred        libtheoradec.so.1
ELF    37260000-3761f000    Deferred        libgallium.so
ELF    3c515000-3c553000    Deferred        libgstaudio-0.10.so.0
ELF    3cfb4000-3cfca000    Deferred        dwmapi<elf>
  \-PE    3cfc0000-3cfca000    \               dwmapi
ELF    42245000-42263000    Deferred        libgcc_s.so.1
ELF    43b6a000-43bab000    Deferred        libtheoraenc.so.1
ELF    45bb8000-45bc0000    Deferred        libogg.so.0
ELF    4900d000-49040000    Deferred        ws2_32<elf>
  \-PE    49010000-49040000    \               ws2_32
ELF    495d8000-49612000    Deferred        libgstffmpeg.so
ELF    4bda2000-4bdde000    Deferred        libpcre.so.3
ELF    4e046000-4e15c000    Deferred        libavformat.so.53
ELF    4edef000-4fa4b000    Deferred        libavcodec.so.53
ELF    50e6f000-50e74000    Deferred        libgmodule-2.0.so.0
ELF    51e9e000-51fbb000    Deferred        libglsl.so
ELF    55490000-554b2000    Deferred        libavutil.so.51
ELF    555ce000-55746000    Deferred        libvorbisenc.so.2
ELF    55941000-55957000    Deferred        libglapi.so.0
ELF    580fc000-5810d000    Deferred        libbz2.so.1.0
ELF    5ab85000-5ac15000    Deferred        liborc-0.4.so.0
ELF    5cbe4000-5cbf2000    Deferred        libgsm.so.1
ELF    5e51e000-5e536000    Deferred        libgstrtp-0.10.so.0
ELF    5f974000-5f983000    Deferred        libgstriff-0.10.so.0
ELF    60c89000-60dd6000    Deferred        libxml2.so.2
ELF    60ed4000-6222b000    Deferred        libllvm-3.0.so.1
PE    65100000-6512c000    Deferred        avresample-lav-1
ELF    664f1000-66514000    Deferred        imm32<elf>
  \-PE    66500000-66514000    \               imm32
ELF    66e0e000-66e31000    Deferred        qedit<elf>
  \-PE    66e10000-66e31000    \               qedit
ELF    68000000-68022000    Deferred        ld-linux.so.2
ELF    68022000-68164000    Dwarf           libwine.so.1
ELF    68164000-6817f000    Deferred        libpthread.so.0
ELF    6817f000-68329000    Deferred        libc.so.6
ELF    68329000-6832e000    Deferred        libdl.so.2
ELF    6832e000-6835a000    Deferred        libm.so.6
ELF    6835a000-68366000    Deferred        libnss_nis.so.2
ELF    68366000-68373000    Deferred        libnss_files.so.2
ELF    68373000-68408000    Deferred        msvcrt<elf>
  \-PE    68390000-68408000    \               msvcrt
ELF    68408000-6846d000    Deferred        advapi32<elf>
  \-PE    68410000-6846d000    \               advapi32
ELF    6846d000-685b4000    Deferred        user32<elf>
  \-PE    68480000-685b4000    \               user32
ELF    685b4000-685ce000    Deferred        version<elf>
  \-PE    685c0000-685ce000    \               version
ELF    685ce000-686e3000    Deferred        ole32<elf>
  \-PE    685e0000-686e3000    \               ole32
ELF    686e3000-6875b000    Deferred        rpcrt4<elf>
  \-PE    686f0000-6875b000    \               rpcrt4
ELF    6875b000-68875000    Deferred        oleaut32<elf>
  \-PE    68770000-68875000    \               oleaut32
ELF    68875000-6889e000    Deferred        msacm32<elf>
  \-PE    68880000-6889e000    \               msacm32
ELF    6889e000-68ab7000    Deferred        shell32<elf>
  \-PE    688b0000-68ab7000    \               shell32
ELF    68ab7000-68b26000    Deferred        shlwapi<elf>
  \-PE    68ac0000-68b26000    \               shlwapi
ELF    68b26000-68c22000    Deferred        comctl32<elf>
  \-PE    68b30000-68c22000    \               comctl32
ELF    68c22000-68c60000    Deferred        winspool<elf>
  \-PE    68c30000-68c60000    \               winspool
ELF    68c60000-68c98000    Deferred        oledlg<elf>
  \-PE    68c70000-68c98000    \               oledlg
ELF    68c98000-68d32000    Deferred        libfreetype.so.6
ELF    68d32000-68d48000    Deferred        libz.so.1
ELF    68d48000-68dd2000    Deferred        winex11<elf>
  \-PE    68d50000-68dd2000    \               winex11
ELF    68dd2000-68ddb000    Deferred        libsm.so.6
ELF    68ddb000-68ded000    Deferred        libxext.so.6
ELF    68ded000-68f21000    Deferred        libx11.so.6
ELF    68f21000-68f3b000    Deferred        libice.so.6
ELF    68f3b000-68f41000    Deferred        libuuid.so.1
ELF    68f41000-68f45000    Deferred        libxau.so.6
ELF    68f45000-68f49000    Deferred        libxinerama.so.1
ELF    68f49000-68f53000    Deferred        libxrender.so.1
ELF    68f53000-68f57000    Deferred        libxcomposite.so.1
ELF    68f57000-68f67000    Deferred        libxi.so.6
ELF    68f67000-68f6d000    Deferred        libxfixes.so.3
ELF    68f6d000-68fc0000    Deferred        libcups.so.2
ELF    68fc0000-68ffe000    Deferred        libgssapi_krb5.so.2
ELF    68ffe000-690c2000    Deferred        libgnutls.so.26
ELF    690c2000-69191000    Deferred        libkrb5.so.3
ELF    69191000-691b9000    Deferred        libk5crypto.so.3
ELF    691b9000-691be000    Deferred        libcom_err.so.2
ELF    691be000-691c7000    Deferred        libkrb5support.so.0
ELF    691c7000-691d9000    Deferred        libtasn1.so.3
ELF    691d9000-6925e000    Deferred        libgcrypt.so.11
ELF    6925e000-69270000    Deferred        libp11-kit.so.0
ELF    69270000-69274000    Deferred        libkeyutils.so.1
ELF    69274000-6928c000    Deferred        libresolv.so.2
ELF    6928c000-69291000    Deferred        libgpg-error.so.0
ELF    69291000-6929a000    Deferred        librt.so.1
ELF    6929a000-692ad000    Deferred        gnome-keyring-pkcs11.so
ELF    6abcb000-6abd2000    Deferred        libxdmcp.so.6
ELF    6ad42000-6ad54000    Deferred        libavahi-client.so.3
ELF    6ae55000-6ae60000    Deferred        libxcursor.so.1
ELF    6b5c3000-6b6bc000    Deferred        libglib-2.0.so.0
ELF    6d35e000-6d367000    Deferred        libnss_compat.so.2
PE    6f540000-6f582000    Deferred        avutil-lav-52
PE    6fd40000-6fd6a000    Deferred        avfilter-lav-3
PE    70d00000-70e0b000    Deferred        avformat-lav-54
PE    71100000-7115e000    Deferred        swscale-lav-2
ELF    731a1000-731ae000    Deferred        libgstapp-0.10.so.0
ELF    74348000-743f0000    Deferred        libvpx.so.1
ELF    744e7000-744ed000    Deferred        libxxf86vm.so.1
ELF    74edb000-74ede000    Deferred        libx11-xcb.so.1
ELF    75950000-759ff000    Deferred        winmm<elf>
  \-PE    75960000-759ff000    \               winmm
ELF    761f9000-762db000    Deferred        comdlg32<elf>
  \-PE    76200000-762db000    \               comdlg32
ELF    77477000-77480000    Deferred        libxrandr.so.2
ELF    786b4000-786d0000    Deferred        msdmo<elf>
  \-PE    786c0000-786d0000    \               msdmo
ELF    7885c000-7887d000    Deferred        libxcb.so.1
ELF    79226000-79331000    Deferred        gdi32<elf>
  \-PE    79230000-79331000    \               gdi32
ELF    7933c000-7935b000    Deferred        libselinux.so.1
ELF    7a23f000-7a24d000    Deferred        libavahi-common.so.3
ELF    7a264000-7a29a000    Deferred        libgsttag-0.10.so.0
ELF    7a71e000-7a738000    Deferred        libnsl.so.1
ELF    7a7c2000-7a7f6000    Deferred        uxtheme<elf>
  \-PE    7a7d0000-7a7f6000    \               uxtheme
ELF    7aac0000-7ab09000    Deferred        libdbus-1.so.3
ELF    7b800000-7ba33000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba33000    \               kernel32
ELF    7bc00000-7bcca000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcca000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\DVMP Basic\DVMP-Basic.exe
    00000028    0
    00000027    0
    00000026    0
    00000025    0
    00000024    0
    00000023    0
    00000009    0 <==
0000000e services.exe
    0000001f    0
    0000001e    0
    00000018    0
    00000017    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001c    0
    00000019    0
    00000014    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001d    0
    0000001b    0
00000021 explorer.exe
    00000022    0
```

---


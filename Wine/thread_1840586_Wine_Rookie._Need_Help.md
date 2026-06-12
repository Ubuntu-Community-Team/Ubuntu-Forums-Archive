---
title: "Wine Rookie. Need Help"
date: 2011-09-07
forum: Wine
---

### Post by brantpadams on 2011-09-07
The title says it all. 

I have a copy of Adobe Premiere Pro CS4 downloaded and I really want to start using it for school. I have downloaded wine in the past with earlier versions of ubuntu, but I could never find out how to get anything to operate on it. This will be the first time I've ever reached out for advice. 

I am running 11.04 on a Dell Inspiron 1525 laptop. Please let me know what other information may be necessary for me to start using this program. As always, thanks for your help.

---

### Post by Toz on 2011-09-07
I think you might be out of luck. See :[http://appdb.winehq.org/objectManager.php?sClass=version&iId=15243]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=15243")
(WineHQ is a good resource to look up compatibility and related information about running specific programs in wine).

Playonlinux ([http://www.playonlinux.com/en]("http://www.playonlinux.com/en")) is another resource you can use. I couldn't find anything regarding Premiere there either.

Your other option is to install a Windows operating system into a Virtualbox/VMWare machine and run the application natively there.

---

### Post by brantpadams on 2011-09-07
Looks like you're right. Oh well. I'll have to dual-boot at some point.

On a side note I went ahead and installed PlayonLinux. Pretty cool, although I was wondering if you could help me out with it. Just to test it, I installed the Sonic Fan Remix game. The installation went fine and I can boot it up, but the video runs extremely slow even on the lowest setting. The audio is top notch, but I'm wondering if I missed something in the initial set up. 

Do you know anything about graphics cards? I can find out how to get you that info. if it would help.

---

### Post by Toz on 2011-09-07
Lets get some info about the card and the driver that you are using. In a terminal window, can you type in the following command and post back the result:
```
lspci | grep VGA
```
and post back the contents of the **/var/log/Xorg.0.log** file.

---

### Post by brantpadams on 2011-09-07
After the terminal input:
> 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)

Was that all you needed to go on?

---

### Post by Toz on 2011-09-08
I'd also like to see the contents of the **/var/log/Xorg.0.log** file to see what driver is loaded and if any errors exist.

---

### Post by brantpadams on 2011-09-08
Apologies, not sure how to do that.

---

### Post by catlover2 on 2011-09-08
```
sudo gedit **/var/log/Xorg.0.log**
```I would try installing wine 1.3 beta from their ppa _[here](https://launchpad.net/~ubuntu-wine/+archive/ppa)_ , as all of the test results on 
WineHQ are for 1.1 and 1.2.

---

### Post by brantpadams on 2011-09-08
It says it couldn't open the file:
> gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.

---

### Post by Toz on 2011-09-08
Interesting.

What do the following commands return?
```
file /var/log/Xorg.0.log
ls -l /var/log/Xorg*
lsmod
dmesg
```

Lets see if its loading and running the intel driver.

---

### Post by brantpadams on 2011-09-08
```
brant@brant-Inspiron-1525:~$ file /var/log/Xorg.0.log
/var/log/Xorg.0.log: data
brant@brant-Inspiron-1525:~$ ls -l /var/log/Xorg*
-rw-r--r-- 1 root root 31480 2011-09-08 14:47 /var/log/Xorg.0.log
-rw-r--r-- 1 root root 32970 2011-09-08 14:28 /var/log/Xorg.0.log.old
brant@brant-Inspiron-1525:~$ lsmod
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  2 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
binfmt_misc            13213  1 
snd_hda_codec_idt      60537  1 
snd_hda_codec_hdmi     27535  1 
joydev                 17322  0 
snd_hda_intel          24113  2 
snd_hda_codec          90901  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi
dell_laptop            13515  0 
r852                   17878  0 
sm_common              16737  1 r852
dcdbas                 14054  1 dell_laptop
snd_timer              28659  2 snd_pcm,snd_seq
nand                   49822  2 r852,sm_common
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  451033  4 
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
drm_kms_helper         40745  1 i915
drm                   184164  5 i915,drm_kms_helper
snd                    55295  14 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   2642531  0 
mtd                    26720  2 sm_common,nand
arc4                   12473  2 
psmouse                73312  0 
serio_raw              12990  0 
b43                   296610  0 
lib80211               14570  1 wl
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
ssb                    45942  1 b43
mac80211              257001  1 b43
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
cfg80211              156212  2 b43,mac80211
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
sdhci_pci              13623  0 
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
ahci                   21591  2 
sky2                   49172  0 
libahci                25548  1 ahci
brant@brant-Inspiron-1525:~$ dmseg
No command 'dmseg' found, did you mean:
 Command 'mmseg' from package 'sunpinyin-utils' (universe)
 Command 'dmesg' from package 'util-linux' (main)
dmseg: command not found
```

---

### Post by Toz on 2011-09-08
Does the following display the contents of the Xorg.0.log file?
```
cat /var/log/Xorg.0.log
```
If so, can you post it back?

However, it looks from your lsmod command that the intel driver module (i915) is loaded and running.

How are you running the game? Double-clicking on an icon? You can always try running the game with the **-opengl** parameter to see if performance improves. You'd need to start it from the command line something like this:
```
wine /path/to/exe -opengl
```
...but you need to figure out the /path/to/exe part.

Also, in playonlinux, go to Settings->System and click on "3D Test". Let it run for about 10 seconds, then close the glxgears window. It should display some test statistics. What are you getting?

---

### Post by brantpadams on 2011-09-08
Quite a large script here:
```
[    16.566] 	ABI class: X.Org Server Extension, version 5.0
[    16.566] (II) Loading extension DOUBLE-BUFFER
[    16.566] (II) LoadModule: "glx"
[    16.566] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    16.566] (II) Module glx: vendor="X.Org Foundation"
[    16.566] 	compiled for 1.10.1, module version = 1.0.0
[    16.566] 	ABI class: X.Org Server Extension, version 5.0
[    16.566] (==) AIGLX enabled
[    16.566] (II) Loading extension GLX
[    16.566] (II) LoadModule: "record"
[    16.567] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    16.567] (II) Module record: vendor="X.Org Foundation"
[    16.567] 	compiled for 1.10.1, module version = 1.13.0
[    16.567] 	Module class: X.Org Server Extension
[    16.567] 	ABI class: X.Org Server Extension, version 5.0
[    16.567] (II) Loading extension RECORD
[    16.567] (II) LoadModule: "dri"
[    16.567] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    16.567] (II) Module dri: vendor="X.Org Foundation"
[    16.567] 	compiled for 1.10.1, module version = 1.0.0
[    16.567] 	ABI class: X.Org Server Extension, version 5.0
[    16.567] (II) Loading extension XFree86-DRI
[    16.567] (II) LoadModule: "dri2"
[    16.568] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    16.568] (II) Module dri2: vendor="X.Org Foundation"
[    16.568] 	compiled for 1.10.1, module version = 1.2.0
[    16.568] 	ABI class: X.Org Server Extension, version 5.0
[    16.568] (II) Loading extension DRI2
[    16.568] (==) Matched intel as autoconfigured driver 0
[    16.568] (==) Matched vesa as autoconfigured driver 1
[    16.568] (==) Matched fbdev as autoconfigured driver 2
[    16.568] (==) Assigned the driver to the xf86ConfigLayout
[    16.568] (II) LoadModule: "intel"
[    16.568] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    16.568] (II) Module intel: vendor="X.Org Foundation"
[    16.568] 	compiled for 1.10.1, module version = 2.14.0
[    16.568] 	Module class: X.Org Video Driver
[    16.568] 	ABI class: X.Org Video Driver, version 10.0
[    16.568] (II) LoadModule: "vesa"
[    16.569] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    16.569] (II) Module vesa: vendor="X.Org Foundation"
[    16.569] 	compiled for 1.10.0, module version = 2.3.0
[    16.569] 	Module class: X.Org Video Driver
[    16.569] 	ABI class: X.Org Video Driver, version 10.0
[    16.569] (II) LoadModule: "fbdev"
[    16.569] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    16.569] (II) Module fbdev: vendor="X.Org Foundation"
[    16.569] 	compiled for 1.10.0, module version = 0.4.2
[    16.569] 	ABI class: X.Org Video Driver, version 10.0
[    16.569] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    16.570] (II) VESA: driver for VESA chipsets: vesa
[    16.570] (II) FBDEV: driver for framebuffer: fbdev
[    16.570] (++) using VT number 7

[    16.572] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    16.572] (WW) Falling back to old probe method for vesa
[    16.572] (WW) Falling back to old probe method for fbdev
[    16.572] (II) Loading sub module "fbdevhw"
[    16.572] (II) LoadModule: "fbdevhw"
[    16.572] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    16.572] (II) Module fbdevhw: vendor="X.Org Foundation"
[    16.572] 	compiled for 1.10.1, module version = 0.0.2
[    16.572] 	ABI class: X.Org Video Driver, version 10.0
[    16.573] drmOpenDevice: node name is /dev/dri/card0
[    16.573] drmOpenDevice: open result is 9, (OK)
[    16.573] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    16.573] drmOpenDevice: node name is /dev/dri/card0
[    16.573] drmOpenDevice: open result is 9, (OK)
[    16.573] drmOpenByBusid: drmOpenMinor returns 9
[    16.573] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    16.573] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    16.573] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    16.573] (==) intel(0): RGB weight 888
[    16.573] (==) intel(0): Default visual is TrueColor
[    16.573] (II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
[    16.573] (--) intel(0): Chipset: "965GM"
[    16.573] (**) intel(0): Relaxed fencing enabled
[    16.573] (**) intel(0): Tiling enabled
[    16.573] (**) intel(0): SwapBuffers wait enabled
[    16.573] (==) intel(0): video overlay key set to 0x101fe
[    16.573] (II) intel(0): Output LVDS1 has no monitor section
[    16.574] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    16.592] (II) intel(0): Output VGA1 has no monitor section
[    16.608] (II) intel(0): Output HDMI1 has no monitor section
[    16.839] (II) intel(0): Output TV1 has no monitor section
[    16.839] (II) intel(0): EDID for output LVDS1
[    16.839] (II) intel(0): Manufacturer: LPL  Model: 301  Serial#: 0
[    16.839] (II) intel(0): Year: 2008  Week: 0
[    16.839] (II) intel(0): EDID Version: 1.3
[    16.839] (II) intel(0): Digital Display Input
[    16.839] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    16.839] (II) intel(0): Gamma: 2.20
[    16.839] (II) intel(0): No DPMS capabilities specified
[    16.839] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    16.839] (II) intel(0): First detailed timing is preferred mode
[    16.839] (II) intel(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
[    16.839] (II) intel(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
[    16.839] (II) intel(0): Manufacturer's mask: 0
[    16.839] (II) intel(0): Supported detailed timing:
[    16.839] (II) intel(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    16.839] (II) intel(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    16.839] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    16.839] (II) intel(0): Supported detailed timing:
[    16.839] (II) intel(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    16.839] (II) intel(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    16.839] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    16.839] (II) intel(0):  D196J&#65533;154W01
[    16.839] (II) intel(0):  $2=Eh&#65533;&#65533;&#65533;
[    16.839] (II) intel(0): EDID (in hex):
[    16.839] (II) intel(0): 	00ffffffffffff00320c010300000000
[    16.839] (II) intel(0): 	00120103802115780ab3409959538d27
[    16.839] (II) intel(0): 	25505400000001010101010101010101
[    16.839] (II) intel(0): 	0101010101017e1d00e8502020304030
[    16.839] (II) intel(0): 	36004bcf100000197e1d00e850202030
[    16.839] (II) intel(0): 	403036004bcf10000000000000fe0044
[    16.839] (II) intel(0): 	3139364a803135345730310a000000fe
[    16.840] (II) intel(0): 	0024323d45688ba7ff01010a202000af
[    16.840] (II) intel(0): EDID vendor "LPL", prod id 769
[    16.840] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    16.840] (II) intel(0): Printing DDC gathered Modelines:
[    16.840] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    16.840] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    16.840] (II) intel(0): Printing probed modes for output LVDS1
[    16.840] (II) intel(0): Modeline "1280x800"x60.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    16.840] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    16.840] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    16.840] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    16.840] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    16.856] (II) intel(0): EDID for output VGA1
[    16.872] (II) intel(0): EDID for output HDMI1
[    17.103] (II) intel(0): EDID for output TV1
[    17.103] (II) intel(0): Output LVDS1 connected
[    17.103] (II) intel(0): Output VGA1 disconnected
[    17.103] (II) intel(0): Output HDMI1 disconnected
[    17.103] (II) intel(0): Output TV1 disconnected
[    17.103] (II) intel(0): Using exact sizes for initial modes
[    17.103] (II) intel(0): Output LVDS1 using initial mode 1280x800
[    17.103] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    17.103] (II) intel(0): Kernel page flipping support detected, enabling
[    17.103] (**) intel(0): Display dimensions: (330, 210) mm
[    17.103] (**) intel(0): DPI set to (98, 96)
[    17.103] (II) Loading sub module "fb"
[    17.103] (II) LoadModule: "fb"
[    17.104] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.104] (II) Module fb: vendor="X.Org Foundation"
[    17.104] 	compiled for 1.10.1, module version = 1.0.0
[    17.104] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.104] (II) UnloadModule: "vesa"
[    17.104] (II) Unloading vesa
[    17.104] (II) UnloadModule: "fbdev"
[    17.104] (II) Unloading fbdev
[    17.104] (II) UnloadModule: "fbdevhw"
[    17.104] (II) Unloading fbdevhw
[    17.104] (==) Depth 24 pixmap format is 32 bpp
[    17.104] (==) intel(0): VideoRam: 262144 KB
[    17.104] (II) intel(0): [DRI2] Setup complete
[    17.104] (II) intel(0): [DRI2]   DRI driver: i965
[    17.104] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[    17.117] (II) UXA(0): Driver registered support for the following operations:
[    17.117] (II)         solid
[    17.117] (II)         copy
[    17.117] (II)         composite (RENDER acceleration)
[    17.117] (II)         put_image
[    17.117] (II)         get_image
[    17.117] (==) intel(0): Backing store disabled
[    17.117] (==) intel(0): Silken mouse enabled
[    17.117] (II) intel(0): Initializing HW Cursor
[    17.144] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    17.148] (==) intel(0): DPMS enabled
[    17.148] (==) intel(0): Intel XvMC decoder enabled
[    17.148] (II) intel(0): Set up textured video
[    17.148] (II) intel(0): Set up overlay video
[    17.148] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[    17.148] (II) intel(0): direct rendering: DRI2 Enabled
[    17.148] (==) intel(0): hotplug detection: "enabled"
[    17.149] (--) RandR disabled
[    17.149] (II) Initializing built-in extension Generic Event Extension
[    17.149] (II) Initializing built-in extension SHAPE
[    17.149] (II) Initializing built-in extension MIT-SHM
[    17.149] (II) Initializing built-in extension XInputExtension
[    17.149] (II) Initializing built-in extension XTEST
[    17.149] (II) Initializing built-in extension BIG-REQUESTS
[    17.149] (II) Initializing built-in extension SYNC
[    17.149] (II) Initializing built-in extension XKEYBOARD
[    17.149] (II) Initializing built-in extension XC-MISC
[    17.149] (II) Initializing built-in extension SECURITY
[    17.149] (II) Initializing built-in extension XINERAMA
[    17.149] (II) Initializing built-in extension XFIXES
[    17.149] (II) Initializing built-in extension RENDER
[    17.149] (II) Initializing built-in extension RANDR
[    17.149] (II) Initializing built-in extension COMPOSITE
[    17.149] (II) Initializing built-in extension DAMAGE
[    17.149] (II) Initializing built-in extension GESTURE
[    17.160] (II) AIGLX: Trying DRI driver /usr/lib/dri/i965_dri.so
[    17.178] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    17.178] (II) AIGLX: enabled GLX_INTEL_swap_event
[    17.178] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    17.178] (II) AIGLX: enabled GLX_SGI_make_current_read
[    17.178] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    17.178] (II) AIGLX: Loaded and initialized i965
[    17.178] (II) GLX: Initialized DRI2 GL provider for screen 0
[    17.179] (II) intel(0): Setting screen physical size to 338 x 211
[    17.191] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    17.203] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    17.204] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    17.204] (II) LoadModule: "evdev"
[    17.204] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.204] (II) Module evdev: vendor="X.Org Foundation"
[    17.204] 	compiled for 1.10.0.902, module version = 2.6.0
[    17.205] 	Module class: X.Org XInput Driver
[    17.205] 	ABI class: X.Org XInput driver, version 12.3
[    17.205] (II) Using input driver 'evdev' for 'Video Bus'
[    17.205] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.205] (**) Video Bus: always reports core events
[    17.205] (**) Video Bus: Device: "/dev/input/event7"
[    17.205] (--) Video Bus: Found keys
[    17.205] (II) Video Bus: Configuring as keyboard
[    17.205] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input7/event7"
[    17.205] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    17.205] (**) Option "xkb_rules" "evdev"
[    17.205] (**) Option "xkb_model" "pc105"
[    17.205] (**) Option "xkb_layout" "us"
[    17.214] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    17.214] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.214] (II) Using input driver 'evdev' for 'Power Button'
[    17.214] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.215] (**) Power Button: always reports core events
[    17.215] (**) Power Button: Device: "/dev/input/event1"
[    17.215] (--) Power Button: Found keys
[    17.215] (II) Power Button: Configuring as keyboard
[    17.215] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    17.215] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    17.215] (**) Option "xkb_rules" "evdev"
[    17.215] (**) Option "xkb_model" "pc105"
[    17.215] (**) Option "xkb_layout" "us"
[    17.215] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    17.215] (II) No input driver/identifier specified (ignoring)
[    17.216] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    17.216] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    17.216] (II) Using input driver 'evdev' for 'Sleep Button'
[    17.216] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.216] (**) Sleep Button: always reports core events
[    17.216] (**) Sleep Button: Device: "/dev/input/event2"
[    17.228] (--) Sleep Button: Found keys
[    17.228] (II) Sleep Button: Configuring as keyboard
[    17.228] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    17.228] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    17.228] (**) Option "xkb_rules" "evdev"
[    17.228] (**) Option "xkb_model" "pc105"
[    17.228] (**) Option "xkb_layout" "us"
[    17.231] (II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event10)
[    17.231] (II) No input driver/identifier specified (ignoring)
[    17.231] (II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event8)
[    17.232] (II) No input driver/identifier specified (ignoring)
[    17.232] (II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event9)
[    17.232] (II) No input driver/identifier specified (ignoring)
[    17.239] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    17.239] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    17.239] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    17.239] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.239] (**) AT Translated Set 2 keyboard: always reports core events
[    17.239] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    17.239] (--) AT Translated Set 2 keyboard: Found keys
[    17.239] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    17.239] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    17.239] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    17.239] (**) Option "xkb_rules" "evdev"
[    17.239] (**) Option "xkb_model" "pc105"
[    17.239] (**) Option "xkb_layout" "us"
[    17.240] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event5)
[    17.240] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[    17.240] (II) Using input driver 'evdev' for 'PS/2 Mouse'
[    17.240] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.240] (**) PS/2 Mouse: always reports core events
[    17.240] (**) PS/2 Mouse: Device: "/dev/input/event5"
[    17.240] (--) PS/2 Mouse: Found 3 mouse buttons
[    17.240] (--) PS/2 Mouse: Found relative axes
[    17.240] (--) PS/2 Mouse: Found x and y relative axes
[    17.240] (II) PS/2 Mouse: Configuring as mouse
[    17.240] (**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
[    17.240] (**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.240] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input5/event5"
[    17.240] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
[    17.240] (II) PS/2 Mouse: initialized for relative axes.
[    17.240] (**) PS/2 Mouse: (accel) keeping acceleration scheme 1
[    17.240] (**) PS/2 Mouse: (accel) acceleration profile 0
[    17.240] (**) PS/2 Mouse: (accel) acceleration factor: 2.000
[    17.240] (**) PS/2 Mouse: (accel) acceleration threshold: 4
[    17.241] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse0)
[    17.241] (II) No input driver/identifier specified (ignoring)
[    17.241] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event6)
[    17.241] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    17.241] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    17.241] (II) LoadModule: "synaptics"
[    17.241] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    17.242] (II) Module synaptics: vendor="X.Org Foundation"
[    17.242] 	compiled for 1.10.1, module version = 1.3.99
[    17.242] 	Module class: X.Org XInput Driver
[    17.242] 	ABI class: X.Org XInput driver, version 12.3
[    17.242] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    17.242] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    17.242] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    17.242] (**) Option "Device" "/dev/input/event6"
[    17.264] (--) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[    17.264] (--) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[    17.264] (--) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    17.264] (--) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[    17.264] (--) AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 16
[    17.284] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    17.284] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    17.288] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input6/event6"
[    17.288] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
[    17.288] (**) AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    17.288] (**) AlpsPS/2 ALPS GlidePoint: MaxSpeed is now 1.75
[    17.288] (**) AlpsPS/2 ALPS GlidePoint: AccelFactor is now 0.156
[    17.288] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    17.288] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    17.288] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    17.288] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    17.303] (II) AlpsPS/2 ALPS GlidePoint: failed to open grail, no gesture support
[    17.303] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    17.303] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse1)
[    17.303] (II) No input driver/identifier specified (ignoring)
[    17.310] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event4)
[    17.310] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    17.310] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    17.310] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.310] (**) Dell WMI hotkeys: always reports core events
[    17.310] (**) Dell WMI hotkeys: Device: "/dev/input/event4"
[    17.320] (--) Dell WMI hotkeys: Found keys
[    17.320] (II) Dell WMI hotkeys: Configuring as keyboard
[    17.320] (**) Option "config_info" "udev:/sys/devices/virtual/input/input4/event4"
[    17.320] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[    17.320] (**) Option "xkb_rules" "evdev"
[    17.320] (**) Option "xkb_model" "pc105"
[    17.320] (**) Option "xkb_layout" "us"
[    17.700] (II) intel(0): EDID vendor "LPL", prod id 769
[    17.700] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    17.700] (II) intel(0): Printing DDC gathered Modelines:
[    17.700] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    17.965] (II) intel(0): EDID vendor "LPL", prod id 769
[    17.965] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    17.965] (II) intel(0): Printing DDC gathered Modelines:
[    17.965] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    18.229] (II) intel(0): EDID vendor "LPL", prod id 769
[    18.229] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    18.229] (II) intel(0): Printing DDC gathered Modelines:
[    18.229] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    18.492] (II) intel(0): EDID vendor "LPL", prod id 769
[    18.492] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    18.492] (II) intel(0): Printing DDC gathered Modelines:
[    18.492] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    23.749] (II) intel(0): EDID vendor "LPL", prod id 769
[    23.749] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    23.749] (II) intel(0): Printing DDC gathered Modelines:
[    23.749] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    24.053] (II) intel(0): EDID vendor "LPL", prod id 769
[    24.053] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    24.053] (II) intel(0): Printing DDC gathered Modelines:
[    24.053] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    24.396] (II) intel(0): EDID vendor "LPL", prod id 769
[    24.396] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    24.396] (II) intel(0): Printing DDC gathered Modelines:
[    24.396] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    24.728] (II) intel(0): EDID vendor "LPL", prod id 769
[    24.728] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    24.728] (II) intel(0): Printing DDC gathered Modelines:
[    24.728] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    25.207] (II) intel(0): EDID vendor "LPL", prod id 769
[    25.207] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    25.207] (II) intel(0): Printing DDC gathered Modelines:
[    25.207] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    26.454] (II) intel(0): EDID vendor "LPL", prod id 769
[    26.454] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    26.454] (II) intel(0): Printing DDC gathered Modelines:
[    26.454] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    30.517] (II) intel(0): EDID vendor "LPL", prod id 769
[    30.517] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    30.517] (II) intel(0): Printing DDC gathered Modelines:
[    30.517] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[  5796.633] (II) config/udev: Adding input device Logitech Logitech Dual Action (/dev/input/js0)
[  5796.633] (II) No input driver/identifier specified (ignoring)
[  5796.634] (II) config/udev: Adding input device Logitech Logitech Dual Action (/dev/input/event11)
[  5796.635] (II) No input driver/identifier specified (ignoring)

```

This version of PlayonLinux doesn't seem to have a 3D test available. I believe it's the newest version.

Also, I've just been selecting it from the menu and hitting "run." I've been trying to figure out how to find the path to it, but no luck.

---

### Post by brantpadams on 2011-09-08
Don't know if this helps, but the installed wine versions I have are 1.3.25 and 1.3.26

---

### Post by Toz on 2011-09-08
> This version of PlayonLinux doesn't seem to have a 3D test available. I believe it's the newest version.
Ok, I had the version from the repositories. I have now installed the latest version. So in that case, just run **glxgears** from the command prompt. I'd be interested in seeing the FPS you're getting. I'm getting about 3000 with an ATI HD2600.

> Also, I've just been selecting it from the menu and hitting "run." I've been trying to figure out how to find the path to it, but no luck.

Ok. With the new version of PlayOnLinux, some of the configuration stuff is easier. Click on Configure, choose "Sonicfamremix", go to the "Display" tab and you can try to tweak some of those settings. First try changing "Direct Draw Renderer" to "opengl and see if that makes a difference.

---

### Post by Toz on 2011-09-08
> **brantpadams said:**
> Quite a large script here:
```
[    16.566] 	ABI class: X.Org Server Extension, version 5.0
[    16.566] (II) Loading extension DOUBLE-BUFFER
[    16.566] (II) LoadModule: "glx"
[    16.566] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    16.566] (II) Module glx: vendor="X.Org Foundation"
[    16.566] 	compiled for 1.10.1, module version = 1.0.0
[    16.566] 	ABI class: X.Org Server Extension, version 5.0
[    16.566] (==) AIGLX enabled
[    16.566] (II) Loading extension GLX
[    16.566] (II) LoadModule: "record"
[    16.567] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    16.567] (II) Module record: vendor="X.Org Foundation"
[    16.567] 	compiled for 1.10.1, module version = 1.13.0
[    16.567] 	Module class: X.Org Server Extension
[    16.567] 	ABI class: X.Org Server Extension, version 5.0
[    16.567] (II) Loading extension RECORD
[    16.567] (II) LoadModule: "dri"
[    16.567] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    16.567] (II) Module dri: vendor="X.Org Foundation"
[    16.567] 	compiled for 1.10.1, module version = 1.0.0
[    16.567] 	ABI class: X.Org Server Extension, version 5.0
[    16.567] (II) Loading extension XFree86-DRI
[    16.567] (II) LoadModule: "dri2"
[    16.568] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    16.568] (II) Module dri2: vendor="X.Org Foundation"
[    16.568] 	compiled for 1.10.1, module version = 1.2.0
[    16.568] 	ABI class: X.Org Server Extension, version 5.0
[    16.568] (II) Loading extension DRI2
[    16.568] (==) Matched intel as autoconfigured driver 0
[    16.568] (==) Matched vesa as autoconfigured driver 1
[    16.568] (==) Matched fbdev as autoconfigured driver 2
[    16.568] (==) Assigned the driver to the xf86ConfigLayout
[    16.568] (II) LoadModule: "intel"
[    16.568] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    16.568] (II) Module intel: vendor="X.Org Foundation"
[    16.568] 	compiled for 1.10.1, module version = 2.14.0
[    16.568] 	Module class: X.Org Video Driver
[    16.568] 	ABI class: X.Org Video Driver, version 10.0
[    16.568] (II) LoadModule: "vesa"
[    16.569] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    16.569] (II) Module vesa: vendor="X.Org Foundation"
[    16.569] 	compiled for 1.10.0, module version = 2.3.0
[    16.569] 	Module class: X.Org Video Driver
[    16.569] 	ABI class: X.Org Video Driver, version 10.0
[    16.569] (II) LoadModule: "fbdev"
[    16.569] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    16.569] (II) Module fbdev: vendor="X.Org Foundation"
[    16.569] 	compiled for 1.10.0, module version = 0.4.2
[    16.569] 	ABI class: X.Org Video Driver, version 10.0
[    16.569] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    16.570] (II) VESA: driver for VESA chipsets: vesa
[    16.570] (II) FBDEV: driver for framebuffer: fbdev
[    16.570] (++) using VT number 7

[    16.572] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    16.572] (WW) Falling back to old probe method for vesa
[    16.572] (WW) Falling back to old probe method for fbdev
[    16.572] (II) Loading sub module "fbdevhw"
[    16.572] (II) LoadModule: "fbdevhw"
[    16.572] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    16.572] (II) Module fbdevhw: vendor="X.Org Foundation"
[    16.572] 	compiled for 1.10.1, module version = 0.0.2
[    16.572] 	ABI class: X.Org Video Driver, version 10.0
[    16.573] drmOpenDevice: node name is /dev/dri/card0
[    16.573] drmOpenDevice: open result is 9, (OK)
[    16.573] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    16.573] drmOpenDevice: node name is /dev/dri/card0
[    16.573] drmOpenDevice: open result is 9, (OK)
[    16.573] drmOpenByBusid: drmOpenMinor returns 9
[    16.573] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    16.573] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    16.573] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    16.573] (==) intel(0): RGB weight 888
[    16.573] (==) intel(0): Default visual is TrueColor
[    16.573] (II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
[    16.573] (--) intel(0): Chipset: "965GM"
[    16.573] (**) intel(0): Relaxed fencing enabled
[    16.573] (**) intel(0): Tiling enabled
[    16.573] (**) intel(0): SwapBuffers wait enabled
[    16.573] (==) intel(0): video overlay key set to 0x101fe
[    16.573] (II) intel(0): Output LVDS1 has no monitor section
[    16.574] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    16.592] (II) intel(0): Output VGA1 has no monitor section
[    16.608] (II) intel(0): Output HDMI1 has no monitor section
[    16.839] (II) intel(0): Output TV1 has no monitor section
[    16.839] (II) intel(0): EDID for output LVDS1
[    16.839] (II) intel(0): Manufacturer: LPL  Model: 301  Serial#: 0
[    16.839] (II) intel(0): Year: 2008  Week: 0
[    16.839] (II) intel(0): EDID Version: 1.3
[    16.839] (II) intel(0): Digital Display Input
[    16.839] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    16.839] (II) intel(0): Gamma: 2.20
[    16.839] (II) intel(0): No DPMS capabilities specified
[    16.839] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    16.839] (II) intel(0): First detailed timing is preferred mode
[    16.839] (II) intel(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
[    16.839] (II) intel(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
[    16.839] (II) intel(0): Manufacturer's mask: 0
[    16.839] (II) intel(0): Supported detailed timing:
[    16.839] (II) intel(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    16.839] (II) intel(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    16.839] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    16.839] (II) intel(0): Supported detailed timing:
[    16.839] (II) intel(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    16.839] (II) intel(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    16.839] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    16.839] (II) intel(0):  D196J&#65533;154W01
[    16.839] (II) intel(0):  $2=Eh&#65533;&#65533;&#65533;
[    16.839] (II) intel(0): EDID (in hex):
[    16.839] (II) intel(0): 	00ffffffffffff00320c010300000000
[    16.839] (II) intel(0): 	00120103802115780ab3409959538d27
[    16.839] (II) intel(0): 	25505400000001010101010101010101
[    16.839] (II) intel(0): 	0101010101017e1d00e8502020304030
[    16.839] (II) intel(0): 	36004bcf100000197e1d00e850202030
[    16.839] (II) intel(0): 	403036004bcf10000000000000fe0044
[    16.839] (II) intel(0): 	3139364a803135345730310a000000fe
[    16.840] (II) intel(0): 	0024323d45688ba7ff01010a202000af
[    16.840] (II) intel(0): EDID vendor "LPL", prod id 769
[    16.840] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    16.840] (II) intel(0): Printing DDC gathered Modelines:
[    16.840] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    16.840] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    16.840] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    16.840] (II) intel(0): Printing probed modes for output LVDS1
[    16.840] (II) intel(0): Modeline "1280x800"x60.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    16.840] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    16.840] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    16.840] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    16.840] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    16.856] (II) intel(0): EDID for output VGA1
[    16.872] (II) intel(0): EDID for output HDMI1
[    17.103] (II) intel(0): EDID for output TV1
[    17.103] (II) intel(0): Output LVDS1 connected
[    17.103] (II) intel(0): Output VGA1 disconnected
[    17.103] (II) intel(0): Output HDMI1 disconnected
[    17.103] (II) intel(0): Output TV1 disconnected
[    17.103] (II) intel(0): Using exact sizes for initial modes
[    17.103] (II) intel(0): Output LVDS1 using initial mode 1280x800
[    17.103] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    17.103] (II) intel(0): Kernel page flipping support detected, enabling
[    17.103] (**) intel(0): Display dimensions: (330, 210) mm
[    17.103] (**) intel(0): DPI set to (98, 96)
[    17.103] (II) Loading sub module "fb"
[    17.103] (II) LoadModule: "fb"
[    17.104] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.104] (II) Module fb: vendor="X.Org Foundation"
[    17.104] 	compiled for 1.10.1, module version = 1.0.0
[    17.104] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.104] (II) UnloadModule: "vesa"
[    17.104] (II) Unloading vesa
[    17.104] (II) UnloadModule: "fbdev"
[    17.104] (II) Unloading fbdev
[    17.104] (II) UnloadModule: "fbdevhw"
[    17.104] (II) Unloading fbdevhw
[    17.104] (==) Depth 24 pixmap format is 32 bpp
[    17.104] (==) intel(0): VideoRam: 262144 KB
[    17.104] (II) intel(0): [DRI2] Setup complete
[    17.104] (II) intel(0): [DRI2]   DRI driver: i965
[    17.104] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[    17.117] (II) UXA(0): Driver registered support for the following operations:
[    17.117] (II)         solid
[    17.117] (II)         copy
[    17.117] (II)         composite (RENDER acceleration)
[    17.117] (II)         put_image
[    17.117] (II)         get_image
[    17.117] (==) intel(0): Backing store disabled
[    17.117] (==) intel(0): Silken mouse enabled
[    17.117] (II) intel(0): Initializing HW Cursor
[    17.144] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    17.148] (==) intel(0): DPMS enabled
[    17.148] (==) intel(0): Intel XvMC decoder enabled
[    17.148] (II) intel(0): Set up textured video
[    17.148] (II) intel(0): Set up overlay video
[    17.148] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[    17.148] (II) intel(0): direct rendering: DRI2 Enabled
[    17.148] (==) intel(0): hotplug detection: "enabled"
[    17.149] (--) RandR disabled
[    17.149] (II) Initializing built-in extension Generic Event Extension
[    17.149] (II) Initializing built-in extension SHAPE
[    17.149] (II) Initializing built-in extension MIT-SHM
[    17.149] (II) Initializing built-in extension XInputExtension
[    17.149] (II) Initializing built-in extension XTEST
[    17.149] (II) Initializing built-in extension BIG-REQUESTS
[    17.149] (II) Initializing built-in extension SYNC
[    17.149] (II) Initializing built-in extension XKEYBOARD
[    17.149] (II) Initializing built-in extension XC-MISC
[    17.149] (II) Initializing built-in extension SECURITY
[    17.149] (II) Initializing built-in extension XINERAMA
[    17.149] (II) Initializing built-in extension XFIXES
[    17.149] (II) Initializing built-in extension RENDER
[    17.149] (II) Initializing built-in extension RANDR
[    17.149] (II) Initializing built-in extension COMPOSITE
[    17.149] (II) Initializing built-in extension DAMAGE
[    17.149] (II) Initializing built-in extension GESTURE
[    17.160] (II) AIGLX: Trying DRI driver /usr/lib/dri/i965_dri.so
[    17.178] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    17.178] (II) AIGLX: enabled GLX_INTEL_swap_event
[    17.178] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    17.178] (II) AIGLX: enabled GLX_SGI_make_current_read
[    17.178] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    17.178] (II) AIGLX: Loaded and initialized i965
[    17.178] (II) GLX: Initialized DRI2 GL provider for screen 0
[    17.179] (II) intel(0): Setting screen physical size to 338 x 211
[    17.191] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    17.203] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    17.204] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    17.204] (II) LoadModule: "evdev"
[    17.204] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.204] (II) Module evdev: vendor="X.Org Foundation"
[    17.204] 	compiled for 1.10.0.902, module version = 2.6.0
[    17.205] 	Module class: X.Org XInput Driver
[    17.205] 	ABI class: X.Org XInput driver, version 12.3
[    17.205] (II) Using input driver 'evdev' for 'Video Bus'
[    17.205] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.205] (**) Video Bus: always reports core events
[    17.205] (**) Video Bus: Device: "/dev/input/event7"
[    17.205] (--) Video Bus: Found keys
[    17.205] (II) Video Bus: Configuring as keyboard
[    17.205] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input7/event7"
[    17.205] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    17.205] (**) Option "xkb_rules" "evdev"
[    17.205] (**) Option "xkb_model" "pc105"
[    17.205] (**) Option "xkb_layout" "us"
[    17.214] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    17.214] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.214] (II) Using input driver 'evdev' for 'Power Button'
[    17.214] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.215] (**) Power Button: always reports core events
[    17.215] (**) Power Button: Device: "/dev/input/event1"
[    17.215] (--) Power Button: Found keys
[    17.215] (II) Power Button: Configuring as keyboard
[    17.215] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    17.215] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    17.215] (**) Option "xkb_rules" "evdev"
[    17.215] (**) Option "xkb_model" "pc105"
[    17.215] (**) Option "xkb_layout" "us"
[    17.215] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    17.215] (II) No input driver/identifier specified (ignoring)
[    17.216] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    17.216] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    17.216] (II) Using input driver 'evdev' for 'Sleep Button'
[    17.216] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.216] (**) Sleep Button: always reports core events
[    17.216] (**) Sleep Button: Device: "/dev/input/event2"
[    17.228] (--) Sleep Button: Found keys
[    17.228] (II) Sleep Button: Configuring as keyboard
[    17.228] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    17.228] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    17.228] (**) Option "xkb_rules" "evdev"
[    17.228] (**) Option "xkb_model" "pc105"
[    17.228] (**) Option "xkb_layout" "us"
[    17.231] (II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event10)
[    17.231] (II) No input driver/identifier specified (ignoring)
[    17.231] (II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event8)
[    17.232] (II) No input driver/identifier specified (ignoring)
[    17.232] (II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event9)
[    17.232] (II) No input driver/identifier specified (ignoring)
[    17.239] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    17.239] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    17.239] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    17.239] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.239] (**) AT Translated Set 2 keyboard: always reports core events
[    17.239] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    17.239] (--) AT Translated Set 2 keyboard: Found keys
[    17.239] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    17.239] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    17.239] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    17.239] (**) Option "xkb_rules" "evdev"
[    17.239] (**) Option "xkb_model" "pc105"
[    17.239] (**) Option "xkb_layout" "us"
[    17.240] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event5)
[    17.240] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[    17.240] (II) Using input driver 'evdev' for 'PS/2 Mouse'
[    17.240] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.240] (**) PS/2 Mouse: always reports core events
[    17.240] (**) PS/2 Mouse: Device: "/dev/input/event5"
[    17.240] (--) PS/2 Mouse: Found 3 mouse buttons
[    17.240] (--) PS/2 Mouse: Found relative axes
[    17.240] (--) PS/2 Mouse: Found x and y relative axes
[    17.240] (II) PS/2 Mouse: Configuring as mouse
[    17.240] (**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
[    17.240] (**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.240] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input5/event5"
[    17.240] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
[    17.240] (II) PS/2 Mouse: initialized for relative axes.
[    17.240] (**) PS/2 Mouse: (accel) keeping acceleration scheme 1
[    17.240] (**) PS/2 Mouse: (accel) acceleration profile 0
[    17.240] (**) PS/2 Mouse: (accel) acceleration factor: 2.000
[    17.240] (**) PS/2 Mouse: (accel) acceleration threshold: 4
[    17.241] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse0)
[    17.241] (II) No input driver/identifier specified (ignoring)
[    17.241] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event6)
[    17.241] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    17.241] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    17.241] (II) LoadModule: "synaptics"
[    17.241] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    17.242] (II) Module synaptics: vendor="X.Org Foundation"
[    17.242] 	compiled for 1.10.1, module version = 1.3.99
[    17.242] 	Module class: X.Org XInput Driver
[    17.242] 	ABI class: X.Org XInput driver, version 12.3
[    17.242] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    17.242] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    17.242] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    17.242] (**) Option "Device" "/dev/input/event6"
[    17.264] (--) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[    17.264] (--) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[    17.264] (--) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    17.264] (--) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[    17.264] (--) AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 16
[    17.284] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    17.284] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    17.288] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input6/event6"
[    17.288] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
[    17.288] (**) AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    17.288] (**) AlpsPS/2 ALPS GlidePoint: MaxSpeed is now 1.75
[    17.288] (**) AlpsPS/2 ALPS GlidePoint: AccelFactor is now 0.156
[    17.288] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    17.288] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    17.288] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    17.288] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    17.303] (II) AlpsPS/2 ALPS GlidePoint: failed to open grail, no gesture support
[    17.303] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    17.303] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse1)
[    17.303] (II) No input driver/identifier specified (ignoring)
[    17.310] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event4)
[    17.310] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    17.310] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    17.310] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.310] (**) Dell WMI hotkeys: always reports core events
[    17.310] (**) Dell WMI hotkeys: Device: "/dev/input/event4"
[    17.320] (--) Dell WMI hotkeys: Found keys
[    17.320] (II) Dell WMI hotkeys: Configuring as keyboard
[    17.320] (**) Option "config_info" "udev:/sys/devices/virtual/input/input4/event4"
[    17.320] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[    17.320] (**) Option "xkb_rules" "evdev"
[    17.320] (**) Option "xkb_model" "pc105"
[    17.320] (**) Option "xkb_layout" "us"
[    17.700] (II) intel(0): EDID vendor "LPL", prod id 769
[    17.700] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    17.700] (II) intel(0): Printing DDC gathered Modelines:
[    17.700] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    17.965] (II) intel(0): EDID vendor "LPL", prod id 769
[    17.965] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    17.965] (II) intel(0): Printing DDC gathered Modelines:
[    17.965] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    18.229] (II) intel(0): EDID vendor "LPL", prod id 769
[    18.229] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    18.229] (II) intel(0): Printing DDC gathered Modelines:
[    18.229] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    18.492] (II) intel(0): EDID vendor "LPL", prod id 769
[    18.492] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    18.492] (II) intel(0): Printing DDC gathered Modelines:
[    18.492] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    23.749] (II) intel(0): EDID vendor "LPL", prod id 769
[    23.749] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    23.749] (II) intel(0): Printing DDC gathered Modelines:
[    23.749] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    24.053] (II) intel(0): EDID vendor "LPL", prod id 769
[    24.053] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    24.053] (II) intel(0): Printing DDC gathered Modelines:
[    24.053] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    24.396] (II) intel(0): EDID vendor "LPL", prod id 769
[    24.396] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    24.396] (II) intel(0): Printing DDC gathered Modelines:
[    24.396] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    24.728] (II) intel(0): EDID vendor "LPL", prod id 769
[    24.728] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    24.728] (II) intel(0): Printing DDC gathered Modelines:
[    24.728] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    25.207] (II) intel(0): EDID vendor "LPL", prod id 769
[    25.207] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    25.207] (II) intel(0): Printing DDC gathered Modelines:
[    25.207] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    26.454] (II) intel(0): EDID vendor "LPL", prod id 769
[    26.454] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    26.454] (II) intel(0): Printing DDC gathered Modelines:
[    26.454] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    30.517] (II) intel(0): EDID vendor "LPL", prod id 769
[    30.517] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    30.517] (II) intel(0): Printing DDC gathered Modelines:
[    30.517] (II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[  5796.633] (II) config/udev: Adding input device Logitech Logitech Dual Action (/dev/input/js0)
[  5796.633] (II) No input driver/identifier specified (ignoring)
[  5796.634] (II) config/udev: Adding input device Logitech Logitech Dual Action (/dev/input/event11)
[  5796.635] (II) No input driver/identifier specified (ignoring)

```

Yep, you're running the intel driver.

---

### Post by brantpadams on 2011-09-08
I average 300 frames every 5 seconds at 60 FPS. Definitely nowhere near 3000!

I'm currently playing around with some of the display settings. What is the benefit of opengl?

Thanks for all the help btw.

---

### Post by Toz on 2011-09-09
> **brantpadams said:**
> I average 300 frames every 5 seconds at 60 FPS. Definitely nowhere near 3000!
Which explains the choppiness you're seeing.

> I'm currently playing around with some of the display settings.
Post back if you find any performance boosts from those settings for your video card.

>  What is the benefit of opengl?
From what I've read, it can improve the performance of some wine games.

Try this:
```
glxinfo | grep render
```
What does it return.

I'm not sure about the intel card that you have, but I've noticed alot of problems with the performance of intel cards in these and other forums.

> Thanks for all the help btw.
No worries - thats why we're here.

---

### Post by brantpadams on 2011-09-09
```
brant@brant-Inspiron-1525:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 965GM GEM 20100330 DEVELOPMENT x86/MMX/SSE2
```

So I'm guessing everything comes down to my video card at this point? I've read in some places that you overclock their performance, but I'm not sure how safe that is. For instance, I'm also using the dolphin emulator and the same choppiness occurs when playing games. Games like Smash Bros. Melee usually runs at a very slow 25% and that's after all the visual tweaks I've made to it. I've had a hard time finding any other kind of setting tweaks to improve performance, but I'm thinking I'm out of luck without a higher end card.

---

### Post by Toz on 2011-09-09
Kind of looks like it. The only other thing I could possibly suggest is maybe trying a newer version of X and intel drivers. If you're interested, have a look at xorg-edgers ([https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")).

---

### Post by brantpadams on 2011-09-09
So which packages out of that list are the ones I would need to try? Sorry, I just don't know which ones are specific to my case.

---

### Post by Toz on 2011-09-09
You can let the apt-package system determine that. You would set up your system to use the ppa, and the rest should happen automatically. 

Do the following from the command line:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```

If it doesn't work out, you can purge the ppa by doing the following:
```
sudo ppa-purge xorg-edgers
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by brantpadams on 2011-09-09
Added all the changes. No noticeable differences. I guess it was worth a shot! 

Good to know what I can handle now anyway. Thanks again for all your input.

---

### Post by Toz on 2011-09-09
Sorry it didn't work out for you.

---


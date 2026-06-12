---
title: "USB Mouse doesn't work after upgrade to 2.6.11-AMD64-K8 package"
date: 2005-06-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by joekr on 2005-06-24
Hey all,

I upgraded from 2.6.10-5-AMD64-K8 to 2.6.11-AMD64-K8 using Synaptic.  When booting into 2.6.11 my mouse doesn't work (at all).  When I boot back into 2.6.10-5 it works again...

How do I enable mouse support using 2.6.11?  I'd like to eventually phase 2.6.10 out as I get my system working using the 2.6.11 kernel.

Thanks I appreciate the help :D

---

### Post by FrzzMan on 2005-06-24
[QUOTE=joekr]Hey all,

I upgraded from 2.6.10-5-AMD64-K8 to 2.6.11-AMD64-K8 using Synaptic.  When booting into 2.6.11 my mouse doesn't work (at all).  When I boot back into 2.6.10-5 it works again...

How do I enable mouse support using 2.6.11?  I'd like to eventually phase 2.6.10 out as I get my system working using the 2.6.11 kernel.

Thanks I appreciate the help :D[/QUOTE]
 My (USB) mouse works with 2.6.11-amd64-k8...

What's your mouse?

---

### Post by joekr on 2005-06-24
It's a run-of-the-mill USB optical wheel mouse produced my Microsoft.

In 2.6.10 lsmod returns

```
joe@amd64box:~$ lsmod
Module                  Size  Used by
powernow_k8            13448  0
proc_intf               4420  0
freq_table              4872  1 powernow_k8
cpufreq_userspace       5456  1
cpufreq_ondemand        7596  0
cpufreq_powersave       2176  0
ipt_limit               2944  7
iptable_mangle          3456  0
ipt_LOG                 7552  7
ipt_MASQUERADE          4096  0
iptable_nat            29476  1 ipt_MASQUERADE
ipt_TOS                 2944  0
ipt_REJECT              7552  0
ip_conntrack_irc       72816  0
ip_conntrack_ftp       73584  0
ipt_state               2432  4
ip_conntrack           52000  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          4352  1
ip_tables              19200  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
nvidia               4569404  12
video                  18760  0
sony_acpi               6864  0
pcc_acpi               13568  0
button                  7776  0
battery                11400  0
container               5120  0
ac                      5640  0
ipv6                  268512  9
smbfs                  72328  2
forcedeth              18880  0
tsdev                   8768  0
snd_intel8x0           35584  3
usbhid                 34176  0
snd_ac97_codec         80992  1 snd_intel8x0
snd_pcm_oss            56676  1
snd_mixer_oss          20288  3 snd_pcm_oss
snd_pcm               102348  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26184  1 snd_pcm
snd                    58600  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11360  4 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
ehci_hcd               33604  0
ohci_hcd               22408  0
floppy                 65456  0
pcspkr                  4024  0
evdev                  10688  0
md                     48768  0
dm_mod                 63768  1
capability              5832  0
commoncap               9536  1 capability
rtc                    13320  0
psmouse                22412  0
mousedev               13148  1
parport_pc             40648  1
lp                     13104  0
parport                40844  2 parport_pc,lp
ide_generic             1728  0
ide_disk               20800  0
ide_cd                 45192  0
cdrom                  43304  1 ide_cd
amd74xx                15472  1
ide_core              150276  4 ide_generic,ide_disk,ide_cd,amd74xx
ext3                  140560  5
jbd                    61104  1 ext3
mbcache                 9160  1 ext3
sd_mod                 18584  8
sata_nv                 9860  12
libata                 55560  1 sata_nv
scsi_mod              143448  2 sd_mod,libata
unix                   30016  706
thermal                15692  0
processor              26432  2 powernow_k8,thermal
fan                     5256  0
fbcon                  38688  0
font                    8960  1 fbcon
bitblit                 5888  1 fbcon
vesafb                  7680  0
cfbcopyarea             4288  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             4288  1 vesafb
joe@amd64box:~$

```

My /etc/modules looks like this

```
amd74xx
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
rtc

```

and /etc/hotplug/blacklist looks like

```
amd74xx
#
# Listing a module here prevents the hotplug scripts from loading it.
# Usually that'd be so that some other driver will bind it instead,
# no matter which driver happens to get probed first.  Sometimes user
# mode tools can also control driver binding.
#
# Syntax:  driver name alone (without any spaces) on a line. Other
# lines are ignored.
#

# uhci ... usb-uhci handles the same pci class
usb-uhci
# usbcore ... module is loaded implicitly, ignore it otherwise
usbcore

#evbug is a debug tool and should be loaded explicitly
evbug

# these drivers are very simple, the HID drivers are usually preferred
usbmouse
usbkbd

# watchdog drivers should be loaded only if a watchdog daemon is installed
acquirewdt
advantechwdt
alim1535_wdt
alim7101_wdt
cpu5wdt
eurotechwdt
i810_tco
i8xx_tco
i810-tco
ib700wdt
indydog
machzwd
mixcomwd
pcwd
pcwd_pci
pcwd_usb
sa1100_wdt
sbc60xxwdt
sc1200wdt
sc520_wdt
scx200_wdt
shwdt
softdog
w83627hf_wdt
w83877f_wdt
wafer5823wdt
wdt285
wdt977
wdt
wdt_pci

# causes no end of confusion by creating unexpected network interfaces
eth1394

# eepro100 is obsoleted by e100 (Ubuntu bug #2156)
eepro100

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
snd_intel8x0m

```

And working xorg.conf (2.6.10-5)

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600]"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	Option		"NoLogo"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-86
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Thanks

---

### Post by subterrific on 2005-06-30
The 2.6.11 kernels are not supported by Ubuntu and provided only for developer testing. You can tell this in synaptic because they don't have the Ubuntu icon beside them. Do you have a good reason for wanting to upgrade from 2.6.10 now? You are better off reporting this as a bug to the Ubuntu kernel team using bugzilla. These forums are not read by the developers, they have better tools like bugzilla in place for bug tracking. That said, since 2.6.12 is out and being used in Breezy, 2.6.11 will probably be dropped all together from Ubuntu repositories, there is little reason for them to spend time working on it.

---


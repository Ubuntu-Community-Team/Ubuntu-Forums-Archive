---
title: "GTA:SA is not working at all with Intel Integrated chipset"
date: 2008-08-09
forum: Wine
---

### Post by sliorda on 2008-08-09
Help!

I can't get GTA to run on my ubuntu (Thinkpad R50e with integrated Intel graphic adapter). Even after upgrading wine from the upstream sources the game still refused to load. I think it's something to do with the graphics adapter I'm using. For some reason, xorg.conf is not saying "i810" under device section, but "Configured Video Device".

When trying to run gta, i only get black screen which changes to white and to black again. when I click anywhere on it, the application exits.

I'm using virtual desktop, and vertex shader support is disabled.

BTW: the game does work flawlessly in windows, on the same machine.

Can someone please help?

thanks.

```
$ wine --version
wine-1.1.2


$ cat /etc/issue.net 
Ubuntu 8.04.1



$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)



$ wine GTA_SA.EXE 
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
fixme:win:EnumDisplayDevicesW ((null),0,0x177f74c,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x12f5c8) : stub
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
Initialised SoundManager
fixme:dsound:IDirectSoundBufferImpl_SetFX (0x27d98f0,0,(nil),(nil)): stub
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)



$ cat /etc/X11/xorg.conf 
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us,il"
	Option		"XkbOptions"	"grp:alt_shift_toggle"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection



$ lsmod
Module                  Size  Used by
snd_rtctimer            4640  0 
usb_storage            73664  1 
libusual               19108  1 usb_storage
usblp                  15872  0 
michael_mic             3456  2 
arc4                    2944  2 
ecb                     4480  2 
ieee80211_crypt_tkip    11648  1 
geode_aes               7176  0 
blkcipher               8324  2 ecb,geode_aes
aes_generic            27712  0 
aes_i586               33536  1 
ieee80211_crypt_ccmp     7936  1 
af_packet              23812  4 
vmnet                  38204  16 
vmblock                16800  3 
vmmon                1824812  0 
i915                   32512  2 
drm                    82452  3 i915
binfmt_misc            12808  1 
ipv6                  267780  20 
uinput                 10240  1 
ppdev                  10372  0 
acpi_cpufreq           10796  1 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
lp                     12324  0 
pcmcia                 40876  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
battery                14212  0 
ac                      6916  0 
snd_intel8x0           35356  5 
snd_ac97_codec        101028  1 snd_intel8x0
video                  19856  0 
ac97_bus                3072  1 snd_ac97_codec
output                  4736  1 video
snd_pcm_oss            42144  0 
snd_pcm                78596  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          17920  1 snd_pcm_oss
thinkpad_acpi          51836  0 
evdev                  13056  7 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
nvram                   9992  2 thinkpad_acpi
serio_raw               7940  0 
psmouse                40336  0 
ipw2200               146120  0 
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
snd_seq_dummy           4868  0 
ieee80211              35528  1 ipw2200
ieee80211_crypt         7040  3 ieee80211_crypt_tkip,ieee80211_crypt_ccmp,ieee80211
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
button                  9232  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  4 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
intel_agp              25492  1 
snd                    56996  20 snd_rtctimer,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
agpgart                34760  3 drm,intel_agp
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
ext3                  136712  4 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  8 
pata_acpi               8320  0 
ata_generic             8324  0 
ata_piix               19588  5 
e100                   37388  0 
mii                     6400  1 e100
libata                159344  3 pata_acpi,ata_generic,ata_piix
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  7 usb_storage,libusual,usblp,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  3 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  5 

```

---

### Post by hikaricore on 2008-08-10
GTA:SA is a very very GPU intense game, which even runs a little slow on my NVIDIA 8600GTS.

My best guess would be that between intel's terrible Linux drivers and the sad opengl abilities
of many intel chipsets that you will not be able to run this game under WINE with your hardware.

---

### Post by sliorda on 2008-08-18
On Windows it runs perfectly. oh well.

thanks for your answer.

---


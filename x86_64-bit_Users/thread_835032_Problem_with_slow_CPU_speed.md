---
title: "Problem with slow CPU speed"
date: 2008-06-20
forum: x86 64-bit Users
---

### Post by marcusj on 2008-06-20
Hi

I have 8.04 2.6.24-19-generic #1 SMP.  I cannot get any CPU speeds other than 600 and 700MHz, although, clearly, I should be able to go faster.  I did a sudo cpufreq-selector -g performance and now it's locked at 700MHz but that's still about a third of its capabilities as far as I can tell (2.33GHz dual core CPU).  If I use cpufreq-selector -g ondemand it hops between 600MHz and 700MHz.  I haven't fiddled with the BIOS yet (ASUS motherboard).

Help?

Useful info below.

Marcus

cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
stepping	: 11
cpu MHz		: 700.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3728.83
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
stepping	: 11
cpu MHz		: 700.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3724.00
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
700000 600000 

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors 
userspace powersave ondemand conservative performance 

lsmod
Module                  Size  Used by
via                    47872  2 
drm                   105896  3 via
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0 
acpi_cpufreq           10832  0 
cpufreq_userspace       6180  0 
cpufreq_powersave       3200  0 
cpufreq_stats           8416  0 
cpufreq_ondemand       11152  2 
cpufreq_conservative    10632  0 
freq_table              6464  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
video                  23444  0 
output                  5632  1 video
container               6656  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
dock                   12960  0 
battery                16776  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
ac                      8328  0 
lp                     14916  0 
ipv6                  311848  30 
snd_hda_intel         440408  4 
snd_pcm_oss            47648  0 
nls_cp437               8320  2 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  3 snd_hda_intel,snd_pcm_oss
cifs                  251152  2 
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
usb_storage            82496  1 
libusual               23520  1 usb_storage
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70856  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10400  1 snd
serio_raw               9092  0 
button                 10912  0 
i2c_viapro             11672  0 
parport_pc             41128  1 
parport                44300  3 ppdev,lp,parport_pc
i2c_core               28544  1 i2c_viapro
via_agp                13184  1 
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
pcspkr                  4992  0 
psmouse                46236  0 
evdev                  14976  4 
ext3                  149264  3 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sg                     41880  0 
sr_mod                 20132  0 
sd_mod                 33280  7 
cdrom                  41512  1 sr_mod
ata_generic             9988  0 
floppy                 69096  0 
via_rhine              29832  0 
mii                     7552  1 via_rhine
ehci_hcd               41996  0 
uhci_hcd               29856  0 
usbcore               169904  5 usb_storage,libusual,ehci_hcd,uhci_hcd
pata_jmicron            8448  0 
ahci                   33028  0 
pata_via               15620  0 
sata_via               14596  3 
pata_acpi               9856  0 
libata                176432  6 ata_generic,pata_jmicron,ahci,pata_via,sata_via,pata_acpi
scsi_mod              178488  5 usb_storage,sg,sr_mod,sd_mod,libata
thermal                19744  0 
processor              41448  2 acpi_cpufreq,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3

---

### Post by marcusj on 2008-06-20
I did a sudo dpkg-reconfigure gnome-applets and now I can tweak from the GUI, but, surprise, surprise, I can only switch between 600 and 700 MHz.

---

### Post by sdennie on 2008-06-20
Have you tried to force a CPU speed?  I don't know if it will work (probably not) but:

```

sudo cpufreq-selector -g userspace -f 2330000

```

If that doesn't work, it might be a BIOS problem.  I'd make sure you have the latest revision of your BIOS.

---

### Post by marcusj on 2008-06-20
Just tried to force the CPU speed, the net effect was it just stuck at 700MHz.  I expect that there may be some checks somewhere that only let the CPU speed be set to values in /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies so you don't toast your CPU?

Can I query my BIOS version from Linux?

---

### Post by sdennie on 2008-06-20
> **marcusj said:**
> Just tried to force the CPU speed, the net effect was it just stuck at 700MHz.  I expect that there may be some checks somewhere that only let the CPU speed be set to values in /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies so you don't toast your CPU?


I figured that would be the case but, it was worth a try.

> 
Can I query my BIOS version from Linux?

Probably.  Try:

```

sudo dmidecode

```

It will print a ton of information (hopefully).  The BIOS version will be towards the top.

---

### Post by marcusj on 2008-06-20
OK, sudo dmidecode gives output below (snipped for some brevity).  According to the Asus website, I might have some luck upgrading to the next version of BIOS (0501):

Version  	0501  	2006/11/10 update
Description 	P3-PE5 BIOS version 0501
1. Support new CPUs. Please refer to our website at: [http://support.asus.com/cpusupport/cpusupport.aspx](http://support.asus.com/cpusupport/cpusupport.aspx)
2. Enhance compatibility with some CPUs
3. Enhance compatibility with some memory modules
4. Modify CPU Fan Speed Warning value from 800RPM to 600RPM for all intel CPU.
5. Fix it will hang during POST when installing 4G memory and a PCI-E VGA card.
6. Modify VGA Share Memory Size option value from "[ 64M]" to "[64MB]".
7. Fix sometimes S4 unstable issue 

BIOS Information
	Vendor: Phoenix Technologies, LTD
	Version: ASUS P5VD2-MX ACPI BIOS Revision 0402
	Release Date: 08/08/2006
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 512 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/360 KB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		AGP is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported

---

### Post by sdennie on 2008-06-20
The BIOS upgrade looks promising to me.

---

### Post by marcusj on 2008-06-20
Thanks for all the help, vor.

I now see on the Asus web site that the E6550 which is fitted in my machine (thanks, local 'trust us we will build it' PC shop, grr....) isn't officially supported by my motherboard / BIOS, although the ever so slightly slower E6300 and faster models (up to E6700) are.  So I may well just be able to hack something in the BIOS to force it to an E6300 (underclock) and the BIOS will then hopefully report a more usable selection of available CPU frequencies to Linux.

---

### Post by marcusj on 2008-06-20
Sigh...

...BIOS upgrade no good.  Couldn't find anything in the BIOS menus that looked useful.  Retried sudo cpufreq-selector -g userspace -f 2330000, to no avail (same result).

The only difference I can see after upgrading the BIOS is that the fan now occasionally spins into hyperdrive, chucking out more air than a Bell Huey...

---


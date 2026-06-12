---
title: "Can't get HW sensors to work please help"
date: 2007-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by shadco on 2007-01-01
I hope someone familiar with lm-sensors can help out here.

MB is a gigabyte ga-965p-ds3

see embedded data below

installed version of lm-sensors  1.2.10.1-2

```

uname -a

	uname -a
	Linux Kubuntu-2 2.6.17-10-generic #2 SMP Tue Dec 5 21:16:35 UTC 2006 x86_64 GNU/Linux

sensors-detect

	# sensors-detect revision 4171 (2006-09-24 03:37:01 -0700)
	
	This program will help you determine which kernel modules you need
	to load to use lm_sensors most effectively. It is generally safe
	and recommended to accept the default answers to all questions,
	unless you know what you're doing.
	
	We can start with probing for (PCI) I2C or SMBus adapters.
	Do you want to probe now? (YES/no): y
	Probing for PCI bus adapters...
	Use driver `i2c-i801' for device 0000:00:1f.3: Intel ICH8
	
	We will now try to load each adapter module in turn.
	Module `i2c-i801' already loaded.
	If you have undetectable or unsupported adapters, you can have them
	scanned by manually loading the modules before running this script.
	
	To continue, we need module `i2c-dev' to be loaded.
	Do you want to load `i2c-dev' now? (YES/no): y
	Module loaded successfully.
	
	We are now going to do the I2C/SMBus adapter probings. Some chips may
	be double detected; we choose the one with the highest confidence
	value in that case.
	If you found that the adapter hung after probing a certain address,
	you can specify that address to remain unprobed.
	
	Next adapter: SMBus I801 adapter at 0500
	Do you want to scan it? (YES/no/selectively): y
	Client found at address 0x08
	Client found at address 0x50
	Handled by driver `eeprom' (already loaded), chip type `eeprom'
	Client found at address 0x52
	Handled by driver `eeprom' (already loaded), chip type `eeprom'
	Client found at address 0x69
	
	Some chips are also accessible through the ISA I/O ports. We have to
	write to arbitrary I/O ports to probe them. This is usually safe though.
	Yes, you do have ISA I/O ports even if you do not have any ISA slots!
	Do you want to scan the ISA I/O ports? (YES/no): y
	Probing for `National Semiconductor LM78' at 0x290...       No
	Probing for `National Semiconductor LM78-J' at 0x290...     No
	Probing for `National Semiconductor LM79' at 0x290...       No
	Probing for `Winbond W83781D' at 0x290...                   No
	Probing for `Winbond W83782D' at 0x290...                   No
	Probing for `Winbond W83627HF' at 0x290...                  No
	Probing for `Silicon Integrated Systems SIS5595'...         No
	Probing for `VIA VT82C686 Integrated Sensors'...            No
	Probing for `VIA VT8231 Integrated Sensors'...              No
	Probing for `AMD K8 thermal sensors'...                     No
	Probing for `IPMI BMC KCS' at 0xca0...                      No
	Probing for `IPMI BMC SMIC' at 0xca8...                     No
	
	Some Super I/O chips may also contain sensors. We have to write to
	standard I/O ports to probe them. This is usually safe.
	Do you want to scan for Super I/O sensors? (YES/no): y
	Probing for Super-I/O at 0x2e/0x2f
	Trying family `ITE'...                                      Yes
	Found `ITE IT8718F Super IO Sensors'                        Success!
	(address 0x290, driver `it87')
	Trying family `National Semiconductor'...                   No
	Trying family `SMSC'...                                     No
	Trying family `VIA/Winbond/Fintek'...                       No
	Probing for Super-I/O at 0x4e/0x4f
	Trying family `ITE'...                                      No
	Trying family `National Semiconductor'...                   No
	Trying family `SMSC'...                                     No
	Trying family `VIA/Winbond/Fintek'...                       No
	
	Now follows a summary of the probes I have just done.
	Just press ENTER to continue:
	
	Driver `eeprom' (should be inserted):
	Detects correctly:
	* Bus `SMBus I801 adapter at 0500'
	Busdriver `i2c-i801', I2C address 0x50
	Chip `eeprom' (confidence: 6)
	* Bus `SMBus I801 adapter at 0500'
	Busdriver `i2c-i801', I2C address 0x52
	Chip `eeprom' (confidence: 6)
	
	EEPROMs are *NOT* sensors! They are data storage chips commonly
	found on memory modules (SPD), in monitors (EDID), or in some
	laptops, for example.
	
	Driver `it87' (should be inserted):
	Detects correctly:
	* ISA bus address 0x0290 (Busdriver `i2c-isa')
	Chip `ITE IT8718F Super IO Sensors' (confidence: 9)
	
	I will now generate the commands needed to load the required modules.
	Just press ENTER to continue:
	
	To make the sensors modules behave correctly, add these lines to
	/etc/modules:
	
	#----cut here----
	# I2C adapter drivers
	i2c-i801
	i2c-isa
	# Chip drivers
	eeprom
	it87
	#----cut here----

sensors

	~$ sensors
	No sensors found!
	Make sure you loaded all the kernel drivers you need.
	Try sensors-detect to find out which these are.




lsmod

	Module                  Size  Used by
	i2c_dev                14216  0
	rfcomm                 51360  0
	l2cap                  31744  5 rfcomm
	bluetooth              64644  4 rfcomm,l2cap
	ipv6                  334432  14
	video                  22920  0
	tc1100_wmi             10632  0
	sbs                    20928  0
	sony_acpi               7704  0
	pcc_acpi               19968  0
	i2c_ec                  7808  1 sbs
	hotkey                 14536  0
	dev_acpi               17540  0
	button                  9888  0
	battery                14088  0
	container               6656  0
	ac                      8328  0
	asus_acpi              21924  0
	af_packet              29452  2
	it87                   29476  0
	hwmon_vid               4992  1 it87
	eeprom                 10000  0
	i2c_isa                 7808  1 it87
	i2c_i801               11668  0
	i2c_core               29312  6 i2c_dev,i2c_ec,it87,eeprom,i2c_isa,i2c_i801
	parport_pc             43560  0
	lp                     16584  0
	parport                49932  2 parport_pc,lp
	tsdev                  11136  0
	snd_hda_intel          23452  1
	snd_hda_codec         219392  1 snd_hda_intel
	snd_pcm_oss            57344  0
	snd_mixer_oss          22784  1 snd_pcm_oss
	usbhid                 51360  0
	sk98lin               212572  0
	sg                     44584  0
	sky2                   50436  0
	snd_pcm               108168  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
	snd_timer              31112  1 snd_pcm
	snd                    79016  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
	soundcore              14112  1 snd
	psmouse                51088  0
	shpchp                 49068  0
	snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
	intel_agp              32704  1
	serio_raw              10244  0
	evdev                  14592  2
	pci_hotplug            38912  1 shpchp
	pcspkr                  5248  0
	floppy                 76648  0
	ext3                  164624  1
	jbd                    74024  1 ext3
	ehci_hcd               40456  0
	uhci_hcd               30096  0
	usbcore               167840  4 usbhid,ehci_hcd,uhci_hcd
	ide_generic             2944  0
	ide_cd                 39584  1
	cdrom                  43816  1 ide_cd
	jmicron                 6912  0 [permanent]
	ahci                   24452  0
	sd_mod                 25728  3
	generic                 7940  0
	ata_piix               13828  2
	libata                 88984  2 ahci,ata_piix
	scsi_mod              181424  4 sg,ahci,sd_mod,libata
	thermal                19472  0
	processor              38280  1 thermal
	fan                     7432  0
	vesafb                 11048  0
	capability              7304  0
	commoncap              10752  1 capability
	vga16fb                16656  1
	cfbcopyarea             5376  2 vesafb,vga16fb
	vgastate               10368  1 vga16fb
	cfbimgblt               4352  2 vesafb,vga16fb
	cfbfillrect             6272  2 vesafb,vga16fb
	fbcon                  45824  72
	tileblit                4736  1 fbcon
	font                   10240  1 fbcon
	bitblit                 8064  1 fbcon
	softcursor              3968  1 bitblit


mount

	/dev/sda1 on / type ext3 (rw,errors=remount-ro)
	proc on /proc type proc (rw,noexec,nosuid,nodev)
	/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
	varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
	varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
	procbususb on /proc/bus/usb type usbfs (rw)
	udev on /dev type tmpfs (rw,mode=0755)
	devshm on /dev/shm type tmpfs (rw)
	devpts on /dev/pts type devpts (rw,gid=5,mode=620)

/etc/fstab

	# /etc/fstab: static file system information.
	#
	# <file system> <mount point>   <type>  <options>       <dump>  <pass>
	proc            /proc           proc    defaults        0       0
	# /dev/sda1
	UUID=f91e0113-975c-41fd-8ff6-012dc31624ec /               ext3    defaults,errors=remount-ro 0       1
	# /dev/sda5
	UUID=528f5657-52f0-4764-bb20-cad0558da24b none            swap    sw              0       0
	/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
	/dev/           /media/floppy0  auto    rw,user,noauto  0       0
	sys              /sys             sysfs       default          0

ls -l /dev/i2c*

	crw-rw---- 1 root root 89, 0 2006-12-31 15:35 /dev/i2c-0

/etc/modules

	# /etc/modules: kernel modules to load at boot time.
	#
	# This file contains the names of kernel modules that should be loaded
	# at boot time, one per line. Lines beginning with "#" are ignored.
	
	lp
	rtc
	
	# Generated by sensors-detect on Sun Dec 31 11:03:49 2006
	# I2C adapter drivers
	i2c-i801
	i2c-isa
	# Chip drivers
	eeprom
	it87


ls -al /sys/class/hwmon
	total 0
	drwxr-xr-x  2 root root 0 2006-12-31 14:45 .
	drwxr-xr-x 26 root root 0 2006-12-31 15:35 ..

/etc/sysconfig/lm_sensors

	#    /etc/sysconfig/lm_sensors - Defines modules loaded by
	#                                /etc/init.d/lm_sensors
	#    Copyright (c) 1998 - 2001  Frodo Looijaard <frodol@dds.nl>
	#
	#    This program is free software; you can redistribute it and/or modify
	#    it under the terms of the GNU General Public License as published by
	#    the Free Software Foundation; either version 2 of the License, or
	#    (at your option) any later version.
	#
	#    This program is distributed in the hope that it will be useful,
	#    but WITHOUT ANY WARRANTY; without even the implied warranty of
	#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
	#    GNU General Public License for more details.
	#
	#    You should have received a copy of the GNU General Public License
	#    along with this program; if not, write to the Free Software
	#    Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
	#
	#
	# See also the lm_sensors homepage at:
	#     http://www.lm-sensors.org/
	#
	# This file is used by /etc/init.d/lm_sensors and defines the modules to
	# be loaded/unloaded. This file is sourced into /etc/init.d/lm_sensors.
	#
	# The format of this file is a shell script that simply defines the modules
	# in order as normal variables with the special names:
	#    MODULE_0, MODULE_1, MODULE_2, etc.
	#
	# List the modules that are to be loaded for your system
	#
	# Generated by sensors-detect on Sun Dec 31 15:41:20 2006
	MODULE_0=i2c-i801
	MODULE_1=i2c-isa
	MODULE_2=eeprom
	MODULE_3=it87
	MODULE_4=coretemp

/etc/init.d/lm_sensors

	#!/bin/sh
	
	PATH=/bin:/usr/bin:/sbin:/usr/sbin
	PROGRAM=/usr/bin/sensors
	
	test -x $PROGRAM || exit 0
	
	case "$1" in
	start)
		echo -n "Setting sensors limits:"
		/usr/bin/sensors -s 1> /dev/null 2> /dev/null
		/usr/bin/sensors 1> /dev/null 2> /dev/null
		echo " done."
		;;
	stop)
		;;
	force-reload|restart)
		$0 stop
		$0 start
		;;
	*)
		echo "Usage: /etc/init.d/sensors {start|stop|restart|force-reload}"
		exit 1
	esac
	
	exit 0

modprobe folowed by seensors

	shad@Kubuntu-2:~$ modprobe i2c-i801
	shad@Kubuntu-2:~$ modprobe i2c-isa
	shad@Kubuntu-2:~$ modprobe eeprom
	shad@Kubuntu-2:~$ modprobe it87
	shad@Kubuntu-2:~$ modprobe coretemp
	FATAL: Module coretemp not found.
	shad@Kubuntu-2:~$ sensors
	No sensors found!
	Make sure you loaded all the kernel drivers you need.
	Try sensors-detect to find out which these are.

```

---

### Post by J33pG33k on 2007-02-25
I don't know exactly how related out situations are/were (I am on an Asus P5W-DH Deluxe), but I can offer a little advice about the coretemp module.  I can say for sure that it is not yet included in the vanilla kernel sources, let alone the Ubuntu kernel 2.6.17-10.  

If you want to obtain support for the Core 2 Duo temperature sensor, you will need to build a new kernel ( 2.6.20+ ) with the coretemp patch.  I am running a custom 2.6.20 kernel with the patch and things are working just fine.  Just do some searching for "coretemp patch" and you should find some more information.

Hope this helps a little. :)

---


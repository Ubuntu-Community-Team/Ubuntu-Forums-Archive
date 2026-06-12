---
title: "Report: Edgy 64 on Dell Inspiron 9400/E1705"
date: 2006-11-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by linuxguiri on 2006-11-09
For the benefit of those considering the purchase of a Dell Inspiron 9400 (aka E1705) or planning to upgrade to Edgy on an existing Inspiron 9400, I thought I'd share my experience.

It'd be great if any Inspiron 9400 Edgy users could share their problem-solving tips here. I'll post any solutions that I find here as well.

This is a new Dell Inspiron 9400 (purchased Nov. 2006) with a fresh install of Edgy Eft 64 on a dual boot system (Ubuntu/WinXP).

Problems/Solutions/Workarounds:
* Problem: Touchpad button AND tap-to-click frequently stop functioning. (Occurs almost every minute. Not an issue in XP.) 
  Solution: add "notsc" to kernel options (Note: Use only with 386-64. Does not work with 386-32.)

* Problem: No WiFi after resume from suspend. (Not an issue in XP.)
  Workaround: Use Network Manager to manage wifi connection. May also need to create 2 scripts to correct resume [issue]("http://www.ubuntuforums.org/showpost.php?p=1795689&postcount=7") with network manager.

* Problem: Slow Ubuntu boot up: on the order of minutes. (WinXP boots in less than 30 seconds.)
  Solution: add "notsc" to kernel options

* Problem: Slow launch of simple applications: takes about 30-60 seconds to launch terminal, Firefox, etc. (The rectangular launch graphic usually advances at a slow speed of about 1 frame per 3 seconds.)
  Solution: add "notsc" to kernel options

* Problem: Super sensitive keyboard driver: characters repeat with a single tap. (This is not the same as holding a key down to repeat: keyboard repeat delay is set to about 3 seconds.) This is not an issue in XP. 
  Solution: add "notsc" to kernel options

* Problem: Both CPUs locked at maximum frequency after resume from suspend (1.83 GHz). CPU temp increases above 67C. 
 Workaround: Create script in /etc/acpi/resume.d/ to run "invoke-rc.d powernowd restart" Details in this [post]("http://www.ubuntuforums.org/showpost.php?p=1791164&postcount=21"). Check CPU freqs with: "sudo cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq" (also "cpu1").


System details:
* Intel Core 2 Duo processor T5600 (2MB Cache/1.83GHz/667MHz FSB)
* 17 inch UltraSharp Wide Screen UXGA Display with TrueLife
* 1GB Shared Dual Channel DDR2 SDRAM at 533MHz 
* 256MB NVIDIA GeForce Go 7900 GS 
* 120GB 5400RPM SATA Hard Drive 
* Intel PRO/Wireless 3945 Internal Wireless
* Integrated 10/100 Network Card and Modem 
* 8x CD/DVD burner (DVD+/-RW) with double-layer DVD+R write capability


Current /etc/X11/xorg.conf:
```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
#	Load	"synaptics"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
	Option		"XkbVariant"	"intl"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"on"
EndSection

# Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
# EndSection

# Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
# EndSection

# Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
# EndSection

Section "Device"
	Identifier	"256 MB NVIDIA GeForce Go 7900 GS"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NvAGP"		"1"
EndSection

Section "Monitor"
	Identifier	"Dell UltraSharp 17 inch Wide Screen UXGA with TrueLife"
	Option		"DPMS"
	HorizSync	28-96
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"256 MB NVIDIA GeForce Go 7900 GS"
	Monitor		"Dell UltraSharp 17 inch Wide Screen UXGA with TrueLife"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad" #"AlwaysCore"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Current /etc/default/acpi-support:
```

ACPI_SLEEP=true

ACPI_HIBERNATE=true

ACPI_SLEEP_MODE=mem

MODULES=""

MODULES_WHITELIST="ipw3945"

SAVE_VBE_STATE=false

VBESTATE=/var/lib/acpi-support/vbestate

POST_VIDEO=false

# SAVE_VIDEO_PCI_STATE=true

USE_DPMS=false

# RADEON_LIGHT=true

# DOUBLE_CONSOLE_SWITCH=true

HIBERNATE_MODE=shutdown

LOCK_SCREEN=true

# DISABLE_DMA=true

# RESET_DRIVE=true

STOP_SERVICES="mysql "

RESTART_IRDA=false

ENABLE_LAPTOP_MODE=false

```

Current /boot/grub/menu.lst:
```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro quiet splash vga=normal notsc
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Microsoft Windows XP Embedded MediaDirect
root		(hd0,4)
savedefault
makeactive
chainloader	+1

```

Suspend did not work originally until I made changes to the acpi-support as posted above.

Virtual consoles were blank after installing nvidia driver. Solution: add vga=normal to kopt in /boot/grub/menu.lst as posted above.

I filed a bug on the Synaptics touchpad issue here: [https://launchpad.net/bugs/70687](https://launchpad.net/bugs/70687) EDIT: Turns out it's not a synaptics bug, it was a timer app issue, solved by adding "notsc" to the kernel options (see above).

For those interested in keeping their MediaDirect function entact with a dual boot system, leave the 3 pre-existing primary partitions, shrink the WinXP partition and place an extended partition for your Ubuntu partitions (including any FAT32 partitions for sharing files with WinXP). You will be able to load MediaDirect by pressing the MediaDirect button when the computer is off. (In Ubuntu, it launches RhythmBox. Cool!)

---

### Post by dbott67 on 2006-11-09
I may be out to lunch on this one, but isn't the Core 2 Duo a 32-bit CPU?  I think you should be using the x86 architecture with SMP kernel.

I've got a Dell 6400 with T2400 and that's what I'm using.  I'm also running Dapper, but it's quite fast.
[http://www.ubuntuforums.org/showthread.php?t=274915](http://www.ubuntuforums.org/showthread.php?t=274915)

-Dave

---

### Post by hesser on 2006-11-09
I am running on one and you must NOT use the 64 bit install. The DUO is still a 32 bit.

Edit: Never mind. I am stupid. You are using the t5600. It is a 64 bit CPU. Sorry

---

### Post by dbott67 on 2006-11-09
> **hesser said:**
> I am running on one and you must NOT use the 64 bit install. The DUO is still a 32 bit.

That's what I thought.

Edit: and I even thought that the Core 2 Duo was 32-bit, but like I said, I could be out to lunch (... and it was good!)

---

### Post by linuxguiri on 2006-11-09
The Core Duo is 32-bit.

The Core 2 Duo is 64-bit.

I have a Core 2 Duo processor.

From Intel's website:
"All Intel® Core™2 Duo processors feature:
 	Intel® dual-core technology
 	Enhanced Intel SpeedStep® Technology
 	Intel® Extended Memory 64 Technology&#934;
 	Execute Disable Bit°"
[http://www.intel.com/products/processor/core2duo/specifications.htm](http://www.intel.com/products/processor/core2duo/specifications.htm)

From wikipedia:
"Intel Core 2 processors feature EM64T"
[http://en.wikipedia.org/wiki/Core_2_Duo](http://en.wikipedia.org/wiki/Core_2_Duo)

> Originally Posted by hesser:
Edit: Never mind. I am stupid. You are using the t5600. It is a 64 bit CPU. Sorry
No worries. I blame Intel: why do they think a little "2" is enough to indicate 64 bit vs. 32 bit?!

---

### Post by dbott67 on 2006-11-09
Very strange... in all of the stuff I've read about the Core 2 Duo (vs. the Core Duo) I've never seen mention of the 64-bit CPU (unlike other CPUs like the Xeon & Itanium).

Not that this is going to fix the problem, but is there a particular reason you want to run the 64-bit version vs. 32-bit version.  From what (limited) stuff I read prior to buying the core duo (I was seriously considering AMD Athlon 64-based chip), I decided that the lack of support from vendors regarding 64-bit drivers & apps would offset any performance benefits that the 64-bit version offered.

Unless there is a pressing need for the 64-bit, I would consider the 32-bit version.

-Dave

---

### Post by AVonGauss on 2006-11-10
I have a new latitude D820 and when trying to install the 64-bit version of Edgy received the same problems you are - slow animations and erratic keys repeating.  I believe the solution is to place "notsc" on your kernel options line in the grub configuration (menu.lst).  This prevents the problem with the Core 2 Duo multiple-frequency scaling from screwing up the kernel timing.

---

### Post by linuxguiri on 2006-11-10
> **AVonGauss said:**
> I have a new latitude D820 and when trying to install the 64-bit version of Edgy received the same problems you are - slow animations and erratic keys repeating.  I believe the solution is to place "notsc" on your kernel options line in the grub configuration (menu.lst).  This prevents the problem with the Core 2 Duo multiple-frequency scaling from screwing up the kernel timing.

Wow!!!! Adding "notsc" to my kernel options appears to have done the trick! No more touchpad, keyboard, or animation problems. :D 

Thank you so much, AVonGauss!

PS What does "notsc" actually do?

---

### Post by AVonGauss on 2006-11-10
If you do a Google search you'll get a much better answer, but the basic problem is that in a Core 2 Duo system the core frequencies are independent of each other (one can run 2000 and the other 1000).  The Linux kernel incorrectly assumes that both cores will run at the same frequency and hence the messed up timing - although why the keyboard driver is using a timer is beyond me...

The "notsc" option disables the timer facility that relies on the core frequency, hence it uses more reliable methods for a Core 2 Duo system.  If you do...

cat /var/log/messages | grep -i time

That should show you the timing method that its chosing to run under...

---

### Post by AVonGauss on 2006-11-11
In case it matters, this should be resolved in kernel 2.6.18.2.

---

### Post by ijuz on 2006-11-12
Because it's basically impossible to find out with google what laptops happily runs 64 bit edgy (or other amd64 versions):

@linuxguiri
Does suspend to disk work reliable (64 bit + nvidia driver) on the 9400?
(just because you can often read that suspend works in 80% of the cases or something like that)
How about noise? (the fans also seem to be OS controlled)


@AVonGauss
Are you using your D820 with 64bit edgy?

---

### Post by linuxguiri on 2006-11-12
> **ijuz said:**
> 
@linuxguiri
Does suspend to disk work reliable (64 bit + nvidia driver) on the 9400?
(just because you can often read that suspend works in 80% of the cases or something like that)
How about noise? (the fans also seem to be OS controlled)


Suspend/resume has worked everytime I've used it after I modified acpi-support as posted above. (This is with the nvidia driver.) The only problem is there's no wireless after resume. I'm sure the wireless thing can be fixed, but I haven't found the solution yet.

The fan doesn't run continually, if that's what you're getting at in terms of noise. It only comes on when the temp gets around 50C and it goes off automatically after the temp has cooled to around 40C.

Another user and I have updated the laptop testing wiki on this model for both 64-bit and 32-bit here: [https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron9400](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron9400)

Hope this helps. Let me know if you have more questions.

---

### Post by LordYama on 2006-11-13
> **AVonGauss said:**
> If you do a Google search you'll get a much better answer, but the basic problem is that in a Core 2 Duo system the core frequencies are independent of each other (one can run 2000 and the other 1000).  The Linux kernel incorrectly assumes that both cores will run at the same frequency and hence the messed up timing - although why the keyboard driver is using a timer is beyond me...

There is a bug when running 32-bit Edgy on this laptop (I'm not sure if it's present in the 64-bit version), where if you resume from hibernation/suspend it locks the second core at its maximum frequency. The first core continues to scale as normal. Could this bug be related? I have noticed that using 'notsc' on a 32-bit kernel creates a kernel panic on boot.

---

### Post by LordYama on 2006-11-13
> **ijuz said:**
> Does suspend to disk work reliable (64 bit + nvidia driver) on the 9400?
(just because you can often read that suspend works in 80% of the cases or something like that)
How about noise? (the fans also seem to be OS controlled)

I realise that this is a 64-bit thread, but I must say that this laptop works superbly with 32-bit Edgy Eft. My main gripe is that the second CPU core is locked at its maximum frequecy after resume (the first core is unaffected). Other than that it boots, shuts down, hibernates and suspends like a dream. Wireless is not adversely affected.

I initially tried 64-bit but was discouraged by the bugs mentioned earlier in this thread. It appears that this laptop is very close to being perfect in 64-bit mode. I am looking forward to trying 64-bit Feisty Faun on it.

> **linuxguiri said:**
> Another user and I have updated the laptop testing wiki on this model for both 64-bit and 32-bit here: [https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron9400](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron9400)

I am that [other user]("https://wiki.ubuntu.com/SridharDhanapalan") :) 

I strongly suggest that you take a look at that wiki page, and please post your own findings there as well.

---

### Post by linuxguiri on 2006-11-16
> **LordYama said:**
> ...this laptop works superbly with 32-bit Edgy Eft. My main gripe is that the second CPU core is locked at its maximum frequecy after resume (the first core is unaffected). 

Is there a command I can run to check to see if the second CPU core is locked at its maximum frequency?

I only know how to check to see if CPU frequency scaling is supported:
```
sudo invoke-rc.d powernowd restart
```

> **LordYama said:**
> 
I initially tried 64-bit but was discouraged by the bugs mentioned earlier in this thread. It appears that this laptop is very close to being perfect in 64-bit mode. 

I'm happy to announce that all the major issues that I had when I started this thread have been taken care of. I now have wifi after resume from suspend. (I installed Network Manager.) I edited the original post with the solutions.

> **LordYama said:**
> 
I am that [other user]("https://wiki.ubuntu.com/SridharDhanapalan") :) 


Pleased to make your acquaintance, fellow Inspirion 9400/Ubuntu user on the other side of the planet. ;)

---

### Post by ijuz on 2006-11-16
> **linuxguiri said:**
> Is there a command I can run to check to see if the second CPU core is locked at its maximum frequency?


x86info -mhz
may show at least the frequency

How long can you run the I9400 on battery with Linux?

---

### Post by linuxguiri on 2006-11-17
> **ijuz said:**
> x86info -mhz
may show at least the frequency

```
x86info v1.17.  Dave Jones 2001-2005
Feedback to <davej@redhat.com>.

Found 2 CPUs
--------------------------------------------------------------------------
CPU #1
/dev/cpu/0/cpuid: No such file or directory
Found unknown cache descriptors: 5 86 87 176 177 240 
Family: 6 Model: 15 Stepping: 6 Type: 0 Brand: 0
CPU Model: Unknown CPU Original OEM
Feature flags:
 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflsh ds acpi mmx fxsr sse sse2 ss ht tm pbe sse3 monitor ds-cpl est tm2 cx16 xTPR
Extended feature flags:
 SYSCALL xd em64t
Instruction TLB: 4K pages, 4-way associative, 128 entries.
Found unknown cache descriptors: 5 86 87 176 177 240 
Processor serial: 0000-06F6-0000-0000-0000-0000
The physical package supports 2 logical processors 

1.8Ghz processor (estimate).

--------------------------------------------------------------------------
CPU #2
Found unknown cache descriptors: 5 86 87 176 177 240 
Family: 6 Model: 15 Stepping: 6 Type: 0 Brand: 0
CPU Model: Unknown CPU Original OEM
Feature flags:
 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflsh ds acpi mmx fxsr sse sse2 ss ht tm pbe sse3 monitor ds-cpl est tm2 cx16 xTPR
Extended feature flags:
 SYSCALL xd em64t
Instruction TLB: 4K pages, 4-way associative, 128 entries.
Found unknown cache descriptors: 5 86 87 176 177 240 
Processor serial: 0000-06F6-0000-0000-0000-0000
The physical package supports 2 logical processors 

1.8Ghz processor (estimate).

--------------------------------------------------------------------------
WARNING: Detected SMP, but unable to access cpuid driver.
Used Uniprocessor CPU routines. Results inaccurate.
```

Mean anything to you?

The Gnome CPU Frequency Scaling Monitor Panel applet tells me that both CPU0 and CPU1 are running at 1 GHz. 

> **ijuz said:**
> 
How long can you run the I9400 on battery with Linux?

I just got the standard 53WHr, 6-Cell, 11.1V battery. It runs about 2 hours with Linux. 

If I could do it over again, I'd pay the extra $50 for the 80WHr, 9-Cell, 14.8V battery. What was I thinking?

---

### Post by ijuz on 2006-11-17
> **linuxguiri said:**
> 
```

1.8Ghz processor (estimate).

1.8Ghz processor (estimate).

```

Mean anything to you?

The Gnome CPU Frequency Scaling Monitor Panel applet tells me that both CPU0 and CPU1 are running at 1 GHz. 


No, doesn't help.
(it does also show the maximum frequency with x86info -mhz on my Dell C810, that was different when it was still using the wrong cpufreq module...)


You may check:
cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq

Doesn't exist on my prehistoric laptop, but probably on yours :-)

---

### Post by linuxguiri on 2006-11-18
Thanks, ijuz, for that command. It seems to return what we're looking for.

It looks like the cpu freq is locked at max on both cpu cores after resume from suspend.

```
cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
```

and

```
cat /sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_cur_freq
```

both return 1.83 GHz after a resume from suspend and the cpu temp steadily climbs.

After I run:
```
sudo invoke-rc.d powernowd restart
```

The freq for both cpu0 and cpu1 is 1 GHz (The freq before the suspend.)

Is there a way to make powernowd automatically restart on resume from suspend?

---

### Post by ijuz on 2006-11-18
> **linuxguiri said:**
> 
Is there a way to make powernowd automatically restart on resume from suspend?

Sure, take a look at /etc/acpi/ or more exactly /etc/acpi/resume.d/

I guess you just can add a script to restart powernowd into that dir.

---

### Post by linuxguiri on 2006-11-22
> **ijuz said:**
> Sure, take a look at /etc/acpi/ or more exactly /etc/acpi/resume.d/


Thanks! That did the trick. Now everytime I resume from suspend my cpu's are not locked at their maximum frequency.

For the record, I created this script: 
/etc/acpi/resume.d/74-restart-powernowd.sh:

```
#!/bin/sh

# Restart powernowd so cpu does not stay locked at maximum speed
invoke-rc.d powernowd restart
```

And made it executable:
```
sudo chmod +x /etc/acpi/resume.d/74-restart-powernowd.sh
```

BTW, I also tried removing powernowd and configuring speedstep-centrino according to this [howto]("http://www.ubuntuforums.org/showthread.php?t=248867"), but it didn't solve the problem and messed up network manager after resume as well. Anyhow, it sounds like powernowd actually starts cpufreq-ondemand and speedstep-centrino in Edgy (can anyone confirm this?)

---

### Post by LordYama on 2006-11-25
> **linuxguiri said:**
> Is there a command I can run to check to see if the second CPU core is locked at its maximum frequency?

The easiest way is to run
```
$ cat /proc/cpuinfo
```

It will tell you the current frequency of each CPU core. At idle, a 2GHz Core 2 Duo (which is what I have) should run at 1000MHz.

> Pleased to make your acquaintance, fellow Inspirion 9400/Ubuntu user on the other side of the planet. ;)

Nice to meet you. Isn't community wonderful? :)

> **linuxguiri said:**
> The Gnome CPU Frequency Scaling Monitor Panel applet tells me that both CPU0 and CPU1 are running at 1 GHz.

That's how it should be most of the time. The CPU only throttles up when it needs to.

> I just got the standard 53WHr, 6-Cell, 11.1V battery. It runs about 2 hours with Linux. 

If I could do it over again, I'd pay the extra $50 for the 80WHr, 9-Cell, 14.8V battery. What was I thinking?

The 9-cell battery is definitely worth purchasing. I can get about three and a half hours out of mine, running basic desktop applications. Another way to save power is to have enough RAM to handle all of your applications without needing to use the swap.

> **linuxguiri said:**
> Thanks! That did the trick. Now everytime I resume from suspend my cpu's are not locked at their maximum frequency.

For the record, I created this script: 
/etc/acpi/resume.d/74-restart-powernowd.sh:

```
#!/bin/sh

# Restart powernowd so cpu does not stay locked at maximum speed
invoke-rc.d powernowd restart
```

And made it executable:
```
sudo chmod +x /etc/acpi/resume.d/74-restart-powernowd.sh
```

Brilliant! That worked for me as well. I also found that Bluetooth sometimes stopped working upon resume, so I added a script to disable it on suspend/hibernate:

```
#!/bin/sh

# Stop Bluetooth
hciconfig hci0 down
```

Save it as /etc/acpi/suspend.d/50-bluetooth-stop.sh and make it executable. I've found that it re activates automatically upon resume, so there's no need for a corresponding wakeup script.

As much as I'd love to say that my issues with this laptop are disappearing, I have discovered a few more.

My display does not reliably turn off when the lid is closed, forcing me to check it every time. GNOME Power Manager is able to tell that the lid is closed, but for some reason it doesn't always turn off the screen.

Hibernate/resume is not as reliable as I had once thought. Sometimes when hibernating, it doesn't turn off the computer. If I turn it of manually, I may or may not be able to resume. If the latter, the system performs a fresh boot.

I am unable to burn a DVD correctly. While K3b says that the burn was successful, the verification process fails. I have noticed that burning tends to fail in the last few hundred megabytes of the disc. I have confirmed this by trying to read the files towards the end of the disc. I have no problem with burning in Windows, using the Sonic software that was supplied by Dell.

---

### Post by heng on 2006-11-29
Using 32-bit ubuntu on the 9400, I had a problem with no sound on restarting from a hibernate.

Adding MODULES="snd_hda_intel" to /etc/default/acpt-support seems to fix this.

---

### Post by jbeckmann on 2006-12-03
Hi,

I have a very special problem with Ubuntu 64 installation on my Inspiron 9400:

Every time I close the cover, the system freezes immediately and completly, but the backlight stays turned on. The same problem occurs with Debian testing for AMD64 but not with Debian testing for i386/P6.

I already tried to stop the acpid etc. before closing it, but that changes nothing.

Any ideas what to do?

Cheers,

Joerg

---

### Post by linuxguiri on 2006-12-17
> **jbeckmann said:**
> Every time I close the cover, the system freezes immediately and completly, but the backlight stays turned on. 

Are you using an Inspiron 9400?
32 bit or 64 bit?
What are the settings in System/Preferences/Power Management Preferences?
What does your /etc/default/acpi-support look like?

---

### Post by mattyj on 2006-12-23
> **AVonGauss said:**
> In case it matters, this should be resolved in kernel 2.6.18.2.


Hello,

I am curious if the more recent kernels have resolved this issue.  I am looking at a Dell D820 with similar behavior and curious if these bugs have been fixed, and which kernel you need to run to fix them on a Core2duo laptop.

This is the only thing I could find on it...


[http://jmspeex.livejournal.com/](http://jmspeex.livejournal.com/)

---

### Post by prince_niceguy on 2007-01-07
thank you so much... i have having a hyper sensitive keyboard... now it is working great.. thanks again....

---

### Post by LordYama on 2007-01-07
Are anyone having problems with burning DVDs? I've been using k3b, which reports a successful burn, but fails on verification. When trying to read the final few hundred megabytes of the disc, I get an I/O error. This happens every time.

---

### Post by prince_niceguy on 2007-01-09
I am not able to suspend or hibernate my computer. I have modified as stated in the first post... any idea what could be wrong???

I am having dell inspiron 6400 with ATI X1300, Intel core 2 duo T5500 (not sure, one with 1.6GHz), 1GB RAM.

Pls. help me...](*,)

---

### Post by linuxguiri on 2007-01-21
> **prince_niceguy said:**
> I am having dell inspiron 6400 with ATI X1300, Intel core 2 duo T5500 (not sure, one with 1.6GHz), 1GB RAM.

Since you have an ATI graphics card, the settings may need to be slightly different. I have a Radeon card.

You might check to see what driver you're using. 

What's it say in your  /etc/X11/xorg.conf ?

I remember reading something about using the fglrx driver. You might want to search the forums for info on that.

---

### Post by shinji257 on 2007-02-27
I found that it doesn't add the Dell Diagnostics partition to the grub menu.  I guess for good reason.  I found that adding the following to the menu.lst file for grub worked around it.  If you don't add it then you can't get to the second stage when you select as the boot option.  Only applies if you opted to keep the 50MB diagnostics partition on the hard drive or if you are still running the stock drive.

title Dell Diagnostics
root (hd0,0)
chainloader +1

Oh and also why does the splash screen look weird for me.  There is no color at all.

This issue only happens with x86_64 Edgy 6.10.  It does not happen with i386 Edgy 6.10 or with either x86_64 or i386 Dapper 6.06

---

### Post by prince_niceguy on 2007-02-28
> **jbeckmann said:**
> Hi,

I have a very special problem with Ubuntu 64 installation on my Inspiron 9400:

Every time I close the cover, the system freezes immediately and completly, but the backlight stays turned on. The same problem occurs with Debian testing for AMD64 but not with Debian testing for i386/P6.

I already tried to stop the acpid etc. before closing it, but that changes nothing.

Any ideas what to do?

Cheers,

Joerg


I too am having the same problem.. i havent tried debian though... any one who has similar issue... please help...

---

### Post by shinji257 on 2007-02-28
I also have this issue.  Close the lid and the system locks up.  Happened on Dapper and Edgy.  Both i386 and x86_64 with no change at all.

---

### Post by sgardne on 2007-03-14
You  talk about adding notsc to the kernel.... what exactly does this mean and how do you accomplish it?

thanks-

---

### Post by linuxguiri on 2007-03-14
> **sgardne said:**
> You  talk about adding notsc to the kernel.... what exactly does this mean and how do you accomplish it? 

assuming you use grub as your bootloader, in order to change the kernel options, from a terminal prompt: 
```
sudo gedit /boot/grub/menu.lst
```

find the line that says something like (look for kopt):
```
# kopt=root=/dev/sda1 ro
```

and add "notsc" to the end so it reads:
```
# kopt=root=/dev/sda1 ro notsc
```

save and close it. 

then, at the command prompt enter:
```
sudo update-grub
```

this wiki page: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto) has more information about grub and kernel options.

this post: [http://www.ubuntuforums.org/showpost.php?p=1741375&postcount=9](http://www.ubuntuforums.org/showpost.php?p=1741375&postcount=9) explains what notsc does.

let me know if this doesn't work for you.

---

### Post by linuxguiri on 2007-03-14
> **shinji257 said:**
> I also have this issue.  Close the lid and the system locks up.  Happened on Dapper and Edgy.  Both i386 and x86_64 with no change at all.

happens to me too. i suspend via menu or Fn+Esc

---

### Post by erdomi on 2007-03-24
Following the advice on this link to help fix a keyboard problem, I added notsc to grub/menu.lst.  However, when I rebooted my computer, I get a kernel panic because the timer is not working.  Is there a way to get around this?

Thanks,
erdomi

---

### Post by linuxguiri on 2007-03-24
> **erdomi said:**
>  when I rebooted my computer, I get a kernel panic because the timer is not working.  Is there a way to get around this?


Do you see the the GRUB boot up screen when you boot?
You should be able to strike "e" to edit the boot option. 
Use the arrow keys to scroll to the line where notsc is written. (It should look something like: "/boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro quiet splash vga=normal notsc".) 
Then, delete "notsc," strike "enter," then "b" to boot. 
Once you're booted into Ubuntu you should be able to edit the grub/menu.lst the same way you did before but this time remove "notsc" instead this time.

> **erdomi said:**
> Following the advice on this link to help fix a keyboard problem, I added notsc to grub/menu.lst.  
Are you running 64 bit Dapper on a Dell Inspiron 9400? 
Did you have problems with characters repeating with a single keystroke?

---

### Post by LordYama on 2007-04-20
> **LordYama said:**
> Are anyone having problems with burning DVDs? I've been using k3b, which reports a successful burn, but fails on verification. When trying to read the final few hundred megabytes of the disc, I get an I/O error. This happens every time.

Never mind. I had Dell replace my burner, and now all is well :)

---


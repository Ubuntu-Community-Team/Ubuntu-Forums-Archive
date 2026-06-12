---
title: "Random reboots"
date: 2008-05-06
forum: x86 64-bit Users
---

### Post by kuja on 2008-05-06
I'm getting random reboots but I'm not sure why. I'm certainly not telling it to reboot, and nothing out of place seems to be showing up in /var/log/syslog, /var/log/dmesg, /var/log/kern.log, or /var/log/messages. Anybody have any ideas?

Edit:
In case it would be helpful -- 
[Here are the hardware specs](http://secure.newegg.com/NewVersion/wishlist/PublicWishDetail.asp?WishListNumber=4729729)

I've also now attached some other potentially interesting info - dmesg, kern, messages, and syslog info pertinent to bootup (there is nothing logged near the time of any of the reboots that have happened anyhow). Also attached is lscpi -vv output, and lshw output.

Edit2:
Ancient post though this may be, feel like it needs closed. I'm fairly convinced it was related to the memory in the system. Oddly enough it passed memtest though ... but I gave it to someone else with a different board years later and he swears up and down one of the sticks was bad ... and that the memory just wasn't that great to begin with. Probably won't buy Patriot memory in the future.

---

### Post by Vadi on 2008-05-06
Reboot as in full reboot, or do you get logged out? Also what video card are you using?

---

### Post by njparton on 2008-05-06
Are you overclocking your system?
 
It sounds like an overclocking and/or hardware related problem, usually when overclocking your CPU or RAM.

---

### Post by kuja on 2008-05-06
Full reboot.
Nvidia 8600GT
No, I'm not overclocking

---

### Post by njparton on 2008-05-06
Is it a new PC/do you get this in windows (if you use it)?

---

### Post by njparton on 2008-05-06
Download memtest86 (google it) and try testing your ram.

---

### Post by kuja on 2008-05-06
> **njparton said:**
> Is it a new PC/do you get this in windows (if you use it)?
It's a new computer
I don't use Windows.
> **njparton said:**
> Download memtest86 (google it) and try testing your ram.
Okay.

---

### Post by kuja on 2008-05-06
Wall time so far of 4 and a half hours, no errors. How long do you recommend I let the test run?

---

### Post by kuja on 2008-05-07
In case it would be helpful -- 
[Here are the hardware specs](http://secure.newegg.com/NewVersion/wishlist/PublicWishDetail.asp?WishListNumber=4729729)

Edit: and I've also now attached some other potentially interesting info - dmesg, kern, messages, and syslog info pertinent to bootup (there is nothing logged near the time of any of the reboots that have happened anyhow). Also attached is lscpi -vv output, and lshw output.

---

### Post by njparton on 2008-05-07
Well, my next question was going to be about your PSU.  Seasonic make nice PSUs but I would have gone for something higher than 500W.

I have a 680i/Q6600 setup with 4GB RAM and an 8800GTS 640 graphics card running from a 600W enermax PSU.

I'm thinking of going SLI but I'd also replace the PSU for something in the 800-1000W range at the same time.

It's something to consider but I'm not sure how you'd test it out.

Also check all you connections to the MB and make sure your CPU heatsink is fitted properly so that your CPU isn't overheating.  It may be worth taking it off, cleaning it and the CPU with some 100% alcohol and then using a thin layer of a quality thermal grease to re-seat it (like AS3).

---

### Post by kuja on 2008-05-07
I was actually shooting for relatively low power consumption with this build. According to my kill-o-watt it'd idling at about 120w but that will go up when I put in the second two gig of ram, second hard drive, and second dvd drive tomorrow (spaced out buying the parts over several paychecks) Accoring to [http://extreme.outervision.com/psucalculator.jsp](http://extreme.outervision.com/psucalculator.jsp) I shouldn't need more than about a 350w psu anyhow.

I'll reseat the heatsink tomorrow when I'm upgrading the rest of the stuff and see if it makes a difference. What *really* bugs me is I haven't found any way to monitor the temp from within linux so there's no way for me to see what the CPU is loading at.

On the other hand, the last several times it rebooted I was using the DVD drive, possibly coincidence but possibly not. I've no idea of a good way to check though, especially seeing as these random reboots really aren't all that frequent.

---

### Post by njparton on 2008-05-07
It's a tough one.  The PSU may be a red herring to be honest.

It may be worth you posting a fresh thread specifically on the subject of CPU (& motherboard) temperature monitoring.

---

### Post by kuja on 2008-05-07
> **njparton said:**
> It's a tough one.  The PSU may be a red herring to be honest.

It may be worth you posting a fresh thread specifically on the subject of CPU (& motherboard) temperature monitoring.

hard to say with regards to the PSU, that definitely could do it but finding out won't be easy.

I have posted a thread about the temp monitoring and didn't really get anywhere with it :(

---

### Post by thekat on 2008-05-07
> **kuja said:**
> I was actually shooting for relatively low power consumption with this build. According to my kill-o-watt it'd idling at about 120w but that will go up when I put in the second two gig of ram, second hard drive, and second dvd drive tomorrow (spaced out buying the parts over several paychecks) Accoring to [http://extreme.outervision.com/psucalculator.jsp](http://extreme.outervision.com/psucalculator.jsp) I shouldn't need more than about a 350w psu anyhow.

I'll reseat the heatsink tomorrow when I'm upgrading the rest of the stuff and see if it makes a difference. What *really* bugs me is I haven't found any way to monitor the temp from within linux so there's no way for me to see what the CPU is loading at.

On the other hand, the last several times it rebooted I was using the DVD drive, possibly coincidence but possibly not. I've no idea of a good way to check though, especially seeing as these random reboots really aren't all that frequent.

I have 2 of these PSUs and like you I am only running
- 1 video card
- 1 hard drive
- 3 120 mm fan
- 1 200 mm fan

So an 80%+ efficient SeaSonic 500 Watt should be adequate.. :)

Temps
```

sudo apt-get install lm-sensors

```

from the command line
type
```

sensors

```
tk

---

### Post by kuja on 2008-05-07
> **thekat said:**
> I have 2 of these PSUs and like you I am only running
- 1 video card
- 1 hard drive
- 3 120 mm fan
- 1 200 mm fan

So an 80%+ efficient SeaSonic 500 Watt should be adequate.. :)

Temps
```

sudo apt-get install lm-sensors

```

from the command line
type
```

sensors

```
tk

```

blackwaltz@terra:~$ sudo apt-get install lm-sensors
[sudo] password for blackwaltz:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsqlite0 libsqlite0-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsensors4
Suggested packages:
  i2c read-edid sensord
The following NEW packages will be installed:
  libsensors4 lm-sensors
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 253kB of archives.
After this operation, 942kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libsensors4 lm-sensors
Authentication warning overridden.
Get:1 http://mirror.anl.gov hardy/main libsensors4 1:3.0.0-4ubuntu1 [41.8kB]
Get:2 http://mirror.anl.gov hardy/main lm-sensors 1:3.0.0-4ubuntu1 [212kB]
Fetched 253kB in 6s (40.4kB/s)
Selecting previously deselected package libsensors4.
(Reading database ... 199790 files and directories currently installed.)
Unpacking libsensors4 (from .../libsensors4_1%3a3.0.0-4ubuntu1_amd64.deb) ...
Selecting previously deselected package lm-sensors.
Unpacking lm-sensors (from .../lm-sensors_1%3a3.0.0-4ubuntu1_amd64.deb) ...
Setting up libsensors4 (1:3.0.0-4ubuntu1) ...
udev active, devices will be created in /dev/.static/dev/

Setting up lm-sensors (1:3.0.0-4ubuntu1) ...

Creating config file /etc/sensors3.conf with new version

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
blackwaltz@terra:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
blackwaltz@terra:~$ sudo sensors-detect
# sensors-detect revision 5016 (2007-11-11 22:20:16 +0100)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): yes
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel ICH9

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): yes
Module loaded successfully.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no):
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively):
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively):
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively):

Next adapter: SMBus I801 adapter at 2000 (i2c-3)
Do you want to scan it? (YES/no/selectively):
Client found at address 0x18
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6680/MAX6681'...                      No
Client found at address 0x1a
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6680/MAX6681'...                      No
Client found at address 0x2e
Probing for `Myson MTP008'...                               No
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM78-J'...              No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `National Semiconductor LM85 or LM96000'...     No
Probing for `Analog Devices ADM1027, ADT7460 or ADT7463'... No
Probing for `SMSC EMC6D100, EMC6D101 or EMC6D102'...        No
Probing for `Analog Devices ADT7462'...                     No
Probing for `Analog Devices ADT7467 or ADT7468'...          No
Probing for `Analog Devices ADT7470'...                     No
Probing for `Analog Devices ADT7473'...                     No
Probing for `Analog Devices ADT7475'...                     No
Probing for `Analog Devices ADT7476'...                     No
Probing for `Andigilog aSC7611'...                          No
Probing for `Andigilog aSC7621'...                          No
Probing for `National Semiconductor LM87'...                No
Probing for `National Semiconductor LM93'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83792D'...                            No
Probing for `Winbond W83793R/G'...                          No
Probing for `Winbond W83791SD'...                           No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG'...                          No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Winbond W83L786NR/NG/R/G'...                   No
Probing for `Winbond W83L785TS-S'...                        No
Probing for `Analog Devices ADM9240'...                     No
Probing for `Dallas Semiconductor DS1780'...                No
Probing for `National Semiconductor LM81'...                No
Probing for `Analog Devices ADM1026'...                     No
Probing for `Analog Devices ADM1025'...                     No
Probing for `Analog Devices ADM1029'...                     No
Probing for `Analog Devices ADM1030'...                     No
Probing for `Analog Devices ADM1031'...                     No
Probing for `Analog Devices ADM1022'...                     No
Probing for `Texas Instruments THMC50'...                   No
Probing for `Analog Devices ADM1028'...                     No
Probing for `ITE IT8712F'...                                No
Probing for `SMSC DME1737'...                               No
Probing for `Fintek F75373S/SG'...                          No
Probing for `Fintek F75375S/SP'...                          No
Probing for `Fintek F75387SG/RG'...                         No
Probing for `Analog Devices ADM1024'...                     No
Probing for `Winbond W83791D'...                            No
Client found at address 0x44
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x4c
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Analog Devices ADT7466'...                     No
Probing for `Andigilog aSC7511'...                          No
Probing for `Dallas Semiconductor DS1621'...                No
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `National Semiconductor LM90'...                No
Probing for `National Semiconductor LM89/LM99'...           No
Probing for `National Semiconductor LM86'...                No
Probing for `Analog Devices ADM1032'...                     No
Probing for `Maxim MAX6657/MAX6658/MAX6659'...              No
Probing for `Maxim MAX6648/MAX6692'...                      No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Winbond W83L771W/G'...                         No
Probing for `Texas Instruments TMP401'...                   No
Probing for `National Semiconductor LM63'...                No
Probing for `Fintek F75363SG'...                            No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `Analog Devices ADT7461'...                     No
Probing for `Fintek F75383S/M'...                           No
Client found at address 0x4e
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Dallas Semiconductor DS1621'...                No
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6659'...                              No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `ITE IT8201R/IT8203R/IT8206R/IT8266R'...        No
Probing for `Fintek F75111R/RG/N (GPIO)'...                 No
Probing for `Fintek F75121R/F75122R/RG (VID+GPIO)'...       No
Client found at address 0x4f
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Dallas Semiconductor DS1621'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no):
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no):
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   Yes
Found `Nat. Semi. PC8374L Super IO Sensors'
    (but not activated)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no):
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See doc/FAQ,
doc/lm_sensors-FAQ.html or http://www.lm-sensors.org/wiki/FAQ
(FAQ #4.24.3) for further information.
If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.
blackwaltz@terra:~$                                         
```

I know they're there because I see them in BIOS ... I just can't access them, modprobing coretemp fails also.

---

### Post by kuja on 2008-05-10
Well, the HSF is mounted securely, I've remounted it just to be sure, I even took the motherboard off the tray to make sure the POS pushpins went and stayed all the way through. I'm still not happy with the temps, but they're not high enough that they would do any damage. (around 55C ... I'll definitely have to get a different HSF and see if that makes a difference)

I also put in my 2GiB of RAM, second optical drive, and second hard drive. The system is now *severely* unstable. I'm also *quite* sure now that there is a hardware problem somewhere in there, but I don't know what :( I've already decided that it isn't the memory, and seeing as it can still sit in memtest for hours, that it isn't the case fans either (I actually had trouble with one of them a while back). This narrows it down to being the optical drives ... which I think somewhat unlikely, the power supply, which I also think somewhat unlikely ... or the motherboard, which will be painful and expensive to admit?

Does anybody know where I can get some sort of adapter for the 8pin extra power supply cable for the motherboard? My old power supply is also a 500w (but its is only a 4-pin), and I'd be more likely to believe that it was the power supply than the motherboard because that would be cheaper in the event that anything came out of my pocket over this :P I'm sure that in a week or so when all is said and done the moral of the story will be not to buy OpenBox Motherboards.

---

### Post by uado on 2008-05-31
I'm afraid I'm not going to be of much help as I know very little about Linux, except to say that I've been using Ubuntu for the past 4 months now, and it has only been in the past week or two that my system has decided to start performing random reboots.
I've got a Dell XPS M1330, and has been rebooting pretty much once a day or every other day. No error message; screen just goes black and returns to the prompt loading screen, as though it's just been switched on.
Nothing's changed these past weeks except downloading some files and installing updates.
I have it set up to dual boot with XP, but what little time I've spent in it, not once has it randomly rebooted. Everything points to a recent update, maybe not happy with hardware? I did notice in amongst those updates that there was one for the Nvidia driver?
Hope this helps in some small way.

---


---
title: "LM-Sensors not working correctly"
date: 2009-11-08
forum: x86 64-bit Users
---

### Post by Maintech on 2009-11-08
I installed LM-Sensors and all the appropriate extra software. I ran "sensors-detect" and had it to 'auto-write' the extra modules to the kernel. I rebooted (just to be absolutely certain all modules were inserted). When I run 'sensors' I only show 1 temp. I have 4 cores and none are shown and none of the voltages or fan speeds. I ran the exact same program in 9.04 and had all listed. Here is my output from 'sensors-detect':
Driver `to-be-written' (should be inserted):
  Detects correctly:
  * Bus `NVIDIA i2c adapter '
    Busdriver `UNKNOWN', I2C address 0x2e
    Chip `Analog Devices ADT7473' (confidence: 5)

Driver `w83627ehf' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `Winbond W83627DHG Super IO Sensors' (confidence: 9)

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)



#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# Chip drivers
# no driver for Analog Devices ADT7473 yet
w83627ehf
coretemp
#----cut here----

Here is my output from 'sensors': acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +120.0°C) 

What have they changed and what do I have to do to fix it???
I have been on google for hours trying to find something. Thanks in advance to anyone who can help.

---

### Post by Maintech on 2009-11-08
UPDATE:
After a 2nd reboot, my CPU temps now show. All I need now is fan speeds and voltages. I have everything in my Conky working now but that.

---

### Post by raygj on 2009-11-09
this works with grub2 for my motherboard.

sudo gedit /etc/default/grub
add
 GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax"
save
run 'update-grub'  to update grub2.
reboot.

---

### Post by Maintech on 2009-11-09
> this works with grub2 for my motherboard.

sudo gedit /etc/default/grub
add
GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax"
save
run 'update-grub' to update grub2.
reboot.

That worked! Where in the world did you find that info?? I looked everywhere but apparently not in the right place.

Thanks!!    :D

---

### Post by imjafo on 2009-11-10
Raygj: I just found your tip. Thanks I have been looking fr this for about a week now. It works perfect on my 9.10 64 bit install.

---

### Post by philinux on 2009-11-10
[http://www.webupd8.org/2009/10/make-lm-sensors-work-in-ubuntu-karmic.html](http://www.webupd8.org/2009/10/make-lm-sensors-work-in-ubuntu-karmic.html)

---

### Post by doas777 on 2009-11-10
gonna have to try that when i get home

---

### Post by liorwohl on 2009-11-10
i have asus p5kpl-cm and ubuntu 9.10, and i also have this problem: fan speeds are not detected.

i have just checked your groub solution and it is not working here.

```
liorwohl@liorwohl-desktop:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +38.0°C  (high = +76.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +34.0°C  (high = +76.0°C, crit = +100.0°C)  

```

```
liorwohl@liorwohl-desktop:~$ sudo sensors-detect
[sudo] password for liorwohl: 
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): 
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801G ICH7

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): 
Module loaded successfully.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

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

Next adapter: NVIDIA i2c adapter  (i2c-3)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-4)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-5)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No

Next adapter: SMBus I801 adapter at 0400 (i2c-6)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
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
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found `Winbond W83627DHG Super IO Sensors'                  Success!
    (address 0x290, driver `w83627ehf')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): 
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `w83627ehf' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `Winbond W83627DHG Super IO Sensors' (confidence: 9)

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
w83627ehf
coretemp
#----cut here----

Do you want to add these lines automatically? (yes/NO)yes
```

---

### Post by Arup on 2009-11-10
Ironically with both my Intel and AMD PCs, installing fresh Karmic and lm-sensors and doing sudo sensors-detect made it work fine with Gkrellm, its showing core temps, system temp, CPU temp and all the related voltages. and fan speeds as well including my Antec PSU fan speed.

---

### Post by raygj on 2009-11-10
> **liorwohl said:**
> i have asus p5kpl-cm and ubuntu 9.10, and i also have this problem: fan speeds are not detected.

i have just checked your groub solution and it is not working here.

```
liorwohl@liorwohl-desktop:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +38.0°C  (high = +76.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +34.0°C  (high = +76.0°C, crit = +100.0°C)  

```

```
liorwohl@liorwohl-desktop:~$ sudo sensors-detect
[sudo] password for liorwohl: 
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): 
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801G ICH7

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): 
Module loaded successfully.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

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

Next adapter: NVIDIA i2c adapter  (i2c-3)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-4)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-5)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No

Next adapter: SMBus I801 adapter at 0400 (i2c-6)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
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
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found `Winbond W83627DHG Super IO Sensors'                  Success!
    (address 0x290, driver `w83627ehf')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): 
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `w83627ehf' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `Winbond W83627DHG Super IO Sensors' (confidence: 9)

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
w83627ehf
coretemp
#----cut here----

Do you want to add these lines automatically? (yes/NO)yes
```

sorry you need to 
> sudo gedit  /etc/modules
and add the following lines to it.
> # Generated by ray to enable p6q sensor 
# Chip driver
w83627ehf force_id=0x8860
save & close gedit
when you reboot all sensors should work.

---

### Post by liorwohl on 2009-11-11
thanks for your help, but it still wont show my fan speeds :-(

i added the line, rebooted my computer, run sensors-detect and restarted again... and it's not working

---

### Post by raygj on 2009-11-11
> **liorwohl said:**
> thanks for your help, but it still wont show my fan speeds :-(

i added the line, rebooted my computer, run sensors-detect and restarted again... and it's not working

in /etc/default/grub  try deleting the line
GRUB_CMDLINE_LINUX="" 
and moving 
GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax"
up to the deleted line position in the /etc/default/grub file.
run 'sudo update-grub' to update grub2.

try rebooting into bios setup utility
right-arrow across to 'Advanced' tab
down-arrow to ADVANCED PCI/PNP SETTINGS
and set to
> Plug and Play O/S   [No] 

then go back [esc] and across to Power tab
and set to
> Suspend Mode                [Auto]
Repost Video on S3 resume   [No]
ACPI 2.0 Support            [Enabled]
ACPI APIC Support           [Enabled]

press <F10> key to save bios settings & reboot

---

### Post by liorwohl on 2009-11-13
funny thing, i haven't had the time to test your last answer yet, but today when i started up my computer, all the sensors was just working :p this is probably because of the last updates  :D

thanks for the help anyway :)

---


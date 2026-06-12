---
title: "Ubuntu x86_64 the fan won't stop running."
date: 2008-10-10
forum: x86 64-bit Users
---

### Post by oceallaighm on 2008-10-10
Hi,

Toshiba, Satellite, L300D-10Q, AMD 64 Turion x 2 Tk57, 4GB ram, 500GB HDD. I have installed Ubuntu x86_68 8.04.1 and installed all of the updates.

The problem is that my fan keeps running, which kind of means that the installation is unusable.

I have been using the 32 bit version on an older Toshiba Satellite Pro 4280, PIII 500Mhz, with 256 MB ram and I have had no issues with the fan running all the time.

Is this issue a 64 bit only problem? Yes, I have Googled and seen some similar posts but not a clear resolution.

Anyone any ideas?

Many thanks.

---

### Post by oceallaighm on 2008-10-11
Hi,

Please find below some additional information, and yes the fan is still
running. I really want to use Ubuntu 8.04.1 x86_64 as my main OS.

xxxx@hardyheron-laptop:/proc/acpi/fan/FAN1# more state
status:                  off

xxxx@hardyheron-laptop:/proc/acpi/thermal_zone/THZN# more cooling_mode
0 - Active; 1 - Passive

xxxx@hardyheron-laptop:/proc/acpi/thermal_zone/THZN# more temperature
temperature:             38 C

xxxx@hardyheron-laptop:/proc/acpi/thermal_zone/THZN# more trip_points
critical (S5):           105 C

xxxx@hardyheron-laptop:/proc/acpi/processor/CPU0# more info
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        no
throttling control:      yes
limit interface:         yes

xxxx@hardyheron-laptop:/proc/acpi/processor/CPU1# more info
processor id:            1
acpi id:                 1
bus mastering control:   yes
power management:        no
throttling control:      no
limit interface:         no

Kernel 2.6.24-19 generic

What further information can I gather and from where? Note in Windows Vista the fan works as it should, it kicks in when necessary, so I don't believe that this is a hardware issue.

Many thanks

---

### Post by oceallaighm on 2008-10-11
Additional observations:-

The air coming out of the air vent is cold, normally this is warm.

In various forums I have seen, that the processor temperature for this model AMD can be up around 60 C / 65 C.

---

### Post by oceallaighm on 2008-10-13
Hi,

I have just installed Ubuntu 8.04.1 i386 on the same laptop and yes the fan is still running thought not as loud as in the x86_64 installation.

xxxx@hardy-laptop:/proc/acpi/fan/FAN1# more state
status:                  off

xxxx@hardy-laptop:/proc/acpi/thermal_zone/THZN# more cooling_mode
0 - Active; 1 - Passive

xxxx@hardy-laptop:/proc/acpi/thermal_zone/THZN# more temperature
temperature:             39 C

xxxx@hardy-laptop:/proc/acpi/thermal_zone/THZN# more trip_points
critical (S5):           105 C

xxxx@hardy-laptop:/proc/acpi/processor/CPU0# more info
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        no
throttling control:      yes
limit interface:         yes

xxxx@hardy-laptop:/proc/acpi/processor/CPU1# more info
processor id:            1
acpi id:                 1
bus mastering control:   yes
power management:        no
throttling control:      no
limit interface:         no

Kernel 2.6.24-19 generic

Apart from the 1 C difference in temperature on the i386 installation and the fact that the fan appears to be labouring somewhat less, I can see little difference, between the issue that I am encountering in both the x86_64 and i386 installations.

Although I have dabbled in Linux for over 10 years, I am neither an expert nor a techie, just a mere end user, who would like to be able to install a 64 bit version of Linux that is useable. 

I have been using Ubuntu 8.04 i386 installed on a Toshiba Satellite 4280, PIII 500MhZ, 256MB RAM, on a 20GB partition, with large swap partition 1GB since May.
Since June in a VM in VirtualBox on a Vista Home Premium host on the Satellite L300D-10Q, over all I have been happy with it. I had hoped that this would be the big move to 64 bit Linux alas that is not to be.

---


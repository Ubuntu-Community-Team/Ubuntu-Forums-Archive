---
title: "CPU temp"
date: 2007-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by ProbablyX on 2007-06-01
Hello!

I just got new PC parts (AMD64 6000+) and I decided on switching from Debian to Kububtu Fiesty.

One thing I'd love to see is my CPU's (or CPUs, I understand a dual core cpu is detected as two regular ones) temp.

Ive installed some theme on superkaramba but my temps just show up as "*" or "X", do I need some special program to make cpu temp reading work?

Thanks!

---

### Post by jamesford on 2007-06-01
probably lm-sensors

---

### Post by ProbablyX on 2007-06-01
> **jamesford said:**
> probably lm-sensors

I tried that but still the same... thanks anyway

---

### Post by jamesford on 2007-06-01
its not enough just to install lm-sensors, theres a whole little procedure that goes something like:
Howto Install and Configure lm-sensors
========================

1. Install lm-sensors using apt-get or the Synaptic GUI.

sudo apt-get install lm-sensors


2. Run the mkdev.sh script in the lm-sensors source. It is extacted below:

a. Copy the script file below to a text editor and save it to a file named mkdev.sh.


```
#!/bin/bash

# Here you can set several defaults.

# The number of devices to create (max: 256)
NUMBER=32

# The owner and group of the devices
OUSER=root
OGROUP=root
# The mode of the devices
MODE=600

# This script doesn't need to be run if devfs is used
if [ -r /proc/mounts ] ; then
if grep -q "/dev devfs" /proc/mounts ; then
echo "You do not need to run this script as your system uses devfs."
exit;
fi
fi

i=0;

while [ $i -lt $NUMBER ] ; do
echo /dev/i2c-$i
mknod -m $MODE /dev/i2c-$i c 89 $i || exit
chown "$OUSER:$OGROUP" /dev/i2c-$i || exit
i=$[$i + 1]
done
#end of file
```


##
b. Make the file executable:

chmod 755 mkdev.sh

c. Run mkdev.sh from the current directory

sudo ./mkdev.sh


3. Now run sensors-detect and answer YES to all YES/no questions.
sudo sensors-detect

i think a reboot is required

EDIT: [B]NB: on some systems installing lm-sensors and configuring it as above leaves u with broken system. i dont recall if the system is totally unbootable, or if ur able to get into text mode, in either case, in text mode or by booting live cd u gotta
sudo nano /etc/modules
find the eeprom entry and comment it out (i think its called eeprom, something similar at least
#eeprom

write this down before trying maybe[/B]

---

### Post by Mr_bleu on 2007-06-01
Thanks!!! I never could figure out why lm sensors would only show my cpu temp.  No other sensors were listed.  I have a core 2 t7200 processor.  I'm gonna try your instructions after I boot back into linux.  :popcorn::KS

---

### Post by ©TriMoon® on 2007-06-06
Which packages are needed to actualy see the temperature graphs on the task bar?

---

### Post by ukripper on 2007-06-06
> **ProbablyX said:**
> Hello!

I just got new PC parts (AMD64 6000+) and I decided on switching from Debian to Kububtu Fiesty.

One thing I'd love to see is my CPU's (or CPUs, I understand a dual core cpu is detected as two regular ones) temp.

Ive installed some theme on superkaramba but my temps just show up as "*" or "X", do I need some special program to make cpu temp reading work?

Thanks!

Use Conky which gives you detailed system activities how you want them and can be forked to desktop with transperency

---


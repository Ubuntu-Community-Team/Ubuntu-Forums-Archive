---
title: "virtualbox usb headset problem ubuntu 64 hardy host    xp guest"
date: 2008-05-26
forum: x86 64-bit Users
---

### Post by Mgiacchetti on 2008-05-26
well i wanted to use a voice chat program so i ended up finding virtualbox and installing windows on it, the only problem was that i could not use my usb headset.
 
found a tutorial, posting my workaround for the fix
 
in terminal...
```
 
sudo gedit /etc/init.d/mountdevusbfs.sh

```
uncomment the four last lines of
```

# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

```
to make it read like this:
```

# Magic to make /proc/bus/usb work
#
 mkdir -p /dev/bus/usb/.usbfs
 domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
 ln -s .usbfs/devices /dev/bus/usb/devices
 mount --rbind /dev/bus/usb /proc/bus/usb

```
save
exit gedit
 
go to system > administration > users and groups
click unlock
type your password and select manage groups
add group
 
```

group name: usbusers
group ID: 1001

```
 
add yourself to this group
 
back to terminal...
```

sudo gedit /etc/udev/rules.d/40-permissions.rules

```
 
now the tut told me to edit "usb devices" but it wasnt in there so i added it..
 
ctrl+f to find the following string
```

LABEL="usb_serial_end"

```
 
after that line insert this:
```

#USB devices (usbfs replacement)
SUBSUSTEM=="usb_device", GROUP="usbusers", MODE="0664"

```
 
save 
exit gedit
 
back in terminal
 
```

sudo gedit /etc/fstab

```
 
at the bottom add the following lines
```

# 1001 is the USB group ID
none /proc/bus/usb usbusers devgid=1001,devmode660 0 0

```
save exit
 
restart ubuntu and plug your usb headset in
 
start virtualbox
 
create the usb filter for the current headset
 
unplug usb
plug in usb
 
start your virtual machine
 
your usb headset should now be working in your machine's xp install
 
 
----note----
I still experience problems with this 
if anyone can advise me it would be great
 
the problem is my sound from usb is choppy.
the sound without usb is great...

---

### Post by Mgiacchetti on 2008-05-27
im now wondering if the following is my choppy sound problem..
 
```

devmode=0600,listmode=0644

```
 
```

MODE="0664"

```
 
```

devgid=1001,devmode660 0 0

```

---

### Post by wenuswilson on 2008-06-02
> **Mgiacchetti said:**
> well i wanted to use a voice chat program so i ended up finding virtualbox and installing windows on it, the only problem was that i could not use my usb headset.
 
found a tutorial, posting my workaround for the fix
 
in terminal...
```
 
sudo gedit /etc/init.d/mountdevusbfs.sh

```
uncomment the four last lines of
```

# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

```
to make it read like this:
```

# Magic to make /proc/bus/usb work
#
 mkdir -p /dev/bus/usb/.usbfs
 domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
 ln -s .usbfs/devices /dev/bus/usb/devices
 mount --rbind /dev/bus/usb /proc/bus/usb

```
save
exit gedit

In my computer the file isn't mountdevusbfs but mountdevsubfs
Not sure if that's universal just thought I'd let everyone know.

---

### Post by fjgaude on 2008-06-03
> In my computer the file isn't mountdevusbfs but mountdevsubfs
Not sure if that's universal just thought I'd let everyone know.

Yep, likely a typo.

---


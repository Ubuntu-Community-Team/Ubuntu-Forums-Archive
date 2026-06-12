---
title: "SCR331 CAC Reader not working...?"
date: 2008-09-29
forum: x86 64-bit Users
---

### Post by torstenaf on 2008-09-29
All,

I'm trying to get my CAC reader working for military login.

**Ubuntu**
Ubuntu 8.04 Hardy Heron x86_64
Kernel 2.6.24-19-generic

**CAC Reader**
[http://www.scmmicro.com/security/view_product_en.php?PID=4](http://www.scmmicro.com/security/view_product_en.php?PID=4)
SCM Microsystems, Inc.
SCR3310 v2.0 SmartOS Powered
P/N: 905032
```
 lsusb
Bus 001 Device 005: ID 04e6:5116 SCM Microsystems, Inc. SCR331-LC1 SmartCard Reader

```

```
dmesg
[  436.840585] usb 1-1: new full speed USB device using uhci_hcd and address 5
[  437.013308] usb 1-1: configuration #1 chosen from 1 choice

```

**Resources**
_Thread - Feb 2007_ [http://symbolik.wordpress.com/2007/02/25/using-dod-cac-and-smartcard-readers-on-linux/](http://symbolik.wordpress.com/2007/02/25/using-dod-cac-and-smartcard-readers-on-linux/)
_Thread - May 2007_ [http://ubuntuforums.org/showthread.php?t=457084&highlight=scr331](http://ubuntuforums.org/showthread.php?t=457084&highlight=scr331)
_Thread - Oct 2007_ [http://ubuntuforums.org/showthread.php?t=564763&highlight=scr331](http://ubuntuforums.org/showthread.php?t=564763&highlight=scr331)
_Ubuntu Install Guide_ [https://help.ubuntu.com/community/CommonAccessCard](https://help.ubuntu.com/community/CommonAccessCard)
_Gentoo Install Guide_ [http://gentoo-wiki.com/HOWTO_DoD_CAC](http://gentoo-wiki.com/HOWTO_DoD_CAC)

**Process**
_1. Installed programs._
```
sudo apt-get install libusb-0.1-4 libpcsclite1 libpcsclite-dev pcscd pcsc-tools build-essential autoconf  libccid
```
*Note, I removed xlibs-dev from the list because it doesn't exist, this is a modification from the original instructions.*

_2. Started the PCSC Daemon_
```
sudo /etc/init.d/pcscd start
```

/var/log/messages:
```
Sep 29 10:52:53 ubuntu-desktop-1 pcscd: configfile.l:129:evaluatetoken() Error with library /usr/lib/pcsc/drivers/serial/libGemPC410.so.1.0.1: No such file or directory
Sep 29 10:52:53 ubuntu-desktop-1 pcscd: configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
Sep 29 10:52:53 ubuntu-desktop-1 last message repeated 22 times
Sep 29 10:52:53 ubuntu-desktop-1 pcscd: pcscdaemon.c:538:at_exit() cleaning /var/run/pcscd
Sep 29 10:52:53 ubuntu-desktop-1 pcscd: pcscdaemon.c:557:clean_temp_files() Cannot unlink /var/run/pcscd/pcscd.comm: No such file or directory

```

_3. See if the daemon is running?_
```
ps aux | grep pcsc
```

Not there. 

_4. Try running pcscd in the foreground with hotplug:_

```
sudo /usr/sbin/pcscd -fH
00000000 pcscdaemon.c:295:main() pcscd set to foreground with debug send to stderr
00000036 pcscdaemon.c:399:main() Hotplug failed: pcscd is not running
```

_5. Try running without the hotplug stuff._

```
 sudo /usr/sbin/pcscd -f
00000000 pcscdaemon.c:295:main() pcscd set to foreground with debug send to stderr
00000296 configfile.l:129:evaluatetoken() Error with library /usr/lib/pcsc/drivers/serial/libGemPC410.so.1.0.1: No such file or directory
00000015 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000005 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000004 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000005 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000014 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000005 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000004 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000013 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000004 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000005 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000013 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000004 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000004 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000005 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000003 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000005 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000008 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000004 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000004 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000004 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000004 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000003 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000007 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000018 pcscdaemon.c:538:at_exit() cleaning /var/run/pcscd
00000015 pcscdaemon.c:557:clean_temp_files() Cannot unlink /var/run/pcscd/pcscd.comm: No such file or directory

```

No joy. Try symlinking the libGemPC401.so.1.0.1 file...

```
sudo ln -s /usr/lib/pcsc/drivers/serial/libGemPC410.so.1.0.3 /usr/lib/pcsc/drivers/serial/libGemPC410.so.1.0.1

```

_5. Try running pcscd again..._

```
 sudo /usr/sbin/pcscd -f
00000000 pcscdaemon.c:295:main() pcscd set to foreground with debug send to stderr
00000341 configfile.l:108:evaluatetoken() Error with device ttyS0: No such file or directory
00000009 configfile.l:109:evaluatetoken() You should use 'DEVICENAME /dev/null' if your driver does not use this field
00000012 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000005 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000004 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000014 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000005 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000006 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000011 configfile.l:203:tok_error() tok_error: invalid value in reader.conf: FRIENDLYNAME
00000033 readerfactory.c:1116:RFInitializeReader() Attempting startup of GemPC410 00 00 using /usr/lib/pcsc/drivers/serial/libGemPC410.so.1.0.1
00000075 readerfactory.c:983:RFBindFunctions() Loading IFD Handler 3.0
00000031 ifdhandler.c:51:IFDHCreateChannelByName() lun: 0, device: /dev/ttyS0
00000104 gbpserial.c:540:OpenGBP() Serial port baudrate already set to 38400 (3)
00000009 GCCmds.c:407:GCCmdSetMode() 

```

It's having trouble with the readers.conf file format for some reason. Also, the Gem driver is not loading? I don't think I need it.

Every now and then, this line gets added to the pcscd output:

```
59998304 GCCmds.c:356:GCCmdConfigureSIOLine() 

```

And then this....

```
59999957 gbpserial.c:556:OpenGBP() Flush serial buffers (3)
00000024 GCCmds.c:407:GCCmdSetMode() 
59999977 gbpserial.c:565:OpenGBP() GCCmdSetMode failed (3.a)
00000031 gbpserial.c:568:OpenGBP() Set serial port baudrate to 9600 (3.a)
00000032 gbpserial.c:568:OpenGBP() Flush serial buffers (3.a)

```

_6. Check if pscsd is running._

```
 ps aux | grep pcsc
root      6866  0.0  0.0  12936   916 pts/1    S+   10:58   0:00 /usr/sbin/pcscd -f
thoward   6893  0.0  0.0   5164   840 pts/2    S+   11:03   0:00 grep pcsc

```

_7. Try running pcsc_scan_
```
 sudo pcsc_scan
PC/SC device scanner
V 1.4.11 (c) 2001-2007, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.4
winscard_msg.c:98:SHMClientSetupSession() Error: connect to client socket: No such file or directory
SCardEstablishContext: Cannot Connect to Resource Manager: Service not available. (0x8010001D)

```

_8. Tried unplugging, replugging the CAC Reader._

```
dmesg
[ 3246.713858] usb 1-1: USB disconnect, address 5
[ 3249.556107] usb 1-1: new full speed USB device using uhci_hcd and address 6
[ 3249.728393] usb 1-1: configuration #1 chosen from 1 choice

```

```
 lsusb
Bus 001 Device 006: ID 04e6:5116 SCM Microsystems, Inc. SCR331-LC1 SmartCard Reader




```

```
/var/log/messages
Sep 29 11:05:16 ubuntu-desktop-1 kernel: [ 3246.713858] usb 1-1: USB disconnect, address 5
Sep 29 11:05:19 ubuntu-desktop-1 kernel: [ 3249.556107] usb 1-1: new full speed USB device using uhci_hcd and address 6
Sep 29 11:05:19 ubuntu-desktop-1 kernel: [ 3249.728393] usb 1-1: configuration #1 chosen from 1 choice

```

*The green light on the reader does not come on.*

Multiple searches on google for the error messages do not yield any significant results. I cannot make sense of the errors.

Does anyone know what I'm doing wrong?

---

### Post by contemno on 2008-11-30
I actually have the SCR-331,
Bus 002 Device 005: ID 04e6:e001 SCM Microsystems, Inc. SCR331 SmartCard Reader

But it appears to be the same issue, and here is how I resolved it:

1. Make sure pcscd is started.

2. Modify /etc/udev/rules.d/50-libccid.rules and add:
    
   ```
# SCR331-LC1.txt
SUBSYSTEMS=="usb", ATTRS{idVendor}=="04e6", ATTRS{idProduct}=="5116", RUN+="/usr/sbin/pcscd --hotplug"
```

   Right after:

   ```
# SCR331-DI.txt
SUBSYSTEMS=="usb", ATTRS{idVendor}=="04e6", ATTRS{idProduct}=="5111", RUN+="/usr/sbin/pcscd --hotplug"
```

3. Unplug and replug the reader.

  I dont know why our readers are listed in /usr/lib/pcsc/drivers/ifd-ccid.bundle/Contents/Info.plist and no udev rule is added to handle it.

And for anyone else with usb readers, just make sure that the vendor and product IDs match the output of lsusb.

Josh

---


---
title: "silverlink problems"
date: 2005-05-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by nrayever on 2005-05-08
hi everyone:

i'm having some problems with my silverlink and tilp (a program to manage ti calculators). the silverlink is a usb cable to connect a calculator to pc. and when i try to setup the comunications options in tilp i got an error

```
tilp    : Configuration file not found, use default values. You can create one by the 'File|Save config' command menu.
tilp    : err: msg_box: Information, Configuration file not found, use default values. You can create one by the 'File|Save config' command menu.

tilp    : setlocale: <es_MX>
tilp    : bindtextdomain: </usr/share/locale/>
tilp    : textdomain: <tilp>
ticables: ticables library version 3.8.7
ticables: setlocale: <es_MX>
ticables: bindtextdomain: </usr/share/locale>
ticables: textdomain: <libticables>
ticables: built for __LINUX__ target.
ticables: checking resources:
ticables:   IO_API: found at compile time (HAVE_TERMIOS_H)
ticables:   IO_ASM: not found at compile time (HAVE_ASM_IO_H).
ticables:   IO_TIPAR: found at compile time (HAVE_LINUX_TICABLE_H)
ticables:   IO_TISER: found at compile time (HAVE_LINUX_TICABLE_H)
ticables:   IO_TIUSB: found at compile time (HAVE_LINUX_TICABLE_H)
ticables:   IO_LIBUSB: found at compile time (HAVE_LIBUSB)
ticables: quick search for parallel/serial ports:
ticables:   serial port found at 0x2f8
ticables:   parallel port found at 0x378
ticables:   serial port found at 0x3f8
ticables:   parallel port found at 0x778
ticables: search for all ports:
ticables:   /dev/parport0 at 0x378
ticables:   /dev/ttyS0 at 0x3f8
ticables:   /dev/ttyS1 at 0x2f8
ticables:   /dev/ttyS2 at 0x3e8
ticables:   /dev/ttyS3 at 0x2e8
ticables: getting method from resources (automatic):
ticables:   check for tty usability:
ticables:     node /dev/ttyS0: exists
ticables:     permissions/user/group: -rw-rw---- root dialout
ticables:     is user can r/w on device: yes
ticables: mapping I/O...
ticables: registering cable...
ticables: list of settings:
ticables:   cable: GrayLink
ticables:   port: serial port #2
ticables:   method: direct access (api)
ticables:   device name: /dev/ttyS1
ticables:   delay value: 10
tifiles : tifiles library version 0.6.1
tifiles : setlocale: <es_MX>
tifiles : bindtextdomain: </usr/share/locale>
tifiles : textdomain: <libtifiles>
tifiles : settings:
tifiles :   calc type: TI92
ticalcs : ticalcs library version 4.5.5
ticalcs : setlocale: <es_MX>
ticalcs : bindtextdomain: </usr/share/locale>
ticalcs : textdomain: <libticalcs>
tifiles : settings:
tifiles :   calc type: TI92
ticalcs : settings:
ticalcs :   calc type: TI92
tilp    : initialized in GTK+ mode.
tilp    : scanning plug-ins... Done !
tilp    : scanning registry... Done !
ticables: getting method from resources (automatic):
ticables:   check for tiusb usability:
ticables:     using devfs: no
ticables:     node /dev/tiusb0: does not exists
ticables:     => you will have to create the node.
ticables:   warning: can't use IO_TIUSB
ticables:   check for lib-usb usability:
ticables:     usb filesystem (/proc/bus/usb): mounted
ticables:     node /proc/bus/usb/devices: exists
ticables:     permissions/user/group: -rw-rw-r-- root root
ticables:     is user can r/w on device: yes
ticables: mapping I/O...
ticables: registering cable...
ticables: list of settings:
ticables:   cable: SilverLink
ticables:   port: USB port #1
ticables:   method: user mode (ioctl)
ticables:   device name: /dev/tiusb0
ticables:   delay value: 10
tifiles : settings:
tifiles :   calc type: V200
ticalcs : settings:
ticalcs :   calc type: V200
ticables: Found <SilverLink>.
ticables: err: usb_claim_interface (could not claim interface 0: Dispositivo o recurso ocupado)
```

need some help, please!! i don't get how to fix it. i have tried what says on tiusbdriver page but not working.

i hoep some one could help me.

thanks

---

### Post by JonahRowley on 2005-05-08
Odd timing, I was about to post about problems with BlackLink on tilp...

Have you loaded tiglusb?  Or is that only for GrayLink?

As for tilp, I've had zero luck with it on my 83+.  Keep replying to this thread (or in PM) if you have an succeses.

---

### Post by nrayever on 2005-05-08
may i ask u JonahRowley, how do i load tiglusb module?? i'm not really an expert with kernel stuff. some help may be useful.

---

### Post by nrayever on 2005-05-21
i found the answer in the same ubuntu forum. the problem was that tiusb device not exists and it must be created

but if you are to lazy to read the solution is this two command lines:

> Creating the device node by hand was the only way I could get it to work:

sudo mknod /dev/tiusb0 c 115 16 
sudo chmod 666 /dev/tiusb0 

here you can find the post in the ubuntu forum:

[http://ubuntuforums.org/showthread.php?p=181320#post181320](http://ubuntuforums.org/showthread.php?p=181320#post181320)

the answer to this problem was found on this page

[http://evan.mcnabbs.org/linux-oss/ticalc/](http://evan.mcnabbs.org/linux-oss/ticalc/)

that's all

---


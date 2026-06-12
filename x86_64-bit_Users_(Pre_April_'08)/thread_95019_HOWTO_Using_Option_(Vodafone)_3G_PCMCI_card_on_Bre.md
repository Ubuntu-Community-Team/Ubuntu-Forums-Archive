---
title: "HOWTO: Using Option (Vodafone) 3G PCMCI card on Breezy"
date: 2005-11-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by eduardgrebe on 2005-11-25
Some time ago I posted a HOWTO for this card on Hoary. It can be viewed here:

[http://ubuntuforums.org/showthread.php?t=49056](http://ubuntuforums.org/showthread.php?t=49056)

Things have become a lot simpler, thanks to Breezy's improved support for the card. I thought I'd post an updated comprehensive HOWTO. Note that I use Breezy PPC on an Apple Powerbook G4. However, I think things will be similar on other platforms. Also note that all network-specific info refer to the Vodacom network in South Africa, but these are easy to adapt.

First, ensure that your PCMCIA services are running and that the OS is detecting the card when it's inserted. This should work automatically. In breezy the card should be set up as a generic serial modem automatically without the need to load modules as in Hoary. To monitor whether things are ok, type the following:
```
sudo tail -f /var/log/syslog
```
When you insert the card, you should see something like the following:
```
Nov 25 19:53:28 localhost kernel: [  399.896613] PCI: Enabling device 0001:11:00.0 (0000 -> 0002)
Nov 25 19:53:28 localhost kernel: [  399.896667] ohci_hcd 0001:11:00.0: OPTi Inc. 82C861
Nov 25 19:53:28 localhost kernel: [  399.899744] ohci_hcd 0001:11:00.0: new USB bus registered, assigned bus number 5
Nov 25 19:53:28 localhost kernel: [  399.899774] ohci_hcd 0001:11:00.0: irq 53, io mem 0xf3000000
Nov 25 19:53:28 localhost kernel: [  399.979238] hub 5-0:1.0: USB hub found
Nov 25 19:53:28 localhost kernel: [  399.979290] hub 5-0:1.0: 2 ports detected
Nov 25 19:53:28 localhost pci.agent[5212]:      ohci-hcd: already loaded
Nov 25 19:53:29 localhost usb.agent[5255]:      usbcore: already loaded
Nov 25 19:53:36 localhost kernel: [  407.409427] usb 5-1: new full speed USB device using ohci_hcd and address 2
Nov 25 19:53:37 localhost modprobe: FATAL: Error inserting option (/lib/modules/2.6.12-10-powerpc/kernel/drivers/usb/serial/option.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Nov 25 19:53:37 localhost usb.agent[5330]:      option: can't be loaded
Nov 25 19:53:37 localhost usb.agent[5330]: missing kernel or user mode driver option
Nov 25 19:53:37 localhost kernel: [  408.615568] option: Unknown symbol usb_serial_disconnect
Nov 25 19:53:37 localhost kernel: [  408.616146] option: Unknown symbol usb_serial_probe
Nov 25 19:53:37 localhost kernel: [  408.616217] option: Unknown symbol usb_serial_register
Nov 25 19:53:37 localhost kernel: [  408.616287] option: Unknown symbol usb_serial_deregister
Nov 25 19:53:37 localhost kernel: [  408.691165] usbcore: registered new driver usbserial
Nov 25 19:53:37 localhost kernel: [  408.710589] drivers/usb/serial/usb-serial.c: USB Serial support registered for Generic
Nov 25 19:53:37 localhost kernel: [  408.722087] usbcore: registered new driver usbserial_generic
Nov 25 19:53:37 localhost kernel: [  408.722103] drivers/usb/serial/usb-serial.c: USB Serial Driver core v2.0
Nov 25 19:53:37 localhost kernel: [  408.740132] drivers/usb/serial/usb-serial.c: USB Serial support registered for Option 3-port card
Nov 25 19:53:37 localhost kernel: [  408.748098] option 5-1:1.0: Option 3-port card converter detected
Nov 25 19:53:37 localhost kernel: [  408.752407] usb 5-1: Option 3-port card converter now attached to ttyUSB0
Nov 25 19:53:37 localhost kernel: [  408.752439] option 5-1:1.1: Option 3-port card converter detected
Nov 25 19:53:37 localhost kernel: [  408.763817] usb 5-1: Option 3-port card converter now attached to ttyUSB1
Nov 25 19:53:37 localhost kernel: [  408.763849] option 5-1:1.2: Option 3-port card converter detected
Nov 25 19:53:37 localhost kernel: [  408.768309] usb 5-1: Option 3-port card converter now attached to ttyUSB2
Nov 25 19:53:37 localhost kernel: [  408.768341] usbcore: registered new driver option
Nov 25 19:53:37 localhost kernel: [  408.768346] drivers/usb/serial/option.c: Option Card (PC-Card to) USB to Serial Driver: v0.3
Nov 25 19:53:37 localhost usb.agent[5316]:      option: loaded successfully
Nov 25 19:53:37 localhost usb.agent[5344]:      option: already loaded

```


You now have a generic USB modem set up at /dev/ttyUSB0.

Let's use wvdial to handle the ppp connection. Edit/create /etc/wvdial.conf. Mine is as follows:

```

[Dialer Defaults]

Phone = *99***1#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT

[Dialer pin]

Init1 = AT+CPIN=1234

[Dialer option]

Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem

[Dialer 2gonly]

Init4 = AT+COPS=0,0,"Vodacom-SA",0

[Dialer 3gonly]

Init4 = AT+COPS=0,0,"Vodacom-SA",2

[Dialer internet]

Init5 = AT+CGDCONT=1,"IP","internet";

[Dialer internetvpn]

Init5 = AT+CGDCONT=1,"IP","internetvpn";

[Dialer myapn]

Init5 = AT+CGDCONT=1,"IP","myapn"

[Dialer 384k]

Init6 = AT+CGEQMIN=1,4,64,384,64,384
Init7 = AT+CGEQREQ=1,4,64,384,64,384

[Dialer 144k]

Init6 = AT+CGEQMIN=1,4,64,144,64,144
Init7 = AT+CGEQREQ=1,4,64,144,64,144

[Dialer 64k]

Init6 = AT+CGEQMIN=1,4,64,64,64,64
Init7 = AT+CGEQREQ=1,4,64,64,64,64


```

You will need to change some of the settings in the file according to your local network. I think the phone number *99***1# is used by all networks for packet switched data, but check with your network. Importantly, you must replace the digits 1234 in the [pin] section with your sim card's PIN. The sections [Dialer internet], [Dialer myapn] and [Dialer myapn] sets up three APNs used by the Vodacom network. Again, check with your network, but "internet" is likely to work.

Once you've configured wvdial, you can use it to establish the ppp connection. You can call sections of wvdial.conf in the command line. 

However, here I experience an irritating problem. The Option card takes about 10 seconds or so after being passed the PIN before it is ready to dial (you can see when it's ready because the green LED will stop flashing, leaving only the blue LED flashing). My wvdial tries to dial before the modem is ready and the ppp connection fails. I therefore run the following, but must press control-C and and run the dialer again before it works.

```

wvdial pin option internet 3gonly 384k
(press ^C after the PIN has been passed to the modem, wait until green LED stops flashing)
wvdial option internet 3gonly 384k

```

Ideally, one should tell wvdial to wait 10 seconds between running the [pin] section and the rest, but I don't know how to do this. Another alternative is to run a terminal app like minicom and manually pass AT+CPIN=1234 to the modem before running wvdial (without the pin flag).

If you want to dial again later without having unplugged the modem, you can use only:

```

wvdial option internet 3gonly 384k

```

It is a good idea to switch off the card before unplugging by typing
```

sudo cardctl eject

```

---

### Post by ssam on 2005-11-25
good work :-)

the best place for things like this is the [wiki.]("https://wiki.ubuntu.com/")

---

### Post by eduardgrebe on 2005-12-03
[QUOTE=ssam]good work :-)

the best place for things like this is the [wiki.]("https://wiki.ubuntu.com/")[/QUOTE]

Thanks. I have posted it to the section of the wiki with stuff from the forums. Hopefully it will be integrated in an appropriate spot.

---


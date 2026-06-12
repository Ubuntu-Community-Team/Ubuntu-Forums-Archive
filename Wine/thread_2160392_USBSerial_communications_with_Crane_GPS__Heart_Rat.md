---
title: "USB/Serial communications with Crane GPS / Heart Rate watch"
date: 2013-07-06
forum: Wine
---

### Post by timpaton on 2013-07-06
I've bought a cheap GPS / heart rate watch. 

For the sake of search-bait in case others are looking for a solution to the same problem, it's a device that has been released just this weekend by Aldi department stores in Australia, under their Crane house-brand. It looks to be identical to a watch being sold by Runtastic under their own brand, albeit with different software ([https://www.runtastic.com/shop/en/runtastic-gps-watch-with-heart-rate-monitor](https://www.runtastic.com/shop/en/runtastic-gps-watch-with-heart-rate-monitor)).

The user manual directs owners to download software from here:
[https://www.produktservice.info/26172330/ba.html](https://www.produktservice.info/26172330/ba.html)

I have installed the software (GPS Master 2.0.14) using Wine, which went without a hitch. The software runs perfectly.

When I connect the watch to my laptop using its USB cable, lsusb gives me:
Bus 003 Device 002: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x UART Bridge / myAVR mySmartUSB light

I've established from various threads that this is the default identification of a CP210x chip, which is a cheap serial-to-USB converter.

dmesg tells me:
[35974.212455] usb 1-1.2: >new full-speed USB device number 13 using ehci_hcd
[35974.307182] usb 1-1.2: >New USB device found, idVendor=10c4, idProduct=ea60
[35974.307193] usb 1-1.2: >New USB device strings: Mfr=1, Product=2, SerialNumber=3
[35974.307199] usb 1-1.2: >Product: CP2104 USB to UART Bridge Controller
[35974.307204] usb 1-1.2: >Manufacturer: Silicon Labs
[35974.307208] usb 1-1.2: >SerialNumber: 00645E55
[35974.308509] cp210x 1-1.2:1.0: >cp210x converter detected
[35974.384196] usb 1-1.2: >reset full-speed USB device number 13 using ehci_hcd
[35974.477005] usb 1-1.2: >cp210x converter now attached to ttyUSB0

... so it appears the device is correctly identified, drivers loaded, and activated as ttyUSB0. All good.

Now, the GPS Master software. To download data from the watch, one selects the Data Transfer -> Receive Watch Data menu item. This gives me a pop-up window:
"Message: No virtual COM port found"
... with an "OK" button to dismiss.

I have tried linking the ports, using: 
ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1

No change to the software's behaviour.

(For what it's worth, I've also tried linking the ttyUSB0 to COM2, COM3 and COM7 which is where the device appeared on my wife's Win7 machine; no difference).

I suspect it should be an easy fix - there must be a way to get this GPS Master software to communicate with the watch on ttyUSB0. I just don't know how to make it happen.

I also tried installing the software supplied by Runtastic - it wouldn't run under WINE. But if we can find a fix here for my Crane watch, then maybe the Crane software will work for people who buy the Runtastic unit. 

Any suggestions to try?

Thanks,
Tim

---

### Post by knedlyk on 2013-10-24
Hi Tim,
I have the same watch, but bought it in Europe as a Conrad Gps NAV II watch with Gps. I tried several times to use com port emulation under wine with the same results. Your post is from July 2013, do you have some luck with this?

---

### Post by rrob on 2014-07-01
Same problem.
Multi NAV-3.

---

### Post by sean lyon on 2014-07-01
same here decent watch loathed to go back to microsoft just to upload some of my rides to FB and the like - even the old Garmin car unit could be found by Ubuntu Perhaps the Apple drivers may be a wat in  trouble is ive no way of opening the apple drivers either :mad:

Ok found this unfortyunatley it doesnt make sense to me Someone able to show me how to make it work ( somethings lost in translation )

Linux driver for the usb/serial port UART Bridge
[http://www.silabs.com/products/mcu/pages/usbtouartbridgevcpdrivers.aspx](http://www.silabs.com/products/mcu/pages/usbtouartbridgevcpdrivers.aspx)

---

### Post by mru00 on 2014-11-04
I have implemented a very basic linux client for the watch: [https://github.com/mru00/GpsWatch](https://github.com/mru00/GpsWatch)
It is in very early development and definitely not end-user ready, but it might help someone out there. 
It should also work for the runtastic gps watch.

---

### Post by knedlyk on 2014-11-08
@mru00, please continue your work! I am very impressed, it really works! I made a PKGBUILD for archlinux: [https://aur.archlinux.org/packages/gpswatch-git/](https://aur.archlinux.org/packages/gpswatch-git/) , it is easy to make a package for ubuntu/debian too.

---

### Post by sean lyon on 2014-11-17
> **mru00 said:**
> I have implemented a very basic linux client for the watch ......

WooHoo thank you!  got the files off the watch into "Golden Cheeta"

---

### Post by knedlyk on 2014-11-17
Project has a new name and repo: [https://github.com/mru00/crane_gps_watch](https://github.com/mru00/crane_gps_watch) . The client completely rewritten in C. Please read README.md before using.

---


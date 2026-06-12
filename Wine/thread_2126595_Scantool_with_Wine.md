---
title: "Scantool with Wine"
date: 2013-03-17
forum: Wine
---

### Post by tdriver on 2013-03-17
I can't seem to get Scantool to run with Wine. I starts to install then stops and tells me i need to continue install. So I reset install it runs to completion, i even get an icon on my desktop. Click on icon it starts to run the program then just stops..nothing happens.. please help...here's the click for the demo version of scantool..[http://www.obdsoftware.net/TrialVersion.aspx](http://www.obdsoftware.net/TrialVersion.aspx)

---

### Post by abrianb on 2013-03-17
I have never found a way to make Scantool work, the linux version or the windows version with wine never finds my elm device. An application that has worked for me is Garmon. It is available at... [http://sourceforge.net/projects/garmon/](http://sourceforge.net/projects/garmon/)

---

### Post by tdriver on 2013-03-17
> **abrianb said:**
> I have never found a way to make Scantool work, the linux version or the windows version with wine never finds my elm device. An application that has worked for me is Garmon. It is available at... [http://sourceforge.net/projects/garmon/](http://sourceforge.net/projects/garmon/)

that looks really nice could you help me with how you set it up

---

### Post by abrianb on 2013-03-17
Download the file and open it with archive manager, extract the file to your desktop. open the file garmon-0.3.1. It contains many items, one of which is the file "INSTALL" , open it and follow the directions in it. when you enter the command cd Desktop/garmon-0.3.1 remember to capitalize the D in desktop. If when running the commands you might run into dependency issues. the script in terminal will tell you that it is missing a library or package. If this happens then open synaptic package manager and copy the name of the library into the search box then install the package. then run the command again in terminal. If I recall correctly I had to do this three times before I got all dependencies filled and I had success. Type garmon into dash and then click on the package to start it. Ask if you need more help.

---

### Post by tdriver on 2013-03-17
> **abrianb said:**
> Download the file and open it with archive manager, extract the file to your desktop. open the file garmon-0.3.1. It contains many items, one of which is the file "INSTALL" , open it and follow the directions in it. when you enter the command cd Desktop/garmon-0.3.1 remember to capitalize the D in desktop. If when running the commands you might run into dependency issues. the script in terminal will tell you that it is missing a library or package. If this happens then open synaptic package manager and copy the name of the library into the search box then install the package. then run the command again in terminal. If I recall correctly I had to do this three times before I got all dependencies filled and I had success. Type garmon into dash and then click on the package to start it. Ask if you need more help.

Well i got it started and ran into this, Package Manager tells me that i have Python Gtk 2 installed. Not sure what's happening here.  


checking pkg-config is at least version 0.9.0... yes
checking for PYGTK... configure: error: Package requirements (pygtk-2.0) were not met:

No package 'pygtk-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYGTK_CFLAGS
and PYGTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by tdriver on 2013-03-17
Well good news, it's working BUT....It's not finding my ElmScan 5

---

### Post by abrianb on 2013-03-18
In preferences device tab I have in the portname box ... "/dev/tty/USB0"   and in the initial baudrate box I have 38400. Some devices need to start slow, Garmon will speed baudrate up once the device is working.

---

### Post by tdriver on 2013-03-21
What device are you using?

---

### Post by abrianb on 2013-03-21
Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Thats what I see when I enter lsusb into terminal with the device plugged in. It is a generic ebay device.

---

### Post by tdriver on 2013-03-24
Ok can't seem to get it to work...when i run lsusb this what i get.
saul@saul-HP-Mini:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05c8:0202 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 004: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 002 Device 005: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
saul@saul-HP-Mini:~$ 

Now it seems to me that i have the same exact reader as you. What do i need to do to get it to read. I changed my dialout permission, that causes it to longer say that it can not open PORT tty/usb0 anymore. Any ideas???

---

### Post by abrianb on 2013-03-25
Once Garmon is open are you plugging the device into the car, click reset in Garmon's device menu, then clicking monitor?

---

### Post by tdriver on 2013-03-29
I did as you suggested. No Luck...I think i have a USB port issue here. Maybe a permission problem, or having to tell Garmon to find the proper USB port. Of course i have no idea how to fix that...

---


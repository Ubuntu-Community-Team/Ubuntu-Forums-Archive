---
title: "Unable to connect to LG VX8800 via Bitpim"
date: 2008-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by VvWolverinevV on 2008-02-07
Hi, lsusb detects my LG VX8800 as ```
Bus 007 Device 003: ID 1004:6000 LG Electronics, Inc. VX4400/VX6000 Cellphone
```

When I try to run Bitpim sync (manually setting the phone to VX6000 and port usb::007::003::1), I get the following error: ```
BitPim version: 1.0.0-Debian
An unexpected exception has occurred.
Please see the help for details on what to do.

Traceback (most recent call last):
  File "/usr/share/bitpim/code/gui.py", line 283, in run
    res=call()
  File "/usr/share/bitpim/code/gui.py", line 158, in __call__
    return apply(self.method, self.args+args, d)
  File "/usr/share/bitpim/code/gui.py", line 1866, in getdata
    self.setupcomm()
  File "/usr/share/bitpim/code/gui.py", line 1849, in setupcomm
    configparameters=comcfg)
  File "/usr/share/bitpim/code/commport.py", line 68, in __init__
    self._openport(self.port, *self.params)
  File "/usr/share/bitpim/code/commport.py", line 97, in _openport
    self.ser=self._openusb(port, timeout)
  File "/usr/share/bitpim/code/commport.py", line 129, in _openusb
    return _usbdevicewrapper(iface.openbulk(), timeout)
  File "/usr/lib/bitpim/native/usb/usb.py", line 165, in openbulk
    raise USBException()
USBException: could not claim interface 1: Operation not permitted

Variables by last 8 frames, innermost last

Frame run in /usr/share/bitpim/code/gui.py at line 276
       resultcb =  <gui.Callback instance at 0x4de1170>
            res =  None
           self =  <WorkerThread(BitPim helper, started daemon)>
           item =  (<gui.Request instance at 0x4de1440>, <gui.Callback instance at 0x4de1170>)
           call =  <gui.Request instance at 0x4de1440>
             ex =  USBException('could not claim interface 1: Operation not permitted',)
              e =  USBException('could not claim interface 1: Operation not permitted',)
          first =  0

Frame __call__ in /usr/share/bitpim/code/gui.py at line 158
           self =  <gui.Request instance at 0x4de1440>
           args =  ()
              d =  Keys []
                   {}
         kwargs =  Keys []
                   {}

Frame getdata in /usr/share/bitpim/code/gui.py at line 1866
           self =  <WorkerThread(BitPim helper, started daemon)>
            req =  <guiwidgets.GetPhoneDialog; proxy of C++ wxDialog instance at _00cc0b0200000000_
           todo =  [(<bound method WorkerThread.rebootcheck of <WorkerThread(BitPim helper, started

Frame setupcomm in /usr/share/bitpim/code/gui.py at line 1849
           name =  'usb::007::003::1'
           self =  <WorkerThread(BitPim helper, started daemon)>
       autofunc =  None
         comcfg =  Keys ['baud', 'hardwareflow', 'retryontimeout', 'softwareflow', 'timeout']
                   {'baud': 115200, 'hardwareflow': False, 'softwareflow': False, 'retryontimeout':
          klass =  <class commport.CommConnection at 0x1a4aef0>

Frame __init__ in /usr/share/bitpim/code/commport.py at line 68
           baud =  115200
   autolistargs =  (<module 'phones.com_lgvx6000' from '/usr/share/bitpim/code/phones/com_lgvx6000.
           self =  <commport.CommConnection instance at 0x4cd2368>
   hardwareflow =  False
   autolistfunc =  None
        timeout =  3
      logtarget =  <WorkerThread(BitPim helper, started daemon)>
configparameters =  Keys ['baud', 'hardwareflow', 'retryontimeout', 'softwareflow', 'timeout']
                   {'baud': 115200, 'hardwareflow': False, 'softwareflow': False, 'retryontimeout':
   softwareflow =  False
           port =  'usb::007::003::1'

Frame _openport in /usr/share/bitpim/code/commport.py at line 110
           baud =  115200
          dummy =  0
    description =  None
           self =  <commport.CommConnection instance at 0x4cd2368>
   hardwareflow =  False
        timeout =  3
   softwareflow =  False
           port =  'usb::007::003::1'

Frame _openusb in /usr/share/bitpim/code/commport.py at line 129
          iface =  <native.usb.usb.USBInterface instance at 0x4de15f0>
      wantedbus =  '007'
           name =  'usb::007::003::1'
            bus =  <native.usb.usb.USBBus instance at 0x4de1248>
           self =  <commport.CommConnection instance at 0x4cd2368>
      wanteddev =  '003'
        timeout =  3
         device =  <native.usb.usb.USBDevice instance at 0x4de17e8>
    wantediface =  1
              _ =  'usb'

Frame openbulk in /usr/lib/bitpim/native/usb/usb.py at line 165
            res =  -1
           self =  <native.usb.usb.USBInterface instance at 0x4de15f0>
           epin =  <native.usb.usb.USBEndpoint instance at 0x4de1758>
              v =  1
          epout =  <native.usb.usb.USBEndpoint instance at 0x4de13b0>
             ep =  <native.usb.usb.USBEndpoint instance at 0x4de13b0>

```

---

### Post by VvWolverinevV on 2008-02-08
*Bump*

Anyone know what's going on here?

---

### Post by rab4567 on 2008-02-11
Hey I've been there I have a Samsung sch-u740 but it should  work on your phone

1.) Go to bitpim.org download the latest debian pacage version 1.0.5.0

2.) Plug in the usb cable to your phone then go to applications> accessories> terminal type lsusb and enter. You should see a string of driver listed thats a good sign.

3.)Then type in terminal sudo bitpim enter then your password and you should get a conformation box stating it recognizes your phone then type in your name and phone model.

Good Luck

Oh yeah you should run Bitpim from the command line (sudo bitpim).

---

### Post by VvWolverinevV on 2008-02-19
This is a start.  If I run Bitpim as root, it detects my phone as "Other CDMA phone."  However, I am unable to download any information from my phone to Bitpim.  The VX8800 is not explicitly supported in version 1.0.0 - Debian.  There is a new release that supports the Venus, but I can't find the source code for x86-64 bit architecture.  Am I stuck just waiting for someone to compile the newer version for 64-bit?

---

### Post by VvWolverinevV on 2008-02-24
*Bump*

---


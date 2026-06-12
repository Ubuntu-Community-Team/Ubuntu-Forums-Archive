---
title: "[SOLVED] Microchip MPLAB"
date: 2007-12-03
forum: Wine
---

### Post by SimonW on 2007-12-03
Hi guys!

Bevore I start posing qestions a 
**short explaination** how to use a **USB to RS232** bridge inside of Wine:

Plug in the USB cable and look inside the syslog imediately. You should see, if and where the device is installed
```
gedit /var/log/syslog
```

Then create a softlink.
```
ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1

```

**This is my problem:**
I got **MPLAB** working without problems, but cannot connect to the ICD2.
It warns I have to disable the FIFO buffer.
I successfully opens the serial port and tries to connect, then it hangs up.

Has anyone an Idea, how to disable the FIFO or solve this porblem an other way?

reards Simon

---

### Post by cogadh on 2007-12-03
I don't know what MPLAB is or what you are actually trying to do, so I could be completely off-base here, but you normally don't need to create symlinks to USB devices in order for Wine to access them. Have you tried running it without that in place?

EDIT - I knew I should have looked a little harder before I posted. This is a known bug in Wine with MPLAB:
[http://bugs.winehq.org/show_bug.cgi?id=4055](http://bugs.winehq.org/show_bug.cgi?id=4055)

---

### Post by SimonW on 2007-12-06
Hello everybody!

Thank you, codagh for the link!
I didn't get MPLAB to run on Linux, instead I'm using now Windows inside of VirualBox for that purpose.

To get **USB running** inside of the **VirtualBox** with Ubuntu Gutsy see:
[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html]("http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html")

It would be nice if the bug would get fixed, althoug I have very little hope, the Bug has been reported for the first time 3 Years ago.

Edit: As it seams, MPLAB does even have Connection-Problems when run on native Windows. In my case it only works correct (with VirtualBox), if I set the Com Port to 1.

Regards,
Simon

---


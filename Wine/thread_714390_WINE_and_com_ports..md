---
title: "WINE and com ports."
date: 2008-03-03
forum: Wine
---

### Post by hvac3901 on 2008-03-03
I have recently found myself using my laptop at work more so than ever before. I work on digital controls for building systems. Air conditioning and services of that nature.

The basic program we use is called Datamate, i installed it under WINE and it worked very well up until the crucial point of connecting it to a building system via a communication port. And it resulted in NO connection or Connection failure.

I am not blaming WINE, but i am curious hoe the Linux environment would employ the COM ports versus the Windows environment. and if WINe has another way of doing that as well.

it is a very basic program, much like say a telenet type program, with a little of GUI added into it. Not fancy at all. I think my issue is that of COM port usage.

I am using a USB to serial adapter to get to the required RJ-11 communication connection, because my computer dosn't have the RS-235 available. I am hoping this is some setting i am missing here. any insight would be greatly appreciated.

I am sure i left something out, please let me know what i may be i will do my best to provide the info.

---

### Post by Whiffle on 2008-03-03
First you'll want to figure out what device your serial converter is.  It should be something like /dev/ttyUSB0.  If you plug in the converter, and then run dmesg in terminal, it should pick it up and list its location.  If not, we'll have to find some drivers for it.

Next, wine handles com ports by having a link to the device (ie /dev/ttyUSB0), in the ~/.wine/dosdevices folder.  This link would be created as follows:
```

ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1

```

With that it might work, although there could be some issues with permissions, but if it doesn't work the first time hope is not lost.

---

### Post by hvac3901 on 2008-03-03
So if i read that right, WINE is not intuitive when it comes to using COM ports, like the horrid windows operating system is?

I have to tell it to use it?

I will be trying my hand at that link setup first thing tomorrow, thank you.

---

### Post by Whiffle on 2008-03-03
Pretty much.  I don't think many people have a use for com ports in wine so they don't set it up automagically.

---

### Post by hvac3901 on 2008-03-18
Hey thanks for the help, i was able to sucessfully set up a com port for wine to use. however it is still not talking on COM1, if you could provide some more help like earlier i would be greatful. thanks.

---

### Post by Superpup on 2008-03-20
Has anyone else had any luck with this?

I'm trying to use a USB-serial adapter for programming radios. I've set up the port in Wine as outlined above. It appears that I've successfully set up the com port, but the programming application doesn't recognize the com port.

If I need to provide any additional information let me know.

Thanks,

---

### Post by hvac3901 on 2008-03-20
> **Superpup said:**
> Has anyone else had any luck with this?

I'm trying to use a USB-serial adapter for programming radios. I've set up the port in Wine as outlined above. It appears that I've successfully set up the com port, but the programming application doesn't recognize the com port.

If I need to provide any additional information let me know.

Thanks,

I can't claim to have any luck, but the software i am using has a COM log, the file reads like many others i have seen where the BAUD rate was completely screwed up, where a single line should read "high, hello, message, hardware?" it reads those letters vertically as in a broken line, all as individual messages one letter at a time, let me see if i can cut and paste it. This message is not from WINE, but the software i am trying to use, this is why i cannot baud rate or something like that is so freaked out i just get kicked.

(6259) recv: "T" - 0 ms.

(6259) recv: "i" - 0 ms.

(6259) recv: "m" - 0 ms.

(6259) recv: "e" - 0 ms.

(6259) recv: "," - 0 ms.

(6259) recv: " " - 0 ms.

(6259) recv: "M" - 0 ms.

(6259) recv: "e" - 0 ms.

(6259) recv: "s" - 0 ms.

(6269) recv: "s" - 0 ms.

(6269) recv: "a" - 0 ms.

(6269) recv: "g" - 0 ms.

(6269) recv: "e" - 0 ms.

(6269) recv: "," - 0 ms.

(6269) recv: " " - 0 ms.

(6269) recv: "C" - 0 ms.

(6269) recv: "a" - 0 ms.

(6269) recv: "n" - 0 ms.

(6269) recv: "c" - 0 ms.

(6269) recv: "e" - 0 ms.

(6269) recv: "l" - 0 ms.

(6269) recv: "," - 0 ms.

(6269) recv: " " - 0 ms.

(6269) recv: "H" - 0 ms.

(6269) recv: "e" - 0 ms.

(6269) recv: "l" - 0 ms.

(6269) recv: "l" - 0 ms.

(6269) recv: "o" - 0 ms.

(6269) recv: "?" - 0 ms.

---

### Post by Superpup on 2008-03-25
So far I have been able to get the com port recognized in 8.04. I couldnt at all in 7.10.

The program I trying to use is called VX Commander. It is a programming utility for a ham radio. When it is reading the radio data, it always stops at 25% now.

Are there any logs that I might be able to find information as to why it is stopping? Or anyone have any ideas?

---

### Post by hvac3901 on 2008-03-25
Well I am lucky, i have a log in the software i am using.

Are you running it with a true serial, or a usb converter? I have recently read that not all of them are Linux friendly.

Yes you can check the system log;  Adminisstration- System Log not sure how much you will find there pertinent to your program, or go to terminal and type "dmesg" it will give you a brief synopsis of the recent activity.

---

### Post by hvac3901 on 2008-03-25
Oh and there are 34 packages in Synaptic for HAM radio stuff, did you check them out?

---

### Post by Superpup on 2008-03-25
I am using a USB-Serial adapter.

I just tried another programming application and it worked fine. So I guess the problem is just with the one program, and not the usb/serial itself. Kinda stinks. I like the other application better!

Yep, I've looked through the ham radio applications. I downloaded some.  A lot of them are for stuff that I'm not really into. I did get some though, and ordered a data cable for my big radio to hook it up and see how it works. That was only available as a 9-pin serial cable too, so hopefully it works through the USB adapter too.

---

### Post by hvac3901 on 2008-03-25
can you differentiate between programs running in linux that connect with success, and those that don't work under wine? or is it hit and miss?

---


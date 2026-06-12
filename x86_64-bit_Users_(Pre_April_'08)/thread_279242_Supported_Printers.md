---
title: "Supported Printers"
date: 2006-10-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by confusimo on 2006-10-17
I have Ubuntu DD 6.06 64 bit.  I use Ubuntu, but also installed Xbuntu and maybe someday Kbuntu.

My printer is broken.  It just is, I already checked everything.  I need a new one. 

Is there a list of supported printers that work with Ubuntu?  Is is the same with Kbuntu and Xbuntu.  Or are those 3 comletely different things?

And if I upgrade to Edgy will it still work.  Or is support for devices different in Edgy?

Thanks,
Confusimo

---

### Post by Sef on 2006-10-17
In general, HP and Epson are the most likely to be supported in Linux.  Go here to find more information: [LinuxPrinting.org]("http://LinuxPrinting.org")

---

### Post by John.Michael.Kane on 2006-10-17
This site [**linux printer_list**]("http://www.linuxprinting.org/printer_list.cgi") has a known list of working printers. 

I'm using an HP LaserJet 5P with no issues.

---

### Post by mrehorst on 2006-10-17
My Samsung ML-1740 works on AMD64 ubuntu.  The ML-1740 doesn't appear on the driver list but ML1710 and 1750 do.  I am using the ML-1710 driver and it works fine.

If you go to the system/administration/printing menu and tell it you want to install a printer, it will give you a HUGE list of printer drivers available to be loaded, from about 40 different manufacturers.

MR

---

### Post by confusimo on 2006-10-17
The SD link has Lexmark Z612 but no 611.  Also Lexmark Z645 is what I'm looking at.  I don't print much so I just need a cheap basic printer.  But 645 is not listed either.  I'll keep looking.

Thanks,
Confusimo

---

### Post by John Jason Jordan on 2006-10-18
> **mrehorst said:**
> If you go to the system/administration/printing menu and tell it you want to install a printer, it will give you a HUGE list of printer drivers available to be loaded, from about 40 different manufacturers.MR
The problem is what people mean by "supported." For example, I have a Samsung color laser that all the Linux sites say is supported. Even Samsung says it is supported under Linux. But after installing the driver I discovered that the only resolution option in Linux is 300 dpi. I have three HP printers as well, and the driver for each one lacks one or more features that is available under Windows. And then you get to the issue of applications. Many applications cannot access several features of the printer, even those features that appear in the driver and in CUPS.

Printing is one of the biggest areas where Linux needs serious catch-up work.

---

### Post by JAPrufrock on 2006-10-18
I'm in the same boat- gotta buy a new printer.  Here's my strategy.  First of all, go for either an HP or Epson- best chance for being compatible with Ubuntu.  Then go shopping, either online or in you favorite discount store. Find a couple/few printers you like and jot down model name, etc.  Then search the internet and ubuntu fora for infomation on your selections.  Pick one that is proven to be 100% supported. You can't miss. Best of luck.

---

### Post by onon_onon on 2006-10-18
I have an Epson Stylus C67 and it works like a charm. I'm very surprised with the linux printer support today. I was out from linux world for a couple of years and now my printer works perfect.
Be on the HP/Epson road and you will get your new printer working.

---

### Post by confusimo on 2006-10-22
Ok, I need a new printer.  DD 6.06 64 bit.  

I'm having trouble finding one.  Probably a laser.

Would I be able to install a printer server instead on my XP-PRO machine.  Hook a printer into the network.  And then just setup the  Ubuntu to print from there.  Doesw any free or opensourse program  on ubuntu supporrt printing from network or printserver?

Thanks,
Confusimo

---

### Post by confusimo on 2006-10-22
I hate Epson.  I've had 4 of them and they all clogged or broke within 2 years.  Epson is no good.

I'd love to use my HP deskjet 3650, but it keeps blinking and won't shutup.  I've tried reseting it and leaving it unplugged all night but still nothing.  Both cartridges are at lest 50% full.  And no paper jam or anything broken.  But it refuses to print or stop blinking.

Thanks,
Confusimo

---

### Post by confusimo on 2006-10-22
Nobody knows about print servers?

Thanks,
Confusimo

---

### Post by agentstewie on 2006-10-22
> **confusimo said:**
> Nobody knows about print servers?

Thanks,
Confusimo

i think there is one already built in linux.
its called CUPS
atleast i think that should help you.
C: Common
U: Unix
P: Printing
S: Service

---

### Post by FluffyElmo on 2006-10-22
You should be able to find an inexpensive laser printer that will work fine with Ubuntu easily enough. My local Office Depot had several last time I looked. It may not say 'Linux' on the box but any printer that supports PCL4, PCL5 or PCL6 *in the printer* will work perfectly.

Many manufacturers, Samsung comes to mind, also release Linux drivers for most of their laser printers where special drivers are needed but it's considered an unsupported option. Your best bet is to make a list of available printers in your price range and then check [http://www.linuxprinting.org/]("http://www.linuxprinting.org/") and search Google to see which of them have decent Linux support. 

To answer your print server question, Ubuntu prints to networked Windows printers via Samba. It's supported out of the box, in the "Add Printer" dialog you pick "Windows Networked (SMB)" and then enter the share name to a printer. Note that I haven't tried printing to a WinXP printer myself so I don't know if there are any driver issues but it *looks* easy enough ;)

Since you're buying a brand new printer though, and not trying to work with one you already have, I think your best bet is to do a bit of research and find a printer that will work well with both operating systems.

---

### Post by confusimo on 2006-10-22
I finally settled on an HP laserjet 1020.  At Costco $124.99 plus tax.  Everywhere else $179.99 plus tax.  Good deal.  Mono only.  No color.  But I'm not doing photographs or anything heavy.  Mostly text or even mapquest nothing too heavy.  

But I have a windows X-PRO machine.  And I don't want 2 printers one for each.  SO it would be nice to do both machines from 1 printer.

I don't know if 1020 is supported.  But when I goto System, Administration, Printing, and add New Printer.  Under HP it says Laserjet 1020.  So it should be supported.

Thanks,
Confusimo

---

### Post by FluffyElmo on 2006-10-23
If the printer is supported under Linux/Ubuntu you can easily share it with the WinXP machine. In the office I have a plotter attached to an Ubuntu server and various Windows machines plot to it without any issues.

The HP may not be fully supported ([http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020")) though things may have improved since those posts. There is also a suggested printer page at [http://www.linuxprinting.org/suggested.html]("http://www.linuxprinting.org/suggested.html"), if you look under monochrome laser they give recommendations. If you do a lot of printing other lasers may be cheaper to run than HP which might offset the initial cost.

In any case since you can share the printer under Ubuntu or Windows it's probably fine either way.

---

### Post by tubasoldier on 2006-10-23
I just replaced my HP laser printer with a Brother HL-2040. Ubuntu uses the HL-2060 driver and it works great. IMO the Brother works better because you do not need that HP stuff running in the background all the time. However, the HP printers to work well. But please buy a CUPS supported printer. it will make your life much easier than trying to get some cheap lexmark working.

---

### Post by confusimo on 2006-10-23
I went to office depot and they said that Brother uses a drum and a toner so it would be very costly.  The drum is like between $150-200.  And plus toner another $50-100.  So it's not worth it.  

HP doesn't ahve a drum only toner so it's cheaper in the long run.

Thanks,
Confusimo

---

### Post by FluffyElmo on 2006-10-23
The drum has a life of over 18000 pages though while toner cartridges typically last around 5000 pages. So you don't have to buy the drum every time you run out of toner. You spend ~$50 each time until the drum goes when you spend ~$200 for both.

Since HP cartridges include the drum you typically end up paying ~$150-$200 every time you run out of toner and it costs you more in the long run.

---

### Post by confusimo on 2006-10-23
I keep getting varied answers.   But the officedepot guy said only 8-10,000 pages with drum.  Anyway HP 1020 toner cartridge is only $69 for me not $150.  So it still cheaper.

Thankks,
Confusimo

---

### Post by John.Michael.Kane on 2006-10-23
confusimo heres guide on print sharing. 

```
**Print server/sharing**
[http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Printing-HOWTO.html](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Printing-HOWTO.html)

[http://tldp.org/HOWTO/SMB-HOWTO-9.html](http://tldp.org/HOWTO/SMB-HOWTO-9.html)
[http://tldp.org/HOWTO/SMB-HOWTO-10.html](http://tldp.org/HOWTO/SMB-HOWTO-10.html)

[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/)

[http://home.pacific.net.sg/~harish/linuxprint.html](http://home.pacific.net.sg/~harish/linuxprint.html)

[http://www.faqs.org/docs/Linux-mini/Debian-and-Windows-Shared-Printing.html](http://www.faqs.org/docs/Linux-mini/Debian-and-Windows-Shared-Printing.html)

[http://www.linuxforums.org/servers/howto:_fileserver_with_samba_and_printserver_with_cups.html](http://www.linuxforums.org/servers/howto:_fileserver_with_samba_and_printserver_with_cups.html)

[http://www.linuxheadquarters.com/howto/networking/samba.shtml](http://www.linuxheadquarters.com/howto/networking/samba.shtml)

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch11_:_Sharing_Resources_Using_Samba](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch11_:_Sharing_Resources_Using_Samba)
```

Also confusimo If you keep getting varied answers. then you need to do some leg work ie: research forum searches. 

Yes we are here to help,however.no one is going to do the leg work for you.  

Once you post a question and it's answered,and you feel the answer/s don't match up to what you have been told then more research should be done on your part.

One should not buy something just cause it has a cut rate price only to find out that it may not be supported,and cost more to maintain.

---

### Post by confusimo on 2006-10-28
Well I returned that got a Samsung ML-2510 and everything works now.  They have native linux drivers on the CD and on their website.  It worked great and tech support was very helpful.  I just have to get a new USB 2.0 cable.  The rest is OK.  It prints great.  No need for windows anymore.

Thanks,
Confusimo

---

### Post by factor on 2006-11-10
hi, i want to buy that printer too, samsung ml-2510, does it works in Edgy 64 bit?

Thanks in advance for your help.

Regards.

---


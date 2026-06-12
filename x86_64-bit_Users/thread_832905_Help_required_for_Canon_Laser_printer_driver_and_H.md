---
title: "Help required for Canon Laser printer driver and Hardy-AMD64"
date: 2008-06-18
forum: x86 64-bit Users
---

### Post by g4r on 2008-06-18
Hello.

I'm desperately trying to have a Canon LBP-1120 working under Hardy AMD64.

I've spent HOURS trying to get it to work, following the various docs found at [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)
and elsewhere.

I've even tried compiling the part of the driver that comes with sourcecode, but no luck whatsoever.

A quick rundown of the system configuration: Kubuntu on AMD64, fully updated upto yesterday, Ghostscript, Canon drivers V 1.60, Canon LBP1120 printer hooked to the USB port.

Here is the full, gruesome story.

I first followed the documentation linked above, installing the 32 bit libraries (apparently under Hardy there's only **ia32-libs** needed), downloading the Canon drivers from their site and installing the Debian packages: no luck.

It's important to note that the documentation liked above is for older versions of the Canon drivers, which only supply the RPM packages. The new 1.60 has debian/Ubuntu packages and they also take care of creating the various fifos and directories in /var.

I could see that the ccpd daemon wasn't starting, apparently it's crashing with a segfault (saw on the kernel messages). The monitoring utility supplied by Canon wouldn't work as it tried to hook up with the ccpd daemon. Printing of course wouldn't work at all.

So I went for the hard route, and recompiled for AMD64 the few bits and pieces found in the Canon Driver archive. This yield some progress, because at least the ccpd daemon would start. It's important to note however that the daemon itself is only provided in binary form, as many of the "support" binaries. I think the difference was made by having compiled 64-bit versions of some of the support libraries (those were installed in /usr/local/lib as per default 'configure' script).
Unfortunately even with the daemon running printing wouldn't work. At least the Canon monitoring utility would start, and inform me the printer was found (thanks for that!).

I've tried hacking the CUPS backed, named 'ccp'. Essentially it just passes data from CUPS to the ccpd daemon via the fifo installed in /var/ccpd/fifo0. I could see NO DATA was being sent to it, possibly meaning there was a configuration problem. I've even tried using the backed to supply the driver with direct data (a postscript file) but still no luck whatsoever - no printer activity at all.
I've checked permissions on every file system object involved (the fifo, the device node under /dev/usb/lp0, etc...) they're all fine.
When the daemon was running, I could see that when trying to print it would spawn some helper processes, captinfo and captfilter, that would swallow 100% CPU (I've let them run for a while of course).

Out of desperation, I've tried using "strace" on the daemon itself, but this didn't give me any particular clue, other than finding out that this driver, running as root, accesses /etc/passwd. And also noting that the logfile, at least on version 1.60 of the driver, is never used nor accessed (instead, stdin and stdout are redirected to /dev/null).

Any help is appreciated, I'm really running out of options and as you can see from the tale above I'm quite resourceful.

---

### Post by Uncle Hotte on 2008-11-08
Hi,

I don't know if this is still actual, but finally I got my Canon Printer LBP5100 working and maybe it will you as well.

I am running Kubuntu 8.04 (Hardy Heron) on an AMD64 architecture and I tried everything, I could find to get my printer working, but no luck at all. It seems that all installation guides and 32bit Debian packages for the LBP5100 printer are not working under Hardy 64bit.

Finally, I found the source code of Canon's driver at their Australian web page. It is for a 32bit architecture, but I could patch the package to compile it on my 64bit machine.


According to the driver documentation, this driver should work with the following printers:
    LBP3310
    LBP5100
    LBP5300
    LBP3500
    LBP3300
    LBP5000
    LBP3210
    LBP3000
    LBP2900
    LBP3200
    LBP-1120/1210

Here is my solution to get the LBP5100 working.

1.
```
Get CAPT source code from [http://support-au.canon.com.au/contents/AU/EN/0900772502.html](http://support-au.canon.com.au/contents/AU/EN/0900772502.html)
```

2.Untar it
```
tar xfz CAPT_Printer_Driver_for_Linux_Src_v170a_uk_EN.tar.gz
cd  CAPT_Printer_Driver_for_Linux_Src_v170a_uk_EN/src/
tar xfz cndrvcups-common-1.70-1.tar.gz
tar xfz cndrvcups-capt-1.70-1.tar.gz
```

3.Install required libraries and (development packages) listed in the readme files in cndrvcups-common-1.70 and cndrvcups-capt-1.70
NOTE: libbuftool will be provided by cndrvcups-common

Install packages build-essential and gettext

4.Build cndrvcups-common-1.70
```
cd cndrvcups-common-1.70
Change “Architecture: i386” in debian/control to “Architecture: amd64”
Run dpkg-buildpackage in cndrvcups-common-1.70

The debian package will be placed in CAPT_Printer_Driver_for_Linux_Src_v170a_uk_EN/src
```

5.Install cndrvcups-common
```
sudo dpkg -i cndrvcups-common_1.70-1_amd64.deb
```

6.Build cndrvcups-capt-1.70
```
cd cndrvcups-capt-1.70
Change “Architecture: i386” in debian/control to “Architecture: amd64”
Change “	dh_shlibdeps” in debian/rules to “#	dh_shlibdeps”
Run dpkg-buildpackage in cndrvcups-capt-1.70
```

The debian package will be placed in CAPT_Printer_Driver_for_Linux_Src_v170a_uk_EN/src

7.Install cndrvcups-capt
```
sudo dpkg -i cndrvcups-capt_1.70-1_amd64.deb
```

8.Change /etc/init.d/ccpd to
```
#!/bin/sh
# ccpd startup script for Canon Printer Daemon for CUPS
# Modified for Debian GNU/Linux
# by Raphael Doursenaud <rdoursenaud@free.fr>.
DAEMON=/usr/sbin/ccpd
LOCKFILE=/var/lock/subsys/ccpd
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
NAME=ccpd
DESC="Canon Printer Daemon for CUPS"
test -f $DAEMON || exit 0
case $1 in
start)
echo -n "Starting $DESC: $NAME"
start-stop-daemon --start --quiet --exec $DAEMON
echo "."
;;
stop)
echo -n "Stopping $DESC: $NAME"
start-stop-daemon --stop --quiet --oknodo --exec $DAEMON
echo "."
;;
status)
echo "$DESC: $NAME:" `pidof $NAME`
;;
restart)
echo -n "Restarting $DESC: $NAME"
start-stop-daemon --stop --quiet --oknodo --exec $DAEMON
sleep 1
start-stop-daemon --start --quiet --exec $DAEMON
echo "."
;;
*)
echo "Usage: ccpd {start|stop|status}"
exit 1
;;
esac
exit 0

```

9.Setup the printer
```
sudo /etc/init.d/cupsys restart
sudo /usr/sbin/lpadmin -p LBP5100 -m CNCUPSLBP5100CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
sudo /usr/sbin/ccpdadmin -p LBP5100 -o /dev/usb/lp0
sudo /etc/init.d/ccpd restart

```

---

### Post by g4r on 2008-11-10
> **Uncle Hotte said:**
> Hi,

I don't know if this is still actual, but finally I got my Canon Printer LBP5100 working and maybe it will you as well.

I am running Kubuntu 8.04 (Hardy Heron) on an AMD64 architecture and I tried everything, I could find to get my printer working, but no luck at all. It seems that all installation guides and 32bit Debian packages for the LBP5100 printer are not working under Hardy 64bit.

Finally, I found the source code of Canon's driver at their Australian web page. It is for a 32bit architecture, but I could patch the package to compile it on my 64bit machine.


Problem is, the "source" package doesn't contain ALL the source code but only a small portion of it. The main binaries (like the ccpd daemon) are provided in binary form only (x86). Plus there are a bunch of .BIN files (I guess they're firmware for the printers), also in strictly binary form.

This would be ok if everything worked fine and dandy. Guess what: it DOES NOT.

In the meantime I've also managed to get the driver running under amd64, but it's VERY UNSTABLE. Example: just unplug the USB cable and the ccpd daemon will segfault. I've tried to work around the problem by having a "keep alive" script checking if the CCPD process is dead and restarting it, but this didn't solve all trouble I had.

I'm encountering daily problems with Firefox and Openoffice: sometimes the printing works, sometimes it doesn't (printer queue stuck), randomly.

Canon is really giving a terrible support to Linux users.

Does anyone knows about an open-source driver that could replace this CCPD crap ?

---

### Post by Uncle Hotte on 2008-11-11
> Problem is, the "source" package doesn't contain ALL the source code but only a small portion of it. The main binaries (like the ccpd daemon) are provided in binary form only (x86). Plus there are a bunch of .BIN files (I guess they're firmware for the printers), also in strictly binary form.

It's true. The driver is not pure open source, but at least it works. So far, I had no problems, but I'm printing not much at the moment.

> Example: just unplug the USB cable and the ccpd daemon will segfault.
I tried this and it works without problems. No segfault, nothing. Which version are you using? 1.70 seems to be the latest and that's what I'm using.

> Does anyone knows about an open-source driver that could replace this CCPD crap ?
Have a look here: [http://www.boichat.ch/nicolas/capt/](http://www.boichat.ch/nicolas/capt/)
It is for another printer but maybe a good starting point...

Cheers

---

### Post by Samir33 on 2008-11-24
Just updated Canon LBP printers info here: [HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900#Compiling the driver (amd64) Steps:"). Feel free to check it out and add extra info...

---

### Post by BatPenguin on 2008-11-29
I'm trying to get my LBP-5100 going, and I ran into the problem that none of these debs seem to work. I get cups errors (header problems etc.) and nothing will print. Probably a bad driver version. I'm using Hardy 32-bit. I followed Uncle Hotte's instructions on trying to compile the 1.70 version (without doing the changes for architecture), but it keeps failing with the following:

```
data_process.c:29:27: error: libxml/parser.h: No such file or directory
data_process.c:30:25: error: libxml/tree.h: No such file or directory
data_process.c:256: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
data_process.c: In function &#8216;XmlToText&#8217;:
data_process.c:315: error: &#8216;xmlDoc&#8217; undeclared (first use in this function)
data_process.c:315: error: (Each undeclared identifier is reported only once
data_process.c:315: error: for each function it appears in.)
data_process.c:315: error: &#8216;pDoc&#8217; undeclared (first use in this function)
data_process.c:316: error: &#8216;xmlNode&#8217; undeclared (first use in this function)
data_process.c:316: error: &#8216;pRoot&#8217; undeclared (first use in this function)
data_process.c:317: error: &#8216;pEntryChildren&#8217; undeclared (first use in this function)
data_process.c:318: error: &#8216;pDesc&#8217; undeclared (first use in this function)
data_process.c:322: warning: implicit declaration of function &#8216;xmlParseMemory&#8217;
data_process.c:323: warning: implicit declaration of function &#8216;xmlDocGetRootElement&#8217;
data_process.c:324: warning: implicit declaration of function &#8216;FindPrtEntryChildren&#8217;
data_process.c:332: error: &#8216;XML_ELEMENT_NODE&#8217; undeclared (first use in this function)
data_process.c:352: warning: implicit declaration of function &#8216;xmlFreeDoc&#8217;
data_process.c:354: warning: implicit declaration of function &#8216;xmlCleanupParser&#8217;
make[3]: *** [data_process.o] Error 1
make[3]: Leaving directory `/home/risto/Downloads/CAPT_Printer_Driver_for_Linux_Src_v170a_uk_EN/src/cndrvcups-capt-1.70/statusui/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/risto/Downloads/CAPT_Printer_Driver_for_Linux_Src_v170a_uk_EN/src/cndrvcups-capt-1.70/statusui'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/risto/Downloads/CAPT_Printer_Driver_for_Linux_Src_v170a_uk_EN/src/cndrvcups-capt-1.70/statusui'
make: *** [build-stamp] Error 2
dpkg-buildpackage: failure: debian/rules build gave error exit status 2
risto@Galactica: 566~/Downloads/CAPT_Printer_Driver_for_Linux_Src_v170a_uk_EN/sr


```

I was hoping there would've been a 32-bit deb somewhere already, but I can't find one. Actually, this Australian site is the only one that I could find having the later version. I've tried both 1.30 and 1.60 debs, and they don't work. I'd really appeciate some help, or if if somebody could be kind enough to compile a 32-bit deb out of the source, that'd be of course even better. I don't know why the compile doesn't work (there were a few problems but I solved them by installing dependencies mentioned, now I'm just not sure what to do). Anybody have any ideas? Thanks.

Edit: In particular, the cndrvcups-common-1.70 pacakge builds fine for me. The message above is from trying to compile the capt driver.

---

### Post by cariboo on 2008-11-29
There are .debs for the OP's printer, plus notes concerning Ubuntu here:

[http://debian.are-ata.org/capt/](http://debian.are-ata.org/capt/)

to BatPenguin:

Unfortunately your printer will not work with Linux see here:

[http://www.openprinting.org/show_printer.cgi?recnum=Canon-LBP-5100](http://www.openprinting.org/show_printer.cgi?recnum=Canon-LBP-5100)

Jim

---

### Post by BatPenguin on 2008-11-30
> **cariboo907 said:**
> 
to BatPenguin:

Unfortunately your printer will not work with Linux see here:

[http://www.openprinting.org/show_printer.cgi?recnum=Canon-LBP-5100](http://www.openprinting.org/show_printer.cgi?recnum=Canon-LBP-5100)

Jim

Thanks for the reply, but actually, it does work. That Openprinting site (I saw it before buying this, too) apparently doesn't consider the Capt driver (maybe for a good reason? :)) 

Anyway, I actually did get this going last night finally. Not by compiling the 1.70 driver but by using the 1.60 debs and following this guide: 

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

When connected locally, the printer works fine now. Really strange that when installing a driver by Canon, you can't just go by what their own documentation says...annoying but good thing there are these how-to's and nice threads like this. But anyway, anybody having problems with 32-bit Hardy and LBP-5100 should just go thorough that how-to's early parts substituting LBP-5100 for the right parts. It works now.

I'm still having problems trying to figure out if I can get this thing to work with my network print server (not a computer but one of those little boxes you can plug parallel and usb printers to). I've been able to use other parallel and USB printers just fine with it before, but because of this frakking capt business, this won't work it the same way that other printers do. In my Canon LaserJet, for example, I can just set the ip address and queue name in System->Administration->Printers and that's it. With the capt stuff, it wont' do. I've tried being creative with the "ccpdadmin -p LBP5100 -o net:192.168.0.2/<queue_name>" command but my understanding at the moment is that this capt thing might understand using a net address but won't take the queue name that my print server needs to distinguish different devices. This is quite off-topic as regards this thread, but if someone has any ideas, I'm all ears.

---

### Post by Uncle Hotte on 2008-12-08
Hello BatPenguin,

I'm glade to hear that you manage to get the 1.60 version running. I found a lot on the Internet that the 1.60 works with Hardy 32-bit. Only 64-bit user have to go the hard way and compile their own 1.70 driver.

But, if you want to upgrade to 1.70, I think you are missing the libxml2 and/or libxml2-dev packages. At least the header files are not found on your machine.

To share the pinter over the network is a completely different story and should have it's own thread. But I'm pretty sure that ccpdadmin is the wrong way. If I understand the docu correct, it's possible to connect the printer by USB or Ethernet. So, Ethernet is only a replacement for USB and not for printer sharing. I would try to setup Cups as a print server.

---

### Post by BatPenguin on 2008-12-17
> **Uncle Hotte said:**
> To share the pinter over the network is a completely different story and should have it's own thread. But I'm pretty sure that ccpdadmin is the wrong way. If I understand the docu correct, it's possible to connect the printer by USB or Ethernet. So, Ethernet is only a replacement for USB and not for printer sharing. I would try to setup Cups as a print server.

Thanks for the reply! Yes, I got it running rather nicely now with the printer connected to another computer via USB and CUPS sharing it to the network. I can print to it fine as long as I have Firestarter off...oddly enough I cannot seem to make printing work with Firestarter on even when allowing all connections or port 631 (which should be enough) to and from the CUPS computer. In any case, that's a separate issue that doesn't have to do with the printer but CUPS/Firestarter, I'll probably post a new thread about it at some point once I have time to research it a bit more. Seems to be a Firestarter problem.

In any case, I found some Canon texts online that said that even under Windows, the sort of 3rd party "print server boxes", that I have, are not supported with these CAPT printers. Canon sells its own little add-on board to turn these printers into network printers (this was something like 150 euros, very steep considering the printer was 350). So yes, sharing through CUPS or maybe Samba is the way to go with these and driver version 1.6 seems to work fine for me (32-bit).

Thanks again for the help.

---

### Post by rocky77 on 2009-03-07
> **Uncle Hotte said:**
> Hi,

I don't know if this is still actual, but finally I got my Canon Printer LBP5100 working and maybe it will you as well.

I am running Kubuntu 8.04 (Hardy Heron) on an AMD64 architecture and I tried everything, I could find to get my printer working, but no luck at all. It seems that all installation guides and 32bit Debian packages for the LBP5100 printer are not working under Hardy 64bit.

Finally, I found the source code of Canon's driver at their Australian web page. It is for a 32bit architecture, but I could patch the package to compile it on my 64bit machine.


According to the driver documentation, this driver should work with the following printers:
    LBP3310
    LBP5100
    LBP5300
    LBP3500
    LBP3300
    LBP5000
    LBP3210
    LBP3000
    LBP2900
    LBP3200
    LBP-1120/1210

Here is my solution to get the LBP5100 working.

1.
```
Get CAPT source code from [http://support-au.canon.com.au/contents/AU/EN/0900772502.html](http://support-au.canon.com.au/contents/AU/EN/0900772502.html)
```

2.Untar it
```
tar xfz CAPT_Printer_Driver_for_Linux_Src_v170a_uk_EN.tar.gz
cd  CAPT_Printer_Driver_for_Linux_Src_v170a_uk_EN/src/
tar xfz cndrvcups-common-1.70-1.tar.gz
tar xfz cndrvcups-capt-1.70-1.tar.gz
```

3.Install required libraries and (development packages) listed in the readme files in cndrvcups-common-1.70 and cndrvcups-capt-1.70
NOTE: libbuftool will be provided by cndrvcups-common

Install packages build-essential and gettext

4.Build cndrvcups-common-1.70
```
cd cndrvcups-common-1.70
Change “Architecture: i386” in debian/control to “Architecture: amd64”
Run dpkg-buildpackage in cndrvcups-common-1.70

The debian package will be placed in CAPT_Printer_Driver_for_Linux_Src_v170a_uk_EN/src
```

5.Install cndrvcups-common
```
sudo dpkg -i cndrvcups-common_1.70-1_amd64.deb
```

6.Build cndrvcups-capt-1.70
```
cd cndrvcups-capt-1.70
Change “Architecture: i386” in debian/control to “Architecture: amd64”
Change “	dh_shlibdeps” in debian/rules to “#	dh_shlibdeps”
Run dpkg-buildpackage in cndrvcups-capt-1.70
```

The debian package will be placed in CAPT_Printer_Driver_for_Linux_Src_v170a_uk_EN/src

7.Install cndrvcups-capt
```
sudo dpkg -i cndrvcups-capt_1.70-1_amd64.deb
```

8.Change /etc/init.d/ccpd to
```
#!/bin/sh
# ccpd startup script for Canon Printer Daemon for CUPS
# Modified for Debian GNU/Linux
# by Raphael Doursenaud <rdoursenaud@free.fr>.
DAEMON=/usr/sbin/ccpd
LOCKFILE=/var/lock/subsys/ccpd
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
NAME=ccpd
DESC="Canon Printer Daemon for CUPS"
test -f $DAEMON || exit 0
case $1 in
start)
echo -n "Starting $DESC: $NAME"
start-stop-daemon --start --quiet --exec $DAEMON
echo "."
;;
stop)
echo -n "Stopping $DESC: $NAME"
start-stop-daemon --stop --quiet --oknodo --exec $DAEMON
echo "."
;;
status)
echo "$DESC: $NAME:" `pidof $NAME`
;;
restart)
echo -n "Restarting $DESC: $NAME"
start-stop-daemon --stop --quiet --oknodo --exec $DAEMON
sleep 1
start-stop-daemon --start --quiet --exec $DAEMON
echo "."
;;
*)
echo "Usage: ccpd {start|stop|status}"
exit 1
;;
esac
exit 0

```

9.Setup the printer
```
sudo /etc/init.d/cupsys restart
sudo /usr/sbin/lpadmin -p LBP5100 -m CNCUPSLBP5100CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
sudo /usr/sbin/ccpdadmin -p LBP5100 -o /dev/usb/lp0
sudo /etc/init.d/ccpd restart

```

Hi,
I have a problem stage 9

```
roque@debian64:~/CAPTDRV160$ /usr/sbin/ccpdadmin -p LBP-810 -o /dev/usb/lp0
/usr/sbin/ccpdadmin: error while loading shared libraries: libcups.so.2: cannot open shared object file: No such file or directory

```

Please help me. I'm under Lenny 64 bits.

Thanks.

---

### Post by stephenr80 on 2009-04-26
same problem here, tried to install with latest version of ubuntu and didn't work. I tried then to install it with 8.10 and didn't work either...

/usr/sbin/ccpdadmin: error while loading shared libraries: libcups.so.2: cannot open shared object file: No such file or directory

I can't also find any cupsys file under /etc/init.d but I've been researching and it looks like after some patch people use now /etc/init.d/cups instead (don't really know the difference)

please help!

---

### Post by stanca on 2009-04-26
TRy using drivers from turboprint.info.
 [http://www.turboprint.info/](http://www.turboprint.info/)

---

### Post by stephenr80 on 2009-04-29
well after some tries, it worked on my Laptop with Xubuntu 8.10, everything seems to be fine to me, my main problem is that in the Guide they never say you have to let the system recognize the printer and then configure it. It didn't work until I tried that. Maybe I'll sort it out and install also in Jaunty.

---

### Post by manolomanolo on 2009-06-12
I followed all the instructions but the printer does not print. I get a notification icon saying everithing is printed correctly but it isn't.

Canon LBP 2900 on Jaunty.
Linux 2.6.28-11-generic on amd64

---

### Post by josipa04 on 2009-07-27
> **manolomanolo said:**
> I followed all the instructions but the printer does not print. I get a notification icon saying everithing is printed correctly but it isn't.

Canon LBP 2900 on Jaunty.
Linux 2.6.28-11-generic on amd64

Same here but for Canon LBP 5000.

Is there any solution?

---

### Post by happ on 2009-07-27
I have Cannon MF 4140 laser printer scanner and fax in one, on Linux Mint Gloria 64. I solved problem with printing, but not with scanning and faxing. For printing: download the package from: [http://software.canon-europe.com/software/0031040.asp](http://software.canon-europe.com/software/0031040.asp).

I chose two rpm_64 packages (common and ufr2-uk) and transform it to deb using alien. Execute two packages. Start printer configuration tool and chose to provide ppd file. Navigate to /usr/share/cups/model and point to file which best fit your printer model. My model is MF 4140, so I chose CNCUPSMF4100ZK.ppd. It works with Intrepid_64 and Jaunty_64, too. Hope it will help you.

As for scanning and faxing I don't need it very frequently, so I installed Windows XP under VirtualBox 3.02. and scan and fax from there.

---

### Post by r0bis on 2009-09-09
Hey, thought this might be of interest. I was so fed up with trying to compile drivers for my Canon LBP5100 on Debian sid amd64, that I went a different route - and so far it is working brilliantly. 

Very briefly - your windows box has a shared virtual postscript printer -> linux box prints on that via Samba -> output from this virtual shared printer is internally redirected via redmon/ghostprint to the actual printer.

You need to set up ghostscript/ghostview (it has ghostprint) on your windows (xp) box. Create a virtual postscript printer there (driver must be the same that you will install on linux; there are plenty of those available). Install redmon; redirect the virtual postscript printer output via ghostprint to your canon printer. Share the postscript printer. Add Samba printer on linux - choose the same driver/.ppd as for your shared virtual printer on windows. Youre set.

[Here]("http://www.debian-administration.org/article/Howto_Canon_LBP_5100_with_Samba_amd64") is full description of the process.

This should work for practically any printer that ghostprint can print to.

---

### Post by AdrianPtchv on 2009-09-09
This issue is getting rather aggravating.
I have bought Canon  LBP3010 yesterday having in mind that Canon claimed they have linux driver.

It was all very fun to find out that after countless struggle, source building installing, reading etc. the printer won't print anything...
I tried Uncle Hotte's method and compiled and installed the drivers but at the stage 9.Setup the printer nothing worked.

sudo /etc/init.d/cupsys restart ---gives:
sudo: /etc/init.d/cupsys: command not found

sudo /etc/init.d/cups restart ---works

In the other commands when I change LBP5110 with LBP3010 the system gives error that could not copy ppd file.
lpadmin: Unable to copy PPD file!

I looked for the ppd in the driver packadge and it was NOT there.

So after all this probably means that the printer has no Linux support right?

This is getting very frustrating since I do not want to use Windows in order to print. I can put it in a virtualbox and try to use it but this would be so clumsy and inelegant decision that I'd rather avoid it.

Please, if someone has any idea of resolving the issue, give it here!

---

### Post by manolomanolo on 2009-09-09
Hi AdrianPtchv

Have you tried to get in contact to Canon support team? Maybe they will help you clirifying the install instructions and possibly modify them in case they where wrong.

You could even pass them a link to this thread... maybe one of them will get in direct contact with the Ubuntu world :)

---

### Post by AdrianPtchv on 2009-09-09
Hi,

I have actually found that there is ppd for it but I have tried so may times different methods that I am afraid I have messed up with the sytem.
Can somebody tell me how can I purge and clean all printer information from Ubuntu in order to start over clean install of the printer?

the output of my ccpdadmin is:

 > CUPS_ConfigPath = /etc/cups/
 LOG Path        = None
 UI Port         = 59787

 Entry Num  : Spooler   : Backend       : FIFO path             : Device Path : Status
 ----------------------------------------------------------------------------
     [0]    : LBP5100   :               :                       : /dev/usb/lp0 : invalid Spool Name
     [1]    : LBP3050   :               :                       : /dev/usb/lp0 : invalid Spool Name
     [2]    : LBP3010   : file          : /dev/null     : /dev/usb/lp0  :


---

### Post by AdrianPtchv on 2009-09-10
After USB cable unplugging and plugging the system somehow found the printer in one moment and printed several pages.
However now the print jobs again are stuck in status "processing".

Maybe the printer URI is not right now? It is usb://Canon/LBP3010/LBP3018/LBP3050 instead of CCP something...?

---

### Post by manolomanolo on 2009-09-10
> However now the print jobs again are stuck in status "processing".
It happens to me too with a Brother DCP-145c.
A workaround is deleting the stuck job, turn the printer off, turn the printer on once again and print the file.

---

### Post by AdrianPtchv on 2009-09-11
Unfortunately this method does not work for me...
It seems that I do have a working driver but some part of the system (probably a setting) is not right. I can not however find a solution so far.

---

### Post by smoothk on 2009-10-06
Hi all!

After some serious pain I was able to make my LBP2900 work on Ubuntu 9.10 amd64 (well, just a test page print as I write, but still :).

I thought I'd share my story here in case anyone needs some info about the latest Ubuntu release and the way it deals with Canon LBP2900.

The bad news is that I wasn't able to compile the drivers from (pseudo)source as explained here: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900")

I was able to compile cndrvcups-common 1.80 ok, but cndrvcups-capt kept giving me errors even though all the dependencies were satisfied.

The good news is that making the already compiled i386 packages work was pretty easy.

I followed the guide linked above and I downloaded the latest 1.80 drivers from the official site.
I also installed every package required by the README files in the Src directories of the two packages (please refer to the guide linked above).

I installed cndrvcups-common with a simple:
```
sudo dpkg -i --force-architecture --ignore-package=libcupsys2 cndrvcups-common_1.80-1_i386.deb 

```

The package libcupsys2 is in fact required but unavailable: its substitute, libcups2 has a virtual package that goes by the name of libcupsys2, but the Canon driver can't get its mind wrapped around the idea, so... ignoring it seems ok since the package contents are (supposedly) actually there but in a different package.

Then, I did pretty much the same with cndrvcups-capt:
```
sudo dpkg -i --force-architecture --ignore-depends=libstdc++5 cndrvcups-capt_1.80-1_i386.deb 

```

Just like above, libstdc++5 has been replaced by ++6, but the Canon drivers doesn't know that.

Finally, I followed the guide for AMD64 with the following instructions:

```
$ sudo /etc/init.d/cups restart
$ sudo /usr/sbin/lpadmin -p LBP1210 -m CNCUPSLBP1210CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
$ sudo /usr/sbin/ccpdadmin -p LBP1210 -o /dev/usb/lp0

$ sudo /etc/init.d/ccpd
```

I tried to print a test page and so far so good: it worked!

Now I'm getting back to work to fix what is mentioned in "Compiling the driver (amd64) Steps".

;)

---

### Post by linxify on 2009-10-10
a Canon LBP2900B on `uname -a`
Linux home-office 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux and followed instructions from [here]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900#Compiling%20the%20driver%20(amd64)%20Steps:")

Printed a test page after step 2. Did not need any additional script/config etc.
:)

---

### Post by notlistening on 2009-11-04
Is this still an issue? I have the 3010 printing fine but i can not get the driver to start using inid.d ccpd will not load correctly. If i start it by from the termial once logged in everything fires up correctly. Any ideas why the inti.d is not working? I am using version 1.80 of the driver and had this working under ubuntu 9.04

---

### Post by rajamohan on 2009-11-05
Hi smoothk,

I had added a thread compiling the driver for see the link below

[html]http://ubuntuforums.org/showthread.php?p=8249954#post8249954[/html]

---

### Post by notlistening on 2009-11-05
I added a guide on the Community Documentation site for using version 1.90 of the driver from Canon. 

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/LBP3010](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/LBP3010)

---


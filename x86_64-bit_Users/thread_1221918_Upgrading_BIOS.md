---
title: "Upgrading BIOS ?"
date: 2009-07-24
forum: x86 64-bit Users
---

### Post by seabiscuit on 2009-07-24
Hi,

I have an Dell XPS15300 system with a Ubuntu32/Ubuntu64 partition.

I needed to upgrade my RAM from 4GB to 8GB. I know that my machine supports 8GB of RAM.

I have tried with the 2 new slots of 4GB and I can't get it past the BIOS. Both my 4 GB sticks work individually and also I can get past BIOS and work OK with 6GB (1 of 2GB and one of 4 GB).

The conclusion was to upgrade the BIOS. I have been to the DELL site to download [http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=19&l=en&s=dhs&catid=1&hidlang=en&hidos=WV64&impid=-1&os=BIOSA&osl=EN&servicetag=B0R6KH1&SystemID=XPS_M1530&TabIndex=](http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=19&l=en&s=dhs&catid=1&hidlang=en&hidos=WV64&impid=-1&os=BIOSA&osl=EN&servicetag=B0R6KH1&SystemID=XPS_M1530&TabIndex=)

and selected category BIOS and as "Operating System" either BIOS or Vista 64 (there are only 3 options vista 32/64 and bios).

What I got on my machine is a file called 1530_A12.EXE.

My question is: How can I run this file or what alternate path should I use to upgrade my BIOS?

so far I tried: 

chmod u+x 1530_A12.EXE 

and when I try to execute I get an error:

sudo ./1530_A12.EXE

run-detectors: unable to find an interpreter for ./1530_A12.EXE 

Please help, as I do not know how can I run such a driver in Ubuntu.

Thank you very much.

---

### Post by John.Michael.Kane on 2009-07-24
Have a read over the below.
[HOWTO: Flash BIOS]("http://ubuntuforums.org/showthread.php?t=318789&highlight=bios")

[http://ubuntuforums.org/showpost.php?p=7588304&postcount=86](http://ubuntuforums.org/showpost.php?p=7588304&postcount=86)

---

### Post by hibliss on 2009-07-24
You can also update from DOS, which can be booted from USB, then you can put the BIOS update file on a CD.

This seems like a decent tutorial -- [http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html]("http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html")

It is not nice of Dell to offer no option of upgrading the BIOS directly from the BIOS.

---

### Post by seabiscuit on 2009-07-24
> **hibliss said:**
> You can also update from DOS, which can be booted from USB, then you can put the BIOS update file on a CD.

This seems like a decent tutorial -- [http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

It is not nice of Dell to offer no option of upgrading the BIOS directly from the BIOS.

There is an option on the download side to choose "Operating System" as BIOS:

[http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=19&l=en&s=dhs&catid=1&hidlang=en&hidos=WLH&impid=-1&os=BIOSA&osl=EN&servicetag=B0R6KH1&SystemID=XPS_M1530&TabIndex=](http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=19&l=en&s=dhs&catid=1&hidlang=en&hidos=WLH&impid=-1&os=BIOSA&osl=EN&servicetag=B0R6KH1&SystemID=XPS_M1530&TabIndex=)

I downloaded the file 1530_A12.EXE and I have this now on my machine. I do not know how to run this file though.

I would bvery much appreciate your help here as I am not an ubuntu expert :(

---

### Post by philcamlin on 2009-07-24
you would have to eiter run it in wine or windows

i wouldent flash your bios in wine though i wouldent trust it 

:(

you can boot one off the cd though cant you 

i used to put it on a usb and boot it :)

---

### Post by hibliss on 2009-07-24
> **seabiscuit said:**
> There is an option on the download side to choose "Operating System" as BIOS:

[http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=19&l=en&s=dhs&catid=1&hidlang=en&hidos=WLH&impid=-1&os=BIOSA&osl=EN&servicetag=B0R6KH1&SystemID=XPS_M1530&TabIndex=](http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=19&l=en&s=dhs&catid=1&hidlang=en&hidos=WLH&impid=-1&os=BIOSA&osl=EN&servicetag=B0R6KH1&SystemID=XPS_M1530&TabIndex=)

I downloaded the file 1530_A12.EXE and I have this now on my machine. I do not know how to run this file though.

I would bvery much appreciate your help here as I am not an ubuntu expert :(

It is the same file no matter which option you pick, the same exe file, which requires Windows or DOS. Did you click the link in my previous post? It tells you what you need to do to create a bootable DOS USB drive.

---

### Post by seabiscuit on 2009-07-24
> **philcamlin said:**
> you would have to eiter run it in wine or windows

i wouldent flash your bios in wine though i wouldent trust it 

:(

you can boot one off the cd though cant you 

i used to put it on a usb and boot it :)

I am really a newbie, and did not really do these type of things before... :(

I would appreciate more detailed instructions.

---

### Post by hibliss on 2009-07-24
There are some very detailed instructions in this thread specific for Dell, or you can use the FreeDOS option -- [http://ubuntuforums.org/showthread.php?t=318789&highlight=bios&page=2]("http://ubuntuforums.org/showthread.php?t=318789&highlight=bios&page=2"). Some reading is required :)

---

### Post by skillllllz on 2009-07-24
Here is a link to the page on the official Dell Linux Wiki which gives instructions on how to update your Dell PC's BIOS, directly from within Ubuntu:

[http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate)


Note: some Dell models do not yet have a BIOS update available which works with this method.

---

### Post by seabiscuit on 2009-07-24
> **skillllllz said:**
> Here is a link to the page on the official Dell Linux Wiki which gives instructions on how to update your Dell PC's BIOS, directly from within Ubuntu:

[http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate)


Note: some Dell models do not yet have a BIOS update available which works with this method.

Hi skillllllz,

great pointer: I followed the instructions there and upgraded to the A12 bios (from A09) from within linux.

I also managed to get my system see the 8GB RAM.

Thanks a lot!

---

### Post by seabiscuit on 2009-07-24
Thanks everybody for your help: this thread helped me to successfully upgrade the bios. Please see above post.

---

### Post by skillllllz on 2009-07-24
> **seabiscuit said:**
> Hi skillllllz,

great pointer: I followed the instructions there and upgraded to the A12 bios (from A09) from within linux.

I also managed to get my system see the 8GB RAM.

Thanks a lot!


It is my pleasure. Information truly is power; I am always happy to share that with others who are willing. :D

---


---
title: "[SOLVED] HDA 32 bit Transfer Mode?"
date: 2007-09-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-09-15
What command will tell me if my Hard Drive is running in 32 bit transfer mode?

If not in 32 bit mode, how do I change it?

---

### Post by bford16 on 2007-09-15
> **crjackson said:**
> What command will tell me if my Hard Drive is running in 32 bit transfer mode?

If not in 32 bit mode, how do I change it?

I think you are looking for the 'hdparm' command.  Here is a link to a web page describing the command and its options.  Be careful.  As the page warns, the command "...can result in filesystem corruption if misued."

[http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=h/hdparm]("http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=h/hdparm")

When I run the command on my drive, I get the result:

IO_support=1 (32 bit)

Good luck!

---

### Post by Kilz on 2007-09-15
> **crjackson said:**
> What command will tell me if my Hard Drive is running in 32 bit transfer mode?

If not in 32 bit mode, how do I change it?

Just a curious question, what is the benefit of running it in 32bit transfer mode?

---

### Post by dcstar on 2007-09-16
> **Kilz said:**
> Just a curious question, what is the benefit of running it in 32bit transfer mode?

Faster performance than 16 bit transfer mode.

Test both (assuming your drive is /dev/hda) with:
```
sudo hdparm -Tt /dev/hda
```

I use "IO_support   =  3 (32-bit w/sync)" myself.

---

### Post by Kilz on 2007-09-16
Thanks for the info, [I found this page]("http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html") which does a good job of explaining it. But for me, all the commands seem to do is slow things down.

---

### Post by crjackson on 2007-09-16
> **dcstar said:**
> Faster performance than 16 bit transfer mode.

Test both (assuming your drive is /dev/hda) with:
```
sudo hdparm -Tt /dev/hda
```

I use "IO_support   =  3 (32-bit w/sync)" myself.

Her is the report from my laptop.  It doesn't seem to clearly indicate which mode I'm in.

[B][SIZE="3"]charles@eMachines-M6809:~$ sudo hdparm -Tt /dev/hda
Password:

/dev/hda:
 Timing cached reads:   928 MB in  2.00 seconds = 463.48 MB/sec
 Timing buffered disk reads:  112 MB in  3.00 seconds =  37.30 MB/sec
charles@eMachines-M6809:~$ 

[/SIZE][/B]

---

### Post by crjackson on 2007-09-16
> **Kilz said:**
> Just a curious question, what is the benefit of running it in 32bit transfer mode?

If working correctly it speeds things up when file transfer demand is high.  Things will feel more responsive under certain conditions.

---

### Post by crjackson on 2007-09-16
Here we go, this is what I was looking for.

[B][SIZE="3"]charles@eMachines-M6809:~$ sudo hdparm -c /dev/hda

/dev/hda:
 IO_support   =  1 (32-bit)
charles@eMachines-M6809:~$[/SIZE][/B]

Thanks for your help.  It's all good now...

---

### Post by crjackson on 2007-09-16
Now this one is the one I'm concerned about.

[B][SIZE="3"]charles@MSI-K8N-Neo4-SLI-Platinum:~$ sudo hdparm -c /dev/sda
Password:

/dev/sda:
 IO_support   =  0 (default 16-bit)
charles@MSI-K8N-Neo4-SLI-Platinum:~$ [/SIZE][/B]

---

### Post by crjackson on 2007-09-16
> **crjackson said:**
> Now this one is the one I'm concerned about.

[B][SIZE="3"]charles@MSI-K8N-Neo4-SLI-Platinum:~$ sudo hdparm -c /dev/sda
Password:

/dev/sda:
 IO_support   =  0 (default 16-bit)
charles@MSI-K8N-Neo4-SLI-Platinum:~$ [/SIZE][/B]


All 4 of my SATA drive on my main system are in 16-bit mode. How do I permanently change this to 32 bit support?

Something in fstab or ment.lst I suppose?

---

### Post by crjackson on 2007-09-16
charles@MSI-K8N-Neo4-SLI-Platinum:~$ sudo hdparm -c1 /dev/sda

/dev/sda:
 setting 32-bit IO_support flag to 1
 HDIO_SET_32BIT failed: Invalid argument
 IO_support   =  0 (default 16-bit)
charles@MSI-K8N-Neo4-SLI-Platinum:~$

---

### Post by crjackson on 2007-09-16
> **crjackson said:**
> [B][SIZE="3"]charles@MSI-K8N-Neo4-SLI-Platinum:~$ sudo hdparm -c1 /dev/sda

/dev/sda:
 setting 32-bit IO_support flag to 1
 HDIO_SET_32BIT failed: Invalid argument
 IO_support   =  0 (default 16-bit)
charles@MSI-K8N-Neo4-SLI-Platinum:~$[/SIZE][/B]

Any takers?

---

### Post by crjackson on 2007-09-16
Even my 2 Optical drives are in 32-bit mode.

What's the deal?  How can I set this for an SATA drive?

[B][SIZE="3"]charles@MSI-K8N-Neo4-SLI-Platinum:~$ sudo hdparm -c1 /dev/hda
Password:

/dev/hda:
 setting 32-bit IO_support flag to 1
 IO_support   =  1 (32-bit)
charles@MSI-K8N-Neo4-SLI-Platinum:~$ sudo hdparm -c1 /dev/hdc

/dev/hdc:
 setting 32-bit IO_support flag to 1
 IO_support   =  1 (32-bit)
charles@MSI-K8N-Neo4-SLI-Platinum:~$[/SIZE][/B]

---

### Post by Yellow Pasque on 2007-09-16
try -c3

>   Query/enable (E)IDE 32-bit I/O support.  A numeric parameter can
              be  used  to  enable/disable  32-bit I/O support: Currently sup&#8208;
              ported values include 0 to disable  32-bit  I/O  support,  1  to
              enable 32-bit data transfers, and 3 to enable 32-bit data trans&#8208;
              fers with a special sync sequence  required  by  many  chipsets.
              The  value  3  works  with  nearly  all 32-bit IDE chipsets, but
              incurs slightly more overhead.  Note  that  "32-bit"  refers  to
              data  transfers  across  a  PCI or VLB bus to the interface card
              only; all (E)IDE drives still have only a 16-bit connection over
              the ribbon cable from the interface card.


---

### Post by crjackson on 2007-09-16
Okay, it seems that SATA drives don't really use the 32-bit setting as it's irrelevant to that type of drive according the the author of hdparm.

I have another system that has an eide drive and it boots to 16-bit mode, but I can change that to 32-bit on the fly using the cli.

Does anyone know how to make that change permanent? I would like it to boot into 32-bit mode when being used by the kids.

Where do I place the command or what does it take to make it stick?

Thanks...

---

### Post by John.Michael.Kane on 2007-09-16
To make edits permanent you have to edit your /etc/hdparm.conf

example hdparm line
hdparm -c 3 /dev/hda

Also hdparm configurations only affect ide devices.

---

### Post by crjackson on 2007-09-16
> **SD-Plissken said:**
> To make edits permanent you have to edit your /etc/hdparm.conf

example hdparm line
hdparm -c 3 /dev/hda

Also hdparm configurations only affect ide devices.

Thanks, that's what I needed to know.  This machine is using an ide drive.  I now have quite a few **uMachines** (pun on **eMachines**) I'm tuning.  Thanks Again...

---


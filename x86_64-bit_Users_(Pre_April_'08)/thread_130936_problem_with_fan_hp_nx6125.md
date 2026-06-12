---
title: "problem with fan hp nx6125"
date: 2006-02-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by bato on 2006-02-15
Hi,

have someone solved the fan problem on hp compaq nx6125??
The fan come up only when processor temperature is very hot. I know that is a kernel bug, but dosen't exist a solution? Is there a command to start fan? I try with acpi -t but it dosen't work, it listed the temperature and the battery charge.

I activeted fan always when AC adaptor is connected by bios but when I disconnected from adaptor the fan dosen't work properly.

Can anyone help me?

---

### Post by alesdoc on 2006-02-17
Hi,

I'm one of thw two guys that have opened the bug-report.

> I try with acpi -t but it dosen't work

This command should work fine. Acpi -t starts the fun only if the temperature goes over 60°...you can try to schedule an operation with crontab:

```
crontab -e
```

Insert this line:

```
*/3 * * * *   /usr/bin/acpi -t > /home/username/test.txt
```

You can check the temperature of the laptop in the fiel test.txt

If you use gnome:

```
sudo apt-get install sensors-applet
```

Start the applet. Set it to check ACPI -> TZ1. If you use sensors-applet you don't need to check the temperature with the crontab.

To check if it works....run...

```
glxgears
```

Ciao

---

### Post by blackwell on 2006-02-17
hi i have one question obout nx6125  
do you use Broadcom wireless device ?

i will be grateful for any ubuntu hardware  support information about nx6125

---

### Post by alesdoc on 2006-02-17
Hi,

my wirelles works....with linuxant...i bought the license....but i read a post in this forum that explain how to have wireless on nx6125 with ndiswrapper.

Now i've to go.

I write you on monday again.

If you want i can give you my contact i a messenger.

Bye

---

### Post by bato on 2006-02-17
Thanks alesdoc!!

I installed sensors-applet and I configured it to launch "acpi -t" command when the processor temperature goes over 60 °C and it works well.


> hi i have one question obout nx6125
do you use Broadcom wireless device ?

i will be grateful for any ubuntu hardware support information about nx6125

Hi blcakwell,
I solved the wireless problem with ndiswrapper:
If you have installed ubuntu amd64 you have to download from [http://support.acer-euro.com/drivers/notebook/ferrari4000.html](http://support.acer-euro.com/drivers/notebook/ferrari4000.html) the "802.11b+g (Broadcom) 3.100.64.0" driver than follow this how-to [http://ubuntuforums.org/showthread.php?t=25683&highlight=HOWTO+wlan]("http://ubuntuforums.org/showthread.php?t=25683&highlight=HOWTO+wlan")

Hope it help you

---

### Post by rocoat82 on 2006-04-15
[QUOTE=bato]
If you have installed ubuntu amd64 you have to download from [http://support.acer-euro.com/drivers/notebook/ferrari4000.html](http://support.acer-euro.com/drivers/notebook/ferrari4000.html) the "802.11b+g (Broadcom) 3.100.64.0" driver than follow this how-to [http://ubuntuforums.org/showthread.php?t=25683&highlight=HOWTO+wlan]("http://ubuntuforums.org/showthread.php?t=25683&highlight=HOWTO+wlan")

Hope it help you[/QUOTE]

Also i've an hp nx6125 and i turned on internet to find the the right distribution of linux to on my laptop (especially for the bugs that afflict the kernel: The first is the annoying double timer interrupt bug (kernel bug #3927). The second is a much more serious ACPI bug (kernel bug #5534), which causes erratic fan behaviour and consequent overheating of the CPU.);

isn't it?

so you advise me to install the last version of ubuntu amd64?

Thanks

---

### Post by hlm_worker on 2006-04-20
Seems that bug fixing attempts are going on...
[http://bugzilla.kernel.org/show_bug.cgi?id=5534](http://bugzilla.kernel.org/show_bug.cgi?id=5534)

---


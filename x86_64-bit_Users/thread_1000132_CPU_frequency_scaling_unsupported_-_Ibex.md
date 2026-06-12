---
title: "CPU frequency scaling unsupported - Ibex"
date: 2008-12-02
forum: x86 64-bit Users
---

### Post by graysky on 2008-12-02
Running Intrepid-amd64 and was attempting to use the Gnome CPU Frequency Scaling applet when it informed me that "CPU frequency scaling unsupported.  You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling."

I know the machine does because it worked fine under Debian/Lenny.  Is there something simple I need to enable or is this a kernel-level thing?

Thanks!

---

### Post by dudumomo on 2008-12-02
Try :
sudo dpkg-reconfigure gnome-applets

---

### Post by graysky on 2008-12-02
I did it, and answered yes to the question about running with root level permissions, but when I load the applet, I get that error.  I don't think the system much less my user is able to use speed step :/

---

### Post by m_l17 on 2008-12-02
Do you have cpufrequtils and sysfsutils installed?

---

### Post by graysky on 2008-12-02
> **m_l17 said:**
> Do you have cpufrequtils and sysfsutils installed?

No, but I just brought them down through aptitude.  

```
~$ cpufreq-info 
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 2:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 3:
  no or unknown cpufreq driver is active on this CPU
```

I have to enable cpu governing somehow..?

---

### Post by m_l17 on 2008-12-02
After I installed cpufrequtils and sysfsutils everything worked. The frequency scaling was set to ondemand.

See if a reboot helps if not try manually:

[http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html]("http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html")

You have to repeat for all cpu cores.

---

### Post by stchman on 2008-12-02
> **graysky said:**
> Running Ibex-amd64 and was attempting to use the Gnome CPU Frequency Scaling applet when it informed me that "CPU frequency scaling unsupported.  You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling."

I know the machine does because it worked fine under Debian/Lenny.  Is there something simple I need to enable or is this a kernel-level thing?

Thanks!

What processor do you have?  Ubuntu Hardy supported frequency scaling OOB with my Athlon 64 and Core2Duo/Core2Quad.

In some Athlon 64 BOIS mobos you need to enable Cool'N'Quiet to get it up and going.

---

### Post by graysky on 2008-12-02
> **stchman said:**
> What processor do you have?  Ubuntu Hardy supported frequency scaling OOB with my Athlon 64 and Core2Duo/Core2Quad.

In some Athlon 64 BOIS mobos you need to enable Cool'N'Quiet to get it up and going.

It's an X3360 and I know it works because Lenny does it just fine... must be something that it has that Ibex is lacking...

---

### Post by graysky on 2008-12-03
When I'm booted into Lenny:

```
$cpufreq-info
cpufrequtils 004: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to cpufreq@lists.linux.org.uk, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 2.40 GHz - 3.40 GHz
  available frequency steps: 3.40 GHz, 3.20 GHz, 2.40 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 2.40 GHz and 3.40 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.40 GHz.
  cpufreq stats: 3.40 GHz:5.90%, 3.20 GHz:0.30%, 2.40 GHz:93.80%  (86)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 2.40 GHz - 3.40 GHz
  available frequency steps: 3.40 GHz, 3.20 GHz, 2.40 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 2.40 GHz and 3.40 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.40 GHz.
  cpufreq stats: 3.40 GHz:1.63%, 3.20 GHz:0.00%, 2.40 GHz:98.37%  (25)
analyzing CPU 2:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 2
  hardware limits: 2.40 GHz - 3.40 GHz
  available frequency steps: 3.40 GHz, 3.20 GHz, 2.40 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 2.40 GHz and 3.40 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.40 GHz.
  cpufreq stats: 3.40 GHz:1.78%, 3.20 GHz:0.00%, 2.40 GHz:98.22%  (29)
analyzing CPU 3:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 3
  hardware limits: 2.40 GHz - 3.40 GHz
  available frequency steps: 3.40 GHz, 3.20 GHz, 2.40 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 2.40 GHz and 3.40 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.40 GHz.
  cpufreq stats: 3.40 GHz:1.86%, 3.20 GHz:0.12%, 2.40 GHz:98.02%  (22)
```

---

### Post by graysky on 2008-12-12
It's been about a week and no solutions in sight.

I noticed that the [color=blue]acpi-cpufreq[/color] driver was active when running Debian/Lenny.  When I attempted to modprobe it under Intrepid, I got the following:

```
$ sudo modprobe acpi-cpufreq
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.27-7-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device
```

I know it's present because:

```
$ locate acpi-cpu
/lib/modules/2.6.27-7-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko
```

Can anyone offer advice for getting it loaded?

Xeon quad-X3360
DFI LT P35-T2R motherboard
Intrepid x86_64

---

### Post by Arup on 2008-12-13
On my Dual quad system, CPU Freq monitor loads normally on my gnome panel and functions fine, default value is on demand and it can be set to conservative or power or powersave, also during heavy loads it indicates full speed function. However if I do cpufreq-info I get a not supported message in terminal. I think in Ubuntu its implemented differently.

---

### Post by graysky on 2008-12-13
Could be because my system is a Xeon X3360 processor... dunno if that's handled differently than a Q9550.  Bottom line is you are able to do that modprobe command, right?

---

### Post by DeMus on 2008-12-13
> **graysky said:**
> Could be because my system is a Xeon X3360 processor... dunno if that's handled differently than a Q9550.  Bottom line is you are able to do that modprobe command, right?

Did you activate the powermanager? Go to:
System - Preference - Session and select Powermanager.
I had this problem once in Hardy Heron 8.04 and somebody told me in this forum to activate the Powermanager. It did the trick.

Success.

DeMus

---

### Post by graysky on 2008-12-13
> **DeMus said:**
> Did you activate the powermanager? Go to:
System - Preference - Session and select Powermanager.
I had this problem once in Hardy Heron 8.04 and somebody told me in this forum to activate the Powermanager. It did the trick.

Thanks for the suggestion - it was enabled.  Since the system can't seem to find the kernel module, I think the problem is much larger than this...

---

### Post by fjgaude on 2008-12-13
Off and on, over the last year or so this cpu freq issue has come up. And a bug report has been issued but given very low priority.

It seems if you overclock a cpu the present freq governor will not work. It works on all my boxes that are not overclocked with 8.10 and 8.04. I mean even the slightest overclocking will cause the governor to not work.

I can't say why the Ubuntu folks have an issue with this when the Debian ones don't.

---

### Post by graysky on 2008-12-13
> **fjgaude said:**
> Off and on, over the last year or so this cpu freq issue has come up. And a bug report has been issued but given very low priority.

It seems if you overclock a cpu the present freq governor will not work. It works on all my boxes that are not overclocked with 8.10 and 8.04. I mean even the slightest overclocking will cause the governor to not work.

I can't say why the Ubuntu folks have an issue with this when the Debian ones don't.

Thanks for the post, I rebooted at stock settings and still nothing is working :(  It has to be a kernel problem.

---

### Post by Arup on 2008-12-13
Is your BIOS showing the temp and volt parameters?

---

### Post by graysky on 2008-12-13
> **Arup said:**
> Is your BIOS showing the temp and volt parameters?

Yeah... again, this works out-of-the-box on Debian/Lenny.

---

### Post by graysky on 2008-12-13
FINALLY!  I figured it out.  I compiled my own kernel based on the Debian/Lenny config file using [these instructions](http://technowizah.com/2005/12/debian-how-to-custom-kernel-compile.html).  Upon rebooting, CPU scaling magically worked with no intervention on my part.  This leads me to conclude that the amd64 kernel for Intrepid is tainted in some fashion such that what I describe in my first post happens!

How can I log this as a bug so the devteam can see it and hopefully fix it?

---

### Post by r m h on 2008-12-13
When I installed 8.10 on a just built super workstation, CPU frequency scaling worked right out of the box.

My super workstation (no OC) has the following parts:
ASUS Rampage II Extreme mainboard
Intel Core i7 2.94GHz 640 CPU (it's a quad core beast with each core hyper-threaded, so linux 'sees' 8 CPUs)
12GB RAM
2 ATI Radeon HD 4850 video cards to drive 4 24" LCDs
3Ware 9650SE with a 6 disk SATA II RAID array

Only when I disabled apic in the BIOS did the CPU frequency scaling fail to function.  When apic was enabled in the BIOS, but I used the grub kernel parameter "noapic", CPU frequency scaling still worked.

YMMV

---

### Post by Arup on 2008-12-13
WOW! thats quite a system, seems like the i7 would match my dual quad core performance and it turns out to be a better value as well. I got 8GB RAM so I can well imagine how 12GB would perform in your system. Dual ATI Radeon is another plus, I have one 4850 dual GPU version, would add the second one by Jan.

---

### Post by graysky on 2008-12-14
> **r m h said:**
> When I installed 8.10 on a just built super workstation, CPU frequency scaling worked right out of the box.

My super workstation (no OC) has the following parts:
ASUS Rampage II Extreme mainboard
Intel Core i7 2.94GHz 640 CPU (it's a quad core beast with each core hyper-threaded, so linux 'sees' 8 CPUs)
12GB RAM
2 ATI Radeon HD 4850 video cards to drive 4 24" LCDs
3Ware 9650SE with a 6 disk SATA II RAID array

Only when I disabled apic in the BIOS did the CPU frequency scaling fail to function.  When apic was enabled in the BIOS, but I used the grub kernel parameter "noapic", CPU frequency scaling still worked.

I dunno what to say... I wonder if the whole problem I'm experiencing is caused by my CPU being a Xeon, not a Q9550?  

@Arup - please stay on topic to help keep the signal-to-noise up.

---

### Post by Arup on 2008-12-14
It could be your particular model of XEON or something in your motherboard BIOS thats preventing lm-sensors from accessing the sensors. I have a ancient dual XEON 450MHz and sensors are all detected by Ubuntu x64.

---

### Post by graysky on 2008-12-14
> **Arup said:**
> It could be your particular model of XEON or something in your motherboard BIOS thats preventing lm-sensors from accessing the sensors. I have a ancient dual XEON 450MHz and sensors are all detected by Ubuntu x64.

lm-sensors can see it just fine, it's the kernel module or something preventing the loading of it that is the cause of this problem.

---

### Post by Robstarusa on 2008-12-19
I have an idea!

With ubuntu stock config, can you do "sort ./.config > ubuntu_config_sorted"

Then do the same for the lenny config.

Can you then do a diff & find out what is different between them ?

Maybe something will stand out.

I know the gutsy kernel bit me.  I had to set CONFIG_SLUB=n to get a lustre "patchless" kernel to work.

Without CONFIG_SLUB disaled, we could regularly crash the entire box by doing a "df" on a lustre (client) mounted filesystem.

---

### Post by Schugy on 2009-01-03
I'm very interested in your kernel config too. I'd thank you for your results a lot.

---

### Post by graysky on 2009-01-04
It's not worth it since enabling some options causing entries for others that aren't present in the original.  The differences are pretty significant and too difficult to understand exactly which options where one and which ones were off.

---

### Post by Schugy on 2009-01-04
I'm currently comparing 
linux-image-2.6.27-1-amd64_2.6.27-1~experimental.1~snapshot.12516_amd64.deb (Lenny)
linux-image-2.6.27-9-generic_2.6.27-9.19_amd64.deb (Intrepid)

and I've seen that Intrepid has a voluntary and Lenny a preemptible kernel.

These are not minor differences and I'd fully understand it if changes in a scheduler or other important components break CPU scaling. I just need to get a AMD64-computer to verify that.

---

### Post by Anubis on 2009-06-03
So much misinformation in these threads. CPU scaling has always worked. Whether it works for you is another issue. I can and always have been able to govern my cpu scaling from the panel with the CPU Freq scaling applet.:D

Well, today after reflashing my BIOS due to Vbox crashing anytime VT is enabled, after restart of the system, the cpu governor plugin I have used since the first iteration of Ubuntu claims that my E8400 does not support scaling, which is totally FALSE. I do not want to reinstall, or switch distros.

---


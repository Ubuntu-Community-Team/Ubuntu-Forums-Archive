---
title: "can vista-32 bit and ubuntu-64 bit be installed on same hard drive"
date: 2008-08-30
forum: x86 64-bit Users
---

### Post by showri on 2008-08-30
I have an hp tablet tx2500z series.I have vista 32bit installed on it and i am trying to install ubuntu 64 bit and have dual OS.My processor is amd turion x2 ultra 64 bit.can I have 32 bit vista and ubuntu 64 bit together or should I have 64 bit vista to install ubuntu 64 bit.I tried to install 64 bit ubuntu  but the laptop keeps shutting down while I start ubuntu 64 bit.it works fine for vista 32 bit.

---

### Post by milton1 on 2008-08-30
vista and ubuntu will operate completely apart from each other. having the 32 bit vista system should not affect your ubuntu install in any way. The shutting down problem is likely a setting issue with ubuntu. Try running one of the live cd's. If it gives the same problem, then there may be some wierd hardware compatibility issue that may need something wierd like a bios update. If the live cd works fine, then it is a setup issue. Have you had a successful install? If not, have you tried the alternate install cd? The alternate install is not as pretty, but it just about always works better.

---

### Post by milton1 on 2008-08-30
An additional question: How are your HDD partitions set up? (size, format, etc.)

---

### Post by showri on 2008-08-30
I tried with live CD but ubuntu 64 would not start.the main ubuntu logo comes for 5 mins and then my laptop shuts down

---

### Post by howlingmadhowie on 2008-08-30
someone told me that if you configure an encrypted partition inside vista, vista will only let you boot it from the microsoft bootloader. this could make dual-booting difficult.

---

### Post by showri on 2008-08-30
160 gb HDD with 10gb for hp recovery and remaing is for OS.It has NTFS partition.

---

### Post by showri on 2008-08-30
> **howlingmadhowie said:**
> someone told me that if you configure an encrypted partition inside vista, vista will only let you boot it from the microsoft bootloader. this could make dual-booting difficult.

so how would you install ubuntu 64 bit and have dual boot with vista 32 bit

---

### Post by milton1 on 2008-08-30
OK, i recommend using the alternate install cd. Also, before trying the install, you will need to setup new partitions for ubuntu. I would go with parted magic live cd to shrink your windows partition, then either setup new partitions manually (ext3 for / and /home, and a swap partition), or let the install cd automatically setup partitions on the free space left over by shrinking your windows partition.

---

### Post by showri on 2008-08-30
i am trying intall ubuntu 64.there are no errors on dvd.i always get this error call critical temperature reached and my laptop shuts down

---

### Post by showri on 2008-08-30
I get this error always.please remove cd from your tray and hit enter.when i press enter my laptop shuts down

---

### Post by milton1 on 2008-08-30
> **showri said:**
> i am trying intall ubuntu 64.there are no errors on dvd.i always get this error call critical temperature reached and my laptop shuts down

Does this happen when running windows? If yes, then you have a hardware problem (anything from busted cooling fan to dust in the heat sink). If no, then something in your bios is having a bit of a snit with the install software.

---

### Post by howlingmadhowie on 2008-08-30
here is the solution to your problem:
[http://ph.ubuntuforums.com/showthread.php?t=845911](http://ph.ubuntuforums.com/showthread.php?t=845911)

basically, you just need to pass the kernel parameter 'acpi=off'

---

### Post by showri on 2008-08-30
the kernel parameter "acpi=off" how can i set this option

---

### Post by howlingmadhowie on 2008-08-30
when the computer starts booting from cd it will give you different boot options. press the e key on the option you want and then edit the boot line that appears to include the phrase "acpi=off"

---

### Post by gali98 on 2008-08-30
See Here for your laptop:

[http://ubuntuforums.org/showthread.php?t=873188](http://ubuntuforums.org/showthread.php?t=873188)

Kory

---


---
title: "unable to boot"
date: 2008-06-19
forum: x86 64-bit Users
---

### Post by emil0r on 2008-06-19
[http://shebang.nu/~emil/error.jpg]("http://shebang.nu/~emil/error.jpg")

That's the error message I get. So far I've ruled out hardware failures since I can access my raid through SystemRescueCD as well as my ethernet card and I'm really stumped as to what it can be. My best guess so far is some kind of driver problem. Any pointers as to what the fault could be would be most welcome.

---

### Post by pixel :-) on 2008-06-20
Kernel panic (at the very bottom of the picture)
Theres a problem at the level of the kernel, this is not good.

It seems that there are problems with raid drivers in linux.The hardware raid ,often,aren't real raids,and that cause problems.[https://wiki.ubuntu.com/Raid]("https://wiki.ubuntu.com/Raid"),go to FakeRaid.

**If it's not it**

It's a new install?Whell sorry,it could be that ubuntu has a fattal bug for your hardware.

Everything was working,you installed the last kernel, and this happened?Restart with an older kernel,in the boot menu.

Your memory is ok?"general protection fault" iplies that memory managment failed, do a mem test,in the boot menu

Did you have a power outage or something?

The live cd works?

try to add more info.

---

### Post by emil0r on 2008-06-20
Ah sorry, probably should've added more info. It's a software raid setup with mdadm. It's detectable and mountable under SystemRescueCD just as the network is. It's LILO that's used and both the normal image and the backup image gives the same fault and I got this fault when I installed the last kernel upgrade. LiveCD works as well (minus being able to mount the partitions, was some bug in the LiveCD kernel that didn't allow that).

Just checked, and the hardware (fake) raid is still turned off in the bios.

Images used are 2.6.22-19-generic and 2.6.22-18-generic (Linux and LinuxOLD).


// Off for the weekend

---


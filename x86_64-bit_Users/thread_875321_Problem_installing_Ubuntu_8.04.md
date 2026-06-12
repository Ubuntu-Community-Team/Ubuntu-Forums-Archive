---
title: "Problem installing Ubuntu 8.04"
date: 2008-07-30
forum: x86 64-bit Users
---

### Post by ludfic on 2008-07-30
Hi

Just downloaded Ubuntu 8.04 LTS Desktop Edition for 64 bit AMD and Intel Computers. I tried to install it on my Dell Inspiron 530 desktop which has the following hardware specs:

Base
Intel® Pentium® Dual-Core E2140 Processor (1.6GHz,800MHz,1MB cache)

Memory
1024MB 667MHz Dual Channel DDR2 SDRAM [2x512]

Video Card
128MB ATI® Radeon™ HD 2400 Pro graphics card

Hard Drive
320GB (7200rpm) Serial ATA/100 Hard Drive with 16MB DataBurst™ cache

I keep getting a command prompt when I boot from the CD. It keeps showing messages about hardware errors and kernel panics. It happens regardless of whether I try to run the OS from the CD or install it.

I used the same CD on my AMD Turion 64 Dell laptop and it ran from the CD without any problems.

I have a suspicion that the version of Ubuntu I downloaded is for AMD processors only, as the image I downloaded is called ubuntu-8.04.1-desktop-**amd64**.iso

Thinking there might be an intel 64bit version as well, I looked for it but couldn't find it.

Could somebody help me out identifying what the problem is?

Thanks

---

### Post by tuxxy on 2008-07-30
the 64bit version available at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

should run on both AMD nad Intel 64bit system,

---

### Post by Sef on 2008-07-31
1) The disk could have gone bad.

2) Your hardware does not support either Ubuntu or GNU/Linux in general.

> Thinking there might be an intel 64bit version as well, I looked for it but couldn't find it.

The intel version is AMD64.  It is called that since AMD came out with it before Intel.

---

### Post by ludfic on 2008-07-31
Thanks for replying.

I am not sure what you mean by 'disk gone bad'. Do you mean the CD ROM or the hard drive?

Regarding hardware, I am sure there are a lot of people out there who have installed Ubuntu 64 bit on a Dell Inspiron 530.

---

### Post by ludfic on 2008-07-31
Hi
Posting a bit more information about this problem:

I insert the CD and get to the boot screen.
Select the option of 'Try Ubuntu without any change to your computer'
This takes me to a command prompt:
---
BusyBox V1.1.3 (Debian...) Built-in shell (ash)

(initramfs)
---
After this, a lot of messages appear, such as:

[201.22...] Hardware Error
[201.22...] CPU0: Machine Check Exception
[201.22...] Kernel panic - not syncing: Machine check

I also tried the advice of another poster on Ubuntu forums by pressing F6 on the boot screen and entering break=top. But this freezes the command prompt, which prevents me from entering the next command he suggests: "modprobe piix"

Anyway, I hope somebody can find the above a bit more helpful and give me some useful advice.

Thanks

---

### Post by xen-uno on 2008-07-31
I could never run the 7.10 Live x64 cd on this machine, but the install via the alternate disk went well. For 8.04, I went with a clean install with the alternate after an on-line 7.10>8.04 upgrade produced a somewhat buggy install.

---

### Post by ludfic on 2008-07-31
Could you tell me what an alternate disk is, and where to get it?

---

### Post by ludfic on 2008-07-31
It's OK. I went to the download page again and there is a check box for alternate download. It says that it's without the graphic installer.

I'll keep you posted on how I get on with the installation. I intend to do a clean install as well.

---

### Post by Sef on 2008-08-01
> It's OK. I went to the download page again and there is a check box for alternate download. It says that it's without the graphic installer.

I'll keep you posted on how I get on with the installation. I intend to do a clean install as well.

It is easy to use.  The only tricky part is if you manually partition.

---

### Post by ludfic on 2008-08-02
Well, I give up. I intalled using the alternate disk. It rebooted into the system. I installed all the updates and restarted. Got the same errors as before. Tried to get back into the system several times afterwards but got the same errors as described before. 

Now I am can't even clean install from the alternate disk anymore.

I am going to return this useless machine and do some research before buying another desktop.

Thanks everyone for replying.

---

### Post by Yellow Pasque on 2008-08-02
Machine check exception sounds like bad RAM or something (CPU/NB/RAM) not receiving enough voltage. Try memtest86 and make sure you reset the BIOS to the defaults.

---


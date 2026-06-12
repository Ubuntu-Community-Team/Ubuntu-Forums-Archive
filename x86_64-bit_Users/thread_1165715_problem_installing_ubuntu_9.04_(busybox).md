---
title: "problem installing ubuntu 9.04 (busybox)"
date: 2009-05-20
forum: x86 64-bit Users
---

### Post by napi1234 on 2009-05-20
hi,

i am new ubuntu user, and i am trying to install ubuntu 9.04 to my amd 2 core 64 bit pc.
i have download the installer from ubuntu website and burn it into cd.
when i start the installation this error occured:

[COLOR=Blue]ata1: softreset failed (device not ready)
modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory
modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory
BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
(initramfs)

[COLOR=Black]so, how do i overcome this problem? can some one give me the solution..

thanks..

[/COLOR][/COLOR]

---

### Post by cholericfun on 2009-05-20
what install are you using (alternate/ desktop)
when you insert the cd do you have the 
"try out ubuntu without installing" option (the LiveCD)

---

### Post by napi1234 on 2009-05-21
hi,
thanks for the reply.. 
yeah.. i`ve try that and the same massage appear..
i am using a desktop installer.
what should i do.

---

### Post by lejuan on 2009-05-21
See [http://ubuntuforums.org/showthread.php?t=1165440](http://ubuntuforums.org/showthread.php?t=1165440) (it is exactly the same problem)

---

### Post by clhsharky on 2009-05-21
Did you burn as ISO

---

### Post by Bonster on 2009-05-21
Had that problem too, to fix it was pretty easy just not obvious. I donno about the CD method, but i used the usb "unetbootin." OK so basically u have to remove the usb/cd out at the ubuntu logo screen and put it back in as fast as u can. That will skip some file that it was trying to load and bypass it then ur in the LIVE cd mode again.

Hope that helps

---

### Post by neylitalo on 2009-05-22
As much as I can't believe it, it worked to remove and re-insert the USB stick when the boot logo appeared. Viva la hack.

---

### Post by rick0713 on 2009-06-04
I can also confirm the inability to install ubuntu 9.04 Gloria. I have tried all the boat options available upon installation.....and all fail the same way. The Busy Box appears and the 'initramfs' prompt appears. The iso image I downloaded was 'ubuntu 9.04-desktop-i386.iso'. My computer is a HP Pavilion with Intel dual 2.4GHZ processors. I have a CD/DVDRW which is from TSST corporation. Its model number is TSSTcorpCDDVDW TS-H653Q. I know this is a X86 64-bit Users forum. I offer this information because it is felt on the 32 bit x86 users as well. Any posting or information as to how to patch this problem would be appreciated.

---

### Post by Bonster on 2009-06-19
> **rick0713 said:**
> I can also confirm the inability to install ubuntu 9.04 Gloria. I have tried all the boat options available upon installation.....and all fail the same way. The Busy Box appears and the 'initramfs' prompt appears. The iso image I downloaded was 'ubuntu 9.04-desktop-i386.iso'. My computer is a HP Pavilion with Intel dual 2.4GHZ processors. I have a CD/DVDRW which is from TSST corporation. Its model number is TSSTcorpCDDVDW TS-H653Q. I know this is a X86 64-bit Users forum. I offer this information because it is felt on the 32 bit x86 users as well. Any posting or information as to how to patch this problem would be appreciated.

Try doing what I said in Post #6

---

### Post by jaf101 on 2009-07-16
Hi,  The advice in #6 worked for me.  I was installing 9.04 (32bit) on a Dell Inspiron 1501.

Thanks!

---

### Post by silverag47 on 2009-07-23
#6 worked for me!!

---

### Post by intel352 on 2009-08-24
post #6 worked for me as well. Using an HP Compaq DX2250, specs here: [http://www.newegg.com/Product/Product.aspx?Item=N82E16883107282](http://www.newegg.com/Product/Product.aspx?Item=N82E16883107282)

UNetBootIn USB method with Ubuntu 9.04

Was able to successfully install Ubuntu after pulling/re-inserting the flash drive.

Does anyone have nay idea what the actual issue is, so that we can just modify the image as needed?

---

### Post by GuavaSauce on 2009-09-05
OMG 8 hours after initial problem i find this and it works (usb method). i swear im almost bald.......funny thing, i had 9.04 install and working fine from a cd, them a CB blew upstairs and then this happend......the funny tricks that gods play on us.

---

### Post by d0.higgs on 2009-10-06
Hi,

I am having this problem on my dell AMD Athlon 64 bit with an NVIDIA card.
I am using a Live CD to install.
I tried many threads and options and I could get no solutions. I am not sure about removing the stick memory advice as I am not using this method.

Any suggestions?

~d

---


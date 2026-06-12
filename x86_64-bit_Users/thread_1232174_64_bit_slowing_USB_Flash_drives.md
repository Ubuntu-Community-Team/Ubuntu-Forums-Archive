---
title: "64 bit slowing USB Flash drives"
date: 2009-08-05
forum: x86 64-bit Users
---

### Post by LordSoretor on 2009-08-05
Hello all. I've seeing this issue for a while now, and finally decided to battle it.

I have Ubuntu 9.04 64bit installed both in my work PC & at home. When I'm copying something to a flash drive, the maximum transfer rate it's about 8 MByte/s, and usually it's about half. Other times it starts at 4 MByte/s and goes down as time passes, even reaching lows of 300 Kbytes/s or so. This is particularly visible with large files (+1GB), and pretty annoying.

Also, when writing on the flash drives, CPU wait tends to go 100%. Sometimes I can see 100% CPU wait when writing to the hard disk too (It's a SATA HD).

I have 2 Kingstons flash drives, 1GB and 8 GB, but I've seen the problem in other drives as well with my computer(s). 

With the same drives on other computers with Ubuntu 9.04 32bit (or other OS) the maximum speed remains constant at about 16 MByte/s, both for writing and reading.

I should say that reading speed is almost constant on my computers, at about 16~18 MByte/s.

Anyway, I really hope someone can lend me a hand solving this.

Thank you.

---

### Post by Arup on 2009-08-05
Go to your BIOS and turn off USB Legacy mode.

---

### Post by LordSoretor on 2009-08-05
Arup, I disabled USB Legacy Support and now it's somewhat faster. Thank you.

Still, the problem remains. At first the speed is 25 MB/s, then as the copy progresses it stabilized at about 4~5 MB/s. The file was 1GB in size.

Below I copy a transcript of the DD command writing to the flash drive. To show how the speed diminishes as the copy goes on.

```
damiana@damiana:~ $ dd if=/dev/zero count=102400w > /media/PEN_8G/testfile-100MB
104857600 bytes (105 MB) copiados, 6,9849 s, 15,0 MB/s

damiana@damiana:~ $ dd if=/dev/zero count=204800w > /media/PEN_8G/testfile-100MB
209715200 bytes (210 MB) copiados, 15,4733 s, 13,6 MB/s

damiana@damiana:~ $ dd if=/dev/zero count=409600w > /media/PEN_8G/testfile-100MB
419430400 bytes (419 MB) copiados, 43,0872 s, 9,7 MB/s
```

---

### Post by Arup on 2009-08-05
> **LordSoretor said:**
> Arup, I disabled USB Legacy Support and now it's somewhat faster. Thank you.

Still, the problem remains. At first the speed is 25 MB/s, then as the copy progresses it stabilized at about 4~5 MB/s. The file was 1GB in size.

Below I copy a transcript of the DD command writing to the flash drive. To show how the speed diminishes as the copy goes on.

```
damiana@damiana:~ $ dd if=/dev/zero count=102400w > /media/PEN_8G/testfile-100MB
104857600 bytes (105 MB) copiados, 6,9849 s, 15,0 MB/s

damiana@damiana:~ $ dd if=/dev/zero count=204800w > /media/PEN_8G/testfile-100MB
209715200 bytes (210 MB) copiados, 15,4733 s, 13,6 MB/s

damiana@damiana:~ $ dd if=/dev/zero count=409600w > /media/PEN_8G/testfile-100MB
419430400 bytes (419 MB) copiados, 43,0872 s, 9,7 MB/s
```


Do you have AHCI mode enabled for your hdd?

---

### Post by darco on 2009-08-05
I too have this issue...I thought it was a bad flash drive since it was fine a few weeks ago. Today I bought another flash drive , 8gig and it is a different brand. I tried to transfer a 4gig file, it was transferring fine until it hit around 780mbs then it slowed to a crawl....usb legacy is off and I do not have ahci enabled on my sata hhd.....

darco

---

### Post by Arup on 2009-08-05
Darco,

Lots are facing this issue, try turning on AHCI and then see if it goes away.

---

### Post by darco on 2009-08-05
> **Arup said:**
> Darco,

Lots are facing this issue, try turning on AHCI and then see if it goes away.

I never knew it was such a huge issue..it was just a coincidence that I saw this thread when I opened up this x64 forum...
I have been reading up on the numerous threads...
just transferred a 4.3g file and it took about 5mins...before it would take longer and the file was incomplete...

d

---

### Post by Arup on 2009-08-05
> **darco said:**
> I never knew it was such a huge issue..it was just a coincidence that I saw this thread when I opened up this x64 forum...
I have been reading up on the numerous threads...
just transferred a 4.3g file and it took about 5mins...before it would take longer and the file was incomplete...

d

Did you turn AHCI on?

---

### Post by LordSoretor on 2009-08-06
Arup, I don't know if AHCI it's enabled on my work PC. I'm pretty sure it isn't at home, because I installed Windows without AHCI support, and if I enable it M$ baby doesn't run.

The work computer is a Lenovo something. I didn't find the AHCI option on the BIOS, just a "SATA 1 configuration" -> Disabled, Compatible of Enhanced. It's on Enhanced now. Is there any command to show if it's enabled or AHCI capable?

You say that if enable AHCI the USB should work OK?

---

### Post by Arup on 2009-08-06
In some cases turning off legacy usb in bios and enabling ahci is helping out the issue. Enhanced should mean AHCI on in most cases.

---

### Post by LordSoretor on 2009-08-10
OK, I enabled AHCI on my home computer and the read from the flash drives is considerably faster.

However, I'm having trouble with my work computer, as I have Legacy USB off, but I've no way to check if AHCI is on or not.

I've been googleing a bit but I can't seem to find how to enable AHCI on Ubuntu.

EDIT: I have installed the mainline kernel 2.6.30-02063004-generic_amd64 and it seems a bit faster somewhat, but it still has drops to 1 MB/s. The only difference is that now it goes back up to 6 or 8 MB/s at times. Before, once the speed started to drop it never recovered.

---

### Post by Arup on 2009-08-11
> **LordSoretor said:**
> OK, I enabled AHCI on my home computer and the read from the flash drives is considerably faster.

However, I'm having trouble with my work computer, as I have Legacy USB off, but I've no way to check if AHCI is on or not.

I've been googleing a bit but I can't seem to find how to enable AHCI on Ubuntu.

EDIT: I have installed the mainline kernel 2.6.30-02063004-generic_amd64 and it seems a bit faster somewhat, but it still has drops to 1 MB/s. The only difference is that now it goes back up to 6 or 8 MB/s at times. Before, once the speed started to drop it never recovered.

AHCI can only be enabled via BIOS.

---

### Post by _khAttAm_ on 2009-08-11
a long active discussion on the issue: [http://ubuntuforums.org/showthread.php?t=1150108](http://ubuntuforums.org/showthread.php?t=1150108)

---

### Post by LordSoretor on 2009-08-11
> **Arup said:**
> AHCI can only be enabled via BIOS.

I know, but I think it's enabled, 'coz my work computer BIOS only has the "Enhanced" option. I want to know if I have to load a kernel module or something like that. To check if my system is using it.

In my home computer, I enabled AHCI and turned off Legacy USB and the transfer is still 16 MB/s read and 8 MB/s write with the flash drives. I guess there's no real change here. I still have to try with another kernel and other distro, probably Debian 5.02 amd64.

---


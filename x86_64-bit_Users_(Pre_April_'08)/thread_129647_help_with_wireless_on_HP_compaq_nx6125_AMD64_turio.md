---
title: "help with wireless on HP compaq nx6125 AMD64 turion"
date: 2006-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by bato on 2006-02-14
Hi everybody,

I have instelled ubuntu-AMD64 on my new hp compaq nx6125 with AMD Turion 64 processor. It works well except for wireless.
I tried with ndiswrapper and windows xp driver for Broadband 802.11 a/g WLAN but it dosen't work. Maybe because windows xp is 32 bit version (and so wlan driver)??

Can anyone help me? 

Sorry for my English

---

### Post by rinch on 2006-02-14
You're right that you need to use the 64-bit driver for your Wireless card.  If I'm right, you have a broadcom card.  So you can download the 64bit drivers for any other laptop which supports that - such as the Acer Ferrari 4000 series.

There is an excellent HOW TO on this here: [http://ubuntuforums.org/showthread.php?t=25683&highlight=HOWTO+wlan]("http://ubuntuforums.org/showthread.php?t=25683&highlight=HOWTO+wlan")

---

### Post by bato on 2006-02-14
ehi Rinch,

you are the man!!!!!! My wireless now works great!
I downloaded windows 64 bit driver [802.11b+g (Broadcom) 3.100.64.0 bit driver] and I follow the how-to.

Thanks a lot friend \\:D/

---

### Post by hlm_worker on 2006-02-14
Hi,
I thought there was a heating issues with the HP nx6125:
[http://http://www.ubuntuforums.org/showthread.php?t=91531&highlight=nx6125]("http://http://www.ubuntuforums.org/showthread.php?t=91531&highlight=nx6125")
[https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6125]("https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6125")
"The fan doesn't come up automatically when the laptop gets too hot."

How did you succeed in installing the ubuntu 64-AMD release (without frying the proc) ?
Regards.

---

### Post by bato on 2006-02-15
I have some problem with fan. It come up automatically when the laptop gets too hot but it starts only when the temperature is very hot and it goes on full throttle while in windows xp the fan come up often and not at full throttle. Seem like windows maintains a costant temperature.

Other problem was gdm not started when I complete the installation, but  I didn't follow the instruction "vga=792 noapic nolapic" at boot. I solved this problem set Option "NoAccel" in Section "Device" of xorg.conf.
I have to try fglrx-driver yet.

---

### Post by bartoszes on 2006-03-29
[QUOTE=bato]ehi Rinch,

you are the man!!!!!! My wireless now works great!
I downloaded windows 64 bit driver [802.11b+g (Broadcom) 3.100.64.0 bit driver] and I follow the how-to.

Thanks a lot friend \\:D/[/QUOTE]

Hi there,
Please tell me, where did you downloaded these drivers. All 64 bit drivers I found so far doesn't work. 
And which ndiswrapper are you using?

Thx for any help.

---

### Post by alesdoc on 2006-03-30
>  have some problem with fan. It come up automatically when the laptop gets too hot but it starts only when the temperature is very hot and it goes on full throttle while in windows xp the fan come up often and not at full throttle. Seem like windows maintains a costant temperature.

Bato...didn't you solve your problem with the fun?

[http://www.ubuntuforums.org/showthread.php?t=130936](http://www.ubuntuforums.org/showthread.php?t=130936)

---


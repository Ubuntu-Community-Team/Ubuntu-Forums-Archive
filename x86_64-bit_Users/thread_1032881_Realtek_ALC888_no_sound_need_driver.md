---
title: "Realtek ALC888 no sound need driver"
date: 2009-01-06
forum: x86 64-bit Users
---

### Post by arionadouble on 2009-01-06
I just recently noticed im getting no sound and can use some help finding the driver for 64-bit

---

### Post by cariboo on 2009-01-07
Are you sure you don't have a driver installed? In a terminal type:

```
sudo lshw -C multimedia
```

and paste the output in your next post. The above command will print out a listing of your sound card including if a driver is installed or not.

Jim

---

### Post by laceration on 2009-01-07
here's how to install Realtek ALC888 sound driver.

At the terminal type 
```
sudo gedit /etc/modprobe.d/alsa-base
```
Provide pw when prompted. Add at the end of file: 
```
options snd-hda-intel model=6stack-dig
```
Save the file. That's it!

---

### Post by firstuser on 2009-10-14
Hi,     Following these instructions, I can find a file alsa-base.conf, but not alsa-base in modprobe.d    Should I create alsa-base?

---

### Post by laceration on 2009-10-14
They are probably the same thing.  Probably changed since this was a few iterations of Ubuntu ago. Try adding it to conf, it won't melt down your computer or anything.

---

### Post by Yellow Pasque on 2009-10-14
The driver is snd-hda-intel; it is pre-installed. All files in /etc/modprobe.d now need .conf on the end per Debian policy.
For the model= keyword it depends on your system. This is the list from ALSA 1.0.21:
```
ALC882/883/885/888/889
======================
  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  arima		Arima W820Di1
  targa		Targa T8, MSI-1049 T8
  asus-a7j	ASUS A7J
  asus-a7m	ASUS A7M
  macpro	MacPro support
  mb5		Macbook 5,1
  mbp3		Macbook Pro rev3
  imac24	iMac 24'' with jack detection
  w2jc		ASUS W2JC
  3stack-2ch-dig	3-jack with SPDIF I/O (ALC883)
  alc883-6stack-dig	6-jack digital with SPDIF I/O (ALC883)
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire	Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  acer-aspire-6530g Acer Aspire 6530G
  acer-aspire-7730g Acer Aspire 7730G
  acer-aspire-8930g Acer Aspire 8930G
  medion	Medion Laptops
  medion-md2	Medion MD2
  targa-dig	Targa/MSI
  targa-2ch-dig	Targa/MSI with 2-channel
  targa-8ch-dig Targa/MSI with 8-channel (MSI GX620)
  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
  lenovo-101e	Lenovo 101E
  lenovo-nb0763	Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky	Lenovo Sky
  haier-w66	Haier W66
  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
  6stack-dell	Dell machines with 6stack (Inspiron 530)
  mitac		Mitac 8252D
  clevo-m720	Clevo M720 laptop series
  fujitsu-pi2515 Fujitsu AMILO Pi2515
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  intel-alc889a	Intel IbexPeak with ALC889A
  intel-x58	Intel DX58 with ALC889
  asus-p5q	ASUS P5Q-EM boards
  mb31		MacBook 3,1
  sony-vaio-tt  Sony VAIO TT
  auto		auto-config reading BIOS (default)
```

---

### Post by grege on 2009-10-18
I have been using an ALC888 for years without having to muck about, the drivers are built in.

No sound does not mean no driver. More often than not it means the wrong options are selected. Usually no sound means digital out is selected, thus muting analog out or PCM volume is set to zero. Unfortunately updates have a bad habit of stuffing settings.

Install Gnome-Alsamixer from Synaptic and experiment with the settings. Play some music and select channels, unmute, raise volumes etc until the sound burst forth.

good luck

---

### Post by Grove on 2009-11-09
> **Temüjin said:**
> The driver is snd-hda-intel; it is pre-installed. All files in /etc/modprobe.d now need .conf on the end per Debian policy.
For the model= keyword it depends on your system. This is the list from ALSA 1.0.21:
```
ALC882/883/885/888/889
======================
  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  arima		Arima W820Di1
  targa		Targa T8, MSI-1049 T8
  asus-a7j	ASUS A7J
  asus-a7m	ASUS A7M
  macpro	MacPro support
  mb5		Macbook 5,1
  mbp3		Macbook Pro rev3
  imac24	iMac 24'' with jack detection
  w2jc		ASUS W2JC
  3stack-2ch-dig	3-jack with SPDIF I/O (ALC883)
  alc883-6stack-dig	6-jack digital with SPDIF I/O (ALC883)
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire	Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  acer-aspire-6530g Acer Aspire 6530G
  acer-aspire-7730g Acer Aspire 7730G
  acer-aspire-8930g Acer Aspire 8930G
  medion	Medion Laptops
  medion-md2	Medion MD2
  targa-dig	Targa/MSI
  targa-2ch-dig	Targa/MSI with 2-channel
  targa-8ch-dig Targa/MSI with 8-channel (MSI GX620)
  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
  lenovo-101e	Lenovo 101E
  lenovo-nb0763	Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky	Lenovo Sky
  haier-w66	Haier W66
  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
  6stack-dell	Dell machines with 6stack (Inspiron 530)
  mitac		Mitac 8252D
  clevo-m720	Clevo M720 laptop series
  fujitsu-pi2515 Fujitsu AMILO Pi2515
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  intel-alc889a	Intel IbexPeak with ALC889A
  intel-x58	Intel DX58 with ALC889
  asus-p5q	ASUS P5Q-EM boards
  mb31		MacBook 3,1
  sony-vaio-tt  Sony VAIO TT
  auto		auto-config reading BIOS (default)
```

thanks m8, that almost did it for my acer aspire 7730z... all i need to do now is figure out how to turn of the metallic buzzing it outputs using 5.1 with my headphones and how to make it really output 5.1 because the only sound i'm getting is only on the main jack.
however it's a start so thanks a lot again.

---

### Post by Grove on 2009-11-09
sidenote: the metallic buzzing was due to the output volume slider being a little over 100% :lolflag:

---


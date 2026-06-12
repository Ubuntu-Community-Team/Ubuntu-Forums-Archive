---
title: "[AirPort] No WPA support?"
date: 2005-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Caesar on 2005-11-16
There is no way to login to a WPA-PSK protected Wi-Fi network?
I only get WEP encryption if try to configure a Wi-Fi network.


:KS  TIA :KS

---

### Post by TimonVO on 2005-11-16
Use the wpa_supplicant package

---

### Post by Caesar on 2005-11-16
I don't know why but when I found that package i thought it was for x86 only.

It looks like this one should work:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=wpasupplicant&searchon=names&subword=1&version=breezy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=wpasupplicant&searchon=names&subword=1&version=breezy&release=all)

Thanks :)

---

### Post by Caesar on 2005-11-17
I'm trying to configure WPA supplicant... does somebody knows what driver should I use for an 802.11b Apple AirPort card? What chipset is used by Apple AP crds? :D (no way to find it via Google)

I' following [this]("http://www.ubuntuforums.org/showthread.php?t=90450&highlight=wpa+breezy") howto but I don't have any **wpa_supplicant.conf** file to edit! I've created a brand new configuration file but I'm not sure if I'm missing something.... anyhelp? Maybe someone could post an example file? :)

:KS TIA :KS

---

### Post by Entity on 2005-11-17
The Airport Extreme is not yet support under linux... I personnally use a PCMCIA wifi card on my Powerbook G4.

---

### Post by Entity on 2005-11-17
[QUOTE=Entity]The Airport Extreme is not yet support under linux... I personnally use a PCMCIA wifi card on my Powerbook G4.[/QUOTE]
This is for Airport Extreme, not old Airport chips

---

### Post by Caesar on 2005-11-27
Yes, my old iBook still uses 802.11b AKA "classic" AirPort (not 802.11g  AKA AirPort Extreme).

I've configured wpa_supplicant but I can't understand why is not working.
What should I check? Is somewhere a log file?

Does somebody know what driver should I use in wpa_supplicant?

---

### Post by ssam on 2005-11-27
```

sam@titania:~$ lsmod | grep airport
airport                 7392  0
orinoco                48308  1 airport
hermes                  8448  2 airport,orinoco

```

so i think that means the diver is orinoco.

---

### Post by Caesar on 2005-11-28
ssam thanks for your help :)

These are the drivers available for WPA_supplicant:
```

  hostap = Host AP driver (Intersil Prism2/2.5/3) [default]
	(this can also be used with Linuxant DriverLoader)
  hermes = Agere Systems Inc. driver (Hermes-I/Hermes-II)
  madwifi = MADWIFI 802.11 support (Atheros, etc.)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wext = Linux wireless extensions (generic)
  ndiswrapper = Linux ndiswrapper
  broadcom = Broadcom wl.o driver
  ipw = Intel ipw2100/2200 driver
  wired = wpa_supplicant wired Ethernet driver
  bsd = BSD 802.11 support (Atheros, etc.)
  ndis = Windows NDIS driver
```

I've tried with hermes but I get an error at boot.
the one working for me the default one (hostap) witch give no errors when booting... but I still can't login into my WPA protected Wi-Fi network.

Any idea of what should I try to fix this iussue?

---


---
title: "HP Scanner 39xx progress install and configure"
date: 2006-06-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by dracan_lin on 2006-06-19
Good morning everyone. I own a HP 3970 Scanjet. I recently switched from M$  64bit Ubuntu and I couldn't get my scanner to work. What I've done so far: 
1. Uninstalled sane
2. downloaded sane source and aplyed the [3970 patch]("http://sourceforge.net/projects/hp3900-series/") and configured and installed sane-backend. 
3. I reeinstalled xsane from the repository
4. running scanimage I got the following ouput 
```
scanimage --list-devices
device `hp3900:libusb:002:003' is a Hewlett-Packard RTS8822 chipset based flatbed scanner
```
5. ```
scanimage --device hp3900:libusb:002:003 > test 
``` my scanner scanned the document and saved.
6. ```
export SANE_DEFAULT_DEVICE=hp3900:libusb:002:003
``` tryed to set the scanner as my primary scanner
7. xsane was still detecting only my tv-tuner (avermedia smthing)
8. sane.d/dll.conf has my scanner listed without a comment #

what did I do wrong?

---


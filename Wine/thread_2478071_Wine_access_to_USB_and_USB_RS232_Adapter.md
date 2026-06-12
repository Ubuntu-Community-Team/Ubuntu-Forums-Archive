---
title: "Wine access to USB and USB RS232 Adapter"
date: 2022-08-16
forum: Wine
---

### Post by dieter-erich on 2022-08-16
Hi,
  I am trying to run two old Win7 programs (Sabsik's cam2com and Hydrotec/bb-sensor's temperature and humidity monitor) via wine from within ubuntu-20.04. Both programs start correctly and show their corresponding GUIs but obviously cannot establish connection to the USB ports (three Olympus cameras) neither to the 4 RS232 ports via a USB > 4x RS232 adapter. Is there any trick to make wine recognize these ports? Everything works well under Windows 10 (set to be compatible with Win7) but I'd like to get rid of Windows altogether. Of note, these cameras are not being recognized by gphoto2. If I understand correctly, the latest version of wine should not need to explicitly define the ports.
Thanks for hints!

---

### Post by QIII on 2022-08-16
I've never explored Wine, but I wonder if [this]("https://wiki.winehq.org/Wine_User%27s_Guide#Serial_and_Parallel_Ports") bit from the Win User's Guide might be of help?

---

### Post by dieter-erich on 2022-08-17
Thanks, I'll try!

---


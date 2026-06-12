---
title: "Nvidia ION"
date: 2009-10-04
forum: x86 64-bit Users
---

### Post by dforstmann on 2009-10-04
I just built an Ion computer and installed Karmic 64bit on it.  I downloaded the 64bit Linux driver filen from Nvidia's website but have no clue how to install it.  Can anyone help me?  I thought I would try this since the Nvidia Graphics driver ver. 185 doesn't seem to work very well.  It cannot save the X11 config & I have to manually reset efter each power cycle.

---

### Post by Arup on 2009-10-04
sudo apt-get install build essential

sudo apt-get remove linux restricted modules

Make sure the driver file is in HOME folder.

Do a ctrl+alt+F2 and this will bring you into text based terminal.

login and do a sudo /etc/init.d/gdm stop

In case you have previously installed nvidia drivers make sure to remove them or do a nvidia-uninstall

After that do a sudo sh NVIDIAxxxxxxxxxx where the x stands for the driver in your HOME folder, you can hit tab after typing in NVIDIA and it will automatically pick up. Your installation process begins and say yes to all, after its done you will be back to the text based terminal, do a sudo reboot and you will have your functional drivers.

Make sure your nvidia driver ends with run2 and not run1.

Good Luck.

---


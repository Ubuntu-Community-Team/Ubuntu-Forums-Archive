---
title: "xserver crashes, cant install"
date: 2007-03-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by eruheru on 2007-03-14
Hey all, I have not been able to install ubuntu on my computer because after the initial load screen red box comes up saying that the xserver crashed. The log on the very bottom says "no screen detected" I really want to get ubuntu working and this problem keeps popping up!
specs:
Graphics: ATI SAPPHIRE Radeon X850XT
CPU: AMD Athlon 64 3800+
mobo: ASUS A8N-E 

If you need any other specs ill be happy to give them. 
Thanks!

---

### Post by teaker1s on 2007-03-14
if installed at grub boot recovery mode, if not install with alternate.iso text install

```
sudo dpkg-reconfigure xserver-xorg
```

if the driver is ati then try changing to vesa which hopefully will give gui

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI?action=show&redirect=BinaryDriverHowto%2Fati]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI?action=show&redirect=BinaryDriverHowto%2Fati")

---

### Post by Ravanous on 2007-03-14
Also try [these instructions]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") for getting the ATI drivers working.

---

### Post by NickK1066 on 2007-03-15
Hmm my X800XL had issues with the live CD for Dapper. In the end I had to install the server version (commandline) and manually install KDE via aptitide.
The problem is that the card identifier returned by the card and the driver mismatch hence it's not detected in the LiveCD.

The X1950XTX was also fun as the driver had to be forced to recognise it as a 1900 series to get OpenGL.

Eitherway the driver installation required the manual version of above to get OpenGL working. The reason was that the standard driver install does not replace the driver in the restricted set - hence the old driver is continued to be loaded on X start up.

---


---
title: "Spore help"
date: 2008-10-01
forum: Wine
---

### Post by superarmy on 2008-10-01
Installed successfully, but when I try run the game the screen goes purple, then black, then back to the desktop in a low resolution, in terminal I get

> fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x93a:0x2621, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer

---

### Post by superarmy on 2008-10-01
Update, I recompiled wine and reinstalled the game, now when I run the game the sounds work but the screen flickers, Spore tab can be seen on desktop in between the flickers, and the entire desktop is unintractable.

---

### Post by superarmy on 2008-10-01
Sorry for the triple post, but scratch the code at the top, as I can't copy the code directly from the terminal as every time I run the game I cant do anything, but amongst the flashes I see, OPERATION INVALID, GL INVALID.

Hope that helps.

---

### Post by the8thstar on 2008-10-01
Windows Game support is not 100% fullproof in Wine. Try to install and run it in Windows if you have it installed on your computer.

---

### Post by superarmy on 2008-10-01
I don't have it installed at the moment, though will probably install it in about a week.

---

### Post by davidryder on 2008-10-01
Is Wine DX9 capable?

---

### Post by superarmy on 2008-10-01
> Is Wine DX9 capable?

I believe so.

---

### Post by superarmy on 2008-10-01
I managed to get the output from terminal

> fixme:thread:SetThreadIdealProcessor (0x98): stub
fixme:thread:SetThreadIdealProcessor (0xa0): stub
fixme:system:SystemParametersInfoW Unimplemented action: 94 (SPI_GETMOUSETRAILS)
fixme:system:SystemParametersInfoW Unimplemented action: 4124 (SPI_GETMOUSESONAR)
fixme:win:EnumDisplayDevicesW ((null),0,0x2fceec0,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3795


---

### Post by superarmy on 2008-10-02
Bump if anyone can find me a workaround for the Terminal output.

---

### Post by the8thstar on 2008-10-04
Try VMWare, VirtualBox or a straight dual-boot. That'll save you unneccessary headaches.

---


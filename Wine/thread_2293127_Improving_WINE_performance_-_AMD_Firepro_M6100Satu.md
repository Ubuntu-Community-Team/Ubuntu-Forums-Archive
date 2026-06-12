---
title: "Improving WINE performance - AMD Firepro M6100/Saturn XT"
date: 2015-09-02
forum: Wine
---

### Post by imrazor on 2015-09-02
When running games under WINE, my Firepro M6100 is generally recognized as a Radeon 5600 Series. This seriously limits performance, and makes games such as Skyrim generally unpleasant to play. I'm currently using Ubuntu 15.04 on a Dell Precision M6600 using the fglrx-updates repository. The date of the installed driver is approx. Feb. 2015. Is there any way to get Wine to detect a better class of Radeon, or load a more current Catalyst driver to improve performance?

---

### Post by QIII on 2015-09-02
*Moved to **Wine***

---

### Post by nargaroth_reg on 2015-09-06
You can try setting the values of the following registry keys located at HKEY_CURRENT_USER\Software\Wine\Direct3D manually:

VideoMemorySize 
VideoPciDeviceID
VideoPciVendorID

You can get the last two values from the output of 'lspci -n'. 
Check [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys) for more info.

---

### Post by imrazor on 2015-10-01
Sorry for the late reply, but for some reason I didn't get a notification. Yes, I've tried setting the PCI device/vendor IDs and manually forcing the VRAM setting. My video adapter is still detected as a Radeon 5600 series...

---

### Post by imrazor on 2015-10-01
Sorry for the late reply, but for some reason I didn't get a notification. Yes, I've tried setting the PCI device/vendor IDs and manually forcing the VRAM setting. My video adapter is still detected as a Radeon 5600 series. Windows detects the card as a Radeon 8950 and performs much better.

I suspect this is a limitation of the fglrx driver (OpenGL revision or somesuch) but I only have my intuition to back me up.

---


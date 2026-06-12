---
title: "Wireless enabled, WiFi icon lit, no wireless networks foud"
date: 2008-07-02
forum: x86 64-bit Users
---

### Post by hobs on 2008-07-02
I recently did a clean install of Ubuntu 8.04 (Hardy) and also set up the KDE 4 desktop on a Dell Vostro 1000 if that changes anything.  Wireless worked for me before the reinstall, but I wanted to get rid of Vista and hopefully get rid of some Ubuntu bugs by doing a clean install.

Once Ubuntu was installed, I opened up Hardware Drivers, checked the box for the Broadcam B43 wireless driver and the firmware, b43-fwcutter, was fetched for me.  Now wireless is enabled and the WiFi icon is lit on my keyboard, but no wireless networks are detected.

I've searched through other posts and most people with 8.04 were able to solve the wireless problems after installing the firmware.  Is there something I'm missing?

Thanks for the help!

---

### Post by ptn107 on 2008-07-08
Make sure the following firmware files exist in the appropriate folders:

/lib/firmware/
bcm43xx_initval05.fw  bcm43xx_microcode11.fw
bcm43xx_initval06.fw  bcm43xx_microcode2.fw
bcm43xx_initval01.fw  bcm43xx_initval07.fw  bcm43xx_microcode4.fw
bcm43xx_initval02.fw  bcm43xx_initval08.fw  bcm43xx_microcode5.fw
bcm43xx_initval03.fw  bcm43xx_initval09.fw  bcm43xx_pcm4.fw
bcm43xx_initval04.fw  bcm43xx_initval10.fw  bcm43xx_pcm5.fw

/lib/firmware/b43/
a0g0bsinitvals4.fw   a0g1initvals13.fw    b0g0initvals4.fw    ucode11.fw
a0g0bsinitvals5.fw   a0g1initvals5.fw     b0g0initvals5.fw    ucode13.fw
a0g0initvals4.fw     b0g0bsinitvals13.fw  lp0bsinitvals13.fw  ucode4.fw
a0g0initvals5.fw     b0g0bsinitvals4.fw   lp0initvals13.fw    ucode5.fw
a0g1bsinitvals13.fw  b0g0bsinitvals5.fw   pcm4.fw
a0g1bsinitvals5.fw   b0g0initvals13.fw    pcm5.fw

/lib/firmware/b43legacy/
a0g0bsinitvals2.fw  a0g1bsinitvals5.fw  b0g0initvals2.fw  ucode11.fw
a0g0bsinitvals5.fw  a0g1initvals5.fw    b0g0initvals5.fw  ucode2.fw
a0g0initvals2.fw    b0g0bsinitvals2.fw  pcm4.fw           ucode4.fw
a0g0initvals5.fw    b0g0bsinitvals5.fw  pcm5.fw           ucode5.fw

If not I can pass them along.

---

### Post by hobs on 2008-07-09
I tried this: [http://ubuntuforums.org/showthread.php?t=759100](http://ubuntuforums.org/showthread.php?t=759100) with no success and it doesn't have all of the files that you listed.

thanks for the help.

---

### Post by ptn107 on 2008-07-13
If you still need the firmware here's the file:
[http://www.flipdrive.com/fileops.php?download=bcm43xx_firmware.tar.gz](http://www.flipdrive.com/fileops.php?download=bcm43xx_firmware.tar.gz)

Unzip to /lib/firmware/

---


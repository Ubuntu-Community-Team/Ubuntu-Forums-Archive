---
title: "64 bit skype is now available!"
date: 2009-08-28
forum: x86 64-bit Users
---

### Post by rajeev1204 on 2009-08-28
Hi

A new version as you all know probably by now is available for skype.2.1 beta.

Its a 64 bit (or rather a 32 bit with some wrapper maybe).

---

### Post by nwadams on 2009-08-28
yay. and it fixes my pulseaudio audio lag issue.

---

### Post by benmoran on 2009-08-28
It works great for me so far! Im also wondering if it's a true 64-bit package this time, or just another wrapped 32-bit app? Probably the latter... oh well. Hopefully one of these days we can enjoy the skype protocol in something like Pidgin or Empathy :guitar:

---

### Post by madmetal on 2009-08-28
> **benmoran said:**
> It works great for me so far! Im also wondering if it's a true 64-bit package this time, or just another wrapped 32-bit app? Probably the latter... oh well. Hopefully one of these days we can enjoy the skype protocol in something like Pidgin or Empathy :guitar:

if you download the .deb you will find out it depends on 32bit libraries so something in the middle , a 32bit application that works fine at 64bit..
sms welcomed as well :)

---

### Post by Yellow Pasque on 2009-08-28
It's still a 32-bit program, but as long as it works..

```
/usr/bin$ ldd skype 
	linux-gate.so.1 =>  (0xf7f27000)
	libasound.so.2 => /usr/lib32/libasound.so.2 (0xf7e28000)
	libXv.so.1 => /usr/lib32/libXv.so.1 (0xf7e22000)
	libXss.so.1 => /usr/lib32/libXss.so.1 (0xf7e1d000)
	librt.so.1 => /lib32/librt.so.1 (0xf7e14000)
	libQtDBus.so.4 => /usr/lib32/libQtDBus.so.4 (0xf7da2000)
	libQtGui.so.4 => /usr/lib32/libQtGui.so.4 (0xf7404000)
	libQtNetwork.so.4 => /usr/lib32/libQtNetwork.so.4 (0xf72ee000)
	libQtCore.so.4 => /usr/lib32/libQtCore.so.4 (0xf70b9000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf709f000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf6fac000)
	libm.so.6 => /lib32/libm.so.6 (0xf6f84000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf6f58000)
	libc.so.6 => /lib32/libc.so.6 (0xf6e00000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf6dfb000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf6ccc000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf6cbc000)
	/lib/ld-linux.so.2 (0xf7f28000)
	libQtXml.so.4 => /usr/lib32/libQtXml.so.4 (0xf6c79000)
	libaudio.so.2 => /usr/lib32/libaudio.so.2 (0xf6c5f000)
	libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf6c37000)
	libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf6bb7000)
	libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf6b70000)
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf6b67000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf6b4c000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf6b36000)
	libglib-2.0.so.0 => /usr/lib32/libglib-2.0.so.0 (0xf6a71000)
	libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf6a66000)
	libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf6a39000)
	libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf6a33000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf6a15000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf6a11000)
	libXt.so.6 => /usr/lib32/libXt.so.6 (0xf69bd000)
	libpcre.so.3 => /lib32/libpcre.so.3 (0xf698b000)
	libuuid.so.1 => /lib32/libuuid.so.1 (0xf6986000)
	libexpat.so.1 => /usr/lib32/libexpat.so.1 (0xf695f000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf695a000)
```

---

### Post by Jazmac on 2009-08-29
I just downloaded the .deb and it was done.  The original instructions didn't work for me.

-Jazmac

---

### Post by wolf4914 on 2009-08-29
My microphone does not work on Jaunty on a test call. Did not try the actual call yet. Had to purge remove previous version for new beta install to work. Have to check on the microphone issue now

---


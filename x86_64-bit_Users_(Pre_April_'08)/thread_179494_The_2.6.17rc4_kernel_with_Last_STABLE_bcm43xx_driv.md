---
title: "The 2.6.17rc4 kernel with Last STABLE bcm43xx driver"
date: 2006-05-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tsai Dung-Bang on 2006-05-20
As far as we know, in dapper, the kernel 2.6.15 has a unstable bcm43xx driver.
So I decide to make a deb kernel image. This kerenl has last driver, and it's more
stable than old one. Such as WEP, reconnect, etc is woring perfect.

Note that this kerenl is only for ibook g4, due to that I reduce lots of options that I do not need.


[http://www.cqis.ncku.edu.tw/~dbtsai/kernel-headers-2.6.17-rc4ibookg4_1_powerpc.deb]("http://www.cqis.ncku.edu.tw/~dbtsai/kernel-headers-2.6.17-rc4ibookg4_1_powerpc.deb")
[http://www.cqis.ncku.edu.tw/~dbtsai/kernel-image-2.6.17-rc4ibookg4_1_powerpc.deb]("http://www.cqis.ncku.edu.tw/~dbtsai/kernel-image-2.6.17-rc4ibookg4_1_powerpc.deb")

---

### Post by benoitc on 2006-05-20
[QUOTE=Tsai Dung-Bang]As far as we know, in dapper, the kernel 2.6.15 has a unstable bcm43xx driver.
So I decide to make a deb kernel image. This kerenl has last driver, and it's more
stable than old one. Such as WEP, reconnect, etc is woring perfect.

Note that this kerenl is only for ibook g4, due to that I reduce lots of options that I do not need.


[http://www.cqis.ncku.edu.tw/~dbtsai/kernel-headers-2.6.17-rc4ibookg4_1_powerpc.deb]("http://www.cqis.ncku.edu.tw/~dbtsai/kernel-headers-2.6.17-rc4ibookg4_1_powerpc.deb")
[http://www.cqis.ncku.edu.tw/~dbtsai/kernel-image-2.6.17-rc4ibookg4_1_powerpc.deb]("http://www.cqis.ncku.edu.tw/~dbtsai/kernel-image-2.6.17-rc4ibookg4_1_powerpc.deb")[/QUOTE]

That's pretty cool :) Could you also provide sources ? I would help us :) Thanks for advance :)

---

### Post by Tsai Dung-Bang on 2006-05-21
Well, the source code is from [www.kernel.org](www.kernel.org). So just download it, and compile it.

But it's a topic that how to setup the config file, you may wnat to extract the deb file, and find the .config file.

And then, I just do that

 make-kpkg --initrd --revision=1 --append-to-version=ibookg4 kernel_image kernel_headers


So if you wnat compile your one, use the source code from kernel.org, and use my config file, you could have your one.

---

### Post by benoitc on 2006-05-21
[QUOTE=Tsai Dung-Bang]Well, the source code is from [www.kernel.org](www.kernel.org). So just download it, and compile it.

But it's a topic that how to setup the config file, you may wnat to extract the deb file, and find the .config file.

And then, I just do that

 make-kpkg --initrd --revision=1 --append-to-version=ibookg4 kernel_image kernel_headers


So if you wnat compile your one, use the source code from kernel.org, and use my config file, you could have your one.[/QUOTE]

Do you have yet support for usplash at startup ? I thought a patch was needed for that?
[QUOTE=Ptero-4]Try this. Install Apple's X11 on your OSX. Run it, and then try and locate the Xf86Config-4 file (I know it's Xfree86, but the basic info is still in a usable format to copy to your ubuntu xorg.conf file) and copy it to your ubuntu home dir (from within ubuntu offcourse) and finally copy over the required parts to your xorg.conf, save it and reload X11. It should run with the settings that Apple's X11 takes from OSX.[/QUOTE]

---

### Post by shorty0927 on 2006-05-22
Thanks for sharing your kernel, Tsai!  I had started building my own, but was having problems with it.  So far, the kernel is working in my Powerbook G4--I'll have to check  your kernel config to see if there's anything I would want to add for my setup.

The BIG question is: did you have to do anything else to get your wireless to work?  I see that softmac and bcm43xx are in the kernel already--did you still have to use fwcutter?

---

### Post by Tsai Dung-Bang on 2006-05-22
Yes, I still need to use the fwcutter to obtain firmware.

The only different between dapper's driver and 2.6.17-rc4's is the latter one is more stable.

So the way to get the wireless working while using my kernel is the same with dapper one.

 Dung-Bang

[QUOTE=shorty0927]Thanks for sharing your kernel, Tsai!  I had started building my own, but was having problems with it.  So far, the kernel is working in my Powerbook G4--I'll have to check  your kernel config to see if there's anything I would want to add for my setup.

The BIG question is: did you have to do anything else to get your wireless to work?  I see that softmac and bcm43xx are in the kernel already--did you still have to use fwcutter?[/QUOTE]

---


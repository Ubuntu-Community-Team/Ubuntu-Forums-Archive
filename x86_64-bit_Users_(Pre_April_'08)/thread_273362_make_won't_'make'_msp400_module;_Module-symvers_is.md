---
title: "make won't 'make' msp400 module; Module-symvers is missing"
date: 2006-10-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by wgaprotest on 2006-10-07
I've been at this for 2 days, and despite all the wonderful help from the irc channel, it seems no one can help me. Now I have made some progress in trying to follow the dyams howto (skiping over to his 4.0 ivtv driver section when warned by him) word for word, and even skipped over to allthepcman's modified section for of the dhyams howto for my dapper installation, and used the downloaded files they mentioned, and used the downloads/howto/troubleshooting sections and drivers from ivtvdriver.org. The ivtv drivers I'm using are 0.4.7.

Absolutely nothing works on one problematic file: msp3400. That module just will not let itself be built during the 'make' because of a repeated error message: 

WARNING: Symbol version dump /usr/src/linux-source-2.6.15/Module.symvers
           is missing; modules will have no dependencies and modversions.

My full kernel is 2.6.15-27-amd64-k8, and although I do have other older kernels, there's nothing older than 2.6.15. 

Other error messages I get subsequent to the make include "no version for "struct_module" found: kernel tainted." just before the start ivtv init section, inside the section it's "msp3400: disagrees about version of symbol struct_module" and "msp3400 not loaded" inside the ivtv init. 

Everything else is fine. the card is detected & loaded, However, I get no audio or video at all, not even a signal. 

Please help!!! Following the howtos word-for-word has been tried (dhyams had one typo in a tar.gz extension, and I even tried that!), skipping to newer drivers has been tried...no joy.

Quick update: I found out that Module-symvers was in an old kernel directory, copied it to the right one for the make, and gone through the whole process again. I don't get the Warning message during the make anymore, but that msp3400 module is still not being built. when i get to the start-ivtv-init string I am still getting the same error messages within that section, and msp3400 still "disagrees..."

---


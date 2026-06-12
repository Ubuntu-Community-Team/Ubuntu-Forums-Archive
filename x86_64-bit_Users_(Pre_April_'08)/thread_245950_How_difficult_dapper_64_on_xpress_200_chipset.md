---
title: "How difficult: dapper 64 on xpress 200 chipset?"
date: 2006-08-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by rcd412 on 2006-08-28
I am setting up a server with a dfi infinity rs482 mobo and i am wondering if that will make things difficult. Does anyone know how hard it is to get this xpress 200 integrated video working? I just need minimal video... IE i don't want to be stuck to the console. Any thoughts anyone?

---

### Post by Kilz on 2006-08-28
> **rcd412 said:**
> I am setting up a server with a dfi infinity rs482 mobo and i am wondering if that will make things difficult. Does anyone know how hard it is to get this xpress 200 integrated video working? I just need minimal video... IE i don't want to be stuck to the console. Any thoughts anyone?

I have a emachine t6524 with the radon express 200. I have 64bit Ubuntu running fine. I do reccommend staying away from the 8.25.18 drivers currently in the repositories as there is a bug with them that causes a crash when turning the computer off. It will hang at a black screen.
I totaly recommend using the [8.26.18 drivers]("https://support.ati.com/ics/support/KBAnswer.asp?questionID=22597") and using [this howto to install it]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2"). There are newer drivers (8.27.10 and 8.28.8 ) but for some reason they will not enable 3d acceleration.

---

### Post by rcd412 on 2006-08-28
thanks i will deffinitly use that driver, hopefully there will be no problems then.

---

### Post by tomdkat on 2006-08-28
I also have an eMachines machine with the ATI XPRESS 200 adapter and I followed Kilz' instructions and they worked flawlessly. :)

Peace...

---

### Post by rcd412 on 2006-08-29
it worked perfectly thank you very much :)

---

### Post by Kilz on 2006-08-29
> **rcd412 said:**
> it worked perfectly thank you very much :)

Your welcome, always happy to save someone else the headache I went through. There are two things you have to know, the next time the kernel is updated you have to enter these commands and then reboot.
```
sudo module-assistant prepare
sudo module-assistant update 
sudo module-assistant build
sudo module-assistant install fglrx 
sudo depmod
```
Also some screen savers may run a little slow because they use hardware acceleration. But if your like me and turn off your monitor, you will never notice it.

---


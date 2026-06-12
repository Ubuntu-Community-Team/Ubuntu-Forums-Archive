---
title: "Compiz fusion shadow not working?"
date: 2008-04-25
forum: x86 64-bit Users
---

### Post by Julius on 2008-04-25
I have successfully installed ubuntu x64 on my PC, nvidia restricted drivers allowed beryl to work (and it works), however, the shadow on the windows and the menus doesn't show at all.


Anybody else experiencing this? 

Specs:
Intel q6600. Mobo: Asus p5k-e
Graphics card: nVidia 8800GT 512mb

---

### Post by Netsurfer on 2008-04-26
> **Julius said:**
> I have successfully installed ubuntu x64 on my PC, nvidia restricted drivers allowed beryl to work (and it works), however, the shadow on the windows and the menus doesn't show at all.


Anybody else experiencing this? 

Specs:
Intel q6600. Mobo: Asus p5k-e
Graphics card: nVidia 8800GT 512mb

Give a look at [http://ubuntuforums.org/showthread.php?p=4799886#post4799886](http://ubuntuforums.org/showthread.php?p=4799886#post4799886)

Try to install (via Synaptic) xserver-xgl. That was good for me.:)
Bye

---

### Post by WakkiTabakki on 2008-04-27
This is apparently a known bug for nvidia 8-series cards. This did it for me:
[http://ubuntuforums.org/showpost.php?p=4803702&postcount=3](http://ubuntuforums.org/showpost.php?p=4803702&postcount=3)

/N

---

### Post by Julius on 2008-04-27
> **WakkiTabakki said:**
> This is apparently a known bug for nvidia 8-series cards. This did it for me:
[http://ubuntuforums.org/showpost.php?p=4803702&postcount=3](http://ubuntuforums.org/showpost.php?p=4803702&postcount=3)

/N

Awesome, thanks! I knew about the bug, and apparently some people were fixing it by manually installing the nvidia drivers, but this is easier and has worked like a charm :D

---


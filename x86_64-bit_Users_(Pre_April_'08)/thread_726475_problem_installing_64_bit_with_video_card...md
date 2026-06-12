---
title: "problem installing 64 bit with video card.."
date: 2008-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mia_tech on 2008-03-16
I've been trying to install ubuntu 64 bit version, but I get a video not supported error when booting from the live cd, my card is a " VIA/S3G UniChrome Pro IGP".. integrated on MB; however, when I boot with the 32 bit version I get all the way to the gui, has anyone come up with this problem or has any advise on the matter

thanks

---

### Post by prince_niceguy on 2008-03-16
there seems to be some problem with the 64 bit install. try using the alternate cd for doing the install and then you should be able to login after the install is done.

---

### Post by Mia_tech on 2008-03-16
> **prince_niceguy said:**
> there seems to be some problem with the 64 bit install. try using the alternate cd for doing the install and then you should be able to login after the install is done.

would I be able to install ubuntu-desktop then?...

thanks

---

### Post by prince_niceguy on 2008-03-16
the alternate cd is similar to the normal cd the only diference is it is text based installer. once install is done it would be as if you have used the normal cd t install the system. you will have the ubuntu-desktop already installed after that.

---

### Post by Kilz on 2008-03-16
> **Mia_tech said:**
> would I be able to install ubuntu-desktop then?...

thanks

Yes, the live cd only has the most common video drivers on it because of limited space, only so much fits on a cd. Install in text mode using the alternate cd.

---

### Post by Mia_tech on 2008-03-17
> **Kilz said:**
> Yes, the live cd only has the most common video drivers on it because of limited space, only so much fits on a cd. Install in text mode using the alternate cd.

ok, I have finally installed the 64 bit version of ubuntu, using the alternate cd, now how would I know I'm running 64, is there anywhere in ubuntu desktop I can find something that says that?

thanks

---

### Post by prince_niceguy on 2008-03-17
run the command 

```
uname -a
```

it should give output like

> Linux  2.6.24-12-generic #1 SMP Wed Mar 12 22:31:43 UTC 2008 x86_64 GNU/Linux


if there is a x86_64 then it is 64 bit.

---

### Post by Mia_tech on 2008-03-17
> **prince_niceguy said:**
> run the command 

```
uname -a
```

it should give output like



if there is a x86_64 then it is 64 bit.

is the "Linux 2.6.24-12-generic" the kernel version?

thanks

---

### Post by prince_niceguy on 2008-03-17
yes it is. i am using hardy though, so it would be a little higher version compared to the one in gutsy.

---


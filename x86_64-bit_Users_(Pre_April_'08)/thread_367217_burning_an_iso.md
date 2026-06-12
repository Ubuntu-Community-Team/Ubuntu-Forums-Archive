---
title: "burning an iso"
date: 2007-02-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by REXXER on 2007-02-21
Hi, im using xubuntu  64 bit, and i want to burn an iso, but its not letting me, i want to burn kubuntu 64bit please help.

---

### Post by invalid on 2007-02-21
What do you mean it is "not letting" you. Are you getting errors from some application?

---

### Post by REXXER on 2007-02-21
no, it just starts to burn, but it completes to fast, and doesn't work

---

### Post by Kilz on 2007-02-21
> **REXXER said:**
> no, it just starts to burn, but it completes to fast, and doesn't work

What are you using to burn the CD?

---

### Post by REXXER on 2007-02-21
im using the program that came with xubuntu called xfburn

---

### Post by Kilz on 2007-02-21
> **REXXER said:**
> im using the program that came with xubuntu called xfburn

Have you checked the md5sum of the image you are burning?

---

### Post by Hendrixski on 2007-02-21
Yeah, it's really important to check that the DL was coret, that's where the m5 checksums come in.  You can check them through a plugin with firefox, or other means... there's a manual somewhere.

---

### Post by REXXER on 2007-02-21
how do i check the md5sum??

---

### Post by REXXER on 2007-02-21
nvm, i checked the md5sum, and it is correct

---

### Post by Kilz on 2007-02-21
> **REXXER said:**
> nvm, i checked the md5sum, and it is correct

Have you tried to use another burning application. k3b is good and should be available in the xubuntu repositories.

---

### Post by REXXER on 2007-02-21
no, im gonna see if i can get it

---

### Post by REXXER on 2007-02-21
TY, i tried using k3b, and it works, tyvm!!!!!

---

### Post by Kilz on 2007-02-21
> **REXXER said:**
> TY, i tried using k3b, and it works, tyvm!!!!!

Your welcome, k3b is one of the best burning applications for linux imho, glad it worked.

---

### Post by REXXER on 2007-02-21
now my problem is that when i try to install kubuntu. I boot from the disk, i choose "start or install kubuntu" and it says loading, but never loads past that????? HELP

---

### Post by REXXER on 2007-02-21
the reason i want to install kubuntu 6.10, is cause i installed xubuntu 6.06 and didnt like it as much as kubuntu (i used it on my old laptop)

---

### Post by Kilz on 2007-02-21
> **REXXER said:**
> the reason i want to install kubuntu 6.10, is cause i installed xubuntu 6.06 and didnt like it as much as kubuntu (i used it on my old laptop)

If you are installing the 64bit version you may want to use the alternate install cd. The desktop one sometimes has problems. You could also just install the kde desktop to your present install, just open a terminal and type this in.

```
sudo aptitude install kubuntu-desktop
```

Then when you boot it will add kde to the possible sessions you can use at the login screen.

---

### Post by REXXER on 2007-02-21
i am trying to dl the kubuntu and the ubuntu alternate 64bit iso, but it says it will take about 250-300 hours each, is that normal?

---

### Post by Kilz on 2007-02-21
> **REXXER said:**
> i am trying to dl the kubuntu and the ubuntu alternate 64bit iso, but it says it will take about 250-300 hours each, is that normal?

No, sounds like you have a busy mirror, try another one.

---

### Post by andrew.46 on 2007-03-30
Hi Rexxer,

 I have had the same problem with xfburn:

> **REXXER said:**
> im using the program that came with xubuntu called xfburn

 Turns out the edgy version is borked. I downloaded Gnomebaker and all was well. Confirms my idea of moving to mainstream Ubuntu shortly, I can't believe that a troubled program like this sits unfixed in the repos.

                               Andrew

---


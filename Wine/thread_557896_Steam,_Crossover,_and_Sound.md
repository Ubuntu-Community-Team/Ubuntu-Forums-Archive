---
title: "Steam, Crossover, and Sound"
date: 2007-09-23
forum: Wine
---

### Post by Ant1jr on 2007-09-23
Help, I've gotten steam to work in crossover office, and even got team fortress 2 up and running, but I don't have sound! What should I do?

---

### Post by GavinZac on 2007-09-23
steam works fine for me, in WINE

---

### Post by Sockerdrickan on 2007-09-23
Yes but he wants sound.

---

### Post by Ant1jr on 2007-09-23
team fortress 2 doesnt even launch in wine, it instantly crashes. css works, but yet no sound.

---

### Post by Ant1jr on 2007-09-23
got sound working in css with wine, but tf2 still doesnt launch. Also css looks like pure **** lighting wise and it crashed after a few minutes

---

### Post by Sockerdrickan on 2007-09-23
Hm what version of WINE

---

### Post by quadomatic on 2007-09-23
Are you using OSS for your sound driver, or ALSA?

ALSA doesn't work (well or at all?) with CS:S.

---

### Post by Ant1jr on 2007-09-23
alsa, where can i get OSS?

---

### Post by quadomatic on 2007-09-23
> **Ant1jr said:**
> alsa, where can i get OSS?

You should just be able to run "winecfg" in the terminal. Then, open up the "Audio" tab. Uncheck the ALSA driver, and check OSS Driver.

Good luck, and I hope this helps!

---

### Post by Ant1jr on 2007-09-23
no sound when I do that

---

### Post by quadomatic on 2007-09-23
> **Ant1jr said:**
> no sound when I do that

Well, try following this guide:

[http://appdb.winehq.org/appview.php?iVersionId=3731](http://appdb.winehq.org/appview.php?iVersionId=3731)

If it still doesn't work, submit a bug and application data.

UPDATE: Hmm, looks like you're not the only one having this problem

[http://ubuntuforums.org/showthread.php?p=3405536#post3405536](http://ubuntuforums.org/showthread.php?p=3405536#post3405536)

---

### Post by Ant1jr on 2007-09-23
no good,

on the second link he doesnt have sound at all, even with alsa. I have sound with alsa but its ****.

---

### Post by placebo0815 on 2007-12-21
Hello,

I first got no sound in steam and steam apps. Afer I ran Crossover Office, I had no any system sounds.

Here is what I did:

in /home/youruser/cxoffice/bin
'click' cxsetup
then you see some entries of applications/games installed
click steam and 'configure'
there is something like 'load sound drivers' - and for me it was empty
--> click change
I have ALSA enabled first, so I put in first ALSA, then did it again with OSS
After that ALSA, OSS were my sound drivers.

I did this with any steam game too.

After starting up the game I had sound.

To get sound after stop playing steam and stopping steam I go to:

/home/chris/cxoffice/bin
there I click cxreset --> choose allbottles --> reset

The above worked for me and I have system sound after playing steam games through cxoffice.

Hope it helps someone.

Best regards,

placebo

---


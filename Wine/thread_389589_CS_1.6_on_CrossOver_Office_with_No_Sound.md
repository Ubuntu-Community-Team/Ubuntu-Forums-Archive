---
title: "CS 1.6 on CrossOver Office with No Sound"
date: 2007-03-20
forum: Wine
---

### Post by ZipCrash on 2007-03-20
I installed Steam and CS 1.6 just fine and I load the game and connect to a server but I can not get any sound. I can't figure out why not, does anybody have any ideas?

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

### Post by jdeslip on 2008-03-25
I have this same problem with crossover games.  Do you mean literally typing the words ALSA and OSS into that box?

---

### Post by handy on 2008-03-26
> **jdeslip said:**
> I have this same problem with crossover games.  Do you mean literally typing the words ALSA and OSS into that box?

Codeweavers would love you to post any problems that you are having with the newly released CX-Games on their forum too, so they can remedy them as quickly as possible, they can only fix what they know about...

---

### Post by jdeslip on 2008-04-07
The solution to my problem was to go in to the cx games winecfg and disable alsa.  I.e. only use OSS.

---


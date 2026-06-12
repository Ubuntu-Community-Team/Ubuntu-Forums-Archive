---
title: "Agfa Scapscan 1212U prob"
date: 2007-04-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Colin.mcewan on 2007-04-26
I am a newbie and I'm having problems with this scanner.

It is recognised and I can get a preview ok but when I ask for a scan (or another preview) I get a message "failed to start scanner. Error during device i/o"

The scanner works with Windows XP. Am I missing something ?

Can anyone help ?

---

### Post by steefjeqv on 2007-04-26
Hi,

I happen to own a Snapscan 1212U too.

I'm using Edgy 32 bit for the moment.
I had the same problem and it was solved by installing firmware.

Untar and add the attached file to the following directory : /lib/firmware.

This could be a solution, but it seems that there are 2 versions of the 1212U.
So this may work but it isn't sure.

Greetings,
Steven

---

### Post by Colin.mcewan on 2007-04-27
Thanks for this.

Tried it but it made no difference. When the scanner takes the preview scan, on the scanner head's return journey it stops half way back and never gets back to the 'start' position.

---

### Post by steefjeqv on 2007-05-21
Hi Colin,

I managed to get my Snapscan working.

After untarring the file I attached in the previous post, you need to edit your snapscan.conf file :

sudo gedit /etc/sane.d/snapscan.conf

One of the first text lines in this file mentions where to add the firmware needed for Xsane to work.

Greetings,
Steven

---


---
title: "Thunderbird POP timeout"
date: 2007-11-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by djinnster on 2007-11-23
Hello,

I'm having a very strange problem with POP timeouts while fetching mail with thunderbird. First of all I installed 64-bit version of Gutsy on an AMD 64 X2 platform. Everything was working fine until I tried to use thunderbird to fetch mail. Whenever there is a large email to fetch (say > 1MB) I get a POP timeout. At first I thought that it must be the new version of thunderbird. I still have fesity installed on an old dell 386 and with thunderbird 1.5 I can still fetch all email - therefore I'm 100% its not a server problem.

I googled and found that people had reported timeouts with thunderbird on AMD 64 bit platforms but they were all windows users and the various fixes suggested either had no affect  (setting timeout to high value in the prefs.js file) or else were not possible to perform on linux.  

I then installed a 32bit version of gutsy on the same machine and still got the timeouts. I then tried to copy the version of thunderbird 1.5 from the old 32 bit dell machine - I thought that this must work but I still get the timeout. Therefore I'm 90% sure that it's due to the processor but for the life of me I can't understand why the processor is affecting the email client? This is why I'm posting the problem here...

I'm kind of tearing my hair out and wasting far to much time on this problem. If anyone has any ideas then I'd be grateful for some help.

Cheers

Rob

---

### Post by offroad64 on 2007-11-23
I'm running close to your specs (AMD Athlon 64 X2 4600+ Gutsy 64bit)
and I have no problems with large email attachments using thunderbird. Could be something else not making nice:confused:

---

### Post by djinnster on 2007-11-29
Thanks for the help.

I now think that this problem is caused by the forcedeth drivers for the particular ASUS motherboard that I'm using ( M2N-E SLI ). It seems to have problems with dual core processors.

I gave up in the end. Might try buying another network card, might try another distribution.

Rob

---


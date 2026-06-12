---
title: "Play Sound concurrently on multiple application."
date: 2009-03-03
forum: x86 64-bit Users
---

### Post by bluedream_zqs on 2009-03-03
Hi, All. I have installed Ubuntu 8.10 on 64bit machine.

I can play audio well for one application. But if I try to play audio using two different audio application, one will complain that error happens. It seems that sound card only can be used for one application .


Any suggestions will be appreciated. Thanks!

Regards.
Steven.

---

### Post by lisati on 2009-03-03
One possibility is to use only one application at a time that uses sound.....

---

### Post by bluedream_zqs on 2009-03-03
Thanks, Lisati.
But I have no choice, I need to use the sound resource concurrently. For example, take several call concurrently using several skypes.

---

### Post by Clancy_s on 2009-03-03
Have you been through the Pulse Audio tune up?  PA shares sound resources between different apps.  The tune up sorted things out for me, beyond that I can't help you but it'd be a good place to start.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by alexroat on 2009-03-14
I have the same problem and I'm looking for a solution for this problem.
Example: I'm watching a video on youtube with firefox and I cannot open Totem or Skype without getting an error.
Viceversa, if I'm watching a movie and I open firefox on a flash content it freezes and I have to kill it.

Any news ?

Thanks.

Alessandro

---

### Post by Grifulkin on 2009-03-14
Ubuntu has always been like that for me, it seems like a GNome thing, when I was screwing around with Kubuntu, the KDE desktop never had a problem handling that, even in 64 bits for me.  I was using KDE 3.5 though.

---

### Post by oldos2er on 2009-03-14
Are you using Pulseaudio? Seems like I struggled with this on earlier (than 8.10) versions of Ubuntu, but it's working fine for me.

 Maybe there's some help here: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---


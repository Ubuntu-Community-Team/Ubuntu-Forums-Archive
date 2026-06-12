---
title: "mic on Dell XPS 1330"
date: 2008-03-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by mschira on 2008-03-23
Hi 
I try to get the build in mic working, but the fix Dell offers:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work)
is only for 32bit.
I couldn;t find a AMD64 bit version.
Solutions?
M.

---

### Post by mschira on 2008-03-24
nobody?
M.

---

### Post by saftaplan on 2008-03-24
[http://ubuntuforums.org/showthread.php?t=702642](http://ubuntuforums.org/showthread.php?t=702642)
I haven't tested it yet, but try this, and let me know if it works :) (I think the hardware in a 1330 doesn't differ much from a 1530)

---

### Post by herger on 2008-04-03
Hi. 
That fix **_doesn't work at all_**.
Is it possible that there is no wauy to have mic working on my Dell XPS 1330?????
:confused::confused::confused::confused:

Thanks and regards

H

---

### Post by sultanoswing on 2008-07-01
> **herger said:**
> Hi. 
That fix **_doesn't work at all_**.
Is it possible that there is no wauy to have mic working on my Dell XPS 1330?????
:confused::confused::confused::confused:

Thanks and regards

H

From the thread above, another solution - simple and worked perfectly for me (credit to jespdj):

On the Ubuntu Hardy release candidate, the microphone works out-of-the-box (ALSA 1.0.16 is already included). You do have to configure it, however:

   1. Double-click the volume control icon in the top right of the screen.
   2. Select Edit / Preferences.
   3. Add "Digital" and "Digital Input Source" to the list of visible tracks.
   4. On the Options tab, select "Digital Mic 1" for "Digital Input Source".
   5. On the Recording tab, set the volume for the microphone.

---

### Post by herger on 2008-07-02
Hi.
Thsnks for Your reply.
I have Gutsy, and I already had the settings You mentioned, but the microphone still doesn't work...
Thanks and regards

H

---

### Post by sultanoswing on 2008-07-03
> **herger said:**
> Hi.
Thsnks for Your reply.
I have Gutsy, and I already had the settings You mentioned, but the microphone still doesn't work...
Thanks and regards

H

Could I be so bold as to suggest you upgrade to Hardy? The 64-bit edition which I'm using on my 1330 is fast and rock stable (with all updates), and the above solution works fine. Given the hardware similarities, your experiences ought to be similar!

---

### Post by crobinson55331 on 2008-07-04
Thanks for the help - your advice worked well for me on my XPS 1330 under 64 bit Hardy:)

---

### Post by herger on 2008-07-07
Hi. Thanks, I was thinking about it, too... Is it possible to pass to Hardy 64 from Gutsy 32? Withot deleating everything, of course.... Sorry about my ignorance....!!!!
Thanks again

H

---


---
title: "Ubuntu 14.04 help with Cisco IP Communicator 8.6.3"
date: 2014-12-28
forum: Wine
---

### Post by stevedub40 on 2014-12-28
Hello all,

I originally posted this in the General forum, but I just realized there is a specific forum for Wine, which may be more appropriate.  I have not had any luck tying to get CIPC to work with this version of Ubuntu.  I've tried Wine version 1.6.2 and 1.7.33, and both have had issues.  I've been able to get everything installed and running, but the main issue is that I can never get audio to work during an active call.  I can get dial tone and even the audio tune wizard to work sometimes, but once the call goes through there is no audio.

Does anyone have any experience with this or can provide any suggestions or recommendations?  This is the final piece that is holding me back from a full changeover to Ubuntu :)

Many thanks!
Steve W.

---

### Post by stevedub40 on 2014-12-31
Hello again everyone,

I was finally able to get CIPC to work properly, so I just wanted to give a quick update in case this helps someone else out.  I had to manually set the audio network IP to the Cisco VPN subnet.  For some reason this is not detected properly like it is in Windows, where it wants to use your local subnet instead.  Once I set this IP I can now hear and be heard during a live call.  This was on Wine version 1.7.33.

---


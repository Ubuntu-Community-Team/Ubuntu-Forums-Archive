---
title: "Bluetooth and audio loss"
date: 2008-08-11
forum: x86 64-bit Users
---

### Post by Thelasko on 2008-08-11
The other day I was transferring files to my phone using bluetooth.  After the transfer was complete, I noticed I no longer had sound.  I restarted my machine and the sound came back.  Has anybody else had this problem?

I'm using 64-bit Hardy Heron, with a usb bluetooth adapter.

---

### Post by pbjoiner on 2008-09-03
I have a different but (I believe) related problem. On Ubuntu (2.6.24-19-generic x86_64) when I attempt to run my LG HBS 200 headset and my MS Wireless Notebook Presenter Mouse 8000 at the same time the response from both becomes bogged down.

The audio cuts out then speeds up (to catch up with the transmitter). The pointer is sluggish and lags. I can comfortably run both under WinXP. I expect the problem lies somewhere in the BT stack. 

I am mostly just adding my two cents here to call further attention to the problem that we are experiencing. I include the original author in my "royal we." 

In my searches of this forum and the larger net I have not encountered a solution. My last thought was to try and set the priority for the daemon to a lower value (-3) to assign more processor time to bluetooth operations. I suspect that I'm using either too high a value or applying it to the wrong app. Any thoughts on this sub-subject?

I wish I had the intelligence to help code this stuff. I just don't. I am a web monkey. Hell, I studied theater in college.

Please help.

---

### Post by John Jason Jordan on 2008-09-03
I have some additional experience that is probably related to the issues you guys are reporting. I have a Sony BT50 audiophile bluetooth headset. At one time I had a Logitech V270 bluetooth mouse as well. Both worked OK, except that every time I moved the mouse the sound would cut out for a moment.

Later I got a Razer bluetooth mouse and now the headset does not cut out when I move the mouse. 

I should also add that both mice suddenly quit working at random once every few days or so. I can just do sudo hidd connect <address> and it restores the mouse. I use a Thinkpad which has a trackpoint that I leave running as well. In case the mouse dies I still have mouse function with the trackpoint, so it's just an annoyance.

Clearly, there is something not quite right about bluetooth on Hardy x86_64. I never tried either device with any other OS or architecture.

---

### Post by Thelasko on 2008-09-03
I should detail my problem a little more.

1. I don't have a bluetooth headset, I have normal 2.1 channel speakers connected by a miniplug to my soundcard.

2. I had a similar problem in Gusty, the sound never came back and I had issues with aplay locking up on boot as a result.  I resolved it by upgrading to Hardy.  [Here are]("http://ubuntuforums.org/showthread.php?t=823893&highlight=aplay") [my posts]("http://ubuntuforums.org/showthread.php?t=820499&highlight=aplay") from this issue.

I'm just glad the sound came back when I rebooted.  Maybe it has to do with pulseaudio.

---


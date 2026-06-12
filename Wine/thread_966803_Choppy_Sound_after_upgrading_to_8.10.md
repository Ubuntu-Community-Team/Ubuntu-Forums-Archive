---
title: "Choppy Sound after upgrading to 8.10"
date: 2008-11-01
forum: Wine
---

### Post by EndOn9 on 2008-11-01
Hi guys,

Since upgrading Ubuntu to 8.10 all my programs run through Wine have been running with very choppy sound. Everything ran perfectly before the upgrade.

Any ideas?

---

### Post by EndOn9 on 2008-11-01
Sorry, should have mentioned I'm using wine 1.0.1 (tried 1.1.7 but this actually made things worse, like when I cliekd 'Test Sound' in the Wine Config the Config would play the sound and then lock up).

Have got the sound configured to ALSA

---

### Post by Dark9204 on 2008-11-01
Try to completely remove wine.
Do this:
In Synaptic package manager select "complete uninstall" then go to your home dir and select "show hidden folders" and delete your .wine folder.

I'm using wine 1.0.1 now and sound is fine. I had the same issue as you with wine 1.1.7 after an upgrade. Another thing were that my FPS were horrible...
Fresh new install of ubuntu 8.10 solevd all problems. Anyway, completely remove it and try again.

---

### Post by Limited on 2008-11-01
Yeah I'm having similar issues with Wine 1.1.7 and the sound quality has gone nuts, going to re-downgrade to an older version I was running to see if it will fix it. Seem to be having issues getting Ventrilo playing the voices of other players, but it will make the noise that i've connected to a server. Had lot's of problems since upgrading. Will give re-installing Wine a go.

---

### Post by deathpulse on 2008-11-01
I had the same problem with 1.1.7.  Downgrade to 1.1.5 and all will be OK.  1.1.7 = buggie

---

### Post by Limited on 2008-11-01
I tried a different approach before I tried re-installing Wine, I instead installed OSS v4, which has solved all of the audio problems I was having. I followed the guide which can be found here...

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Since installing these Ventrilo has weirdly started responding to my push to talk buttons aswell, although still requires focus and ventriloctrl is still broken :(

Either way, hope this helps someone :)

---

### Post by EndOn9 on 2008-11-02
Thanks for the replies guys :)

Tried purging Wine from the system before re-installing it. No cigar, just the same as before.

Re-installing OSS would only help if I'm using OSS drivers right? I'm using ALSA. Don't really want to switch either as everything else seems to work fine.

---

### Post by Ng Oon-Ee on 2008-11-02
I can't remember where I got this from, but since I upped to 8.10 I've been using OSS instead of Alsa for everything in Wine. This was based on a comment made on another forum that the Alsa drivers for Wine were buggy and unreliable compared to the OSS drivers.

For this to work with Pulseaudio (default sound server in Hardy and Intrepid), just 'convert' it (not sure what the actual term is) to Alsa using 'aoss' (install that from Synaptic).

Then, you can just run your application using

```
aoss wine <your program>.exe
```

Works terrific on my setup.

---


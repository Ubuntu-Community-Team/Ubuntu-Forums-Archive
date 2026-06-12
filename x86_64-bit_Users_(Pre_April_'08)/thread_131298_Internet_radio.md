---
title: "Internet radio"
date: 2006-02-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by racymind on 2006-02-16
I  cant get anything going here...

I'm trying to listen to kexp ([www.kexp.org](www.kexp.org)) .  They have streaming mp3 , windows media, realmedia...

I have tried rhythmbox, xmms.   I have tried pasting the location of the media link into the players.  The error is 'unexpected end of stream'

I love internet radio, so this is important to me...

any ideas?

imac g3 350 - an old, cute thing...

---

### Post by niviche on 2006-02-16
I am not in front of Kubuntu right now, but I believe that Amarok support streaming mp3s. You might have to add it as a playlist somewhere.

---

### Post by slux on 2006-02-16
Streaming mp3 should most definitely work and be fairly easy in xmms and beep-media-player (well, assuming you have mp3 support installed). 

What kind of URL are you getting inside your player? Have you tried adding [http://kexp-mp3-128k.cac.washington.edu:8000/](http://kexp-mp3-128k.cac.washington.edu:8000/) which is what the .pls file for that stream points to?

---

### Post by rudiz on 2006-02-16
The same link is also in Streamtuner. And it plays with XMMS.

Install streamtuner with apt.

---

### Post by racymind on 2006-02-16
Yeah, I tried pasting/typing  in [http://kexp-mp3-128k.cac.washington.edu:8000/listen.pls](http://kexp-mp3-128k.cac.washington.edu:8000/listen.pls)

and i still get the error

---

### Post by rudiz on 2006-02-16
Try Streamtuner...it works.

Kexp is in Shotcast in Streamtuner.

sudo apt-get install streamtuner

---

### Post by slux on 2006-02-16
No, don't add "listen.pls" to the end but put in the url exactly as I pasted it. XMMS won't work if you try to add an pls file as a stream url anyway.

---

### Post by Revolution on 2006-02-16
I use RealPlayer on my box.
I clicked the "Listen" link on kexp and it started streaming.

Too easy.

---

### Post by ssam on 2006-02-16
you'll need gstreamer0.8-mad to play mp3s in rhythmbox. you can install it with synaptic.

see [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by racymind on 2006-02-18
Thanks for the help - 

streamtuner plugged me in.  I first had to change my repositories.   Then I had to find where the application installed itself.

Then...it was great!


problem solved.

---


---
title: "Ableton not working with Wine"
date: 2008-11-22
forum: Wine
---

### Post by PhoenixMaster00 on 2008-11-22
Ive got Ableton 7.03 and Wine 1.1.9 and it installs fine but when i go to load it up the load screen comes up it gets to create new live set and then a little box comes up with 'serious program error Ableton live will close down after this message box closes'

Anyone else had similar problems?

---

### Post by PhoenixMaster00 on 2008-11-23
bump.

---

### Post by jon.reeve on 2009-01-31
I'm getting this same problem. Did you figure out how to fix it?

---

### Post by NuttyMonk on 2009-02-02
i get the same error too.

i changed the audio drivers that Wine uses (in the Wine config) to use Jack, not ALSA and it went past the error and loaded up Ableton, although now it tells me that audio has been disabled in Ableton when it loads (i do have the option of selecting the audio drivers but it tells me that Jack doesn't exist).  I'm not sure what Jack is, i must have installed it at some point in the past.  Maybe i have to load Jack before i load Ableton.  Is it a program or just a set of drivers?

Anyway, when i get it working i'll get back to you with the answer.  :-)

---

### Post by NuttyMonk on 2009-02-02
ok, another update.  When i start Ableton without starting the Jack Audio Server, i get a list of audio outputs e.g....

Wine Jack DirectSound Driver DX (1 through 8)
JACK WaveOut 0 Wave (1 through 8 again)

...but when i click on any of them Ableton says it can't connect to the audio device.

If i start the Jack Audio Server before i start Ableton, the list of audio outputs is empty.  Odd.  But i'm gonna persevere and see what i can do with it.

---

### Post by NuttyMonk on 2009-02-02
Well, it was even simpler than having to muck about with the Jack Audio Server which is far too complicated and awkward.  I just turned on the OSS drivers in the Wine Config and turned all of the others off.  Then in Ableton i could choose a soundcard as i normally would when using Ableton in Windows.  I have all of the controls i normally would as well, latency, sample rate etc. 

It works perfectly and i'm already bashing away at a Tech-House remix of Love Lockdown by Kanye West ;-)

NM

p.s. i'm using Wine 1.1.14 and Ableton Live 7.0.3

---

### Post by jon.reeve on 2009-02-07
Thanks! Ableton now starts and the audio works. Now if I could only figure out how to get it to recognize an external MIDI controler it'd be great. Also, it seems to think my screen is a lot bigger than it is so the window is twice as big as the screen, and I can only see the top half of it.

---

### Post by NuttyMonk on 2009-02-07
i found that there are problems rendering audio tracks down with ableton.  even just freezing a track doesn't work.  i've decided to do a dual boot system instead using windows for all my music stuff.  it'll be a lot easier and i can keep the windows OS as clean as possible to get the most out of my music software.

---


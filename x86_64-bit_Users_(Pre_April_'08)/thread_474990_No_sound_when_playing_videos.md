---
title: "No sound when playing videos"
date: 2007-06-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Deathwish238 on 2007-06-15
I have an Audigy 2 ZS Notebook.  Music plays just fine using RhythmBox, but I have not been able to hear anything when I play a movie.  I've tried movies embedded onto a website and not embedded...no luck either way.  I've tried avi files, mov files, and youtube as well.

Any help is appreciated

---

### Post by Cappy on 2007-06-16
Have you selected your sound card in (System-->Preferences-->Sound) in the "Device" dropdown?
Are you using either "Autodetect" or "ALSA" in the other dropdowns?

Do you have multiple sound cards? For instance, do you have an onboard sound card as well as your Audigy 2 ZS Notebook?
Reply with the output from ```
sudo asoundconf list
``` and also ```
cat /proc/asound/cards
```



Try run the video in a terminal.
For instance,
try starting totem using
```
totem
```
and then open a video.


or Close all firefox windows and
```
firefox
```
and try to play a youtube video.

Have you used Kilz's script yet for Flash?
[http://ubuntuforums.org/showthread.php?t=425672](http://ubuntuforums.org/showthread.php?t=425672)

---

### Post by Deathwish238 on 2007-06-16
Oddly enough...I get sound with WMV files but no video.  Retried a youtube video and I get video but no sound.  I tried another AVI file and I'm also getting no video but only sound.

Now here's what's blowing my mind.  I opened up RhythmBox played and then paused a song.  I tried playing a WMV or AVI file, this time I get video but no sound!  However I do get a warning saying the sound card is already in use

> **Cappy said:**
> Have you selected your sound card in (System-->Preferences-->Sound) in the "Device" dropdown?
Are you using either "Autodetect" or "ALSA" in the other dropdowns?The "device" selected for each field is Multichannel Playback.  The Default Mixer Tracks is Audigy 2 ZS Notebook [SB0530] (ALSA Mixer)

If I select anything else I do not hear anything when clicking Test.

> **Cappy said:**
> 

Do you have multiple sound cards? For instance, do you have an onboard sound card as well as your Audigy 2 ZS Notebook?
Reply with the output from ```
sudo asoundconf list
``` and also ```
cat /proc/asound/cards
```

Yeah I also have a Realtek onboard sound card.

Names of available sound cards:
IXP
Modem
Audigy2


 0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 2 with ALC250 at 0xc0003400, irq 17
 1 [Modem          ]: ATIIXP-MODEM - ATI IXP Modem
                      ATI IXP Modem rev 2 at 0xc0003800, irq 17
 2 [Audigy2        ]: Audigy2 - Audigy 2 ZS Notebook [SB0530]
                      Audigy 2 ZS Notebook [SB0530] (rev.0, serial:0x20011102) at 0x2000, irq 23

> **Cappy said:**
> 
Try run the video in a terminal.
For instance,
try starting totem using
```
totem
```
and then open a video.No video, just sound.  Play a song and pause it in rhythmbox and I get no sound just video.

> **Cappy said:**
> 
or Close all firefox windows and
```
firefox
```
and try to play a youtube video.Running firefox from the terminal brings up the version without flash installed

> **Cappy said:**
> 

Have you used Kilz's script yet for Flash?
[http://ubuntuforums.org/showthread.php?t=425672](http://ubuntuforums.org/showthread.php?t=425672)Yes I have.  Flash works fine...except no sound

---

### Post by Cappy on 2007-06-16
Try running this
```
sudo asoundconf set-default-card Audigy2
```
and reboot after.

If that doesn't work, try changing the (System-->Preferences-->Sound) fields to "ALSA".

---

### Post by Ocxic on 2007-06-17
sounds to me like you don'e have all the proper codecs installed..

---

### Post by Deathwish238 on 2007-06-17
I was thinking that too actually...which ones should I be using?

---

### Post by Cappy on 2007-06-17
These:
```

echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list

```

```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install w64codecs

```

---

### Post by Deathwish238 on 2007-06-19
> **Cappy said:**
> Try running this
```
sudo asoundconf set-default-card Audigy2
```
and reboot after.

If that doesn't work, try changing the (System-->Preferences-->Sound) fields to "ALSA".Youtube now has sound.  Thank you, however avi and wmv files have no video, just sound.



> **Cappy said:**
> These:
```

echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list

```

```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install w64codecs

```Tried this, didn't help.  Should I first uninstall my previous codecs?

---

### Post by Cappy on 2007-06-19
Shouldn't need to.

Do you have video card drivers installed? (System-->Administration-->Restricted Drivers Manager)

Can you right click on the video, goto Properties, goto the "Audio/Video" tab, and under **Video** post the Codec of the files that won't play? Will any of your videos play?

Have you tried turning off Beryl (The red gem in the notification area) or (System-->Preferences-->Desktop Effects) if you have them enabled?

From: [http://ubuntuforums.org/showthread.php?p=1649012](http://ubuntuforums.org/showthread.php?p=1649012)
Try:
```

rm -rf ~/.gstreamer-0.10
gst-inspect-0.10

```

Try running totem in the console to see if you get any error messages.

I usually wouldn't mention it, but you may just want to try Automatix and use it to install video codecs, it may fix something =-/
[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by Deathwish238 on 2007-06-20
It says "ATI accelerate graphics driver"  is "Not in use".  I clicked Enabled and voila, everything works!

Thanks for your help guys

---

### Post by ncreek on 2007-10-31
Cappy

I am have the same problem. Everything plays vid and aud except in firefox flash(vid works). WMV and all runs under Ubuntu fine but not in Firefox. did a complete uninstall on FF_64 and reinstalled with non-free Flash. Still zilch. I followed the trail of code you layed out to Deathwish238. I have one sound card and I set it default. For some reason even after booting I can not use ALSA. I get a device busy. All works fine(except flash) using default or Autodetect. Anything you can help with ??

---


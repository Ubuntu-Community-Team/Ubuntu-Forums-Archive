---
title: "Headphones/mic + speaker issue"
date: 2009-05-01
forum: x86 64-bit Users
---

### Post by rdmike on 2009-05-01
Hi all,

I've just installed the 64 bit version of Ubuntu 9.04 and have things updated without much issue save one. I have my headset/mic plugged into my desktop and, for some reason, whenever I play a video or audio file the sound is directed to both the headphones and external speakers at the same time. I want to use the headset for skype but need to have the external speakers muted while using it. Any ideas or suggestions?

---

### Post by rdmike on 2009-05-01
Ok, I  was able to get my mic working but its still playing through both the headphones speakers and the monitor's built in speakers. So, how do I set it to mute the external speakers when the headphones are plugged in?

---

### Post by rdmike on 2009-05-02
I could really use some help with this. Please..........:)

---

### Post by John Jason Jordan on 2009-05-02
> **rdmike said:**
> I could really use some help with this. Please..........:)

Depending on what sound features are installed there will be different things to check. Start by right-clicking on the volume control in the panel and then select Volume Control. There are a ton of sliders and buttons in there that do various things. Which ones you have depend on what sound card you have and what modules are installed.

If that doesn't help find a solution I hope someone smarter than me responds, but I know next to nothing about sound. I just know that I had the same problem a very long time ago and solved it by checking or unchecking a button in the Volume Control.

---

### Post by rdmike on 2009-05-02
Hey, thanks for the reply! Yes, I was able to get the mic working that way but, for some reason, I can't get the speakers built into the monitor to shut off when the headphones are plugged in. The weird thing is, to me, that in the mixer controls it recognizes headphones are plugged in. Gotta be something simple I think lol.

---

### Post by rdmike on 2009-05-05
Can anyone help me figure this out?

---

### Post by Grenage on 2009-05-05
Is it supposed to disable the speakers when the headphones are plugged in?

Regardless, you might be able to make a script which toggles the speakers to disable or enable.  Or turn the speakers off?

---

### Post by jackie hayes on 2009-05-05
Just registered here because I'm having the exact same problem.  In Intrepid, it worked fine -- plugged in the headphones, speaker goes quiet.  After the update, the monitor speaker just keeps chugging when the headphones are plugged in.

---

### Post by rdmike on 2009-05-06
"Is it supposed to disable the speakers when the headphones are plugged in?"

Disabled is probably the wrong term but yes any time one plugs in their headphones sound should be diverted to the headphone speakers rather than the normal [external] speakers; nothing new or cutting edge there.

What's the missing link here? It has to be something simple. Could it be that Ubuntu cannot recognize the front headphone and mic jacks? (there's a set on the back of the tower too I think)

---

### Post by luctor on 2009-05-06
My bet is that you have a HDA soundcard.
Open a terminal and type
```
lsmod | grep snd
```

and see if there's 'snd-hda' somewhere in the output, if so take a look at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and scroll to the section > Manually Specify Module Parameters.

In ***my case***, because I have a ***Dell Inspiron 531***, I had to edit
```
/etc/modprobe.d/alsa-base
```, adding the line
```
options snd-hda-intel model=6stack-dell
```

Just to clarify : I have a ***Dell*** Inspiron so that's why I had to insert **6stack-dell**. You can have a look at [http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt) for other models

---


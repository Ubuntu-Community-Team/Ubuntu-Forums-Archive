---
title: "Problem with installing Skype"
date: 2009-06-07
forum: x86 64-bit Users
---

### Post by Tauriel on 2009-06-07
Hi all,

new Ubuntu user here. ):P I only installed Ubuntu (the 64-bit version) a few days ago on my new laptop, so I'm still learning how to use it.

Now, I want to install Skype on it. I found a good tutorial, which guided me through the installation. The Package Installer says that it's been successfully installed, but I can't find Skype in my Applications list.

Can anyone please help me with this?


I also want to note that I'm no programmer - I'm not a complete computer idiot, but I've only used Windows until now, so I have little to zero knowledge about working in Ubuntu and Linux in general... :redface:

---

### Post by Bucky Ball on 2009-06-07
Try System->Preferences->Main Menu

Click on the 'Internet' icon in the left column. Is Skype in the right hand column with no tick? If so, tick it, close and you should find it under 'Applications->Internet->Skype'.

:)

---

### Post by Tauriel on 2009-06-07
No, it's not there either. :( When I start the installation package again, it says that the application is already installed and I can reinstall it. I tried to reinstall it, but I have still the same problem...

---

### Post by kiridude on 2009-06-07
What happens if you open a terminal and type:

```
skype
```

---

### Post by Tauriel on 2009-06-07
Ah! It's working! :D Thanks, kiridude!

But it's still not listed in the Applications list. Does it mean I have to start it every time through Terminal? Or is there a way to put a link to it on the desktop? 

Also, I got these messages in the terminal:

```
Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
ALSA lib ../../../src/pcm/pcm.c:2165:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so

```And the bit about "Cannot open shared library" repeated about 30 times.

The Skype does start, though.

And now I have another problem - when I make a Test Call, it says "Problem with Audio Playback". What can I do about it?

---

### Post by kiridude on 2009-06-07
How did you install skype?

---

### Post by Tauriel on 2009-06-07
I downloaded skype_ubuntu-2.0.0.72-1_amd64.deb and ran it.

---

### Post by Bucky Ball on 2009-06-07
It is much better to add it from the repositories! That way it is updated along with everything else. You need to add the Medibuntu repository to your software sources, though.

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

---

### Post by kiridude on 2009-06-07
As bucky ball says, its better from the repositories. Add as per the link he provided, then run: sudo apt-get update, then: sudo apt-get install skype.

This, however, is not your main concern. You are suffering from a bug that affects 64 bit users for skype. There are a couple of solutions in this [thread]("http://ubuntuforums.org/showthread.php?t=432295") for you. 

As a side note, I would recommend giving Ekiga a try. It's open source and the help forums are really good

---

### Post by Bucky Ball on 2009-06-07
kiridude, with the Medibuntu repo added, Skype will be right there in Synaptic Package Manager without needing to use the terminal (after you are alerted and run the update manager after adding the repo, of course). :)

As for the Problem with Audio Playback, you need to open Skype, click the 'S' icon in the bottom left hand corner and choose 'Options'.

Go to 'Sound Devices' and start to experiment by changing the device for 'Sound In'. Go through them one by one and make a test call. See which one works and you should be sweet. I have been running Skype on 64bit for ages with no special tweaks and no problem. Usually just a matter of identifying the correct device (Skype doesn't seem to choose to good in Ubuntu). :)

---

### Post by kiridude on 2009-06-07
Since you are a 64 bit user Bucky ball, you know better than me - I am still a 32 bitter :D  

I'm curious, do you get the errors he gets also even though you have no problems using skype cuz they seem to point to missing libraries? Or maybe they are due to an incomplete installation...

---

### Post by Bucky Ball on 2009-06-07
I'm thinking something dicky with the installation, but you never know. No, I've never had any probs with it. I loaded from a .deb but on the last build I did I added the Medibuntu repositories and did it that way, so then I uninstalled Skype from my own machine, added the repo and did the same so it would update.

No prob either way. The 32bit Skype would run in 64bit also, without a problem, unless, of course, as you say, the 32bit packages were missing. Hmm.

---

### Post by Tauriel on 2009-06-07
Bucky Ball - Brilliant, it worked perfectly! :D I added the Medibuntu repository, removed Skype, and installed it again through Medibuntu - and it's now in my Applications list! Woo! :D Thank you so very much for your help!

I still have to work on that Problem with Audio Playback - I tried all the options in the Sound In category, and none of them seems to work.

I wonder - do I need to look for another driver for my sound card? (I've installed Ubuntu on my new laptop - it's an Acer Aspire 6350 G)

---

### Post by Bucky Ball on 2009-06-07
Very welcome. I shouldn't think it is a driver thing. What headset have you got plugged in to use with Skype and where is it plugged? It is after the hwplug: it is plugged into. It would be 'hwplug: whatever it is using'. Oh, hang on, you said audio playback. Maybe set 'Sound In' back to default and try diddling with the other one, 'Sound Out'. Mine are all set to 'default' and they 'just worked', but I have two other machines and on one they 'just didn't'. I needed to experiment until I got the right combination.

Watch the error when you make a test call for which it is; playback or record. That will let you know which one needs dealing with. Is it giving you the ring on the test call or just failing as soon as you try to make one? If it is the latter, it is audio out you need to deal with.

:)

Incidentally, if you can hear music files okay, your soundcard is fine.

---

### Post by Tauriel on 2009-06-07
I haven't tried any audio files yet, but I've watched an online video tutorial (on how to set up Skype :P ), and it worked fine, on my laptop's speakers.

Now, I tried to change the audio settings in Skype, with my headset plugged in.

When I chose "pulse" on Sound Out (and everything else was default), I got very quiet sound on my speakers (even though the headset was plugged in - and there was silence in the headset), it rang once on Test Call and I got an error message Problem with Audio Capture.

I wonder why it seems to ignore the headset...

---

### Post by Bucky Ball on 2009-06-07
Okay, now tweak the 'Sound In'. That is for audio capture.

---


---
title: "Ubuntu 8.10 64 Bit, Microphone problem in Skype, VMWare Server 2.0 problems"
date: 2009-03-23
forum: x86 64-bit Users
---

### Post by mikepre on 2009-03-23
Greetings.
I have tried to solve my issues reading all newsgroups and forums I could, but this time I have to admit that I'm in a dead end road and do not know how to continue.

I finally took the decision to get rid of Windows and installed Ubuntu 8.10 64 bit on my DELL Inspiron 1420.

All Windows I need was virtualized using VMWare Server 2.0 64 bit for Linux. One of these VM's is a Windows XP one, where I play with Pentaho Opensource BI (need to have a Pentaho machine running on top of Windows). The problem I face is that I get sound in my Ubuntu host machine, but I have no way to activate the sound virtual driver to get sound from the Windows XP virtual machine... Why do I need that you will ask?..

Since I'm not able to use a microphone (internal or external) in my Ubuntu 8.10 x64 (I need it to use Skype), I decided to install Skype inside the Win XP virtual machine...

1.- If I just could use a microphone to use Skype for Linux v 2.0.0.72, installed using the following command:

sudo apt-get install ia32-libs lib32asound2 libasound2-plugins; wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu-amd64;](http://www.skype.com/go/getskype-linux-ubuntu-amd64;) sudo dpkg -i skype-install.deb; sudo dpkg -i getlibs-all.deb; sudo getlibs -p libqtcore4 libqtgui4 bluez-alsa 

I wouldn't need to have sound in the Win XP VM.

2.- Provided that I've seen a lot of users with mic problems in Ubuntu, and the threads are still open, is there any way to get Audio and Mic to work in VMWare Serevr 2.0 64 bit Windows virtual machines?

Thank you

Michael

---

### Post by 3Miro on 2009-03-23
I have never done skype under virtual machine and the only VM that I have used is Virtual Box anyway. Here are my 2 cents however:

I had trouble making skype work under 6.10 mainly with the sound. After I force the architecture, I had to either kill pulseaudio or go into the skype settings and set the output to pulse and the input to my microphone device. I hope this helps, if not, good luck trying the other way.

---

### Post by mikepre on 2009-03-23
Thank you 3 Miro.

I already killed, disabled and even uninstalled pulseaudio.

I do have sound, I can reproduce mp3, even if someone calls me by skype, I can hear everything.

The point is that not even the internal speaker nor an external one works.

I'll try further, if i find something, I'll post the results, since there seems to be a lot of people with the same problem.

Saludos

Michael

---

### Post by 3Miro on 2009-03-24
If you go to the volume control and unmute the Microphone, can you hear yourself speak? If Linux cannot connect yo your Microphone in general, no Virtual Machine would. VM on Linux side is just a program that is using the same Drivers and resources that any other program is.

---

### Post by mikepre on 2009-03-24
Thank you buddy, I solved the problem.

What I did was:

1) reinstall pulseaudio
2) Follow these instructions (I also have an Intel Audio Card in my DELL Inspiron 1420) 

[http://members.chello.hu/balla.gyorgy/balla-it/html/articles/20081230-asus-onboard-soundcard-configuration-on-xubuntu.html](http://members.chello.hu/balla.gyorgy/balla-it/html/articles/20081230-asus-onboard-soundcard-configuration-on-xubuntu.html)

3) Each time I open, Skype, I first killall pulseaudio ;), ie, I run from a terminal:

killall pulseaudio
skype


Incredible but it works with internal mic and external one attached to front panel (I do not know with USB Mic, I do not use one).

Thank you for your help, and yes, as I expected, if I have no mic in the host, no mic in the VM... now I can uninstall skype from that Win XP VM

Cheers

Michael

---

### Post by 3Miro on 2009-03-24
Glad to help.

I was killing pulseaudio on my laptop, however, I managed to get it working without. I entered option under skype and went on sound devices. I choose pulse for all input options and had to play a little to get the correct mic (pulse doesn't work). You might have to do that right after reboot with pulseaudio running and never being killed. That is, if you feel like messing further with it.

---


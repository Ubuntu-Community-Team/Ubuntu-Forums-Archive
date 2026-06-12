---
title: "Sound Card Disappears"
date: 2006-08-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by siegeszug on 2006-08-20
Hi, I am a Linux n00b who has recently converted from WinXP to Ubuntu Dapper.  Everything is working deliciously save for a minor bug with my sound.  My sound card just disappears!

It usually happens when I have to do a full system restart.  When the system starts back up, I don't have any sound.  I look in the System->Preferences->Sound, my card is no longer in the list!  When I go and double click the volume control in the upper right hand corner, and go File->Change Devices, my sound card is not listed there either.  Using lscpi I can see my sound card is listed.  So I have no idea why it randomly decides to lose it! ](*,) 

In order to get my sound card back, I have to go sudo update-modules and do a full system restart.  Once I do that, my sound card re-appears in the list and resumes being the default sound device.  So I figured I'd try and make my first post in the official Ubuntu forums to get an answer.  

I'm using a SoundBlaster Live! 24 bit sound card (el cheapo Wal-Marto card) and I do not mind if the answer is "Use a more Linux friendly sound card" since I already had to do that with my video card (Damn you ATI!).  :D 

Thanks for listening and all the future help to follow!

---

### Post by juicemansam on 2006-08-20
I'm not sure how much this will help, but I'd look at which modules exist when the sound card works and when it doesn't. I'm pretty sure that if you're using the alsa drivers, that the kernel modules is most likely called snd-emu10k1 (or snd-emu10k1x). If that modules is not loaded when your sound is gone, you can add it's name to the /etc/modules file. Also, don't forget to check out your dmesg messages during both working and non-working sound scenarios. Good luck!

---


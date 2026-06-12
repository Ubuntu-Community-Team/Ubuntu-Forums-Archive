---
title: "Lockup after first sound played on Soundcard"
date: 2006-06-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by metrix on 2006-06-21
Hello!

I have a new ASUS M2V motherboard with soundcard model 
REALTEK ALC660.  Whenever Ubuntu boots up in live mode everything works fine but once I have installed Ubuntu 64 on the hard drive and try to boot, the sound card goes into an infinite sound loop on the login screen.  Once I type in my login and password, I get to a solid colored screen where the system hangs..  I can to a terminal window and try to restart alsa but that does not fix the problem.  

Does anyone know where I would start troubleshooting a problem like this? are there known issues with this soundcard? is there something I'm missing?  ANY help or ideas would be greatly appreciated!

Brandon

P.S. If someone happens across this thread after the thread dies and has a solution, please e-mail me at [email]metrix1978@gmail.com[/email].

---

### Post by incubus on 2006-06-21
Brandon,

It's probably a good idea to see what you got in the log.

$ dmesg

...should give you some lines of output. Try to look for the ones related to your Realtek. I'm not sure how it's gonna be called, but I would try some variation of:
$ dmesg |grep Realtek

Also, it could be an inappropriate module for it. What do you have in:
$ lsmod

Something like "snd_intel"?
Googling or seaching this forum for your soundcard model would be one way to go, because there's a good chance somebody had the same problem before.  I had a problem with mine as well (also the Asus & Realtek combo), which was solved in Dapper (before that I had to go to Realtek's website and download their drivers).

Another thought: could it be something else that is causing the crash? Perhaps the video card?

incubus

EDIT: By the way, I'd recommend you against posting your email here. It's an easy prey for spammers. Ask people to send you a Private Message instead.

---

### Post by metrix on 2006-06-22
Thank you, your reply has helped me a great deal! before I posted I did search google/this forum for my motherboard and soundcard model but did not find anything.  

The chipset is being picked up as an intel module right now.  

snd_hda_intel          21664  1
snd_hda_codec         175048  1 snd_hda_intel

After my reply I found that if I ran the alsa-utils stop, killed aplay, went back to X logged in, and then killed esd that I could go ahead and log into the desktop.  Should the soundcard be loaded under an intel driver?  I am going to try to find an ALSA forum to see if there is any information on the trouble this driver is having.

Brandon

P.S.
Just in case someone else googles for the same problem, i am going to write out the instructions on how to atleast get back into ubuntu here.

1. Let Ubuntu get to the login screen. when the sound driver starts screwing up, hit ctrl + alt + F1 to get to a terminal and login
2. cd /etc/init.d
3. sudo ./alsa-utils stop <the sound should stop repeating>
4. ps -ef |grep aplay
5. sudo kill the aplay pid's
6. hit alt + F7 (takes you back to your login screen)
7. login  (if it locks up again, do step 4 and 5 again except to grep and kill esd

---

### Post by guillaumeavril on 2007-08-15
Hello!

I've got the same problem with an asus M2V but not with the integrated sound card. But when I try playing a music with mplayer in the terminal there was a problem about SNDRV_PCM_IOCTL_DRAIN . The problem involved was in fact the motherboard and the linux kernel so i added pci=nomsi at the end of the kernel boot line in /boot/grub/menu.lst and everything was ok then.

:popcorn:

---


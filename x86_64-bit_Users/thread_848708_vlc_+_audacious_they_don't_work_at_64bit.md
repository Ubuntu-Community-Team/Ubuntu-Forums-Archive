---
title: "vlc + audacious they don't work at 64bit"
date: 2008-07-03
forum: x86 64-bit Users
---

### Post by ilcontegis on 2008-07-03
Hi,
This is amazing....is the first time that ubuntu makes me so angry!
I made a new installation on a 64bit pc. And as usual I wanted to install xmms and vlc...xmms I gave up, for a dependency that can not be satisfied even if I install the library...
But the amazing thing is that in vlc does not work the audio and audacious it block after 2 seconds crashing. If i listen a mp3 or I watch a film on totem everything works fine. WHY?
I tried already to reinstall but no changes.....

Do you have a any ideas how to solve this 2 problems?

Thank you
:)

---

### Post by lavinog on 2008-07-04
They work ok on my 64bit system.
what are your specs?
can you post the command line output?

---

### Post by ilcontegis on 2008-07-04
> **lavinog said:**
> They work ok on my 64bit system.
what are your specs?
can you post the command line output?


let's see if i remember well...the pc is in italy i'm in japan..so when my brother wakes up i will ask him to give me the command line output

for the spec:
m/b asus p5q pro
cpu intel dual core 3ghz
ram 2x2gb corsair 1066mhz raptor
gpu nvidia 8800gt
os ubuntu 8.04.1 64 bit completely up to date

I will post later the command line
thanks

edit here the konsole output

> 
VLC:

andrea@Artax:~$ vlc
VLC media player 0.8.6e Janus

with SUDO

andrea@Artax:~$ sudo vlc
[sudo] password for andrea: 
VLC media player 0.8.6e Janus
starting VLC root wrapper... using UID 1000 (andrea)

AUDACIOUS

andrea@Artax:~$ audacious
Killed

with SUDO

andrea@Artax:~$ sudo audacious
[sudo] password for andrea: 
I/O warning : failed to load external entity "/root/.config/audacious/playlist.xspf"


Do you understand something from this?
What can I do?

---

### Post by soxs on 2008-07-04
did you try to purge them (including any config files apt-get purge vlc audacious leaves?)

You should add /var/log/messages aswell /var/log/debug and /var/log/auth.log and /var/log/daemon.log

---

### Post by Artemis3 on 2008-07-05
Try this in a terminal: killall pulseaudio ; vlc

Also try resetting vlc settings, by deleting ~/.vlc folder.

I know you are angry with current release, so i will save you some, more frustration: avoid audacious 1.5.0, it is buggy as hell.

BTW: never ever run programs as root (sudo), unless you are doing serious system maintenance.

---

### Post by stchman on 2008-07-06
I have Audacious and VLC  working on three different machines running 64 bit.

---

### Post by ilcontegis on 2008-07-06
i did format and reinstall all fine now...:guitar:

---


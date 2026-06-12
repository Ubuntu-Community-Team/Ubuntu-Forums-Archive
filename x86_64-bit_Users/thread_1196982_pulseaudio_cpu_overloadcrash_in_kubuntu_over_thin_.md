---
title: "pulseaudio cpu overload/crash in kubuntu over thin client"
date: 2009-06-25
forum: x86 64-bit Users
---

### Post by Defrector on 2009-06-25
Pulseaudio in kubuntu is exiting due to cpu overload. Details:

The setup is a server / somewhat-thin client config. Both sides have pulseaudio 0.9.14 installed. Both use same 64-bit version of kubuntu 9.04 up-to-date as of this posting and use ssh for X11 forwarding.

When both client and server have the pulseaudio process running, pulseaudio on both ends will use 100+% of the CPU and one side will give up with a CPU limit message. No sound gets passed in this situation, ever.

However, if I kill the pulseaudio process on the server end and ensure that the pulseaudio process on the thin client is running, things work fine.

I cannot remove the pulseaudio package as phonon needs it installed to recognize that pulseaudio is an option. But as I said, the process itself causes issues.

Tried inserting a script with 'kill pulseaudio' in the server's ~/.kde/Autostart directory but the pulseaudio process persists.

Tried using 3rd party repo to install newer version of pulseaudio (0.15?), and it somewhat fixed the issue but the system became unstable so it had to be rolled back.

Already removed pulseaudio from /etc/init.d but it still shows up on kde login.

So what I ideally would love to get some help on is one of the following:

1. a hack to keep the pulseaudio process from launching, or at least something to snipe it whenever it tries to run.

or... 

2. A way to keep the two pulseaudio processes from overloading the CPU and crashing when they see each other on the network.

I've been at this for about 12 hrs so I'm going to sleep. Any brilliant ideas would be appreciated when I wake up.

---

### Post by Arup on 2009-06-26
KDE doesn't use Pulse, it uses Arts instead so if its showing Pulse, there is something wrong.

---

### Post by Defrector on 2009-06-26
I am using KDE4, which uses Phonon instead of aRts.
( [http://multimedia.kde.org/](http://multimedia.kde.org/) )

---

### Post by Defrector on 2009-06-27
....solved??

I used a 3rd party repo which supplied an pre-official version of pulseaudio/pulselib 0.9.15 (current for 9.04 is 0.9.14), had issues, switched back to 0.9.14 and now pulseaudio does not overload and crash. Theoretically the two situations should be the same but no?

EDIT: I speculate that this time was different because I used "remove completely" in synaptic for all pulseaudio packages and then reinstalled. Perhaps configs were bad?

---


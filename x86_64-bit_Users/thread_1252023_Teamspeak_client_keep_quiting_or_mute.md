---
title: "Teamspeak client keep quiting or mute"
date: 2009-08-28
forum: x86 64-bit Users
---

### Post by superdif on 2009-08-28
Hi all,
I am running a fresh (2-3 weeks) (re-)install of Kubuntu 9.04 64 bits and this time I'm having problems with Teamspeak client (from repo).

Basically Teamspeak either close itself after 2 seconds after connecting to a server or it gets the output muted (with no possibility to unmute).

For the later I usually (it's a problem that I'm already familiar) solve by reloading Alsa:
```
$ sudo alsa reload
```

but the first problem (auto-closing of the client itself) is a mystery. I tried to launch the client from a console to check if it give any error, but it output nothing.

Any idea on how to solve it (or at least how to debug it)?

Thank in advance.

---

### Post by superdif on 2009-08-31
Sorry for the bumping, but is there anyone with some idea?

---

### Post by sherl0k on 2009-09-02
I bet you it's PulseAudio that's giving you problems.

You can always uninstall it to see if that fixes the problem.

```
sudo aptitude purge pulseaudio
```

then reboot and see how it goes. If you don't like the results, just reinstall it.

---

### Post by superdif on 2009-09-06
> **sherl0k said:**
> I bet you it's PulseAudio that's giving you problems.

You can always uninstall it to see if that fixes the problem.

```
sudo aptitude purge pulseaudio
```

then reboot and see how it goes. If you don't like the results, just reinstall it.

That was it!!!

Strangely even if I run TeamSpeak with aoss I had the crash issue, but now without PulseAudio, it is running correctly.

Thank for the advice.!:P

---

### Post by ethoxyethaan on 2009-09-07
superdif, i had the same problem 3 years ago, ever since i just gave up on the linux teamspeak client and use the windows version via wine.

1: it does not lock up teamspeak audio
2: it does not lock up audio from other programs

only downside of using the windows teamspeak is that in order to use push to talk you need to have your cursor inside the teamspeak client.

i use voice activation most of the time so it was not really a problem.

---


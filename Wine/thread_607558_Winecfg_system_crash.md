---
title: "Winecfg system crash"
date: 2007-11-09
forum: Wine
---

### Post by sgardino on 2007-11-09
I'm having an issue trying to run winecfg.  Wine starts to create my home folder then gives me the following error and locks up my computer:

fixme:  Mixer:ALSA_MixerInit  no master control found on MPU-401 UART, disabling mixer


Any help would be greatly appreciated!

Thanks:guitar:

---

### Post by Lab on 2007-11-09
Same problem here, any help :confused:

When I run winecfg from terminal I get this
```

fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer

```

It opens a window, when I click the audio tab the terminal gets this error message
```

fixme:jack:JACK_drvLoad error loading the jack library libjack.so.0, please install this library to use jack

```

Any ideas please?

---

### Post by sgardino on 2007-11-09
Well, at least you can move on to a next step, mine crashes my computer entirely....

That being the case, you should probably check symnatic and see if you libjack.so.0 is installed, and if it is, it wouldn't hurt to re-install it and restart the X-Server.  It's possible though that you are going to have to make a symlink to libjack if it is installed.  As for how to do that, I'm not sure, but maybe someone can help :confused:

---

### Post by cogadh on 2007-11-09
That "fixme" message is due to the fact that your sound card does not do hardware sound mixing and does not have a master volume control. It is not a showstopper bug, many people have that error and it shouldn't cause wine to crash. The only real way to get rid of it is to configure software sound mixing in ALSA and create a virtual master volume control device, or replace your sound card with one that can actually do hardware mixing.

The Jack "fixme" just means that you don't have the Jack library installed. It's not really required anyway unless you intend to use the Jack sound driver, but most people will want to use ALSA or OSS.

Just a note, "fixme" messages are just developer notes about items that have not been implemented or fully completed in Wine yet. They don't mean anything to a normal user, unless the particular missing feature they refer to is required by the application you are trying to run.

As for your crash/lockup, the first thing you should try is a complete uninstall and purge of Wine, then re-install it:
```
sudo apt-get remove --purge wine
```

---

### Post by sgardino on 2007-11-10
thank you cogadh

---

### Post by deeck on 2008-04-26
Hi everyone.

I had the same problem, when I start winecfg:

 fixme:jack:JACK_drvLoad error loading the jack library libjack.so.0, please install this library to use jack

I need to use "jack" for wineasio, I have installed all the jack libraries and libjack.so.0 exist in /usr/lib/, /usr/lib32/ and /usr/lib64 

:S

any ideas?

thanks you!

---

### Post by mario.almeida on 2009-01-19
sudo apt-get install libjack0

---


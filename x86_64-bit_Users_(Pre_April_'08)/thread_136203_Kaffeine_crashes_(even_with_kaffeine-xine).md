---
title: "Kaffeine crashes (even with kaffeine-xine)"
date: 2006-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by tribut on 2006-02-25
Hey.

Kaffeine always crashes when I try to play *any* file. Amarok plays music just fine (through both gstreamer and xine). 
This is the only message kaffeine prints (with kaffeine-gstreamer enabled) before it dies:
```
warning: leaving MCOP Dispatcher and still 2 object references alive.
```
With kaffeine-xine it just segfaults.

Any ideas? I already tried deleting ~/.kde/share/config/kaffeinerc, but that doesn't change anything. So far everything worked fine on my new amd64 system. But this is kinda disappointing.


felix
(KDE 3.5.1, Kaffeine 0.7.1)

---

### Post by Trab on 2006-02-25
ummm try reinstalling it?
i dunno the KDE way to do it...is there somehting similiar to apt-get or synaptic?

---

### Post by tribut on 2006-02-25
[QUOTE=Trab]ummm try reinstalling it?[/QUOTE]
Thanks for the suggestion, but I had already tried
```
apt-get install --reinstall kaffeine kaffeine-xine kaffeine-gstreamer
```
with no luck :cry: 

felix

---

### Post by tribut on 2006-02-27
OK, I investigated a little further and it happens only with arts as sound backend! Here is the output of kaffeine --verbose before it dies:
```
load_plugins: plugin mad will be used for audio streamtype 01.
audio_arts_out: ao_open bits=16 rate=44100, mode=8
audio_arts_out: 2 channels output
load_plugins: plugin dxr3-mpeg2 failed to instantiate itself.
video_out_xv: VO_PROP_INTERLACED(0)
load_plugins: plugin mpeg2 will be used for video streamtype 00.
KCrash: Application 'kaffeine' crashing...
```
It seems to be crashing somewhere in libxine - of course the backtrace is not really helpfull with a non-debug kaffeine:
```
(gdb) bt
#0  0x00002aaaacfc86f8 in qstrdup () from /usr/lib/libqt-mt.so.3
#1  0x00002aaaacd0054f in QObject::setName () from /usr/lib/libqt-mt.so.3
#2  0x00002aaaacc6bb88 in QWidget::setName () from /usr/lib/libqt-mt.so.3
[...]
#9  0x00002aaaaae04845 in _x_ao_mode2channels () from /usr/lib/libxine.so.1
#10 0x00002aaaaae061d0 in _x_ao_mode2channels () from /usr/lib/libxine.so.1
[...]
#19 0x00002aaaaae005a2 in _x_waveformatex_le2me () from /usr/lib/libxine.so.1
#20 0x00002aaaae9a90fa in start_thread () from /lib/libpthread.so.0
```
Anyone know how to further investigate the problem? Should I file a bug-report?

---


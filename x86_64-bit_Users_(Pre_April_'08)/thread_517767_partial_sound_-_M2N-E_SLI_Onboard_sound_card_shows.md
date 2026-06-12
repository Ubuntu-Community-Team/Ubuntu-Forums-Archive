---
title: "partial sound - M2N-E SLI Onboard sound card shows up as USB Audio"
date: 2007-08-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Elvis1985 on 2007-08-04
Hi,

My new pc, with a M2N-E SLI motherboard, runs the AMD64 version of Ubuntu 7.04 Feisty Fawn.
My onboard sound card shows up as PnP audio device in System>Preferences>Sound.

The sound test with the ALSA, ESD, or OSS drivers will give me the error message "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not establish connection to sound server".

I can get sound when I select USB-Audio, and in totem the sound works as well.
Unfortunately, when I try to view flash movies in my browser, or play the same files in Mplayer, there will be no sound.
Also, if I try to open alsamixer, it will tell me "alsamixer: function snd_ctl_open failed for default: No such device".

Is there any way to get 1 of the 'regular' mixers to manage usb sound, or could i somehow get Ubuntu to recognize my sound card as an actual sound card instead of a usb device?

I have already tried removing the physical connection to my front panel (which had plugs for a headset, so I was hoping that would be the reason), but that gave me the same errors, and disabling usb sound in the bios just eliminated the device entirely.

This is the device entry from 'lshw':

 *-usb:0
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: iomemory:fe02f000-fe02ffff irq:23
        *-usbhost
             product: OHCI Host Controller
             vendor: Linux 2.6.20-16-generic ohci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 2.06
             capabilities: usb-1.10
             configuration: driver=hub maxpower=0mA slots=9 speed=12.0MB/s
           *-usb
                description: Audio device
                product: PnP Audio Device
                physical id: 7
                bus info: usb@1:7
                version: 0.10
                capabilities: usb-1.10 audio-control
                configuration: driver=snd-usb-audio maxpower=500mA speed=12.0MB/s


My other option is to go and buy a pci sound card, but i find that kind of silly when I'm already supposed to have 6-channel onboard sound support. Also, it would fill up my last pci-slot, which i might still want to use for something else...

Any help would be very welcome and greatly appreciated!

---

### Post by nss0000 on 2007-08-05
BigE:

No, I think you're scr*wed with UBUNTU & any M2N-mobo. I got a generic SB16 workalike card to solve the problem running DAPPERx64.

---

### Post by zeroconf on 2007-08-22
I use also Asus M2N-E SLI motherboard with Kubuntu 7.04 and no sound. Amarok, mplayer will play but no sound is heard. What to do? At the [M2N-E SLI  homepage]("http://www.asus.com/products4.aspx?modelmenu=2&model=1419&l1=3&l2=101&l3=370&l4=0") there is at [audio driver download section]("http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M2N-E%20SLI") written CM6501 as the audio chip. As promised [here](http://www.qbik.ch/usb/devices/showdev.php?id=3925), there will be full support in ALSA 1.0.14, which [is used in Gutsy Gibbon (Ubuntu 7.10)](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=alsa&searchon=names&subword=1&version=gutsy&release=all). So we will see, if it will work there...
```
cat /proc/asound/version
``` will show the ALSA version.

This CM6501 theme is also spoken [here](http://ubuntuforums.org/showthread.php?p=3232232). Also [here](http://www.linuxquestions.org/questions/showthread.php?t=508691) is one forum about that.
[Here](ftp://dlsvr02.asus.com/pub/ASUS/misc/audio/c-media/) is new versions of CM6501 drivers for Windows and some older versions for Linux.
[Here](http://www.cmedia.com.tw/forums/viewtopic.php?t=807) is the forum at CMedia webpage about CM6501.

Also this trick didn't help, that if you create ~/.asound file wich contains this:
```

pcm.usb-audio {
type hw
card 0
}

ctl.usb-audio {
type hw
card 0
}

```

One trick is also disable USB legacy support in BIOS....

At the command line:
```
$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such device
```
```
$ lsmod | grep snd
snd_usb_audio          79744  1
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  2 snd_usb_audio,snd_pcm_oss
snd_page_alloc         10888  1 snd_pcm
snd_usb_lib            17280  1 snd_usb_audio
snd_hwdep               9988  1 snd_usb_audio
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
usbcore               134280  6 snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,ohci_hcd
```
```
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).
```
```
$ uname -r
2.6.20-16-generic
```

---

### Post by Cerny on 2007-08-30
Yah i've had the same problem when I try to test my system. I thought i was going crazy because it would run fine with my dual boot and i would run XP. But those hints seem to help.. well i'll do what i can and in the mean time i'll just hope for the best with gusty.

---

### Post by Cerny on 2007-08-30
Wait, did the trick work when you tired to disable the USB connection in the BIOS or did you end up starting at square one again?

---


---
title: "X-Fi OSS ESD Hardy Issue"
date: 2008-06-24
forum: x86 64-bit Users
---

### Post by wingle on 2008-06-24
I've been having enormous problems getting my audio to work in Hardy Heron with my X-Fi Xtreme Gamer.  I've been following various guides (mostly on these forums) and I'm almost there.

The issue now is that while the esd process is running I get no audio from applications.  The log-in and log-out sounds work fine.  If I kill the esd process then the _next_ application I load (VLC, Firefox, whatever) will have great sound.  All subsequently loaded applications will have no sound.

This is my ossinfo:
```
 ossinfo -v3
Version info: OSS 4.0 (b1016/200806162350) (0x00040003) 
Platform: Linux/x86_64 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 (ben-desktop)

Number of audio devices:	2
Number of audio engines:	2
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: sbxfi0 Sound Blaster X-Fi (SB073x) interrupts=207021 (207021)
    PCI device 1102:0005, subdevice 1102:0031
 2: ossusb0 USB audio core services


Mixer devices
 0: Sound Blaster X-Fi (SB073x) (Mixer 0 of device object 1)
    Device file /dev/oss/sbxfi0/mix0, Legacy device /dev/mixer0
    Priority: 1
    Caps: 
    Device handle: PCI00311102-0000:05:00.0-mx01
    Device priority: 1


Audio devices
Sound Blaster X-Fi (SB073x) output  /dev/oss/sbxfi0/pcm0  (device index 0)
    Legacy device /dev/dsp0
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 0/Sound Blaster X-Fi (SB073x) output
                     Busy (OUT) by PID 7636 / npviewer.bin label 'npviewer.bin' 
    Input formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Output formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Device handle: PCI00311102-0000:05:00.0-au01
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 48000 - 92600
    HW Type: Not indicated.
    Minimum latency: Not indicated

Sound Blaster X-Fi (SB073x) input  /dev/oss/sbxfi0/pcmin0  (device index 1)
    Legacy device /dev/dsp1
    Caps: TRIGGER MMAP 
    Modes: INPUT  
      In engine   1: 1/Sound Blaster X-Fi (SB073x) input
                     Available for use 
    Input formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Output formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Device handle: PCI00311102-0000:05:00.0-au02
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 48000 - 96000
    HW Type: Not indicated.
    Minimum latency: Not indicated
```

Is anyone able to decipher that lot and give me a hint please?

Any advice would be most welcome.
wingle

---

### Post by beniwtv on 2008-06-25
Hi,

```
Busy (OUT) by PID 7636 / npviewer.bin label 'npviewer.bin'
```

This is using your sound... the flash plugin. With OSS, only one application at a time can access the sound card, unless you use a hardware mixer.

I suppose the X-Fi has a hardware mixer, maybe you need to enable it... or configure the applications to use it.

That's one of the reasons of using ALSA by default in Ubuntu. 

I don't have any experience with OSS, as I use Pulseaudio + ALSA, but it might point you in the right direction. *hopes*

Cheers,

---


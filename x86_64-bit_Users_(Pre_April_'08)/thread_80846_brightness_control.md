---
title: "brightness control??"
date: 2005-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by erez1012 on 2005-10-23
the brightness in my mac i book is very high
how can i change thet???
thanks

---

### Post by Rxke on 2005-10-23
Normally with the f1/f2 keys, just like in OS X, but in combination with the 'fn' key.

If this does not work, install pbbuttons (should be installed as standard)

---

### Post by erez1012 on 2005-10-24
:):)

thanks
you are the man!!

---

### Post by Rxke on 2005-10-24
You're welcome :D

Often questions like these do not get an answer, because they are considered "basic" or "obvious" etc. But just because of this, actually searching for an answer gets harder this way :s

---

### Post by pauljwells on 2005-10-24
Smetimes you do't even know there's a question to be asked! I found on my 12" AlPB that the volume control buttons work fine, but the brightness ones don't do anything. I tried editing the conf file for pbbuttons to no avail. I changed the keys from 228 and 229 to 111 and 112, since the volume ones were 113, 114 and 115 - seemed logical but...

Anyone any ideas?

---

### Post by grim1234 on 2006-03-14
Same problem here, the volume controls work fine but the brightness control does nothing when fn+F1 or fn+F2 is pressed.

pbbuttonsd.conf : 

```

# Configuration file for PBButtonsd >= Version 0.5
# for complete list of options please see pbbuttonsd.conf man-page

# [SYSTEM]
#userallowed           = "paranoid"	; user who is allowed to use IPC
autorescan            = no		; automatic rescan of event devices
CmdTimeout            = 8

# [MODULE POWERSAVE]
onAC_policy           = performance	; nochange, performance, custom or powersave
onAC_TimerAction      = none		; none, suspend-to-ram, suspend-to-disk, blankscreen
onAC_CoverAction      = suspend-to-ram
onAC_KeyAction        = none		; SleepKey
onAC_SuspendTime      = 0		; time in 1/10 seconds
onAC_DimTime          = 0		; time in 1/10 seconds

onBattery_policy      = powersave
onBattery_TimerAction = none		; none, suspend-to-ram, suspend-to-disk, blankscreen
onBattery_CoverAction = suspend-to-ram
onBattery_KeyAction   = none		; SleepKey
onBattery_SuspendTime = 0		; time in 1/10 seconds
onBattery_DimTime     = 0		; time in 1/10 seconds

SleepKey              = 116
SleepKeyDelay         = 0		; values > 0 may be dangerous, if the power key is used to trigger sleep
BWL_first             = 22		; first battery warnlevel, time in minutes
BWL_second            = 10		; second battery warnlevel, time in minutes
BWL_last              = 3		; last battery warnlevel, time in minutes
Script_PMCS           = "/etc/power/pmcs-pbbuttonsd %s %s %s"
EmergencyAction       = sleep		; action, if battery is critically low
HeartbeatBeep         = no		; beep, if nothing else showed that the computer lives
CPULoad_sleeplock     = yes
CPULoad_min           = 20		; value in percent
CPULoad_period        = 20		; time in seconds
NETLoad_sleeplock     = yes
NETLoad_min           = 4096		; traffic in Bytes/s
NETLoad_period        = 20		; time in seconds
NETLoad_device        = "eth0"

# [MODULE DISPLAY]
#LCD_Brightness        = 8		; initial LCD brightness level
LCD_FadingSpeed       = 5		; 0 = no smooth fading
LCD_AutoAdjust        = yes		; only on Aluminum PowerBooks
LCD_IllumUpKey        = 225
LCD_IllumDownKey      = 224
LCD_Threshold         = 94
LCD_AutoAdjMin_Bat    = 2		; autoadjust parameter
LCD_AutoAdjMax_Bat    = 7
LCD_AutoAdjMin_AC     = 1
LCD_AutoAdjMax_AC     = 15
#KBD_Brightness        = 0		; initial keyboard illumination level
KBD_OnBrightness      = 5		; initial level if KBD on/off key is pressed
KBD_FadingSpeed       = 5		; 0 = no smooth fading
KBD_AutoAdjust        = yes		; only on Aluminum PowerBooks
KBD_IllumUpKey        = 230
KBD_IllumDownKey      = 229
KBD_IllumOnKey        = 228
KBD_Threshold         = 28		; only on Aluminum PowerBooks
dev_FrameBuffer       = "/dev/fb0"
UseFBBlank            = yes
DimFullyDark          = no
CRT_MirrorKey         = 65 + ctrl

# [MODULE MIXER]
SoundSystem           = OSS		; none, auto, OSS or ALSA
#Volume                = 50		; initial volume level
Speakers_muted        = no		; mute after startup?
VolumeUpKey           = 115
VolumeDownKey         = 114
MuteKey               = 0		; default: 113; disabled since
					; gnome-settings-daemon already handles this
OSS_Mixer             = "/dev/mixer"	; settings for OSS
OSS_Channels          = "volume, speaker"
ALSA_Card             = "default"	; settings for ALSA
ALSA_Elements         = "Master, 'PC Speaker'"
MixerInitDelay        = no

# [MODULE CDROM]
dev_CDROM             = "/dev/cdrom"
EjectCDKey            = 161
EjectCDKeyDelay       = 0

# [MODULE PMAC]
dev_PMU               = "/dev/pmu"
dev_ADB               = "/dev/adb"
TPModeUpKey           = 225 + alt
TPModeDownKey         = 224 + alt
TPMode                = notap
KBDMode               = fkeysfirst
Batlog                = none
NoTapTyping           = no


```

powerbook is a 12" G4 Aluminium DVI 1ghz.

Some of the keys are in the wrong positions, this could be related. Most work okay, but shift+2 gives " rather than the @ that is printed.Anyone know which keyboard map this is? The backslash is above the right shift key. I'll try to get a photo posted later.

Thanks.

---

### Post by Rxke on 2006-03-14
Seems to be a problem, particular to Al Books, then?
I don't know, maybe the LCD_autoadjust prevents actual adjustment? (very wild guuess, I've no autoadjust on my ancient Clamshell) all the [MODULE DISPLAY] parameters are identical to my conf, anyway... Even AutoAdjust (which it doesn't have, hmm?)

re: the keyboardlayout, no idea, except it isn't French (of Flemish (which -totally offtopic- uses French layout, instead of Dutch, which is kind of crazy, because that's the same language, heh. But that's geopolitical history, I guess, back from the times the intellectuals in Flanders spoke French instead of their own language)

---

### Post by Rxke on 2006-03-14
Oh, probablysuperfluous, but on Ubuntu, you have to press Fn+Fx keys repeatedly, not like in OS X, where keeping them pressed down increases/decreases brightness. And sometimes the first press doesn't react very instantaneously, depending on what's going on elsewhere (lots of other apps open etc.)

---

### Post by ssam on 2006-03-14
could you check a dapper live cd to see if the brightness keys work [http://cdimage.ubuntu.com/releases/dapper/flight-5/](http://cdimage.ubuntu.com/releases/dapper/flight-5/) if not can you file a bug on launchpad.

i think the keymap to get @ for shift 2 is english international, or english ISO or something similar. i stick with it the wrong way around so that i can use #, and not lose £.

---

### Post by grim1234 on 2006-03-22
Hi, Sorry for the delay, i've now tested with the flight 5 live cd and niether the brightness nor the volume controls work. I will submit a launchpad bug report. 

In addition, I'd be happy to test any aspects of ubuntu, as I've got a spare partition, and don't use ubuntu on the powerbook for anything critical. I'd certainly like to get involved a bit more.

---

### Post by n00bWillingToLearn on 2006-04-06
I am haveing the same problem (volume works but brightness doesn't) on a 17'' powerbook. I don't care much about the function keys not working but is there another way I can change the brightness?

---

### Post by projectle on 2006-05-05
Already tested with this and no avail...
pbbcmb LCDAUTOADJUST 0
pbbcmd KBDAUTOADJUST 0
pbbcmd LCDBRIGHTNESS 15
pbbcdm KBDBRIGHTNESS 15

Works just fine under Suse, Fedora & Gentoo.
Not Ubuntu.

---

### Post by projectle on 2006-05-06
Actually, let me fix that...

pbbcmd config LCDAUTOADJUST 0
pbbcmd config KBDAUTOADJUST 0
pbbcmd config LCDBRIGHTNESS 15
pbbcmd config KBDBRIGHTNESS 15

Also, I believe that I have identified the problem...

[http://bugzilla.kernel.org/show_bug.cgi?id=6385](http://bugzilla.kernel.org/show_bug.cgi?id=6385)

It would seem that there is a current issue with the complete 2.6.16 kernel tree (resolved in 2.6.17_rc3) with the keywest I2C driver. Aparently, this is what is utilized for the ambient light sensor, backlight adjustment settings, audio/video controlls, thermal management and several other items called by pbbuttonsd.

I do realize that we are in the 2.6.15 kernel tree at the moment, but there is nothing that says that patch or two didnt accidentally get pulled in.

---


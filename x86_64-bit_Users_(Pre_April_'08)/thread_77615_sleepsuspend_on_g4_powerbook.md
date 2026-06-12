---
title: "sleep/suspend on g4 powerbook"
date: 2005-10-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by tr333 on 2005-10-17
anyone know how to get sleep/suspend working in breezy?  i have a G4 powerbook.

---

### Post by Joe_lurker on 2005-10-17
Mine worked fine "out of the box".  What does yours do when you close the lid?

Joe

---

### Post by tr333 on 2005-10-17
it seems to do nothing.
the screen doesn't turn off, and the sleep-light doesn't turn on.

---

### Post by tr333 on 2005-10-17
is the sleep/suspend controlled by the operating system, or the hardware?

---

### Post by Joe_lurker on 2005-10-17
Both!  There is a switch in the laptop that notifies the bios.  The bios then notifies the OS.

Does the computer sleep under OSX?

Joe

---

### Post by cooldude127 on 2005-10-17
it works perfectly for me with an ibook g4 933MHz. what kernel version are you using?

---

### Post by tr333 on 2005-10-18
the computer sleeps perfectly under OSX.
how do i determine the kernel version?

---

### Post by emax on 2005-10-18
I have just installed 5.10 on my Powerbook (having just deflected from Fedora Core 4!).

I was very impressed seeing how well sleep works on my friend's iBook 800 G4.

However on my PowerBook G4 (1.33GHz), closing the lid does nothing.  the dmesg command shows no sign of capturing the fact that the lid has been closed either.

Could it be that sleep isn't supported on certain G4 PowerBooks or do I have a configuration problem?

Sleep works perfectly in OS X Tiger BTW.

---

### Post by Joe_lurker on 2005-10-18
From a terminal enter the following command:

ps -e | grep pbbuttonsd

You should see output such as:

 4393 ?        00:00:10 pbbuttonsd

If you do not then the power daemon is not running.  This is what controls the power and mac keys (sound, led brightness, etc.)

-Joe

---

### Post by tr333 on 2005-10-18
the output of that command is 

" 4490 ?        00:00:00 pbbuttonsd"

i have no idea what that is telling me.

---

### Post by Joe_lurker on 2005-10-18
It's telling you that the pbbutonnsd service is watching for "events" such as lid closing and eject key press.  You can view the man page for pbbuttonsd for more information ('man pbbuttons' at the terminal prompt).

Try entering the following command in a terminal:

pbbcmd sleep

This should put the computer to sleep.  Pressing a key should wake it up.

-Joe

---

### Post by emax on 2005-10-18
[QUOTE=tr333]the output of that command is 

" 4490 ?        00:00:00 pbbuttonsd"

i have no idea what that is telling me.[/QUOTE]

It's telling you that pbbuttonsd is running on your machine.

It's running on mine too but I still can't get the PowerBook to sleep :-(

EDIT:  Didn't see Joe's post above....

Just tried pbbcmd sleep...  still no joy!

---

### Post by Joe_lurker on 2005-10-18
Maybe there is something running keeping the system awake.  Try this:

Re-boot the computer into single-user mode - at the boot: prompt enter 'Linux single'.
At the terminal prompt enter 'pbbuttonsd -d' to start the button service.
Again at the terminal prompt enter 'pbbcmd sleep'.

If this doesn't put the computer to sleep I am stymied.

-Joe

---

### Post by sulobanks on 2005-10-18
I had the same problem with my ibook g4.  I edited /etc/pbbuttonsd.conf and replaced 'suspend-to-ram' with 'suspend-to-disk'.  Now it works fine.  Blankscreen doesn't unblank for me.  Suspend-to-ram crashes the comp completely.  But suspend-to-disk seems to do the trick with no problems. Even my usb mouse wakes up (which didn't happen with hoary).

Amendment:  System->Logout->Suspend the computer actually suspends the comp. Shutting the lid just blanks the screen for me. Even though I've set both onAC_CoverAction and onBattery_CoverAction to suspend-to-disk. I restarted pbbuttonsd and restarted the comp with no change.*shrugs* I suppose I'll go look through bugzilla and see if some of these bugs are listed.

---

### Post by tr333 on 2005-10-19
i was reading through the man page for pbbuttonsd.conf and i found "dev_pmu" under the PMAC module.  would this setting have any effect on sleep?

---

### Post by emax on 2005-10-19
[QUOTE=Joe_lurker]Re-boot the computer into single-user mode - at the boot: prompt enter 'Linux single'.
At the terminal prompt enter 'pbbuttonsd -d' to start the button service.
Again at the terminal prompt enter 'pbbcmd sleep'.

If this doesn't put the computer to sleep I am stymied.
-Joe[/QUOTE]

Thanks Joe, just tried this with no joy again :-(

[QUOTE=sulobanks]I had the same problem with my ibook g4.  I edited /etc/pbbuttonsd.conf and replaced 'suspend-to-ram' with 'suspend-to-disk'.  Now it works fine.  Blankscreen doesn't unblank for me.  Suspend-to-ram crashes the comp completely.  But suspend-to-disk seems to do the trick with no problems.[/QUOTE]

Not for me :-(  I tried the above as well as the blankscreen option but to no avail.  The screen stays on when I close the lid

[QUOTE=sulobanks]Amendment:  System->Logout->Suspend the computer actually suspends the comp. Shutting the lid just blanks the screen for me. Even though I've set both onAC_CoverAction and onBattery_CoverAction to suspend-to-disk. I restarted pbbuttonsd and restarted the comp with no change.*shrugs* I suppose I'll go look through bugzilla and see if some of these bugs are listed.[/QUOTE]

Sounds more like the behaviour I get.  I can't see a suspend option under "System->Logout".  I just get "Log Out" "Shut Down" or "Restart the computer" (under GNOME).

---

### Post by tr333 on 2005-10-19
[QUOTE=emax]Sounds more like the behaviour I get.  I can't see a suspend option under "System->Logout".  I just get "Log Out" "Shut Down" or "Restart the computer" (under GNOME).[/QUOTE]
same occurs for me.  no suspend option.

joe:  the reboot didnt change anything.  still nothing.  its not that important, but it would be nice to get it working.

---

### Post by Joe_lurker on 2005-10-21
This is still in the back of my mind.  I have been busy but I will keep thinking about the issue.  I have been trying to replicate it on my powerbook to no avail yet.

Joe

---

### Post by pauljwells on 2005-10-24
FWIW I have similar issues wth my 12" AlPB. pbbuttonsd is running, but the only things that seem to work are the sound volume keys (press fn and the key). No LCD, no sleep, no 'suspend' in the gnome menu. There doesn't seem to be much info out in googleland either...

---

### Post by Joe_lurker on 2005-10-24
Could somebody who's sleep doesnt' work please post their /etc/pbbuttons.conf and /etc/yaboot.conf.

Joe

---

### Post by tr333 on 2005-10-25
pbbuttonsd.conf:
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

yaboot.conf:
```
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/hda2
device=/pci@f4000000/ata-6@d/disk@0:
partition=4
root=/dev/hda4
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hda3

fgcolor=light-green
bgcolor=purple
defaultos=macosx

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"

```

---

### Post by Joe_lurker on 2005-10-25
What is the output from the command:

'pbbcmd query TAG_SLEEPSUPPORTED'

-Joe

---

### Post by emax on 2005-10-25
[QUOTE=Joe_lurker]What is the output from the command:

'pbbcmd query TAG_SLEEPSUPPORTED'

-Joe[/QUOTE]

On my machine:

euan@rmac:~$ pbbcmd query TAG_SLEEPSUPPORTED
0
euan@rmac:~$

---

### Post by Joe_lurker on 2005-10-25
That means sleep is not supported.  What version of the kernel are you using?  You can find this with 'uname -r'.

Joe

---

### Post by tr333 on 2005-10-25
i get the same result.  my kernel version is 2.6.12-9-powerpc

---

### Post by Joe_lurker on 2005-10-25
I think we missed this before.  Make sure you have a /dev/pmu node.  To find out enter 'ls -l /dev/pmu'.  You should see outout like this:

crw-rw----  1 root root 10, 154 2005-10-25 12:39 /dev/pmu

If you don't have this node then create it.  Enter the following commands:

cd /dev
sudo ./MAKEDEV pmu

-Joe

---

### Post by tr333 on 2005-10-26
the pmu device already exists on my machine.

---

### Post by barontola on 2005-10-26
[QUOTE=Joe_lurker]I think we missed this before.  Make sure you have a /dev/pmu node.  To find out enter 'ls -l /dev/pmu'.  You should see outout like this:

crw-rw----  1 root root 10, 154 2005-10-25 12:39 /dev/pmu

If you don't have this node then create it.  Enter the following commands:

cd /dev
sudo ./MAKEDEV pmu

-Joe[/QUOTE]

having the same problem myself on my 12" powerbook g4 867mhz, i tried the MAKEDEV command but got this output:

```
./MAKEDEV: don't know how to make device "pmu"
```

---

### Post by emax on 2005-10-26
[QUOTE=tr333]the pmu device already exists on my machine.[/QUOTE]

Same here:

euan@rmac:~$ ls -l /dev/pmu
crw-rw----  1 root root 10, 154 2005-10-26 10:35 /dev/pmu
euan@rmac:~$

and I'm running the following stock ubuntu kernel:

euan@rmac:~$ uname -r
2.6.12-9-powerpc
euan@rmac:~$

---

### Post by tr333 on 2005-10-28
[QUOTE=barontola]having the same problem myself on my 12" powerbook g4 867mhz, i tried the MAKEDEV command but got this output:

```
./MAKEDEV: don't know how to make device "pmu"
```[/QUOTE]
did you run the command with sudo?

---

### Post by emax on 2005-11-02
[QUOTE=Joe_lurker]I think we missed this before.  Make sure you have a /dev/pmu node.  To find out enter 'ls -l /dev/pmu'.  You should see outout like this:

crw-rw----  1 root root 10, 154 2005-10-25 12:39 /dev/pmu[/QUOTE]

I had this node - didn't have to create it.

I'm running the stock ubuntu 2.6.12-9-powerpc kernel (fresh install).

I know that pbbuttonsd is running although it seems that sleep is not supported:

pbbcmd query TAG_SLEEPSUPPORTED returns a 0.

Anything else I can check to see what might be the cause?

I have tried editing my pbbuttons.conf file and changing the behaviour on lid closure to blank the screen, that doesn't work either.

My brightness keys don't work but my volume keys do.

Any help would be much appreciated.

---

### Post by joacim on 2005-11-02
I have the same problem with suspend on my iBook G4, but my pbbuttonsd is not running. 

Running: sudo /etc/init.d/pbbuttonsd start

results in this:

Starting pbbuttonsd: ERROR: Can't open mixer device [/dev/mixer]. File missing.

And I don't have a /dev/mixer file.

Trying to make the device file:

sudo ./MAKEDEV /dev/mixer or sudo MAKEDEV /dev/mixer

results in:

/sbin/MAKEDEV: don't know how to make device "/dev/mixer"

Suspend worked fine under Hoary (after removing dri in xorg.conf), but after the upgrade to Breezy (done after the final version was released) it no longer goes into sleep after I've closed the lid, nothing happens. The volume icon in the gnome-panel is also gone.

Any suggestions would be appreciated. :)

Cheers,

Joacim

---

### Post by Joe_lurker on 2005-11-02
It sounds like you have sound configuration problems.  That would be a different thread.  But the sleep problem can probably be fixed by modifying your '/etc/pbbuttonsd.conf' file.  On or about the line 64 you will see "[MODULE MIXER]".  Change the line "SoundSystem = OSS" to read "SoundSystem = none".    

-Joe

---

### Post by joacim on 2005-11-02
changing the setting in /etc/pbbuttonsd.conf from "SoundSystem = OSS" to "SoundSystem = auto", fixed my suspend issue! 

Thanks a lot, made my Breezy experience much better. :D 

I'll figure out the sound issue later, not really a problem, since the volume/keyboard buttons work and sound seems to work allright, only the volume-icon that's missing that I notice so far.

Thanks!

Joacim

---

### Post by emax on 2005-11-03
[QUOTE=Joe_lurker]It sounds like you have sound configuration problems.  That would be a different thread.  But the sleep problem can probably be fixed by modifying your '/etc/pbbuttonsd.conf' file.  On or about the line 64 you will see "[MODULE MIXER]".  Change the line "SoundSystem = OSS" to read "SoundSystem = none".    [/QUOTE]

Details of my setup are detailed further up.  I thought I'd post my pbbuttons.conf.  Am I missing something here??
```

# Configuration file for PBButtonsd >= Version 0.5
# for complete list of options please see pbbuttonsd.conf man-page

# [SYSTEM]
#userallowed           = "paranoid"     ; user who is allowed to use IPC
autorescan            = no              ; automatic rescan of event devices
CmdTimeout            = 8

# [MODULE POWERSAVE]
onAC_policy           = performance     ; nochange, performance, custom or powersave
onAC_TimerAction      = none            ; none, suspend-to-ram, suspend-to-disk, blankscreen
onAC_CoverAction      = suspend-to-ram
onAC_KeyAction        = none            ; SleepKey
onAC_SuspendTime      = 0               ; time in 1/10 seconds
onAC_DimTime          = 0               ; time in 1/10 seconds

onBattery_policy      = powersave
onBattery_TimerAction = none            ; none, suspend-to-ram, suspend-to-disk, blankscreen
onBattery_CoverAction = suspend-to-ram
onBattery_KeyAction   = none            ; SleepKey
onBattery_SuspendTime = 0               ; time in 1/10 seconds
onBattery_DimTime     = 0               ; time in 1/10 seconds

SleepKey              = 116
SleepKeyDelay         = 0               ; values > 0 may be dangerous, if the power key is used to trigger sleep
BWL_first             = 22              ; first battery warnlevel, time in minutes
BWL_second            = 10              ; second battery warnlevel, time in minutes
BWL_last              = 3               ; last battery warnlevel, time in minutes
Script_PMCS           = "/etc/power/pmcs-pbbuttonsd %s %s %s"
EmergencyAction       = sleep           ; action, if battery is critically low
HeartbeatBeep         = no              ; beep, if nothing else showed that the computer lives
CPULoad_sleeplock     = yes
CPULoad_min           = 20              ; value in percent
CPULoad_period        = 20              ; time in seconds
NETLoad_sleeplock     = yes
NETLoad_min           = 4096            ; traffic in Bytes/s
NETLoad_period        = 20              ; time in seconds
NETLoad_device        = "eth0"

# [MODULE DISPLAY]
#LCD_Brightness        = 8              ; initial LCD brightness level
LCD_FadingSpeed       = 5               ; 0 = no smooth fading
LCD_AutoAdjust        = yes             ; only on Aluminum PowerBooks
LCD_IllumUpKey        = 225
LCD_IllumDownKey      = 224
LCD_Threshold         = 94
LCD_AutoAdjMin_Bat    = 2               ; autoadjust parameter
LCD_AutoAdjMax_Bat    = 7
LCD_AutoAdjMin_AC     = 1
LCD_AutoAdjMax_AC     = 15
#KBD_Brightness        = 0              ; initial keyboard illumination level
KBD_OnBrightness      = 5               ; initial level if KBD on/off key is pressed
KBD_FadingSpeed       = 5               ; 0 = no smooth fading
KBD_AutoAdjust        = yes             ; only on Aluminum PowerBooks
KBD_IllumUpKey        = 230
KBD_IllumDownKey      = 229
KBD_IllumOnKey        = 228
KBD_Threshold         = 28              ; only on Aluminum PowerBooks
dev_FrameBuffer       = "/dev/fb0"
UseFBBlank            = yes
DimFullyDark          = no
CRT_MirrorKey         = 65 + ctrl

# [MODULE MIXER]
SoundSystem           = none            ; none, auto, OSS or ALSA
#Volume                = 50             ; initial volume level
Speakers_muted        = no              ; mute after startup?
VolumeUpKey           = 115
VolumeDownKey         = 114
MuteKey               = 0               ; default: 113; disabled since
                                        ; gnome-settings-daemon already handles this
OSS_Mixer             = "/dev/mixer"    ; settings for OSS
OSS_Channels          = "volume, speaker"
ALSA_Card             = "default"       ; settings for ALSA
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

---

### Post by Joe_lurker on 2005-11-05
It looks like not all PowerBook hardware is supported by the kernel.  I was at the understanding that PowerBook support was rather complete but I was wrong.

That leaves compiling your own kernel if you want to try that out.  You would need to have the latest source code and follow the instructions.  It's not too hard except trying to figure out which options you need.  From the sounds of it that probably will not solve the problem for everyone.  I am not sure wich PowerBooks the latest kernel supports.

Sorry - that's the best I could do!

-Joe

---

### Post by tr333 on 2005-11-05
thanks for all your help on this joe.

hope it is fixed in time for dapper.

---

### Post by corin on 2005-11-07
I have exactly the same symptoms (nothing happens when lid closes,
pbbcmd query SLEEPSUPPORTED returns 0) but on my iBook G4 1.33Ghz.

So it seems to be a problem not particular to PBooks but also for iBooks.

regards,
ricardo

---

### Post by pauljwells on 2005-11-12
If your sound is all working ok then you've probably just somehow got the icon deleted. Try a right click on the top panel and you'll see a pulldown menu with something like 'add applet' (I'm not on my ubuntu box at the mo so can't check). This should bring up a window with lots of stuff you can add, including 'volume control'. Add this and it should give you back the little speaker.

---

### Post by scotth on 2005-11-21
I had this same problem under breezy on my ibook g4(with a radeon).  To get it to sleep I had to take out video=ofonly(needed for the install) from /etc/yaboo.conf and run ybin.  That got sleep any everything working.  

Its important to note that as far as I know, only recent radeons are working for sleep.  If you have a geforce, then I don't think sleep will work.  It may have changed, but last time I checked that was the current state of things.

---

### Post by khc on 2005-11-23
[QUOTE=sulobanks]I had the same problem with my ibook g4.  I edited /etc/pbbuttonsd.conf and replaced 'suspend-to-ram' with 'suspend-to-disk'.  Now it works fine.  Blankscreen doesn't unblank for me.  Suspend-to-ram crashes the comp completely.  But suspend-to-disk seems to do the trick with no problems. Even my usb mouse wakes up (which didn't happen with hoary).

Amendment:  System->Logout->Suspend the computer actually suspends the comp. Shutting the lid just blanks the screen for me. Even though I've set both onAC_CoverAction and onBattery_CoverAction to suspend-to-disk. I restarted pbbuttonsd and restarted the comp with no change.*shrugs* I suppose I'll go look through bugzilla and see if some of these bugs are listed.[/QUOTE]

Did it actually do suspend to disk, or just suspend to RAM? IIRC suspend to disk is not supported on linuxppc.

---

### Post by corin on 2005-11-27
[QUOTE=scotth]I had this same problem under breezy on my ibook g4(with a radeon).  To get it to sleep I had to take out video=ofonly(needed for the install) from /etc/yaboo.conf and run ybin.  That got sleep any everything working.  

Its important to note that as far as I know, only recent radeons are working for sleep.  If you have a geforce, then I don't think sleep will work.  It may have changed, but last time I checked that was the current state of things.[/QUOTE]

Thanks scotth, now it works fine!

Now to other issues:
1. sound too low
2. I can't seem to mount the OSX partition with rw permissions for a user other than root (mount doesn't seem to be honouring the uid/gid params...)

thanks!
ricardo

---


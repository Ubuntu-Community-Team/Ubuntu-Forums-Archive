---
title: "No Audio"
date: 2007-11-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by d00by on 2007-11-04
**[COLOR="Red"]I cannot hear any sound.[/COLOR]**

After installing ubuntu I could hear the login sound after logging in.

I updated my nvidia accelerated graphics card in the restricted drivers thingy. (I am a complete n00b)

I think that may have been the source of the problem. I say 'may' because I did not notice the sound issue until a few hours ago when I tried to play an mp4 file. It searched and installed some codecs. That is when I noticed the audio issue. I could see the video but could not hear any audio.

I then tried playing an mp3 file. No sound!!

What have I messed up? Was it because of codecs or the graphic card thingy??

Also, I am [COLOR="Red"][COLOR="Red"]_**not able to access google**_[/COLOR][/COLOR] websites. Google is my LIFE.

i have no problem accessing other sites!

These are the firefox extensions installed.

[HTML]Last updated: Mon, 05 Nov 2007 03:29:14 GMT
User Agent: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.8) Gecko/20071022 Ubuntu/7.10 (gutsy) Firefox/2.0.0.8
Extensions (enabled: 19, disabled: 0):

    * Adblock Plus 0.7.5.3
    * BBCodeXtra 0.2.5.6
    * Download Statusbar 0.9.5.1
    * DSLR Notifier 1.2
    * Flat Bookmark Editing 0.8.1
    * Gmail Notifier 0.6.1
    * Google Notebook 1.0.0.18
    * Greasemonkey 0.7.20070607.0
    * InfoLister 0.9f.2
    * Linkification 1.3.3
    * PDF Download 0.9.3.2
    * RSS Ticker 1.9
    * Secure Login 0.8.1.4
    * ShowIP 0.8.05
    * StumbleUpon 3.12
    * SwitchProxy Tool 1.4.1
    * Tab Mix Plus 0.3.6
    * ubufox 0.4~beta1
    * Yahoo! Mail Notifier 1.0.0.2

Themes (1):

    * Firefox (default) 2.0 [selected]

Plugins (5):

    * DivX® Web Player
    * QuickTime Plug-in 7.2.0
    * Shockwave Flash
    * Totem Web Browser Plugin 2.20.0
    * Windows Media Player Plug-in 10 (compatible; Totem)

[/HTML]

 I disabled Greasemonkey as I thought that It may be messing up my google access. Did not work!! :(


Help! :confused:

---

### Post by d00by on 2007-11-05
Additional info. Does this help in isolating what is causing this audio issue?

lspci -v gives this info on audio device

```
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
```

---

### Post by brianbarry on 2007-11-05
In the past I've the source of my sound issues to be the PCM level in the mixer settings to be at 0 for no reason.  I've also found that re-installing alsa to solve a sound problem.

Brian

---

### Post by d00by on 2007-11-05
How do I access the PCM level?

Also, there are many alsa packages installed in the synaptic package manager. How do I know which also package to re-install.

Just after installing ubuntu, I was able to hear the login sound.

I don't know what I messed up which lead to sound disappearing. It is very frustrating when one cannot get sound going as it is SUCH an integral part of the computer experience! :(

---

### Post by rsambuca on 2007-11-05
Just right-click the sound icon on the top menu bar.  Select "Open Volume Control".  Then make sure that PCM and front are both on.

---

### Post by Attila2452 on 2007-11-05
:confused::lolflag::lolflag:i had the same problem last nite! i fixed it tho ...  i used a some what similar forum but i hope this helps. (mine was way more decriptive!) it was EXACT! 

your sound  card might just be messed up.

Good LUCK.


 - Attila Hajzer -:guitar::guitar:

---

### Post by d00by on 2007-11-05
> **Attila2452 said:**
> :confused::lolflag::lolflag:i had the same problem last nite! i fixed it tho ...  i used a some what similar forum but i hope this helps. (mine was way more decriptive!) it was EXACT! 

your sound  card might just be messed up.

Good LUCK.


 - Attila Hajzer -:guitar::guitar:
can you post that link?

Also, I checked the volume controls. They are fine. 

Still no sound. :(

---

### Post by brianbarry on 2007-11-05
When I re-installed alsa, I just re-installed alsa-base.

Good Luck,
Brian

---

### Post by rykel on 2007-11-05
Nope... bad news, reinstalling alsa- base and making sure all controls in volume control are OK did NOT return my sound...

---

### Post by Attila2452 on 2007-11-05
how do you post a forum..... i can only post a thread....... god i feel stuped...... PLEASE HELP

---

### Post by Attila2452 on 2007-11-05
ok i read a thread a couple days ago about security! i dont have any anti virus stuff on my computer! i need it! i need the best stuff applied for Ubuntu PLEASE someone help poor old Attila out lol 



ASAP! 


 - Attila Hajzer -

---

### Post by rykel on 2007-11-06
Hi all,

My sound is finally back!!!

[INDENT][LIST=1]
[*]Right-Click Volume Applet
[*]Open Volume Control
[*]Edit
[*]Preferences
[*]Headphone Jack Sense
[*]Close
[*]Switches
[*]UN-check Headphone Jack Sense
[/LIST][/INDENT]

My laptop soundcard is ICH6.

Hope that helps.     :guitar:

---

### Post by d00by on 2007-11-06
> **rykel said:**
> Hi all,

My sound is finally back!!!

[INDENT][LIST=1]
[*]Headphone Jack Sense
[/LIST][/INDENT]

My laptop soundcard is ICH6.

Hope that helps.     :guitar:

I don't have this option. see the attached screenshot.

I am making some progress here at this thread.

[http://ubuntuforums.org/showthread.php?t=604496]("http://ubuntuforums.org/showthread.php?t=604496")

 Can you make any suggestion at that link??

---

### Post by dabl on 2007-11-06
> **Attila2452 said:**
> ok i read a thread a couple days ago about security! i dont have any anti virus stuff on my computer! i need it! i need the best stuff applied for Ubuntu PLEASE someone help poor old Attila out lol 



ASAP! 


 - Attila Hajzer -


What makes you think you need anti-virus protection for your Linux system?  There's clamav for anti-virus and guarddog for firewall, but I dumped 'em both after the first month of no action at all.  If you're behind a router, and you changed the factory default IP address, you're more likely to meet Elvis than to get a virus.   :lolflag:


~ poor ole dabl

---

### Post by rykel on 2007-11-06
> **d00by said:**
> I don't have this option. see the attached screenshot.

I am making some progress here at this thread.

[http://ubuntuforums.org/showthread.php?t=604496]("http://ubuntuforums.org/showthread.php?t=604496")

 Can you make any suggestion at that link??

Actually I do not have the answer too... I found my solution on launchpad.net by accident... what I suggest you do is to enable ALL the options, and then enable/disable them and see if you can get your sound back by trial-and-error.

---

### Post by tmask on 2007-11-06
> **rsambuca said:**
> Just right-click the sound icon on the top menu bar.  Select "Open Volume Control".  Then make sure that PCM and front are both on.

OMG THANK YOU!

Nothing else had worked before.  That was the answer all along :3 thank you!:mrgreen::biggrin::grin::D:)

---

### Post by rsambuca on 2007-11-06
Right on!  Now crank up them tunes!

:guitar:

---

### Post by jaybombalous on 2007-11-06
what does ```
asoundconf list
``` return? How did u install those codecs?

---

### Post by ganeshvembu on 2007-11-07
Same here
no audio on my Lenovo N3000 Y410
i have this installed
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Lenovo Unknown device 384e
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f8300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

i am running Ubuntu 7.10 x64
sound works when i suspend the machine and bring it back to life, but not if the machine reboots or hibernates
any thoughts??
thanks

---


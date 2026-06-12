---
title: "Sound issues in xine and xmms"
date: 2006-01-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by t0bb3 on 2006-01-27
Hi

When I type "xine name.of.movie.with.ac3.sound.avi" on the command line I get an error about the audio device being unavailable. If I open the same movie using the xine gui I don't get that message and I hear the sound just fine. Why is that?

I have a simular problem with xmms. When I first try to play a music file it says it couldn't open audio and that I should check that no other program is blocking the soundcard. If I then rightclick on xmms and choose something from the menu, like "about", and then click on OK I can now play music without any error message. In fact, I just have to double click on xmms and it won't show the message about not being able to open the audio device

mplayer can play sound just fine, and the Gnome UI sounds play just fine.

All sound goes through spdif to my surround sound reciever.

Any ideas?

---

### Post by jpkotta on 2006-01-27
Which audio output plugin are you using?  If GNOME audio works, then the esd plugin will probably work best.  This applies to both xmms and xine.  

A possible cause of the trouble is the fact that OSS (the legacy sound system) can only handle one sound at a time.  If you use ALSA (properly configured) or a sound daemon like ESD or ARTS, then you can play many sounds at once.

---

### Post by t0bb3 on 2006-01-27
Thanks for the fast response :)
I changed the audio output plugin in xmms from alsa to eSound Ouput Plugin. That took care of that problem.

Changing to esd in xine makes the problem go away there as well, but it brings a  new problem. When I use alsa as the output plugin in xine my surround reciever automaticly recognizes the sound output as ac3 surround sound. If I use esd it doesn't.

So to me it looks like I have to do some configuring in alsa. But where do I start? What needs to change?

Or is there some command I can use to stop any sound currently playing so this new sound can play?

---

### Post by jpkotta on 2006-01-27
Try adding this to ~/.asoundrc (the user ALSA config file).  It enables the dmix plugin, which allows multiple sounds to be played simultaneously.  Use the links for further information.

```

# http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php?module=Generic
# http://alsa.opensrc.org/index.php?page=DmixPlugin
# http://www.linux.com/article.pl?sid=04/08/09/1513255

pcm.dsp0 {
    type plug
    slave.pcm "dmix"
}


# mixer0 can stay unchanged, because
# it isn't used anyway, I guess ;)
ctl.mixer0 {
    type hw
    card 0
}

```

---

### Post by t0bb3 on 2006-01-27
My .asoundrc file is already pretty cusomized. It's from the MythTV wiki. I needed this to get any sound out of the spdif port at all... Here it is the way I had it when it didn't work.```
# Override the default output used by ALSA.
# If you do not override the default, your default
# device is identical to the (unmixed) analog device
# shown below.  If you prefer mixed and/or digital
# output, uncomment the appropriate four lines below
# (only one slave.pcm line).
pcm.!default {
  type plug
## Uncomment the following to use mixed analog by default
#  slave.pcm "dmix-analog"
## Uncomment the following to use unmixed digital by default
#  slave.pcm "digital-hw"
## Uncomment the following to use mixed digital by default
  slave.pcm "dmix-digital"
}

# Alias for analog output on the nForce2/4 (hw:0,0)
# - This is identical to the device named "default"--which
# always exists and refers to hw:0,0 (unless overridden)
# - Therefore, we can specify "hw:0,0", "default", or "analog"
# to access analog output on the nForce2/4
pcm.analog {
 type plug
 slave.pcm "analog-hw"
}

# Control device (mixer, etc.) for the nForce2 card
ctl.analog {
 type hw
 card 0
}

# Alias for (rate-converted) mixed analog output on the
# nForce2 (hw:0,0)
#  - This will accept audio input--regardless of rate--and
# convert to the rate required for the dmix plugin
# (in this case 48000Hz)
pcm.mixed-analog {
 type plug
 slave.pcm "dmix-analog"
}

# Control device (mixer, etc.) for the nForce2 card
ctl.mixed-analog {
 type hw
 card 0
}

# Alias for (rate-converted) digital (S/PDIF) output on the
# nForce2 (hw:0,2)
#  - This will accept audio input--regardless of rate--and
# convert to the rate required for the S/PDIF hardware
# (in this case 48000Hz)
pcm.digital {
 type plug
 slave.pcm "digital-hw"
}

# Control device (mixer, etc.) for the nForce2 card
ctl.digital {
 type hw
 card 0
}

# Alias for mixed (rate-converted) digital (S/PDIF) output on the
# nForce2/4 (hw:0,2)
#  - This will accept audio input--regardless of rate--and
# convert to the rate required for the S/PDIF hardware
# (in this case 48000Hz)
pcm.mixed-digital {
 type plug
 slave.pcm "dmix-digital"
}

# Control device (mixer, etc.) for the nForce2 card
ctl.mixed-digital {
 type hw
 card 0
}

# The following devices are not useful by themselves.  They
# require specific rates, channels, and formats.  Therefore,
# you probably do not want to use them directly.  Instead use
# of of the devices defined above.

# Alias for analog output on the nForce2 (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.analog-hw {
 type hw
 card 0
 # The default value for device is 0, so no need to specify
}

# Control device (mixer, etc.) for the nForce2/4 card
ctl.analog-hw {
 type hw
 card 0
}

# Alias for digital (S/PDIF) output on the nForce2/4 (hw:0,2)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.digital-hw {
 type hw
 card 0
 device 2
}

# Control device (mixer, etc.) for the nForce2/4 card
ctl.digital-hw {
 type hw
 card 0
}

# Direct software mixing plugin for analog output on
# the nForce2/4 (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.dmix-analog {
 type dmix
 ipc_key 1234
 slave {
   pcm "analog-hw"
   period_time 0
   period_size 1024
   buffer_size 4096
   rate 48000
 }
}

# Control device (mixer, etc.) for the nForce2/4 card
ctl.dmix-analog {
 type hw
 card 0
}

# Direct software mixing plugin for digital (S/PDIF) output
# on the nForce2/4 (hw:0,2)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.dmix-digital {
 type dmix
 ipc_key 1235
 slave {
   pcm "digital-hw"
   period_time 0
   period_size 1024
   buffer_size 4096
   rate 48000
 }
}

# Control device (mixer, etc.) for the nForce2/4 card
ctl.dmix-digital {
 type hw
 card 0
}
```

And this is what it looks like now (and this works :) )```
# Override the default output used by ALSA.
# If you do not override the default, your default
# device is identical to the (unmixed) analog device
# shown below.  If you prefer mixed and/or digital
# output, uncomment the appropriate four lines below
# (only one slave.pcm line).
pcm.!default {
  type plug
## Uncomment the following to use mixed analog by default
#  slave.pcm "dmix-analog"
## Uncomment the following to use unmixed digital by default
  slave.pcm "digital-hw"
## Uncomment the following to use mixed digital by default
#  slave.pcm "dmix-digital"
}

# Alias for analog output on the nForce2/4 (hw:0,0)
# - This is identical to the device named "default"--which
# always exists and refers to hw:0,0 (unless overridden)
# - Therefore, we can specify "hw:0,0", "default", or "analog"
# to access analog output on the nForce2/4
pcm.analog {
 type plug
 slave.pcm "analog-hw"
}

# Control device (mixer, etc.) for the nForce2 card
ctl.analog {
 type hw
 card 0
}

# Alias for (rate-converted) mixed analog output on the
# nForce2 (hw:0,0)
#  - This will accept audio input--regardless of rate--and
# convert to the rate required for the dmix plugin
# (in this case 48000Hz)
pcm.mixed-analog {
 type plug
 slave.pcm "dmix-analog"
}

# Control device (mixer, etc.) for the nForce2 card
ctl.mixed-analog {
 type hw
 card 0
}

# Alias for (rate-converted) digital (S/PDIF) output on the
# nForce2 (hw:0,2)
#  - This will accept audio input--regardless of rate--and
# convert to the rate required for the S/PDIF hardware
# (in this case 48000Hz)
pcm.digital {
 type plug
 slave.pcm "digital-hw"
}

# Control device (mixer, etc.) for the nForce2 card
ctl.digital {
 type hw
 card 0
}

# Alias for mixed (rate-converted) digital (S/PDIF) output on the
# nForce2/4 (hw:0,2)
#  - This will accept audio input--regardless of rate--and
# convert to the rate required for the S/PDIF hardware
# (in this case 48000Hz)
pcm.mixed-digital {
 type plug
 slave.pcm "dmix-digital"
}

# Control device (mixer, etc.) for the nForce2 card
ctl.mixed-digital {
 type hw
 card 0
}

# The following devices are not useful by themselves.  They
# require specific rates, channels, and formats.  Therefore,
# you probably do not want to use them directly.  Instead use
# of of the devices defined above.

# Alias for analog output on the nForce2 (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.analog-hw {
 type hw
 card 0
 # The default value for device is 0, so no need to specify
}

# Control device (mixer, etc.) for the nForce2/4 card
ctl.analog-hw {
 type hw
 card 0
}

# Alias for digital (S/PDIF) output on the nForce2/4 (hw:0,2)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.digital-hw {
 type hw
 card 0
 device 2
}

# Control device (mixer, etc.) for the nForce2/4 card
ctl.digital-hw {
 type hw
 card 0
}

# Direct software mixing plugin for analog output on
# the nForce2/4 (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.dmix-analog {
 type dmix
 ipc_key 1234
 slave {
   pcm "analog-hw"
   period_time 0
   period_size 1024
   buffer_size 4096
   rate 48000
 }
}

# Control device (mixer, etc.) for the nForce2/4 card
ctl.dmix-analog {
 type hw
 card 0
}

# Direct software mixing plugin for digital (S/PDIF) output
# on the nForce2/4 (hw:0,2)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.dmix-digital {
 type dmix
 ipc_key 1235
 slave {
   pcm "digital-hw"
   period_time 0
   period_size 1024
   buffer_size 4096
   rate 48000
 }
}

# Control device (mixer, etc.) for the nForce2/4 card
ctl.dmix-digital {
 type hw
 card 0
}

```

The weird thing is I've had it like in the first part for like a month, and it's not until now it stoped working...

---

### Post by jpkotta on 2006-01-28
Looks like you know more about this stuff than me; I barely understand my ~/.asoundrc

---

### Post by t0bb3 on 2006-01-28
Hehe, I doubt it. I just copied that stuff from the MythTV wiki... Don't really understand it myself ;)

---


---
title: "Sound Blaster Audigy SE, Flash, and mixing"
date: 2007-09-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by brharri1 on 2007-09-20
Ok, so I got a new SB Audigy SE card since my onboard card apparently hasn't been working so well. I disabled the onboard device in my BIOS, and after much trouble, got my new card to "work." Now, I haven't gotten the full 5.1 working yet, but that's a battle for another day. My current problem is that I have a choice between having sound work in flash (ie youtube) OR be able to have more than one program use sound at once. Here's what I mean.

If I delete my /home/brian/.asoundrc then I can have several programs using sound open at once. 

If I restore my .asoundrc then youtube sound works, but then I can't open any other sound using program at the same time. Here are the contents of my .asoundrc

> 
# Override the default output used by ALSA.
# If you do not override the default, your default
# device is identical to the (unmixed) analog device
# shown below.  If you prefer mixed and/or digital
# output, uncomment the appropriate four lines below
# (only one slave.pcm line).
### Currently set w/digital-hw as the default output,
### comment out this entire section to use unmixed
pcm.!default {
  type plug
## Uncomment the following to use mixed analog by default
#  slave.pcm "dmix-analog"
## Uncomment the following to use unmixed digital by default
  slave.pcm "digital-hw"
## Uncomment the following to use mixed digital by default
  #slave.pcm "dmix-digital"
}

# Alias for analog output on the Audigy (hw:0,0)
# - This is identical to the device named "default"--which
# always exists and refers to hw:0,0 (unless overridden)
# - Therefore, we can specify "hw:0,0", "default", or "analog"
# to access analog output on the Audigy
pcm.analog {
 type plug
 slave.pcm "analog-hw"
}

# Control device (mixer, etc.) for the Audigy card
ctl.analog {
 type hw
 card 0
}

# Alias for (rate-converted) mixed analog output on the
# Audigy (hw:0,0)
#  - This will accept audio input--regardless of rate--and
# convert to the rate required for the dmix plugin
# (in this case 48000Hz)
pcm.mixed-analog {
 type plug
 slave.pcm "dmix-analog"
}

# Control device (mixer, etc.) for the Audigy card
ctl.mixed-analog {
 type hw
 card 0
}

# Alias for (rate-converted) digital (S/PDIF) output on the
# Audigy (hw:0,0)
#  - This will accept audio input--regardless of rate--and
# convert to the rate required for the S/PDIF hardware
# (in this case 48000Hz)
pcm.digital {
 type plug
 slave.pcm "digital-hw"
}

# Control device (mixer, etc.) for the Audigy card
ctl.digital {
 type hw
 card 0
}

# Alias for mixed (rate-converted) digital (S/PDIF) output on the
# Audigy (hw:0,0)
#  - This will accept audio input--regardless of rate--and
# convert to the rate required for the S/PDIF hardware
# (in this case 48000Hz)
pcm.mixed-digital {
 type plug
 slave.pcm "dmix-digital"
}

# Control device (mixer, etc.) for the Audigy card
ctl.mixed-digital {
 type hw
 card 0
}

# The following devices are not useful by themselves.  They
# require specific rates, channels, and formats.  Therefore,
# you probably do not want to use them directly.  Instead use
# of of the devices defined above.

# Alias for analog output on the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.analog-hw {
 type hw
 card 0
 # The default value for device is 0, so no need to specify
}

# Control device (mixer, etc.) for the Audigy card
ctl.analog-hw {
 type hw
 card 0
}

# Alias for digital (S/PDIF) output on the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.digital-hw {
 type hw
 card 0
 device 0
}

# Control device (mixer, etc.) for the Audigy card
ctl.digital-hw {
 type hw
 card 0
}

# Direct software mixing plugin for analog output on
# the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format. You can edit the rate to use 
# another sampe rate like 9600
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

# Control device (mixer, etc.) for the Audigy card
ctl.dmix-analog {
 type hw
 card 0
}

# Direct software mixing plugin for digital (S/PDIF) output
# on the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format. You can edit the rate to use 
# another sampe rate like 9600
pcm.dmix-digital {
 type dmix
 ipc_key 1235
 slave {
   pcm "digital-hw"
   period_time 0
   period_size 1024
   buffer_size 4096b
   rate 48000
 }
}

# Control device (mixer, etc.) for the Audigy card
ctl.dmix-digital {
 type hw
 card 0
}

# setups the speakers for 5.1 and 4.1, shouldnt be needed as its already preconfigured 
# but if you got problems with the speaker setup this is needed.

pcm.ch51dup {
         slave.pcm surround51
         slave.channels 6
         type route
         ttable.0.0 1
         ttable.1.1 1
         ttable.0.2 1
         ttable.1.3 1
         ttable.0.4 0.5
         ttable.1.4 0.5
         ttable.0.5 0.5
         ttable.1.5 0.5
}

# for 4.1 speakers
pcm.ch41dup {
         type route
         slave.pcm surround41
         slave.channels 5
         ttable.0.0 1
         ttable.1.1 1
         ttable.0.2 1
         ttable.1.3 1
         ttable.0.4 0.5
         ttable.1.4 0.5
}


Any help is much appreciated.

-Brian

---


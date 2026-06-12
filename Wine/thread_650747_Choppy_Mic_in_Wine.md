---
title: "Choppy Mic in Wine"
date: 2007-12-26
forum: Wine
---

### Post by constchar* on 2007-12-26
I get very choppy mic input with Wine 0.9.51 and ALSA.
In wineconfig the only "Wave In" that shows up is "Mic Capture"
and it seems to be really choppy or prone to lockups.

Initially I had no "Wave In" but then I used this asound.conf and
then the "Mic Capture" showed up:
```

# Set default sound card
# Useful so that all settings can be changed to a different card here.

pcm.snd_card0
{
	type hw
	card 0
	device 0
}

ctl.snd_card0
{
	type hw
	card 0
	device 0
}

# Allow mixing of multiple output streams to this device

pcm.output
{

	type dmix
	ipc_key 1024
	ipc_perm 0660 # Sound for everybody in your group!
	slave.pcm "snd_card0"

	slave
	{
		# This stuff provides some fixes for latency issues.
		# buffer_size should be set for your audio chipset.
		period_time 0
		period_size 1024
		buffer_size 8192
	}

	bindings
	{
		0 0
		1 1
	}

}

pcm.input
{

	type dsnoop
	ipc_key 2048
	slave.pcm "snd_card0"

	## Possible artsd full duplex fix:

	slave
	{
		period_time 0
		period_size 1024
		buffer_size 8192
	}

	bindings
	{
		0 0
		1 1
	}

}

# This is what we want as our default device
# a fully duplex (read/write) audio device.

pcm.duplex
{
	type asym
	playback.pcm "output"
	capture.pcm "input"
}

###################
# CONVERSION PLUG #
###################

# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).

pcm.!default
{
	type plug
	slave.pcm "duplex"
}

########
# AOSS #
########

# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)

pcm.dsp0
{
	type plug
	slave.pcm "output"
}

```

I really have no idea what I'm doing here to be honest so if somebody with
more experience can help me fix this then I'd really apprechiate it!

Thanks, Jimmy.

---


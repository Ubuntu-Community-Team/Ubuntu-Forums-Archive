---
title: "Starcraft on a 2nd monitor using NVidia 304.xx drivers"
date: 2012-09-16
forum: Wine
---

### Post by darinmiller on 2012-09-16
The following script will enable Starcraft to run on a 2nd monitor (or external laptop monitor) using the correct 4:3 aspect ratio using NVida current 304.xx series drivers.  The script uses the NVidia/Xrandr viewport settings; thus enabling monitors lacking a native EDID mode of 640x480 to display Starcraft fully zoomed with aspect ratio scaled.

Ensure to replace the DFP and HDMI reference to match your hw setup.  Also, the compiz sections can be deleted if Compiz is not used, i.e. KDE users.

Note: the screen "zoom" is set after Starcraft is launched.  Otherwise wine throws an error specifiying inability to set the resolution.

```
#!/bin/sh
# Using NVidia's 302.17 driver to control zoom level of a full screen application
# Note:
#     depending on hw setup, you may need to change XRANDR HDMI-0 reference to VGA-0 
#     depending on hw, nvidia-settings reference DFP-x to CRT-x

# Switch to metacity if compiz enabled. (Easier than fusion-icon and preserves certain windows' workspaces.)
cz=0
pid=`ps -A | grep compiz | nawk '{print $1}'`
if [ $pid ]; then
	metacity --replace &
	# Sometimes compiz does not die...
	pid=`ps -A | grep compiz | nawk '{print $1}'`
	if [ $pid ]; then kill -9 $pid \&; fi
	cz=1
fi

dualScreen="false"
if [ `xrandr | grep "HDMI" | nawk '{print $2}'` = "connected" ]; then dualScreen="true"; fi

appDir="C:\Games\Starcraft\\"
app="Starcraft.exe"
prog=$appDir$app
WINEPREFIX="$HOME/.wine"
env WINEPREFIX="$WINEPREFIX" wine "$prog" &

# Ensure app is launched by waiting for PID to appear 
while [ ! `ps -C $app -o pid=` ]
do
	sleep 1
done

# Give the app a few seconds to set the video resolution
sleep 2

if [ $dualScreen = "true" ]; then
	nvidia-settings --assign CurrentMetaMode="DFP-1:nvidia-auto-select {ViewPortIn=640x480, ViewPortOut=1600x1200+160+0 }, DFP-0:NULL" 
  else
	nvidia-settings --assign CurrentMetaMode="DFP-0:nvidia-auto-select {ViewPortIn=640x480, ViewPortOut=1600x1200+160+0 }" 
fi

while [ `ps -C $app -o pid=` ]
do
	sleep 3
done

if [ $dualScreen = "true" ]; then
	# the following line broke as of 304.43, evidently nvidia-setttings fails at setting devices that are turned off
	#nvidia-settings --assign CurrentMetaMode="DFP-1:nvidia-auto-select +0+0, DFP-0:nvidia-auto-select +1920+0"
	nvidia-settings --assign CurrentMetaMode="DFP-1:nvidia-auto-select +0+0"

	#workaround for the nvidia-settings failure, replace HDMI-0 with VGA-0 if needed
	xrandr --output LVDS-0 --right-of HDMI-0 --auto
 else
	nvidia-settings --assign CurrentMetaMode="DFP-0:nvidia-auto-select +0+0"
fi

if [ $cz -eq 1 ]; then compiz --replace \&; fi
```

---


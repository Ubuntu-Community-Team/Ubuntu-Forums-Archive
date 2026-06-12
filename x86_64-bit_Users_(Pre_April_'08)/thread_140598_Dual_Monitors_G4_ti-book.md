---
title: "Dual Monitors G4 ti-book"
date: 2006-03-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by shreeswifty on 2006-03-06
hi folks 

found this very insightful how-to which worked great for a G4 Ti-book with a radeon card

[http://ozlabs.org/~jk/docs/mergefb/](http://ozlabs.org/~jk/docs/mergefb/)

n order for the laptop to be usable both with and without the external monitor, we need to resize the desktop space to the new viewable area - without restarting X.

In the first case, the viewable desktop changes - simply unplugging the external monitor will leave bits of the desktop around the edges unvieweable.

In the second, unplugging a monitor that shows a different part of the desktop results in an entire screen worth of desktop being unviewable. You can do what Chris does, and use a scrolling-viewport-based window manager, like fvwm, but then you still have a large area where the mouse can disappear into.

Fortunately, using xrandr, we can resize the desktop on the fly.

Unfortunately, there are a few problems:

    * The standard clone mode of video drivers won't let you clone a screen with a different resolution; and
    * xrandr doesn't work with Xinerama.

configuration

The following examples are based on my particular hardware configuration:

    * G4 PowerBook (PowerBook 5,6)
    * ATI Radeon 9600 (RV350) video card, with a DVI output
    * x.org 6.8.2 (from Ubuntu Breeezy)

Your mileage may vary with other hardware, but you will need a Radeon card for this to work.

If you'd like to refer to my xorg.conf: here it is. It defines an external monitor running at 1280x1024, running in the 'mirroring' mode described below.
basic setup

To output on both monitors, xorg.conf needs two "Device" sections, two "Monitor" sections, and two "Screen" sections. However, only one of the Screens is actually referred to in the ServerLayout configuration.

The basic structure of the Device sections:

Section "Device"
        Identifier      "ATI Radeon 9600 (Primary)"
        Driver          "radeon"
        BusID           "PCI:0:16:0"
EndSection

Section "Device"
        Identifier      "ATI Radeon 9600 (Secondary)"
        Driver          "radeon"
        BusID           "PCI:0:16:0"
        Screen          1
EndSection

The trick: both require a PCI ID, even though it's the same

The Monitor sections define the monitors available. Since most new monitors use DDC to discover the available settings, these sections are brief:

Section "Monitor"
        Identifier      "Laptop LCD"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "External Monitor"
        Option          "DPMS"
EndSection

The Screen sections describe the available physical viewports, which are later merged into the one X Screen. Even though the Modes settings aren't strictly necessary, I find it help to explicitly define which settings you want to be available:

Section "Screen"
        Identifier      "Internal Screen"
        Device          "ATI Radeon 9600 (Primary)"
        Monitor         "Laptop LCD"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x854"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "External Screen"
        Device          "ATI Radeon 9600 (Secondary)"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x854" "1280x1024"
        EndSubSection
EndSection

mirroring

To set up the first example, we use mergefb in clone mode - just configure the primary device section with the MergedFB, MetaModes and MergedDPI options. The MergedFB option specifies the individual modes for the two monitors, primary first. You'll need to include one pair of modes for the optimal resolution for both displays, and one for the 'highest-common-denominator' for the two displays.

Section "Device"
        Identifier      "ATI Radeon 9600 (Primary)"
        Driver          "radeon"
        BusID           "PCI:0:16:0"
        Option          "MergedFB" "true"
        Option          "MetaModes" "1280x854-1280x854 1280x854-1280x1024"
        Option          "MergedDPI" "100 100"
EndSection

Also, make sure that the larger of the monitors can display at the resolution of the smaller one, and that both have that resolution present in their Screen section -> Display subsection -> Modes parameter.

With this setup, the overall X configuration will have two resolutions available, one matching each display. The xrandr program can be used to switch between these two resolutions while X is running. When running at the resolution of the larger monitor, the smaller monitor will scroll around the desktop with the mouse - however, since you're mirroring, you can hide this display from view.
merging

Merging allows you to use both monitors as separate viewports onto the same desktop when they're available, then resize the desktop to the smaller laptop panel when the external monitor isn't available. Like the mirroring configuration, we merge the two screens into one, but rather than cloning the display, we offset the viewports using the CRT2Position option

Section "Device"
        Identifier      "ATI Radeon 9600 (Primary)"
        Driver          "radeon"
        BusID           "PCI:0:16:0"
        Option          "MergedFB" "true"
        Option          "MetaModes" "1280x854 1280x854-1280x1024"
        Option          "MergedDPI" "100 100"
        Option          "CRT2Position" "LeftOf"
EndSection

This will place the secondary monitor to the left of the primary one.

One caveat: the resulting desktop must be rectangular - ie, if you've placed the secondary monitor to the left or right of the primary, the vertical resolution of the monitors must be equal. Otherwise, the smaller monitor will scroll when the mouse is moved to the non-visible area. I'm told that this is fixed in recent x.org CVS.
output routing

If you're using a DVI connector for the external monitor, you may come across the following:

    * The external monitor only mirrors the internal one, and is fixed at the same resolution; or
    * The external monitor doesn't show anything at all

In this case, you'll need to change registers on the radeon device. To do this, benh and tridge have modified the radeontool utility - download the source, or a binary for powerpc machines.

To route the second head to the external DVI output:

Note that the output is from my hardware - the initial register value 0x000345cd will probably differ on your machine - substitute as appropriate.

    *

      First, see find what sort of card you have. lspci on my machine shows:

      0000:00:10.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

      - I have a RV350.
    * Read the value of the FP_GEN_CNTL register:

      [jk@pokey ~]$ sudo radeontool regmatch FP_GEN_CNTL
      FP_GEN_CNTL (0284)      0x000345cd

    *

      Update the FP_GEN_CNTL register:

      For r200, r300, rv350 and later:

      Set the register to old-value & ~0x0c07 | 0x0405:

      [jk@pokey ~]$ sudo radeontool regset FP_GEN_CNTL $((0x000345cd & ~0x0c07 | 0x0405))

      For v200, rv250 and rv280:

      Set the register to old-value & ~0x2007 | 0x2005:

      [jk@pokey ~]$ sudo radeontool regset FP_GEN_CNTL $((0x000345cd & ~0x2007 | 0x2005))

For more details (and routing options), check out this email

Also, you'll need to start X with the largest monitor attached, so that it is detected properly. Alternatively, you could disable DDC and set the ModeLines explicitly.
putting it all together

I use this script to call xrandr and set the radeon's registers. Invoke as:

[jk@pokey ~]$ xmode dual

to set dual-headed mode, and

[jk@pokey ~]$ xmode single

when the external monitor is removed.
acknowledgements

---

### Post by ssam on 2006-03-06
thanks

i keep meaning to figure out how to do this, but have not got round to it. now i might give it a try.

---


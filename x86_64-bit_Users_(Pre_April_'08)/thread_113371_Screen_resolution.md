---
title: "Screen resolution"
date: 2006-01-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by UncleBulgaria on 2006-01-06
Hi,

Having just installed the AMD 64 version I appear to have done something stupid when going through the installation routine.  I thought it was asking me to select my screen resolution (1280x 1024) but it would appear that it was asking me to remove resolutions that I cannot display (it was 2am in the morning, should have waited until the next day).  Anyway, I am stuck in '1024 x 768' and no option for '1280 x 1024' in the Screen Resolution part of Preferences.  Is there an easy way to rectify (I am a newbie) or do I have to reinstall?

Thank you for any help you can provide.

Robert.

---

### Post by xmastree on 2006-01-06
You can edit the /etc/X11/xorg.conf file to add different resolutions. Back it up first, then edit it. You'll see which section has the resolutions, it should be fairly obvious once you look at it. If not, ask again.

---

### Post by hogoh on 2006-01-06
PLEASE, READ ALL OF THIS (inckluding the postscript) OR JUST SKIP IT:

You might try to edit XF86Config-4 (XFree86 X Window System server configuration file)  If you do, try do so with caution: maybe, make a copy of it before you do the edit, by ~ in a terminal window ~ becoming root and running

cp /etc/X11/XF86Config-4 /etc/X11Config-4.custom

then if your editing goes adrift you can copy the *-custom file back to overwrite the one that's been mis-edited

For more on the above theme try, in a terminal window 
less /etc/X11/XF86Config-4
and read what comes up.  You might, too, as the above less output will say try running
man XF86Config-4
and reading what that manual page says; it's helpful!

So, once you've some idea what you're in the middle of,
the editing to do is in the Section "Screen" of the XF86Config-4 file where
there'll be a lot of SubSection "Display" parts in the "Screen" Section
they'll be headed "Display" then, under that heading, yo'ull see Depth numbers like 1, 4, 8, 15, 16, 24 (no commas in file versions) and
under, say,                  Depth 1 
you'll see, for example
                                   Modes "800x600" "640x480"

if you edit such lines to incude the resolution you're missing (& any others you fancy) then it (or they) ought to appear in Screen Resolution Choices from which you select the resolution you want ~ once you've left root.

A bit fiddley but an alternative to re-installing!

Hope that's some help
                                      

P.S. 1)  I've done an edit like the one I outline above it worked in Debian and the XF86 files in the Ubuntu & Debian 3.1 aren't, I suspect, going to be much different.
2)  I don't visit this Forum often so if you ask a question about what I've put I may not see it for days and you'll not see any answer from me for at least as long BUT others may tell you the answer!

---

### Post by xmastree on 2006-01-06
> I've done an edit like the one I outline above it worked in Debian and the XF86 files in the Ubuntu & Debian 3.1 aren't, I suspect, going to be much different.
Except that in ubuntu, the config file is **/etc/X11/xorg.conf** rather than XF86Config

---

### Post by handy on 2006-01-06
You'll soon be rich collecting all the $0.02 worth, here's mine.

If your using a CRT, input your horizontal & vertical refresh rates as per the manual for your monitor, or google for it.

Here is a copy of the section with MY refresh rates.
==========================
Section "Monitor"
Identifier "Generic Monitor" <-- don't edit
Option "DPMS" <-- don't edit
HorizSync 30-107 <-- change these
VertRefresh 48-120 <-- change these
EndSection
==========================

When you restart or give that command that I forget, you should have more options & probably you will be in the highest res' possible @ the highest refresh rate.

Works for me...:p 

handy

---

### Post by Suger on 2006-01-06
Are you thinking about ```
sudo /etc/init.d/gdm restart
``` or Ctrl+Alt+Backspace ?

---

### Post by handy on 2006-01-06
Yes

Thanks  :rolleyes: 

handy

---

### Post by UncleBulgaria on 2006-01-07
Thanks for all the ideas.  I tried them out with no success so decided to reinstall and the monitor is still stuck on '1024 x 768'.  I have updated to the latest NVIDIA driver  and I am now wondering if the problem has arisen because of the monitor it shows me as having.  Here is a copy of the relevant part of my edited xorg.conf (I did the Ctrl+Alt+Backspace after editing and again after installing the NVIDIA driver):

[INDENT]Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768"
	EndSubSection
EndSection[/INDENT]

And the NVIDIA Settings utility shows me as having a CRT monitor (CRT-0).  I actually have a 17" TFT monitor (Digimate L-1718 ) which has the normal '1280 x 1024' native resolution and 75hz refresh rate.

Any help will again be appreciated.

Regards,

Robert.

---

### Post by skylark on 2006-01-07
I don't have your setup so I'm just guessing in the dark here. I did some googling for the specs of your monitor. Try changing the following in your xorg.conf and see it makes any difference:

"HorizSync 28-51" to "HorizSync 30-62"
"VertRefresh 43-60" to "VertRefresh 50-75"

(restart x/reboot or whatever to test).

---

### Post by handy on 2006-01-08
That should do it...

handy

---

### Post by encikraju on 2007-01-02
Hi,
why my /etc/X11/xorg.conf doesnt have horisync and vertrefresh?

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

---

### Post by xthaparian on 2007-01-02
> Thanks for all the ideas. I tried them out with no success so decided to reinstall and the monitor is still stuck on '1024 x 768'. I have updated to the latest NVIDIA driver and I am now wondering if the problem has arisen because of the monitor it shows me as having. Here is a copy of the relevant part of my edited xorg.conf (I did the Ctrl+Alt+Backspace after editing and again after installing the NVIDIA driver):

Section "Device"
Identifier "NVIDIA Corporation NV43 [GeForce 6600 GT]"
Driver "nvidia"
BusID "PCI:5:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV43 [GeForce 6600 GT]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768"
EndSubSection
EndSection
And the NVIDIA Settings utility shows me as having a CRT monitor (CRT-0). I actually have a 17" TFT monitor (Digimate L-1718 ) which has the normal '1280 x 1024' native resolution and 75hz refresh rate.

Any help will again be appreciated.

Regards,

Robert.

Do Following

```
$ sudo cp /etc/apt/xorg.conf /etc/apt/xorg.conf_working-bak
```

this is to make sure that just in case you screwup something you can recover your screen

```
$ sudo dpkg-reconfigure xserver-xorg
```

This will reconfigure your graphics card.
When asking for your graphics card make sure you choose nvidia.

At this point it will also ask you about the screen resolution your monitor can support.

Ebable the screen resolution your monitor is capable of displaying. 

1280 x 1024 in your case and 1024x786.

also go through default settings while configuring the xorg and thats it.. 
In the end it will write the xorg.conf file..

Now I recommend

```
$ sudo /etc/init.d/gdm restart
```

or

```
# sudo shutdown -r now
```

After this your should be able to select the screen resolution of your choice



Option 2.

Als you can Edit your xorg.conf manually to look like this

....
Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV43 [GeForce 6600 GT]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 16
Modes **"1280x1024"** [COLOR="red"]**"1280x1024"**[/COLOR] "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes **"1280x1024"** **[COLOR="Red"]"1280x1024"[/COLOR]** "1024x768"
EndSubSection
EndSection
...
...

The reason for this is that **FIRST "1280x1024"** is for GDM resolution and **[COLOR="red"]SECOND "1280x1024"[/COLOR]** is for Max Desktop resolution.


;)

---

### Post by xthaparian on 2007-01-02
> **encikraju said:**
> Hi,
why my /etc/X11/xorg.conf doesnt have horisync and vertrefresh?

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

If you follow the general HOWTO for 3D in graphics card, this will generally not showup in the xorg.conf file.

But you can definetly get the extra PUNCH out of your screen if you add the exact range of frequencies.

You can Google your monitors freq range and punch that it.

---

### Post by encikraju on 2007-01-04
Hi, thanks for reply. I don't get what you mean. Newbie. Could you explain a little bit.

The freq.

Horiz. Frequency: 30-81

---


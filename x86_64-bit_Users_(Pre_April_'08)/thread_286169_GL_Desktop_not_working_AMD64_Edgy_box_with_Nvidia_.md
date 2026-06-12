---
title: "GL Desktop not working AMD64 Edgy box with Nvidia Beta drivers"
date: 2006-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by jonah1980 on 2006-10-27
Hi I've been trying to get GL desktop / compiz working for ages on my edgy amd64 box and i could really do with some help.

I've tried the howtos and tutorials but they're either for beryl or 32bit, or repositories have missing packages etc.

Can anyone help me out without a howto link please, it would be really appreciated.

Ok, so i've installed the Nvidia Beta 9.whatever drivers.

I've intsalled: compiz-freedesktop, compiz-freedesktop-gnome, gnome-compiz-manager and libgnome-compiz-manager.

i've got the little dice thing in the system tray.

Also i've added:
# Enable 32-bit ARGB GLX Visuals
    Option "AddARGBGLXVisuals" "True"

# If you are using an older version of compiz that
# does not support rendering into the Composite
# Overlay Window, you will need to disable clipping
# of GLX rendering to the X Root window with this
# option, or you will get a blank screen after
# starting compiz:
#    Option "DisableGLXRootClipping" "True"

to my "Screen" section of xorg.conf

After all this when i click to enable the GL Desktop effects i lose the titlebars and borders from my windows for couple of seconds (but you can tell xgl is not on, cos when you hover over stuff there's no effect).
Then a second later the window borders appear etc and the Enable GL Effects box is still ticked in the system tray and the preferences window. But no effects, then when you close prefs dialog window and reopen it the box is unticked again.

Please someone help me out! Thanks...

---

### Post by jonah1980 on 2006-10-28
turns out i'm not using the nvidia proprietary driver but the "nv" setting in xorg instead.

putting "Nvidia" won't work, i thought it was working because the drivers are installed but on reboot the x server crashed and told me to do the reconfigure command, i didn't realise this set it back to "nv"

i've tried putting "nvidia" again in xorg.conf but the x server just crashes every time, so i'm set back to "nv" until hopefully someone can help me out.

When the x server crashes using nvidia a blue screen comes up and it says "Failed to start x server"... and asks if you'd like to "view x server output?"

when i press "yes" it says:

"FATAL: Could not open 'lib/modules/2.6.17-10-generic/volatile/nvidia.ko"

Please someone help me get the beta nvidia drivers working...

---

### Post by FedeXX on 2006-10-28
> **jonah1980 said:**
> turns out i'm not using the nvidia proprietary driver but the "nv" setting in xorg instead.

putting "Nvidia" won't work, i thought it was working because the drivers are installed but on reboot the x server crashed and told me to do the reconfigure command, i didn't realise this set it back to "nv"

i've tried putting "nvidia" again in xorg.conf but the x server just crashes every time, so i'm set back to "nv" until hopefully someone can help me out.

When the x server crashes using nvidia a blue screen comes up and it says "Failed to start x server"... and asks if you'd like to "view x server output?"

when i press "yes" it says:

"FATAL: Could not open 'lib/modules/2.6.17-10-generic/volatile/nvidia.ko"

Please someone help me get the beta nvidia drivers working...

Mumble mumble...Forgot to install the appropirate "linux restricted modules" package?

---

### Post by jonah1980 on 2006-10-28
i'm dumb. i think i installed the i386 installer, tried it again with amd64 one from nvidia and it's working. just now trying to get titlebars on my windows, compiz seems to work though...

---

### Post by FedeXX on 2006-10-28
> **jonah1980 said:**
> i'm dumb. i think i installed the i386 installer, tried it again with amd64 one from nvidia and it's working. just now trying to get titlebars on my windows, compiz seems to work though...

For titlebars you must install cwgd, and run

```

cgwd --replace

```

---

### Post by jonah1980 on 2006-10-28
again more problems, got my titlebars back but still can't seem to use compiz. it works when i install it but when i reboot the machine gdm locks up and i can't do anything, i just have a mouse to move around but nothing to click on. so i've no yet again removed all the compiz stuff - am i best off with beryl, i thought compiz was supposed to be better!?

---

### Post by FedeXX on 2006-10-28
> **jonah1980 said:**
> again more problems, got my titlebars back but still can't seem to use compiz. it works when i install it but when i reboot the machine gdm locks up and i can't do anything, i just have a mouse to move around but nothing to click on. so i've no yet again removed all the compiz stuff - am i best off with beryl, i thought compiz was supposed to be better!?

:|

Beryl IS better! But beryl needs edgy, compiz doesn't...If it isn't a problem for you, go with beryl (i use beryl too ;) ) 

Thanks Quinnstorm!

---

### Post by jonah1980 on 2006-10-28
switched to beryl even though wanted to use compiz. i was told compiz was more stable and faster in performance.

but had to go with beryl cos wouldn't work in compiz, now beryl is working pretty good!

---


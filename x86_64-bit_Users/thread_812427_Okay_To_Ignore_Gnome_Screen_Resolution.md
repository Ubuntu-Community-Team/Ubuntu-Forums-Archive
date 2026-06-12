---
title: "Okay To Ignore Gnome Screen Resolution?"
date: 2008-05-29
forum: x86 64-bit Users
---

### Post by linux4me on 2008-05-29
I just did a clean install of 64-bit Hardy after using 32-bit Hardy for a week or so. It seems much faster to me, and I haven't had any problems yet. My Nvidia 7600 GS was detected and Ubuntu offered to install the nvidia restricted driver on first boot, which I did. 

I noticed after restarting that Gnome (System->Preferences->Screen Resolution) reports the correct screen resolution for my monitor (1280 x 1024) but only gives me the option of 50, 51, and 52 Hz. Sixty is the recommended refresh rate for my monitor.

I installed nvidia-settings to see if Gnome's reported resolution was correct. In nvidia-settings, the resolution and refresh were set to "Auto" so I set them to the native values for my monitor and saved the changes to my xorg.conf, then restarted. 

I rechecked nvidia-settings after the restart and the values were saved. Gnome still reports 50 Hz.

Reading the posts here about screen resolution, it appears that Gnome may be incorrectly reporting the refresh rate with the nvidia driver, and that the one to trust is the value in nvidia-settings, but I couldn't find where anyone came right out and said as much. I don't want to be doing any harm to my monitor.

Is it safe to just ignore the value in Gnome?

---

### Post by gsiliceo on 2008-05-29
Yes, i've seen this problem in lots of screen configurations using ubuntu(lots being 5 or so) and the screen works perfectly but the number is wrong.

---

### Post by RAOF on 2008-05-30
This is an artefact of the way nVidia cludges TwinView into X.  The nvidia driver deliberately mis-reports the refresh rate it is using, so all non-nVidia-specific tools will be displaying an incorrect rate.

---

### Post by gsiliceo on 2008-05-30
That is evil of them.

---

### Post by linux4me on 2008-05-30
> This is an artefact of the way nVidia cludges TwinView into X. The nvidia driver deliberately mis-reports the refresh rate it is using, so all non-nVidia-specific tools will be displaying an incorrect rate.

So I'm assuming artifact == safe to ignore. Thanks, RAOF.

> **gsiliceo said:**
> That is evil of them.

That is evil of them, but at least they provide Linux drivers...

---

### Post by aaron.d on 2008-05-30
> **linux4me said:**
> I just did a clean install of 64-bit Hardy after using 32-bit Hardy for a week or so. It seems much faster to me, and I haven't had any problems yet. My Nvidia 7600 GS was detected and Ubuntu offered to install the nvidia restricted driver on first boot, which I did. 

I noticed after restarting that Gnome (System->Preferences->Screen Resolution) reports the correct screen resolution for my monitor (1280 x 1024) but only gives me the option of 50, 51, and 52 Hz. Sixty is the recommended refresh rate for my monitor.

I installed nvidia-settings to see if Gnome's reported resolution was correct. In nvidia-settings, the resolution and refresh were set to "Auto" so I set them to the native values for my monitor and saved the changes to my xorg.conf, then restarted. 

I rechecked nvidia-settings after the restart and the values were saved. Gnome still reports 50 Hz.

Reading the posts here about screen resolution, it appears that Gnome may be incorrectly reporting the refresh rate with the nvidia driver, and that the one to trust is the value in nvidia-settings, but I couldn't find where anyone came right out and said as much. I don't want to be doing any harm to my monitor.

Is it safe to just ignore the value in Gnome?


A good way of checking is by checking the Input info or similar on your monitor directly. It should tell you both res and refresh being fed to it. Then you would have known the software was mis-reporting. Most LCDs now have this feature.

---

### Post by linux4me on 2008-05-30
> **aaron.d said:**
> A good way of checking is by checking the Input info or similar on your monitor directly. It should tell you both res and refresh being fed to it. Then you would have known the software was mis-reporting. Most LCDs now have this feature.

Thanks! My monitor does have that ability, and it verifies that I'm running at my desired resolution and refresh rate. I didn't even think of checking with the monitor's menu.

---


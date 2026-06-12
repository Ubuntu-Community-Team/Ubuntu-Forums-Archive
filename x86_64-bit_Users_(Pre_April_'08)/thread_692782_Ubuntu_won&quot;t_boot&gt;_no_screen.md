---
title: "Ubuntu won&quot;t boot&gt; no screen"
date: 2008-02-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by slambrick on 2008-02-10
My ubuntu won't boot intoi any screen. It does the me test then the monitor turns itself off and stays off. I suspect it is the Nvidia graphics driver which I had a lot of trouble getting to run. This has started to happen after I suddenly had a pile of file errors at boot which had to be manually corrected with fsck. The starange thing is I can usually get in after waiting a while and then hitting CTRL-ALT- BCKSPCE to restart gdm.
I used Envy to install the graphics driver which seemed to work in manual mode. it didn't detect my card (Nvidia 8800GT) automatically. It was working for a while. I have tried to reinstall it with no change. Should I just rebuild and start again? Can I repair the fil system properly? How do I do this? Any other clues?

Thanks
Steve. L.

Ubuntu AMD64, 4 gig Ram, Nvidia 8800GT, Winfast DTV2000 H, Seagate 500GB Seagate 160GB. Windows Vista H premium.

---

### Post by shadow_slicer on 2008-02-11
Could it be you have bootsplash enabled in your grub configuration (/boot/grub/menu.lst)? As mentioned in numerous [threads ]("http://ubuntuforums.org/showthread.php?t=688165") in this forum, bootsplash doesn't work with newer nvidia cards. This seems like the most likely explanation for the 'no screen' problem you describe. Though it should be pausing for a few seconds after POST, to let you enter the grub menu before continuing to boot (though some people do remove this delay to speed up the boot process). 

In any case you can check /boot/grub/menu.lst for 'splash' and remove it everywhere it appears (as described in the last part of [this post]("http://ubuntuforums.org/showpost.php?p=4272442&postcount=5")).

As for the file system errors, I don't have any idea about them. I'm not even certain they are related. I only know about this bootsplash problem because I ran into it myself.

---


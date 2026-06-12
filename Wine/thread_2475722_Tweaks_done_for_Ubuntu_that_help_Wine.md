---
title: "Tweaks done for Ubuntu that help Wine?"
date: 2022-06-06
forum: Wine
---

### Post by Tadaen_Sylvermane on 2022-06-06
I've been trying to play about with both Arch and Debian. I keep coming back to Ubuntu for the sole reason that with wine (from winehq) staging my fps in World of Warcraft never drops below 80. On Debian and Arch it never get's above 50. 

Both Debian and Ubuntu they use the same exact wine-staging 7.9 from the winehq repository save for the debian <> ubuntu different repo. My last attempt with Arch used the wine 7.8 from the AUR. Same thing with the Xorg driver stuff. Debian's is older than Ubuntu, Arch's is obviously going to be the newest. Still Ubuntu wins by miles. Same thing with the Vulkan stuff, it's in the middle. On any of them I do exactly zero custom stuff with Wine. The only thing I add is the dxvk is manually installed on all 3. No winetricks stuff, no winecfg stuff. Just run the installer with ```
wine ~/Downloads/Battle.net.exe
``` Once it's installed I can just run battle.net & wow from there with zero troubles.

 I can't imagine it's the kernel specifically because both the backport kernel and the stock kernels on Debian have the same issue. Arch's kernel is way ahead of both Ubuntu and Debian. *EDIT* Unless it's a compile option which would make no sense because if it makes that big a difference it would be standard for all one would think.

I'm figuring it's got to be a variable or something somewhere that Ubuntu automatically sets but it isn't normally set by default anywhere else? I don't know how to get a full list of Wine variables. At this point it's about the why. I don't much care about switching as much as trying to crack this nut. There has to be a reason for it.

*EDIT* Have confirmed it is not a vsync issue as well.

---


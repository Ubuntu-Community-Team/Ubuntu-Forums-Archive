---
title: "Please Help- Gutsy_64 Flash Audio Broken!"
date: 2007-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by ncreek on 2007-11-03
I know - NOT ANOTHER FLASH PLAYER ISSUE! Unfortunately yes and first things first. Have a Via VT8237A onboard audio card. I used the upgrade util to go from feisty_64 to gutsy several weeks ago and have lost the sound on upgraded firefox_64 flash non free. I don't think that it ever worked but noticed it shortly after upgrading. All sound on all apps i.e. Totem, mplayer, amarok, system sounds work alright, with reservations. Alsa and Oss are not functioning but switching to ESD or Autodetect modes in any apps gives me sound. Have followed excellent diags on this forum and at ALSA. I have found the following. 

Machine sees both my analog and digital VT82xx cards. Module "snd_hda_intel", which is the correct module per ALSA site for this card is installed and running. The change is that this module has apparently been compiled into the kernel with Gutsy?? instead of using ALSA directly? Again apparently this is why ALSA and OSS modules lock up or give a "failed to initialize  sound card" reply to me. Again switching to ESD or Autodetect using default drivers gives perfect sound.

I have done a complete removal of both Firefox and the non_free Flash, reboot and reinstall both. Flash video is excellent but no audio.Under feisty i had both the 32 and 64 firefox installed and running perfectly. Feisty Firefox_64 had flash installed with the Ndiswrapper, running well. I did all updates prior to upgrade and neither removed nor changed anything. First indication of problem was in Amarok. The sound was poor and no surround present. The first time I changed to another module in Amarok I found that speaker selection was blanked and ALSA could not initialize the card. Since I started diagnosing problem I have unfortunately added a LOT of unneeded apps. Fortunately none of these harmed my existing sound in any apps but have not fixed the flash problem. I am not sure that this demands a Launchpad write-up? Strange no one else has the problem.

---

### Post by ncreek on 2007-11-03
Follow-up to this issue. I ran a back trace on firefox and got the following:

firefox
LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/libflashplayer.so [/usr/lib/firefox/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]


Why the 32b class. i loaded the Flash_non_free with Synaptic?? How do I get the right flash installed?

Checking Firefox config now and don't see obvious answer????

---

### Post by Kilz on 2007-11-03
> **ncreek said:**
> Follow-up to this issue. I ran a back trace on firefox and got the following:

firefox
LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/libflashplayer.so [/usr/lib/firefox/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]


Why the 32b class. i loaded the Flash_non_free with Synaptic?? How do I get the right flash installed?

Checking Firefox config now and don't see obvious answer????

The reason is quite simple. Flash, even though it is working with the 64bit browser, is doing it through a wrapper (nspluginwrapper). The error you see isnt stopping your sound. It is the result of storing the 32bit file that is wrapped in the plugin folder. It isnt being used, the wrapped one is. The reason it has to use the wrapper is because it is 32bit.  Since it is 32bit it is looking for 32bit (sound) libraries.
[This file might help solve the issue.]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb") You might also want to make sure ia32-libs is installed. Since I dont run Gutsy would you please report the [bug on launchpad]("https://bugs.launchpad.net/ubuntu") so that others dont have this problem. After you do please place a link to it here so I can add the solution for the developers.

---

### Post by ncreek on 2007-11-03
Thanks Kilz for the info. Unfortunately the link didn't work. I filed a bug and linked.I have tried just about everything without help. Surely there is an answer. Incidentally I have ia32-lib,but as a precaution reloaded. Still no resolution.

---

### Post by Kilz on 2007-11-03
> **ncreek said:**
> Thanks Kilz for the info. Unfortunately the link didn't work. I filed a bug and linked.I have tried just about everything without help. Surely there is an answer. Incidentally I have ia32-lib,but as a precaution reloaded. Still no resolution.

Sorry fixed the link , try it now

---

### Post by Yellow Pasque on 2007-11-04
If you're using the OSS4 package from 4front, you need to manually edit and compile flashsupport.c (located in /usr/lib/oss/lib). Comment out the #define SSL line and compile with the suggested command, substituting -m32 for -lssl. You'll need to have gcc and the gcc-multilib package for it installed.

Once you have the library created (libflashsupport.so), place it in the /usr/lib/firefox/plugins and /usr/lib directories and restart your browser if necessary.

---


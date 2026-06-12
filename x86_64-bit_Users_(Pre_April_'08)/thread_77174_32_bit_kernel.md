---
title: "32 bit kernel?"
date: 2005-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by shawn on 2005-10-16
I installed breezy on my brothers amd 64 and I didn't realise that most stuff is not ready for the 64 bit world. I wanted to kick his arse at cube but there is not a 64 bit version available. So to go back to 32 bit can I just install the k7 kernel and boot to that? What would happen to the 64 bit packages?

---

### Post by RAOF on 2005-10-16
Actually, it's more involved.  The problem is not that the kernel is 64bit ('cause a 64bit kernel can actually run 32bit binaries too), but that essentially all of binaries & libraries and everything is 64bit.  I **think** that if you installed a k7 kernel and tried to boot it would die very early - the 32bit kernel can't run 64bit stuff, and everything you have is 64bit.

You will actually need to fully install a 32bit version of Ubuntu.  From scratch.

---

### Post by archiesteel on 2005-10-17
[QUOTE=RAOF]You will actually need to fully install a 32bit version of Ubuntu.  From scratch.[/QUOTE]

Actually, there is another way. You can install an ia32 chroot on your 64-bit system. I did this to install a 32-bit version of Firefox in order to have a Flash player (there's no 64-bit flash player as of yet) as well as for playing streamed Quicktime movies on Apple's website (some of the sound codecs are 32-bit only, it seems). Some people have had success installing Cedega (formerly WineX) on a 64-bit system (you can install 64-bit versions of Cedega but some games don't like it...).

Check the unofficial Transgaming Wiki site for a quick'n'dirty chroot Howto:

[http://cedegawiki.sweetleafstudios.com/index.php?title=Ubuntu#Building_a_clean_32bit_chroot_with_debbootstrap_on_AMD64](http://cedegawiki.sweetleafstudios.com/index.php?title=Ubuntu#Building_a_clean_32bit_chroot_with_debbootstrap_on_AMD64)

It's not really the kernel that makes a system 64-bit or 32-bit, it's the system libraries and the apps...

---


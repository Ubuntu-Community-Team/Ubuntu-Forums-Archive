---
title: "installed soundcard but using onboard audio instead"
date: 2006-04-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by doggod on 2006-04-30
Is there a way to configure this?    I have an X-Fi card installed but have onboard AC97 audio as well.   TIA

---

### Post by Ribs on 2006-04-30
Try to disable the on-board via your BIOS if you can... Ubuntu will actually set up both sound cards. You'll notice the choice in applications like Beep Media Player (which I use).

Sadly, it's not possible to specify a 'default'... As soon as the machine reboots, Ubuntu will assign the 'default' to a random card. This is a very annoying bug if you don't have a way to turn off on-board audio in the BIOS ](*,)

---

### Post by doggod on 2006-04-30
I'm sorry, I should have been clearer.  There aren't any Linux drivers for 
the Creative X-Fi card.  My Asus  A8V has onboard AC97 sound which is enabled
in the bios.  I also have an M-audio Moblepre usb preamp audio interface.
Ubuntu has no problem seeing the Moblepre but as far as I can tell the on-
board sound isn't recognized.
  I installed Beep Media Player since you suggested it and tried different sound 
configurations and still have no audio output at all.  
  Any suggestions?  Thanks again.

---

### Post by rubengs on 2006-05-10
[http://www.ubuntuforums.org/showthread.php?t=164768&highlight=a8v+audio](http://www.ubuntuforums.org/showthread.php?t=164768&highlight=a8v+audio)


> When a PCI soundcard is present in an Asus A8V or A8V Deluxe system, the
BIOS will disable the onboard AC97 and MC97 devices. This patch enables
them. The soundcard now works on my A8V Deluxe, shows up in lspci output,
in /proc/asound/cards, has mixer controls, plays audio, on both 32 bits
and 64 bits systems.
Patch is against 2.6.16-rc3.


A patch is necessary to use both cards. I don't know where to get it, the referenced thread is not helpful, maybe we need more research.

---

### Post by bobpur on 2006-05-12
I, too, have an X-fi sound card and AC97 on-board sound. Before I installed the X-fi card, I disabled the onboard sound in the BIOS. I, then, installed the drivers for the X-fi card. I was really disappointed when the X-fi sound was worse than the onboard sound. I then deleted ALL audio drivers for both and only installed the drivers for the X-fi card. Now I can vibrate the neighbors windows. 
I think this is (kind of) aside from your problem, but I'd hate to see someone waste a good X-fi card for onboard sound. Good Luck.

---

### Post by puppy on 2006-06-09
That's an interesting comment bobpur considering there is NO SUPPORT for the Creative X-Fi under linux - i.e. it will not work, whatever you try as there are no drivers, zilch, zero. How is yours working? By magic?

---


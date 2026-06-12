---
title: "Getting Sound on Ubuntu!!!!"
date: 2010-12-09
forum: Zimbabwe Team
---

### Post by girri on 2010-12-09
Hie folks!

I am ne on this forum and your help will be greatly appreciated.

I have been trying to play some music on Ubuntu OS, but there is no sound coming out. Its the same, if I try to play dvds, cds or anything from your tube or online tutarials.

This is the same again on Windows XP OS. But when I use Mozzilla Firefox, surprisingly I am getting sound. Ihave tried to download compactible drivers to no avauil.

Anyone encountered this precarious problem before?

---

### Post by amsterdamharu on 2010-12-09
When you say it doesn't produce sound in Windows as well it suggests hardware mixup (put output plug in microphone or something).

Can you post the output of the following command (in Ubuntu)?
```
cat /proc/asound/card0/codec#* | grep Codec
```

I assume you have the speaker icon in your menu bar (in Ubuntu). Can you right click it and select "sound preferences"? Make sure the output volume is not mutes. Then start some program to play sound and check the applications tab. The application playing sound should be listed there (again with the options to change volume or mute it).

---

### Post by NIT006.5 on 2010-12-13
Hi girri,

As well as providing the output of that command, please also clarify:

Are you getting any errors at all? Or does the software indicate that the media is playing and you just can't hear anything? For DVDs and YouTube, are you able to see the video with no sound, or is the video not working either?

---


---
title: "Lost sound in WoW"
date: 2008-05-09
forum: Wine
---

### Post by sjprice on 2008-05-09
So, I had WOW running great, but I must have done something. I have lost all sound in WoW. I can hear mp3's fine, I can hear the test sound in WINE, so I think it has to be in WoW. I thought it was something in the Config.WTF. So I started with a blank one, but nothing. I reverted to a saved copy, still nothing.

Inside WoW, sound is enabled, but the Game Sound Output is greyed out. Any thoughts?

---

### Post by Chriis on 2008-05-09
Are you set to Alsa Driver in Audio tab of Wine config?

Chriis

---

### Post by sjprice on 2008-05-09
I did have it set for ALSA and was getting no sound. So I tried several different setting and all of my audio tests would fail, even with just ALSA. I finally figured out that I had Rhythmbox running and that was causing the failures.

So I enabled ALSA and OSS and it passed, so I tried WoW and boom, sound. So I dropped ALSA and no sound. So, I have sound with ALSA and OSS checked in the Audio settings of WINE. Dont know if that is normal or not, but it works for me.

---

### Post by sjprice on 2008-05-09
And now of course I cant listen to Rhythmbox while playing. Opens and says is playing, but no music. So I have to have sound in wow, or my music collection, but not both at the same time...grrrrrrr...


EDIT: Sorry to have a running dialog with myself, but I fixed this by setting the Ubuntu sound settings to ALSA (In System > Sounds). It was on Autodetect. I now have sound in WoW and can listen to mp3s at the same time. Hope it helps someone else :)

---


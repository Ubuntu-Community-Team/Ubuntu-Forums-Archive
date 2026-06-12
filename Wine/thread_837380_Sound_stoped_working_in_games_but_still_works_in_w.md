---
title: "Sound stoped working in games but still works in winecfg"
date: 2008-06-22
forum: Wine
---

### Post by 1veedo on 2008-06-22
After a reboot none of the sound in any of my wine apps works anymore.  The winecfg audio test works just like it always has but for whatever reason none of my games have sound anymore.  They all worked before, flawlessly.

As far as I can tell there is nothing wrong.  I get no errors from winecfg, or in the console, and none of the games pop up and give me any audio errors.  I just don't get it.  None of the configurations have changed, either, and I dont think a wine update slipped by me (unless there was a recent update like yesterday cause I didn't actually look this time).

---

### Post by Cup of Squirrels on 2008-06-23
Wine is notorious for sound issues in games.

Do you have any other audio programs open when playing games, like music players or flash on a website? If so, close them and try (Might require a reboot)

Otherwise, try my fix:

type "wincefg" into your terminal, and head over to the audio tab. You'll see a list of different sound drivers. By default I believe ALSA is ticked - untick it, and tick OSS driver instead.

Next, highlight the main OSS driver option on your list, and at the bottom of the menu you should see some extra options. Tick "driver emulation" and then apply. Load up a game and see if it works.

Otherwise, tinker with the hardware acceleration setting. If nothing works, put it back to its default setting and try the same with ALSA.


It would also be worthwhile to do a search on the ubuntu forums here for this issue - loads of people have the same issue.

---

### Post by 1veedo on 2008-06-26
Yeah I've had wine not work because an audio program is open but I don't have any running when I'm encountering this issue.  I have also restarted alsa etc and tried changing the audio settings in winecfg.  It's really weird because it used to work, and still technically does (winecfg), just none of the games do.

---

### Post by 1veedo on 2008-07-04
Well, it started working again.  I have version 1 now but it wasn't the upgrade that fixed it.

I never had any sound issues before, except for an occasional conflict with another process.

---


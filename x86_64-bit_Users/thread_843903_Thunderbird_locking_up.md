---
title: "Thunderbird locking up"
date: 2008-06-28
forum: x86 64-bit Users
---

### Post by netsurfau on 2008-06-28
This one's getting really annoying.

When I start T/Bird the first time after booting up 'puter it works until the next check for mail, at which point it locks up solid & have to do a "Force Quit" to close.

From then on, for the rest of the day, when I start it up, it locks as soon as d/loading emails, I have to Force Quit and restart to be able to read my emails.

Thunderbird Version 2.0.0.14 (20080502) that I installed through the Add/Remove... under Applications menu.

OS: Ubuntu 7.10 (Gutsy) amd64-bit

There are no errors for TB listed in either it's or Ubuntu's logs.

---

### Post by dtach on 2008-06-30
i dont really know jack ****, but maybe you could try reinstalling the program?

---

### Post by Soarer on 2008-07-01
Yes, mine is doing that too.

In fact now I can't start Thunderbird at all. It just hangs, no screen is displayed and thunderbird-bin is using 50% CPU.

Gutsy 64, Core 2 Duo, Nvidia 8-series.

---

### Post by bikeboy on 2008-07-01
Try running it from a terminal so you can see some output when it freezes.

---

### Post by Soarer on 2008-07-01
Sorry, I should have said. I tried that - thunderbird %u - and nothing is printed in the terminal. Just 50% CPU usage and... that's it. 

Actually, it happens (the CPU usage) for a while and then stops, returning to the prompt. When started from the menu it never stops. 

I also rebooted, but no difference. :(

---

### Post by Greyed on 2008-07-01
Do you have any addons installed?

---

### Post by Soarer on 2008-07-01
> **Greyed said:**
> Do you have any addons installed?

Yes, the ones I remember - Lightening, Plaxo, Remove Dupes, Scheduleworld. 

The last had an update recently, but it was working OK afterwards.

---

### Post by Greyed on 2008-07-01
Ok, don't recall if TBird has a similar way to startup without addons as Firefox does.  Uhm...

Ah-HA, Google knows all.

Try this:
```

thunderbird -safe-mode

```

That'll prevent the addons from loading.  Won't point to a specific addon as a problem but will narrow down the field from addons (most common vector) and TBird itself.

---

### Post by Soarer on 2008-07-01
It loads Thunderbird fine.

So I'll disable the add-ons one-by-one and see which is causing it.

Many thanks.

---

### Post by Soarer on 2008-07-01
And it turns out to be Lightening. I believe I saw another thread earlier with a fix for this. I'll look it up again.

---

### Post by Greyed on 2008-07-01
Good to hear.  And fooie, looks like the OP found help in another forum but didn't post what helped here nor marked it as solved.  Ah well.  :D  Thanks for coming back and adding the cause for others to see.

---

### Post by Soarer on 2008-07-01
And this is the thread with the Lightning fix - although it hasn't worked for me yet.

[http://ubuntuforums.org/showthread.php?t=778326&highlight=thunderbird]("http://ubuntuforums.org/showthread.php?t=778326&highlight=thunderbird")

I'll play with it later, after work. :)

---

### Post by netsurfau on 2008-07-02
After a number of re-installs this arvo, I just found out TB isn't the problem.

I'm having a complete failure of practically ALL multimedia playback.
Sounds, video files, flash etc. the whole lot seems screwed at present.

Whenever TB tried to play the custom .wav file I had to notify when
emails arrived, the sound was locking it up.

One issue resolved all my MM to get sorted out.

---

### Post by philinux on 2008-07-02
Started today for me. Grays out then have to force quit. Even had to ctrl backspace as well.

Only addon Ive got is webmail and thats been fine for months.

[http://ubuntuforums.org/showthread.php?t=847297](http://ubuntuforums.org/showthread.php?t=847297)

---

### Post by pchandle on 2008-07-07
I had the same lock up problem with TB on Gutsy Gibbon. Upgraded to Hardy Heron, with no difference - problem still occured when checking email after startup. After using the -safe-mode option noted earlier in this thread, I was able to nail the cause. It turned out to be the webmail plug-in that kept locking up my system. Just another reason to drop my hotmail I guess.
PC.

---


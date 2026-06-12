---
title: "Vent thru wine... OSS arguement?"
date: 2007-09-12
forum: Wine
---

### Post by weezerisrock on 2007-09-12
I have vent running thru wine.  Things work great!  I can hear other people, they can hear me, and my push to talk button works even when vent is in the background.  My problem arises when I am using World of warcraft in Cedega.  As soon as the game loads my vent goes silent.  PTT and everything still works people text me in game telling me they can hear me.  However I can hear nothing.

I've marked it as the game by hitting the push to talk over and over to make sound.  The second the game loads that goes silent.  I have winecfg setup as OSS currently however I have also tried ALSA, I have also tried world of warcraft with OSS and ALSA settings.  Still nothing.  I've tried winecfg with both OSS and ALSA.  Nothing.

If anyone has any ideas I would really appriciate hearing them!

Thank you.

=w=

---

### Post by weezerisrock on 2007-09-13
bump for some love?

---

### Post by Seraed on 2007-09-13
Have you tried using the aoss wrapper?

---

### Post by weezerisrock on 2007-09-15
at the risk of sounding completely noob, how would I go about doing that?  I looked in the winecfg but didn't see a setting for it.

---

### Post by bwhitaker on 2007-09-15
Did this just start happening for you? Or has this been a long standing issue.

I switched my wife's machine over to ubuntu about 2 weeks ago, pretty much all she does is play yahoo games, World of Warcraft and talk on vent.  I had everything working 2 weeks ago, including using vent while playing wow.  Now vent becomes silent when wow is open, also vent gets a failure to bind input device message when you open it with wow already running.

---

### Post by weezerisrock on 2007-09-15
Don't know if it is an new issue or not.  I recently switched to ubuntu.  I know I did have it working once and was extremely excited.  The next day nothing.  And everything I have tried has been unsuccessful.  I know the issue deals with control of the sound card and vent's control of it is being taken away when World of Warcraft starts.

---

### Post by bwhitaker on 2007-09-15
I just did some digging on the wow boards and found this:

[http://forums.worldofwarcraft.com/thread.html?topicId=1531075321&sid=1](http://forums.worldofwarcraft.com/thread.html?topicId=1531075321&sid=1)

[http://forums.worldofwarcraft.com/thread.html?topicId=1602361123&sid=1](http://forums.worldofwarcraft.com/thread.html?topicId=1602361123&sid=1)

[http://forums.worldofwarcraft.com/thread.html?topicId=1272012664&sid=1](http://forums.worldofwarcraft.com/thread.html?topicId=1272012664&sid=1)

I'm wondering if they pushed part of this early and it's causing the issue.  I'll see if i can take a look at her computer later tonight.  I canceled my account months ago or I would try it on my laptop.

---

### Post by weezerisrock on 2007-09-16
It hasn't been pushed yet.  Its possible they are making small adjustments but I haven't seen a patch since the last time I had it working.

---

### Post by bwhitaker on 2007-09-16
Ok I think I got it working.  I was running wow though Crossover office, and vent through standard wine.  WoW was using OSS(defualt) and vent was on Alsa.  I changed the CX bottle use alsa. This allowed both of them to work at the same time. 

I did find one smaller issue, apparently when you log a character on it seems to break vent, to fix this simply alt tab and disconnect/reconnect to vent.  This seems to have fixed her issues.


Hope this heps.

---


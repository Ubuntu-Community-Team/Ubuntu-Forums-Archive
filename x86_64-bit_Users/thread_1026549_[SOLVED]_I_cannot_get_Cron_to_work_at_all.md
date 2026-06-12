---
title: "[SOLVED] I cannot get Cron to work at all"
date: 2008-12-31
forum: x86 64-bit Users
---

### Post by mick316 on 2008-12-31
Hey all, I have a clean install of Intrepid (64 bit) and I want to use cron to launch my torrent client for my off peak downloads.

Here is what I am using   01 04 * * * export DISPLAY=:0 && ktorrent

I have also tried gnome-schedule & the results are the same.

I have tried to launch firefox, gnome-terminal, thunderbird and nothing happens.

Any help would be greatly appreciated.

Thanks.

---

### Post by mick316 on 2009-01-02
Update, I have also tested with Fcron and still no luck using fcrontab. I don't want to go back to Hardy  just so that I can get this working.

---

### Post by mick316 on 2009-01-03
I have made some more progress.Using gnome-schedule, I can get a one off task to run at whatever time, but if I make it recurrent it won't run at all.

---

### Post by Cheesehead on 2009-01-03
Congratualtions, you beat the 'display=:0' trick that stumps a lot of users.

Check your path to ktorrent and other apps. Often in cron you must explicitly define your path ('/bin/foo' instead of 'foo')

I assume cron is working, and responds to a test?

---

### Post by mick316 on 2009-01-03
Cheesehead,
Thanks for your reply,
Yes cron is working, if I run with today's date it will work fine, If I set it to go off recurrently (* * *), then it fails to work. That is what has me stumped now.

---

### Post by Cheesehead on 2009-01-04
In your example, 01 04 * * *, you're trying to execute at 04:01 a.m. daily? 

Are you using the 'crontab -e' command to change your crontab, or another method?

What happens if you try a recurring-every-minute test?
(example)* * * * * DISPLAY=:0.0 /usr/bin/zenity --info --title "Test" --text "Cron Test"

Does the run/failure show up in your /var/log/syslog? Can you post the relevant lines?

---

### Post by mick316 on 2009-01-04
Yes I wanted, to run at 1.04am every morning., but for the point of the exercise, either will do.

I was using crontab-e and also gnome-schedule.

With regards to the test, I can't see anything launching but, here are the lines from the log:

Jan  5 07:16:01 mike-desktop /usr/sbin/cron[5271]: (mike) RELOAD (crontabs/mike)
Jan  5 07:16:02 mike-desktop /USR/SBIN/CRON[8586]: (mike) CMD (DISPLAY=:0.0 /usr/bin/zenity --info --title "Test" --text "Cron Test")
Jan  5 07:17:01 mike-desktop /USR/SBIN/CRON[8613]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  5 07:17:01 mike-desktop /USR/SBIN/CRON[8620]: (mike) CMD (DISPLAY=:0.0 /usr/bin/zenity --info --title "Test" --text "Cron Test")
Jan  5 07:18:02 mike-desktop /USR/SBIN/CRON[8642]: (mike) CMD (DISPLAY=:0.0 /usr/bin/zenity --info --title "Test" --text "Cron Test")
Jan  5 07:19:01 mike-desktop /USR/SBIN/CRON[8660]: (mike) CMD (DISPLAY=:0.0 /usr/bin/zenity --info --title "Test" --text "Cron Test")
Jan  5 07:20:01 mike-desktop /USR/SBIN/CRON[8676]: (mike) CMD (DISPLAY=:0.0 /usr/bin/zenity --info --title "Test" --text "Cron Test")
Jan  5 07:20:32 mike-desktop /usr/bin/crontab[8692]: (mike) LIST (mike)
Jan  5 07:20:42 mike-desktop /usr/bin/crontab[8696]: (mike) LIST (mike)
Jan  5 07:20:51 mike-desktop /usr/bin/crontab[8700]: (mike) LIST (mike)
Jan  5 07:21:00 mike-desktop /usr/bin/crontab[8704]: (mike) LIST (mike)
Jan  5 07:21:01 mike-desktop /USR/SBIN/CRON[8713]: (mike) CMD (DISPLAY=:0.0 /usr/bin/zenity --info --title "Test" --text "Cron Test")
Jan  5 07:21:09 mike-desktop /usr/bin/crontab[8727]: (mike) LIST (mike)
Jan  5 07:21:18 mike-desktop /usr/bin/crontab[8736]: (mike) LIST (mike)
Jan  5 07:21:27 mike-desktop /usr/bin/crontab[8740]: (mike) LIST (mike)
Jan  5 07:21:36 mike-desktop /usr/bin/crontab[8744]: (mike) LIST (mike)
Jan  5 07:21:45 mike-desktop /usr/bin/crontab[8748]: (mike) LIST (mike)
Jan  5 07:21:54 mike-desktop /usr/bin/crontab[8752]: (mike) LIST (mike)

---

### Post by Cheesehead on 2009-01-05
1) Have you tried:
4 1 * * * DISPLAY=:0.0 /bin/ktorrent   (that may not be the correct path to ktorrent)

2) Workaround: If you're tired of banging your head against a wall and just want it to work from your user crontab:
4 1 * * * /user/you/daily.torrent.start.script

And place a script that works, named appropriately, in the right place to actually launch ktorrent.

---

### Post by mick316 on 2009-01-05
I will give it a shot when I get home, and report tomorrow.

Thanks again so much for your help and patience with this. 

I have a workaround, that means I have to set it every night manually using gnome-schedule. Ke sera sera.

It just bugs me that this used to work fine in 8.04 and not now.

---

### Post by mick316 on 2009-01-06
Tried again and still no luck, I will stick with the one time work around. Thanks for all your help.

---

### Post by mick316 on 2009-04-19
For anyone having trouble with this - I finally got it working. 

I had to do this first - sudo chown user:user ~/.Xauthority (user being your username).

The problem is to do with Xauthority and xhost. I could get it to run by typing this command in terminal: "xhost +" .

Someone from another forum said to add this line "echo "xhost local:username > /dev/null" >> ~/.bashrc" to /etc/bash.bashrc.

Once done, xhost is configured at log in, and cron now has no problems launching GUI's.

---

### Post by Slim Odds on 2009-04-19
> **mick316 said:**
> Someone from another forum said to add this line "echo "xhost local:username > /dev/null" >> ~/.bashrc" to /etc/bash.bashrc.

Once done, xhost is configured at start up, and cron now has no problems launching GUI's.

Your .bashrc file only gets sourced when you log in. So if you reboot your machine but don't log in.... then your cron job will not work.

---

### Post by mick316 on 2009-04-19
Thanks for that - Noted and Corrected - Cheers.

---


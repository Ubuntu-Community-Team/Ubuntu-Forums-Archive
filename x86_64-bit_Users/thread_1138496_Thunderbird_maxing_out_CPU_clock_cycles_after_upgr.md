---
title: "Thunderbird maxing out CPU clock cycles after upgrade to Jaunty"
date: 2009-04-26
forum: x86 64-bit Users
---

### Post by Cincinnatux on 2009-04-26
On a Dell m1330 XPS (Intel T9300) I've been running 64-bit Ubuntu.  When I upgraded from 8.10 to 9.04, however, Thunderbird stopped working smoothly.  When I start Thunderbird, it connects with my mail server, sees how many messages need to be downloaded, and starts downloading them.  After anywhere from 0-5 emails, it stops.  Using System Monitor, I can watch as the CPU History shows a dramatic uptic in CPU usage, such that one of my two cores pegs out at 100% and stays there.  Quitting Thunderbird and restarting it will get me another 0-5 emails, so every day I start/quit Thunderbird dozens of times just to download my email.  It works, but the user experience is, well, annoying.

I have not been able to find any other references to T-bird having this problem on other machines after upgrading to Jaunty, so I'm suspicious that I've got something peculiar on my end and I just lack the Linux smarts to investigate.  Here's what I've tried thus far:

1.  I disabled Compiz and all attendant eye candy, but that did not seem to help.  
2.  I rebooted several times.  No help there.
3.  I used Synaptic to re-install T-bird.  Made no difference.
4.  I shut down Deluge and Firefox, thinking maybe there was a problem sharing network resources.  Made no difference.

I'm willing to do a lot more work here but do not know where to begin.  Would it be easiest for me simply to roll back to 8.10?  I'd be fine with that.  8.10 was treating me well - other than my inability to play OpenFracas after upgrading from 8.04.

Even an RTFM response would be fine, so long as you can name the text I should hunt down and read.  

Many thanks!

---

### Post by Shriner on 2009-04-26
Running BOINC? If so, see here: [http://ubuntuforums.org/showthread.php?t=1137783](http://ubuntuforums.org/showthread.php?t=1137783)

---

### Post by Cincinnatux on 2009-04-27
Thanks for the tip, Shriner.  That's not my issue, however, so I'm still searching for answers.  FWIW, Thunderbird changed its behavior on me today.  Now, each time I click "Get new mail" it says it only finds one new email and then gets it.  To retrieve the next email, I can click on the "get new mail" button again, and that seemed to work about four or five times (thus retrieving only four or five emails out of the 30+ that were pending but whose existence Thunderbird was unaware) before maxing out my CPU again and ceasing to retrieve email.  Really odd.

---

### Post by Jive Turkey on 2009-04-27
I had a similar problem in Intrepid.  I resolved it by disabling/uninstalling one of the plugins I was using, actually, I think it was a theme oddly enough.

---

### Post by Cincinnatux on 2009-04-28
Fantastic suggestion!  I went in and disabled Lightning.  We'll see if that works.

---

### Post by Cincinnatux on 2009-04-28
Looks like JiveTurkey hit the nail on the head.  Disabling Lightning has restored normal function to Thunderbird.  I wasn't using Lightning anyhow, so I'm not particularly interested in troubleshooting the issue further.:guitar:

---


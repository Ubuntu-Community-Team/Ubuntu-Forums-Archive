---
title: "Firefox won't run"
date: 2006-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Minilek on 2006-02-08
I have seen the various threads about plugins and java with firefox using an amd64...but I can't even get firefox itself to run!  When I run firefox nothing happens... I don't get any error messages or anything -- it just never opens (and appears nowhere when typing ps).  I've tried looking at various error logs in /var/log but found nothing.  I tried apt-get removing then reinstalling it -- again nothing.  I also tried sudo apt-get install mozilla-browser -- that browser didn't work either.  Has anyone experienced anything like this?

---

### Post by sylvester_0 on 2006-02-08
Sounds like you're system is pretty mucked up and it may just be better to start over. Make sure and do a validation on you CD and don't do a "server" install.

If you want to try to fix it, start by opening a konsole and running firefox from there...it'll tell you where it's having problems.

---

### Post by Minilek on 2006-02-08
Right after the post, I fiddled around some more and got it working..something was wrong with some of my file permissions for some reason (in particular, the .mozilla folder in my home directory had wrong permissions).  I removed that directory, apt-get removed firefox, then reinstall firefox and now it works.

Now to worry about plugins... : )

Thank you though!  And what do you mean running it from a konsole (konsole=terminal?)?   I ran it from a terminal but no errors showed.

---

### Post by sylvester_0 on 2006-02-08
Cool! Good job fixing it....did you try the terminal method after or before you fixed it? If you had tried it before it should have told you that your permissions were wrong.

Side note: Yes...konsole=terminal.... I just hate gnome and LOVE my yakuake! Check out that program if you're a kde user.

---

### Post by Minilek on 2006-02-08
I had been running it from the terminal before and got no permissions-related error messages (or any error messages for that matter)... I'm not sure why.

---


---
title: "Ubuntu Stalls"
date: 2008-07-15
forum: x86 64-bit Users
---

### Post by Imaginationac on 2008-07-15
It's not a huge problem yet, but randomly the entire system becomes unresponsive. I'm not doing anything resource intensive either. I noticed this mostly while running Firefox. Has anyone had any similar problems? Is there anything I can do to solve this?

---

### Post by Sef on 2008-07-15
1) What version of Ubuntu do you have?

2) Are you running Firefox 2 or 3?

---

### Post by firecat53 on 2008-07-17
I have also seen this. I'm on Hardy 64, using the default Firefox 3.0 and nvidia-glx-new drivers from the repos. I believe it's related to the nvidia drivers, but I'm not sure. I've just lived with it, as it doesn't happen that often, and the system always recovers after 15-30 sec. The other thing I see is that after that happens, I'll start getting a periodic flicker in the display (like every minute or 2). To get rid of that, I'll Ctrl-Alt-F1 to get to one of the virtual terminals and then just Crtl-AltF7 to get back to my desktop.

Anyway, it'd be nice to get this all the fixed, but at least its more manageable now than it was on Gutsy and before!!

Scott

---

### Post by ooolongT on 2008-08-11
I am having the same problem.  I am a total newbie, but I am really enjoying Ubuntu.  I am on 8.04, and Firefox3.  I think I have nVidia drivers too, and am happy to check if someone can tell me how to do that.

---

### Post by TonyMo on 2008-08-12
If this stalling is happening while using Firefox, try this...

Go to Firefox->Preferences and select the Security Tab

Uncheck "Tell me if the site I'm visiting is a suspected attack site"

and 

Uncheck "Tell me if the site I'm visiting is a suspected forgery"

This stopped the stalling for me on two Hardy installations....

Hope this works for you

---

### Post by kaligus on 2008-08-12
> **Imaginationac said:**
> It's not a huge problem yet, but randomly the entire system becomes unresponsive. I'm not doing anything resource intensive either. I noticed this mostly while running Firefox. Has anyone had any similar problems? Is there anything I can do to solve this?

On a similar note and to add info to the thread.

I did not have a single lock up or freeze or anything for two months.

I added 2GB ram today (3GB total) and have had raise elephants three times after waiting for 10 minutes.

AMD-64
Nvidia (restricted) F4-6600
Firefox-3 (seems to be flash or ad-block related)

any more info I can gather?

---

### Post by wd5gnr on 2008-08-12
Not sure if it is the same problem, but I've noticed that FireFox 3 sometimes turns grey for a few seconds. The system stays responsive, but FireFox sleeps. The warning settings didn't help. I _think_ it has to do with flash on the page, but I'm not 100% certain. It does recover though.

---


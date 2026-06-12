---
title: "Acer Aspire 9300 - Cannot hear sound"
date: 2007-05-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mr. Brownstone on 2007-05-09
I tried alsamixer and nothing was muted. The driver seems to have loaded fine and I don't get any errors but I can't hear anything.

I ran a script in another thread which shows my ALSA information: [http://pastebin.ca/478756](http://pastebin.ca/478756)

Thanks a lot for any assistance!

---

### Post by Mr. Brownstone on 2007-05-10
Does anyone else have this problem?

---

### Post by EduMaxwell on 2007-05-15
I have an Acer Aspire 5051 and had a similar problem.  You may have already done this, but in ALSA mixer go to Edit > Preferences.  There you will find a number of unselected options, possibly including a "surround" option.  Using trial and error (by selecting certain volume controls and making sure they are NOT muted), you might find the solution to your problem without going into terminal mode.  After a lot of sweat and tears and reconfigurations, I finally solved my problem with this simple approach.  I noted that you have already made sure nothing is muted, but you did not indicate whether you had enable certain sound functions in your Preferences.  Try it and let me know if it works for you.

---

### Post by Mr. Brownstone on 2007-05-15
That was it! Thanks a lot for the help!

---

### Post by strumluff on 2007-05-15
Just to inform you, as I also own an Acer Aspire (5050) I discovered that if you want sound from the headphone jack then that is referred to as the Front Speakers in ALSA mixer. If you want sound from the laptop speakers then I found that Surround is the line to alter.

---

### Post by faizoro on 2007-10-20
I am having the same sort of trouble with my 9300-5317 in Ubuntu Gutsy.  The fixes you describe I suspect don't really apply though I admit I am not knowledgable enouph to be sure I am just failing in my tweaking.  Note: under Ubuntu Edgey I took the steps you describe and it (partially) worked sometimes (what I mean is- I had reinstalled UBU a couple of times in my experimentation with dual booting and also with Vista and the first time I had been able to get it to work, later I had some trouble and I think finally I was able to get it to work- though the mic and line out never worked properly).  

Too bad- I am bummed out about the audio as I enjoy UBU so much.

---


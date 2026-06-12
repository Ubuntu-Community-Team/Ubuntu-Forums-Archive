---
title: "Pulseaudio in 64-bit?"
date: 2008-12-18
forum: x86 64-bit Users
---

### Post by SeePU on 2008-12-18
I am running 64-bit Kubuntu 8.10.

I was looking for the install instructions for installing Pulseaudio in a 64-bit Linux OS, preferably one for Ubuntu or Kubuntu.

Can anyone refer me to the 'how-to' or provide instuctions?

I'm not sure if it's any different than the standard install on a 32-bit Linux distro but it might.  I thought I'd ask for specific instructions before I install a lot of stuff.

Thanks in advance.

For the moment, I'll keep looking for them.

---

### Post by Sef on 2008-12-18
Ubuntu and Kubuntu come with Pulse Audio.

---

### Post by kostkon on 2008-12-18
If you want more access to its features, install the *PulseAudio Device Chooser*.

---

### Post by Sef on 2008-12-18
> If you want more access to its features, install the *PulseAudio Device Chooser*.


You can download it from Adept.  Set it to 'All Available Applications'.

---

### Post by SeePU on 2008-12-19
Oh, my bad.  I guess you could say it was a dumb question.  Sorry!

Thanks for the info, guys!

---

### Post by Sef on 2008-12-19
> Oh, my bad.  I guess you could say it was a dumb question.  Sorry!

You did not ask a dumb question.  The only dumb questions are the ones that are not asked because no one can respond to it to give an answer.

---

### Post by SeePU on 2008-12-20
> **Sef said:**
> You did not ask a dumb question.  The only dumb questions are the ones that are not asked because no one can respond to it to give an answer.
Thanks. ;)   I have another question then:

Is this page still relevant to setting up Pulseaudio?

[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

Currently, on my system, I don't see any way of adjusting volume or starting pulseaudio automatically.  I know there are many pulseaudio packages available but I'm not sure which ones to add to my system.  Also, in the above 'how to', there are some edits to a file and in the main pulseaudio 'how to', instructions include a creation and edit to /etc/asound.conf.  Is this necessary in Ubuntu or just follow the above 'how to?'  Of course, these questions apply to setup in 64-bit Ubuntu unless they apply to both 32-bit and 64-bit (I will assume so until informed otherwise).

---

### Post by SeePU on 2008-12-20
> **Sef said:**
> You can download it from Adept.  Set it to 'All Available Applications'.
The package, 'padevicechooser?'  

But, will pulseaudio start automatically whenever I start up a media device?

I didn't find that in Hardy.  I had to type 'Pulseaudio -D' each time and it wasn't the smoothest process (imho).

---

### Post by Sef on 2008-12-20
>  But, will pulseaudio start automatically whenever I start up a media device?

I have not had a problem with it.  I am using Intrepid.

---

### Post by SeePU on 2008-12-20
I install it and there's STILL problems!

I get the message:

'Connection failed; connection refused.'

Same pulseaudio problem that happened in Hardy.

In other words, it's not set up by default.  It's also horrible.  You have to edit or set up according to either the Pulse Audio howto I provided or go to the Pulseaudio site.  It's DEFINITELY not working 'out of the box' in Ubuntu.

---

### Post by kostkon on 2008-12-20
> **SeePU said:**
> In other words, it's not set up by default.  It's also horrible.  You have to edit or set up according to either the Pulse Audio howto I provided or go to the Pulseaudio site.  It's DEFINITELY not working 'out of the box' in Ubuntu.
No, It think you are wrong. It is setup by default in Ubuntu (not so well in 8.04, though) and is working well in the majority of cases.

The how-to you are quoting it's just an added bonus, to make PulseAudio work even better, especially in 8.04. In 8.10 it's pretty well setup.
> **SeePU said:**
> I install it and there's STILL problems!

I get the message:

'Connection failed; connection refused.'
Same pulseaudio problem that happened in Hardy.
Now, in your case, I suspect there is problem, obviously, and PulseAudio crashes or it's not loading at startup.

First of all, could you check that you have PulseAudio in your session list. Can you check if you can find it in the list in *System &#8594; Preferences &#8594; Sessions*?

---

### Post by SeePU on 2008-12-20
> **kostkon said:**
> No, It think you are wrong. It is setup by default in Ubuntu (not so well in 8.04, though) and is working well in the majority of cases.

The how-to you are quoting it's just an added bonus, to make PulseAudio work even better, especially in 8.04. In 8.10 it's pretty well setup.

Now, in your case, I suspect there is problem, obviously, and PulseAudio crashes or it's not loading at startup.

First of all, could you check that you have PulseAudio in your session list. Can you check if you can find it in the list in *System &#8594; Preferences &#8594; Sessions*?
How am I wrong?!?  It didn't work 'out of the box' in Hardy (although the claim is that it does) and now it's clear it doesn't either in Intrepid.

There's almost *100* pages added to that 'how-to- page.  That suggests to me that it usually doesn't work properly.  I don't know why it works on your system or someone else's.  I don't have access to your computer but I go by the facts - it doesn't work.

There is also more than one 'how to' page for PulseAudio consisting of various edits and adding to files.  That shows that there is much needed configuration involved.  

I don't know what you mean by 'sessions.'

---

### Post by SeePU on 2008-12-20
[http://ubuntuforums.org/showthread.php?t=973637]("http://ubuntuforums.org/showthread.php?t=973637")

I rest my case.

I never thought a Linux app would be worse than the infamous Network Manager but PulseAudio wins!

---

### Post by Sef on 2008-12-20
>  I never thought a Linux app would be worse than the infamous Network Manager but PulseAudio wins!The app worked well, but it was not properly set up in Ubuntu.   In other distros, it was well set up.

> I install it and there's STILL problems!

I get the message:

'Connection failed; connection refused.'
I wonder if you problem is a firewall problem.  That the firewall is blocking your site.   Have you set up a front-end GUI for your firewall or changed it via the Terminal?   (IPTables is installed by default.)

---

### Post by SeePU on 2008-12-20
I don't think a firewall is the problem.

I was able to progress a bit more.

I finally found 'KUser' in the menu which I used to set up the user 'pulse' and user 'myself/me' (etc.) into the following groups - pulse, pulse-rt and pulse-access.   I hope I did this right.

I then created the /etc/asound.conf file according to a lot of pulseaudio instructions out there and added it accordingly:

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

I know that is for Ubuntu 7.10 but maybe it's applicable still to Intrepid?   Anyway, I tried it and now the volume meter bars move with audio from media players.  I don't know if this is a full fix or what but some part of my pulseaudio works now (it seems).   

I know that some pulse audio instructions have more text added in the /etc/asound.conf file (see the instructions for pulseaudio in Debian, for e.g.) but for now, I will take it unless I run into issues.  If something craps out or doesn't work, I'll add the rest or research some more.

It's unfortunate, you have to configure but my main complaint was that 'out of the box' claim didn't really do much for me.  But, thanks for putting up with me.

---

### Post by SeePU on 2008-12-20
Just found out it doesn't work if I use my browser for producing audio.  For e.g., if I play a YouTube video.  Not sure what to do for that.  

Any ideas?

---

### Post by Ng Oon-Ee on 2008-12-21
> **SeePU said:**
> Just found out it doesn't work if I use my browser for producing audio.  For e.g., if I play a YouTube video.  Not sure what to do for that.  

Any ideas?
Just a suggestion, there is no real differnece in using Pulseaudio in 64-bit vs 32-bit, all the packages are compiled for both anyway. You may receive better and faster help in some other sub-forums, specifically those to do with Multimedia.

And about Pulseaudio working out-of-the-box, a clean install of Intrepid should have it working with common hardware. That was my experience, and the 'facts' you're working off are based on a thread meant mainly for issues with Pulseaudio in Hardy, where there WERE many issues, which I myself encountered and had to fix. Of course, if you're upgrading from Hardy to Intrepid (not a clean install) then some issues would follow you over in the form of wrongly set conf files etc.

If some apps are producing sound but others aren't, you'd first have to ensure that the apps that DO are doing it through pulseaudio. Use pavucontrol to see if the apps producing sound appear under 'playback'. If not, then those apps are actually directly accessing the sound card.

For firefox, try to native 64-bit flash 10 plugin, fixes a lot of issues, its here in the 64-bit forums somewhere. Or run firefox from terminal and try and see if any error messages are generated.

---

### Post by SeePU on 2008-12-21
Well, it was a fresh install of Kubuntu Intrepid 8.10 and PulseAudio would not work 'out of the box' for me.  I had to configure and create the /etc/asound.conf file and add text to it like previously described.  

That's *my* experience and 100 pages or more of posts of other people having problems in both Hardy AND Intrepid attest to that.   So, I am not wrong, like I said.  

I would appreciate any assistance getting Flash video/audio to work with PulseAudio and if I should go to the Multimedia section for that, I can do that quite willingly.  Thanks for the tip.

---

### Post by Ng Oon-Ee on 2008-12-21
Well, all the best in getting it working, then.

---


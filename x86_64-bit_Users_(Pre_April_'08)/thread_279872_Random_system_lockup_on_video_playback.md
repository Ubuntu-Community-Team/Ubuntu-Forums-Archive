---
title: "Random system lockup on video playback"
date: 2006-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by fabertawe on 2006-10-18
Hi folks,

I want to check if anyone has any ideas about this before I report it on Launchpad as it's a critical issue for me but I can find no bug reported so it makes me suspect it's a local problem.

I'm getting random system lockups on playing back video (confirmed with mp4, wmv, aspx, flv) with all my players (MPlayer, VLC, Xine, Democracy TV player and MPlayer plugin in Swiftfox). It can happen at different places or not at all with the same video clip. The desktop will freeze (everything apart from mouse pointer movement) and the sound will continue for a little while (varying amounts) before also stopping.

I am using DD 6.06, amd64-k8. I have installed the 32bit codecs and MPlayer32 (are all the above filetypes related to this?). This has only been happening recently (or so it seems, maybe I've been lucky with the randomness until lately).

I've also searched the logs but can find nothing incriminating (bare in mind I'm a relative noob though).

Any pointers would be greatly appreciated.

Cheers ... Paul

EDIT: Just happened with an m4v video also.

---

### Post by John.Michael.Kane on 2006-10-18
If the hard locks are with this one clip that could mean the clip is shot.

Have you tried another clip or dvd?

---

### Post by fabertawe on 2006-10-18
> **SD-Plissken said:**
> If the hard locks are with this one clip that could mean the clip is shot.

Have you tried another clip or dvd?

This has happened with many clips, at least one of all of the types mentioned in my first post. I have not had a single problem playing back DVDs.

Thanks ... Paul

---

### Post by fabertawe on 2006-10-25
Ok... I'm almost positive this is down to the Deskbar panel applet. Is **anyone** running this and able to play back file types such as wmv without incident? Especially if you're running the amd64-k8 kernel.

Please take the time to reply if you can, before I contact the Deskbar people.

Cheers ... Paul

---

### Post by RSingh on 2008-05-12
Im having the same problem as described here, random lockups on video playback. Im only able to use the mouse and the audio plays and no video and the system is frozen. I have a intel chipset and 32 bit system, GMA 950 card and 1G RAM.

Any Ideas...

---

### Post by RSingh on 2008-05-18
bump!

any ideas anyone???

---

### Post by branbuntu on 2008-05-26
I am experiencing the same problem.
HP NC6400 PC with 1GB RAM, Ubuntu Hardy.

The lock-up happens in any player on the the first attempt of playback of a DivX file after a boot-up.

The problem seems to happen when the video is played back in a workspace other than 1 (the panel on the left).

I'll keep researching and let you know if I see any other consistent behavior.

Update: I haven't seen a lock-up recently, my system has the latest patches as of June 2008.

---

### Post by RSingh on 2008-05-27
Man, This is getting annoying. Already 3 lockups in one day!.

Last time I tried playing a normal AVI and the screen flickered for a second and then the entire screen went black with purple dashed lines.

Whats even funny is that System Log isn't registering anything.

---


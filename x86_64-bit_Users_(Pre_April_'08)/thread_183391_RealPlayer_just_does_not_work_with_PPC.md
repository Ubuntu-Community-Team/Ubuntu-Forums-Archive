---
title: "RealPlayer just does not work with PPC"
date: 2006-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Uta on 2006-05-27
Please correct me if I am wrong and you have Ubuntu PPC installed that plays RealPlayer files. I'd love to hear from you. I first tried RealPlayer 10, which installed fine but just didn't work. The BBC News feed opens a window, it says it's buffering but nothing happens. I also tried Helix built for Linux PPC and got the same results. I understand about Flash not working but Realplayer? Please let me know if there is anyone who has RealPlayer working on a Ubuntu PPC. I am currently using Dapper on my iBook G4. (I installed on my Ubuntu/Dell laptop and it works perfect).

---

### Post by jazzmuzik on 2006-05-27
mplayer with the extra codecs installed can play real media although I generally download the media first, then view it. My point is I don't know how well it handles streaming media. Real sucks anyway.

---

### Post by ssam on 2006-05-28
did you find the powerpc realplayer on the helix downloads page?

do you get any error messages when you run it from a terminal?

did you install libstdc++5, in synaptic?

---

### Post by Uta on 2006-05-28
Thanks for your reponse, as mentioned I did download the Helix RP for PPC; from their page. I did a search and I found that libstdc++5 was already installed.
I open the BBC News video link, RealPlayer opens a window, it says it's buffering and that is it, it never loads and the RealPlayer logo that is in the window is doubled and split. Do you have a functioning RealPlayer working on a PPC platform, streaming video or sound? Thanks!

---

### Post by jsonder on 2006-05-29
I'm streaming from npr right now.  After fixing a problem (another player had controlled the audio according to the error message)

I dumped mplayer, kaffine, xine, gxine to get Real working again.  However, I'm running Real 8 and just using it for audio.

I tried BBC video and was told that I needed a subscription (not likely).  No video with the feeds I'm playing with for npr.  I'll go look at their web site.

John

---

### Post by jsonder on 2006-05-29
Follow up.  Real 8 (what is available for the PPC architecture) doesn't seem to be able to play videos.  I compared Dapper Dan Beta 2 on a ppc and a core duo.  The core duo has RealPlayer 10.0.7.785 (gold) which plays videos at the real site.  The same videos will not play with RealPlayer 8 on my mac mini.

---

### Post by Uta on 2006-05-29
If I understand you correctly you can stream video with RealPlayer 10.0.7.785 (gold), running Dapper on a PPC platform, if it's the new Apple box with the Intel processor? Interms of BBC, just click on one of the video feeds on the right even though it says you need a subscription.

---

### Post by jsonder on 2006-05-29
I don't know about new apple boxes.  The core duo 2300 w/ 1 gig RAM, dvd burner, 15.4-inch lcd, etc., was a Dell special offer ($800).  

I haven't gotten the graphics into 1280x800 yet and am using Ubuntu in 1024x768.

However, the Intel-based macs are **not** PPC architecture.  You use an i386 installation followed by a "sudo apt-get install linux-686" command.  Then do the updating and such.

I am not a ware of a RealPlayer10 being available for the PPC architecture.  If there is one, will you point me in the direction to find it?

John

---

### Post by Uta on 2006-05-30
[QUOTE=jsonder]I'm streaming from npr right now.  After fixing a problem (another player had controlled the audio according to the error message)


John[/QUOTE]

I am having the same issue about another device controlling the audio. How did you fix it? I don't have mplayer installed only the default Movie Player/sound video apps that come with Dapper. My error is: "Cannot open the audio device. Another application may be using it." I get this error message when RealPlayer opens the file.
All I'm trying to do is play a, "smil file".
Remember I'm a PPC version of Dapper.

---


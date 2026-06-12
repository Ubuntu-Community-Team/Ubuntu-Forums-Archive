---
title: "kde on 64 bit?"
date: 2006-12-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by rplantz on 2006-12-03
When I was running dapper, I installed kde to try it out. I tried both doing just kde and doing kubuntu. It was extremely slow compared to gnome. And I was never successful at getting kmail to work with my imap accounts.

Now I am running edgy. Rather than try kde on edgy, I installed a second distro on my machine, Debian. I thought that kde might work better under Debian because is it more desktop agnostic than ubuntu. Debian works very well with gnome (seems a bit faster than ubuntu) but is extremely slow with kde and kmail does not work with my imap accounts. Essentially, I get the same behavior with kde under Debian as I did under dapper.

I'm running an amd64 3200+ in 64-bit mode, nvidia geforce fx5200, 128MB and have 1GB ram.

Has kde simply not made it into the 64-bit world yet?

---

### Post by napsilan on 2006-12-03
I'm running kubuntu edgy 64 with beryl, and it seems fine to me.  I'm using a n AMD 64 3200, nvidia 7800gt, and 2gb ram.

---

### Post by Bhawns on 2006-12-03
Hi I am also in full 64bit mode using Gonome on Ubuntu 6.06LTS (not ready to do edgy 6.10 yet. What I want to know is where you got the debian packages from and how is it installed.

---

### Post by rplantz on 2006-12-03
> **Bhawns said:**
> Hi I am also in full 64bit mode using Gonome on Ubuntu 6.06LTS (not ready to do edgy 6.10 yet. What I want to know is where you got the debian packages from and how is it installed.

First, I think the only way to do it is with a fresh install. When I first installed ubuntu, about 1-1/2 years ago, I thought that I was getting a debian installation. Well, I've learned some since then. I don't think you can convert ubuntu to debian.

I installed the "etch" release, which is "testing." It is not called "stable," but most people find it to be just fine. I don't think I would try to run it on, say, a server for a business. I would go with the "stable" version.

I did a net install, starting with a CD I downloaded [here](http://www.debian.org/devel/debian-installer/). I used a dsl connection. It took about 1-1/2 hours. I am using only 80 GB of my 160 GB disk for ubuntu, so I was able to easily partition the unused half for debian.

---

### Post by kuja on 2006-12-04
If you find it to be slow, try taking a look at [this page](http://www.ubuntuforums.org/showthread.php?t=277090&highlight=kde-core).

For best results set it up from a command-line-only(alternate cd) or server install(?server cd?).

---

### Post by rplantz on 2006-12-04
I appreciate the comments you have all made.

Are any of you using kmail? I still cannot get it to work with my imap accounts.

I have been successful at getting a dozen other email environments working, all the way from mail on my Mac to mutt on my Linux. So I don't think I'm setting kmail up incorrectly. On the other hand, I recently chased a dual booting problem for many hours -- until a sharp-eyed reader pointed out that I had typed a "." instead of a "-" in a file name. :oops:

---

### Post by koshcu on 2006-12-05
I am using kmail on kubuntu/edgy 64bit and I have been using kmail in general for about 5 years now with imap and pop3 setups. I have not run into any issues.

I am not really sure where your problem would be. I have connected to a fair number of different imap and pop servers (all unix ones) and it has just worked.

I also have not had any speed issues under kde in a very long time.

---

### Post by rplantz on 2006-12-05
Since kde is the most popular Linux desktop, it's very weird that I have so many problems with it.

I tried installing just kmail last night and running it from my gnome desktop. Same problem. I set it up to connect to my imap account with my isp, using the same configuration as my evolution. kmail connects (it sees the folders on my imap account) then tells me to wait while it downloads the data. It uses 100% of the cpu (an amd64 3200+) for several minutes. After 15 minutes or more, I finally give up.

Oh well, gnome and evolution work well for me. I was simply curious about kde since it is more popular.

---

### Post by kuja on 2006-12-05
100% cpu usage? Sounds like a most unwelcome bug ... [http://bugs.kde.org](http://bugs.kde.org)
You know what to do ;)

---


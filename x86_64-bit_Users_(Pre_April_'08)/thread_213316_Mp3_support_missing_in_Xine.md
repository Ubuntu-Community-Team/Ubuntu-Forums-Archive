---
title: "Mp3 support missing in Xine"
date: 2006-07-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by cocteau on 2006-07-11
Hi

   I seem to have run into a strange problem with xine. When I try and play one my avi files it gives me this error:

'The stream 'foo' uses an unsupported codec:

Audio codec: MPEG Layer 2/3 (0x0)

Start playback anyway?'


   If I chose yes, the video is playing but there is no sound. Strange as I can use XMMS to play Mp3s without any problems.
   Various posts on these forums seem to suggest that I am missing libxine-extracodecs but since that is not available for the 64 bit ubuntu is there another solution?

---

### Post by frodon on 2006-07-11
Check that you installed all the codecs : 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

However if it depends on the libxine-extracodecs package, i'm not sure that there's a solution other than having a 64bit version for this package.

---

### Post by mogelhead on 2006-07-11
I'm not at my ubuntu box currently but the [ubuntu package lists]("http://packages.ubuntu.com/dapper/libs/libxine-extracodecs") suggests that libxine-extracodecs is available for dapper amd64.

Have you enabled the multiverse repository?

There is a [good guide]("https://help.ubuntu.com/community/RestrictedFormats") about howto enable sound and video codecs. There is a link in there about howto enable the universe and multiverse repositories.

---

### Post by cocteau on 2006-07-11
Thanks

   I'm kind of doing the 'huh what... how?!' thing. I though I had checked every damn place for a 64bit version of libxine-extra codec package, but yes it was available and it works. Thank you.

   However solving one problem has lead to a few others. I am following the codec guide and I have enabled pretty much every standard repo, except the cd one.
   Still I am having these issues:

- No package named gstreamer0.10-pitfdll (and no version 0.8 either)
- No package named gstreamer0.10-plugins-bad-multiverse
- Package gstreamer0.10-plugins-ugly-multiverse is there but won't install because of missing dependency (liblame0 >= 3.96.1-1)

---

### Post by RAOF on 2006-07-11
> **cocteau said:**
> ...
- No package named gstreamer0.10-pitfdll (and no version 0.8 either)
- No package named gstreamer0.10-plugins-bad-multiverse
- Package gstreamer0.10-plugins-ugly-multiverse is there but won't install because of missing dependency (liblame0 >= 3.96.1-1)

1) Pitfdll has never worked for x86-64 as far as I know.  It'd need to be quite a bit more complex (provide a translation layer between the 64bit gstreamer and the 32bit win32 dlls).

2) & 3) seem odd.  **I** can see them (bad-multiverse & liblame) just fine.  The fact that -plugins-ugly-multiverse is (strangely) in *Universe*, and you can see it, suggests to me that the multiverse repository isn't really being used.

Which is odd, 'cause you've installed libxine-extracodecs, which **is** from Multiverse...

---

### Post by cocteau on 2006-07-11
> **RAOF said:**
> 2) & 3) seem odd.  **I** can see them (bad-multiverse & liblame) just fine.  The fact that -plugins-ugly-multiverse is (strangely) in *Universe*, and you can see it, suggests to me that the multiverse repository isn't really being used.

Which is odd, 'cause you've installed libxine-extracodecs, which **is** from Multiverse...

   Well, maybo not. I installed the libxine-extracodecs from the [link that mogelhead provided]("http://packages.ubuntu.com/dapper/libs/libxine-extracodecs").

   However I should have all repositories enabled. From the documentation I gather that the multiverse is added to apt, it's just not enabled. The repos I have enabled are:

Ubuntu 6.06 LTS
   Officially supported
   Restricted copyright
Ubuntu 6.06 LTS Updates
   Officially supported
   Restricted copyright
Ubuntu 6.06 LTS
   Community maintained (universe)
   Officially supported
   Restricted copyright
Ubuntu 6.06 LTS Backports
   Officially supported
   Restricted copyright
   Community maintained (universe)
   Non-free (multiverse)

All the security updates ones too and raof.dyndns.org/falcon.
Except for the falcon ones every repos is enabled for both binary and source files.

  Am I missing anything?

---

### Post by RAOF on 2006-07-11
Yes.  You're missing Multiverse ;).  You might notice that you have Multiverse enabled on **Backports**, but not on the main Ubuntu repository.

---

### Post by cocteau on 2006-07-11
Thanks! It works like a charm now!

Yup... I had yet again been looking in all the wrong places. A simple edit button would suffice. Duh...

One of the things that I _really_ have to get used to in Ubuntu is that almost everything seems to have a gui attached to it and there is so much less need for the command line, which is flippin' wonderful for a newbee like myself.

Thank you again. I can now enjoy Maynard Keenan's complaining on my stereo instead of through my crappy laptop speakers :d

---


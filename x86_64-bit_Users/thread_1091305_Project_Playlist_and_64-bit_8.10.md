---
title: "Project Playlist and 64-bit 8.10"
date: 2009-03-09
forum: x86 64-bit Users
---

### Post by ThatBosnianDude on 2009-03-09
I just installed 64-bit 8.10, I downloaded flash and most flash sites seemed to work, like myspace music player and youtube, but the player on [www.playlist.com](www.playlist.com) does not, so I did some research and found out that I might need 64-bit versions of flash and java, so I get the 64-bit versions of those plugins and I still have the same problem, instead of the player showing up I get a blank box. I also heard that I might need a 64-bit version of Firefox, not sure about that, if I do need a 64-bit of Firefox where can I download it? Any help with this issue will be greatly appreciated because I love [www.playlist.com](www.playlist.com) lol. Thank you for your time. :D

---

### Post by ThatBosnianDude on 2009-03-09
Nobody has encountered this before?

---

### Post by Yellow Pasque on 2009-03-09
Did you uninstall the repo version of Flash before trying to download/install the 64-bit Alpha?

> I also heard that I might need a 64-bit version of Firefox, not sure about that, if I do need a 64-bit of Firefox where can I download it?
If you're using the version of Firefox that came with Ubuntu, it is 64-bit.

---

### Post by ThatBosnianDude on 2009-03-09
No I didn't version the the repo version, do I just have to remove that version or do I have to remove the repo and 64-bit version then install the 64-bit again? Thank you for your response by the way, I was starting to think nobody was gonna respond lol.

---

### Post by ThatBosnianDude on 2009-03-09
I love Ubuntu, I am so tiered of Vista and it's problems, but this is just effin ridiculous, how much time and effort I have to put in to get a damn flash audio player working, and still it does not work, what the hell is going on? I know that support for 64-bit is limited but can we at least get a flash player to work? This time I told my self im gonna stick with Ubuntu, im gonna make it work, but now I find out I can't use my favorite music streaming site and I can't sync up my iPod Touch without having to use a wireless network (which I have, but I am not doing that every time I want to sync my iPod with my computer). Looks like im going back to Vista for the fifth time due to my frustration with Ubuntu. I really tried this time, but no avail.

---

### Post by cariboo on 2009-03-10
I tried the playlist.com player and It worked just fine, I'm using the 64-bit beta from [Adobe]("http://labs.adobe.com/downloads/flashplayer10.html"), click the link for the download page.

First completely remove the flashplugin-nonfree using System-->Administration-->Synaptic Package Manager. Then double click the file you downloaded from Adobe and extract it so some where you   can find it. Next press Alt-F2 and type:

```
gksu nautilus
```

this will open the file manager as root navigate to where you saved the extracted file and copy it to Filesystem-->usr-->lib-->mozilla-->plugins

Or to do it in a terminal:

```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins
```

Jim

---

### Post by ThatBosnianDude on 2009-03-19
I will give it a try, again. Even though I already uninstalled Ubuntu I just find my self day dreaming about it lol. I think im in love with an operating system, is that weird? I'll just set up a Dual Boot. Thanks for your advice.

---

### Post by ThatBosnianDude on 2009-03-19
Cariboo you are the effin sh!t man or woman not sure which one you are lol. It worked like a charm thanks a bunch!

PS. Am I the one who has to switch this thread to SOLVED, if so, how do that?

---


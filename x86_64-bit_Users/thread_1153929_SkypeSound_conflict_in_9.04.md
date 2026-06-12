---
title: "Skype/Sound conflict in 9.04"
date: 2009-05-09
forum: x86 64-bit Users
---

### Post by gewitty on 2009-05-09
When I installed 9.04 first, I had system sounds and Skype sound, but nothing in any multimedia apps. Eventually, I tracked down a 'How To' at [www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html). Once I followed this, I got multimedia sound working OK, but both Skype and Picasa had been removed.

After a bit of trial and error, I discovered that the problem seems to be with libasound2-plugins. When this is installed via Synaptic, multimedia sound works, but Skype and Picasa are removed. If I re-install Picasa, it works just fine and the sound is still OK. However, as soon as I re-install Skype, libasound2-plugins is removed.

So, I can have multimedia sound without Skype, or Skype without multimedia sound. Obviously there is some sort of conflict, but how can I get both working together?

---

### Post by khelben1979 on 2009-05-09
If you download and install the static version of Skype I believe your problem will get solved. [Here]("http://www.skype.com/go/getskype-linux-static") you got it.

---

### Post by gewitty on 2009-05-11
I've tried the static version of Skype from the repositories, using Synaptic. This didn't cure the problem.

When I install Skype, it uninstalls lib32asound2-plugins (killing all multimedia sound playback). When I install lib32asound2-plugins, it uninstalls Skype (and Picasa).

Crazy!

---

### Post by khelben1979 on 2009-05-11
> **gewitty said:**
> I've tried the static version of Skype from the repositories, using Synaptic. This didn't cure the problem.

When I install Skype, it uninstalls lib32asound2-plugins (killing all multimedia sound playback). When I install lib32asound2-plugins, it uninstalls Skype (and Picasa).

Crazy!

Yes, but **don't** install it that way.

---

### Post by gewitty on 2009-05-11
Didn't realise there is a difference. I'll try the download you suggest and see if that works.

---

### Post by gewitty on 2009-05-13
I just downloaded the recommended static file and installed it as per the ReadMe file instructions:

"We recommend copying the
skype binary to /usr/bin and installing sounds/, lang/ and avatars/ into
the /usr/share/skype directory."

This did not appear to have any effect, even after a reboot. I tried running Skype from a Terminal and got the following error message:

dave@dave-desktop:~$ skype
skype: error while loading shared libraries: libXv.so.1: cannot open shared object file: No such file or directory
dave@dave-desktop:~$

There are two other files in the downloaded archive and I'm not sure where these should go. They are: skype.conf and skype.desktop

---

### Post by R Clemons on 2009-05-13
try installing skype-static-oss from the medibuntu non-free repositories.

---

### Post by gewitty on 2009-05-13
Same problem. skype-static-oss wants to uninstall the lib32asound2-plugins, which kills all my multimedia sound.

Installing Picasa or Wine-based apps through Synaptic also removes this package.

Can I suggest that the problem needs to be fixed from the lib32asound2-plugins end of things, since finding a solution for Skype alone will still not resolve the Picasa and Wine issues.

---

### Post by khelben1979 on 2009-05-13
> **gewitty said:**
> I just downloaded the recommended static file and installed it as per the ReadMe file instructions:

"We recommend copying the
skype binary to /usr/bin and installing sounds/, lang/ and avatars/ into
the /usr/share/skype directory."

This did not appear to have any effect, even after a reboot. I tried running Skype from a Terminal and got the following error message:

dave@dave-desktop:~$ skype
skype: error while loading shared libraries: libXv.so.1: cannot open shared object file: No such file or directory
dave@dave-desktop:~$

There are two other files in the downloaded archive and I'm not sure where these should go. They are: skype.conf and skype.desktop

I think I know what your problem might be. I see that you have posted this problem under x86 64 bit users. Hmm... I believe that the static version doesn't support the 64 bit platform very well, if not at all. *oops*

I recommend that you post this problem over at the Skype forum. I know that you should be able to run 32bit compiled applications on a 64bit optimized distribution, but that it did require some special package to be installed. I'm not sure of the name of it though.

Please take a look at this article: [Running 32-bit Applications on 64-bit Debian GNU/Linux]("http://www.debian-administration.org/article/Running_32-bit_Applications_on_64-bit_Debian_GNU/Linux") (I haven't finished reading it myself yet) :)

---

### Post by gewitty on 2009-05-13
Just had a quick look through the linked Debian article. A lot of it is above my head, but it seems to suggest that the problem is with running 32 bit apps on a 64 bit system. What I don't understand is that both the Skype and Picasa installations I've got come from the Ubuntu 64 bit repositories and should be 64 bit apps themselves. So what is it that requires the lib32asound files to get sound working in things like Amarok, which is also a 64 bit app?

The other really puzzling thing is that I have found the problem on two machines now. One of which _was_ working perfectly with both Skype, Picasa and the lib32asound-plugins running together. It only stopped working after I tried an unsuccessful update of the graphics driver. Something which is completely unconnected with any sound application.

I'm beginning to think that 9.04 has some serious instabilities which need sorting out.

---

### Post by khelben1979 on 2009-05-13
> **gewitty said:**
> I'm beginning to think that 9.04 has some serious instabilities which need sorting out.

I think they would appreciate your bug reports.

---

### Post by gewitty on 2009-05-13
I'm not sure how I would describe what seems to be happening!

I just tried installing the lib32asound2 package (without the lib32asound-plugins) on the second machine and guess what - it worked! I now have VLC, Amarok, YouTube, etc, all with sound AND I have Skype and Picasa working.

As soon as I can get to it, I'll try the same thing on the other machine.

---

### Post by Arup on 2009-05-14
I have installed both static and regular via repos on my x64 Jaunty and both have worked out well with no issues. 

How did you try to update the graphic driver, the reccomended and functioning way is via Jockey which fetches the tested driver from the Ubuntu repos.

---


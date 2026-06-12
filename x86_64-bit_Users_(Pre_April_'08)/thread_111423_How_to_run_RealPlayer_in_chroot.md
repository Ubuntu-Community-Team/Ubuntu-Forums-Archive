---
title: "How to run RealPlayer in chroot"
date: 2006-01-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-01-02
N00bie Linux user with Compaq AMD64 running Breezy-64.

For some time I have been trying to get this computer to run Acrobat Reader 7.0 and RealPlayer. Thanks to several others I finally managed to get chroot installed. And I also installed Acrobat Reader 7.0 via Synaptic32, and just this morning managed to get it running. (Thanks to Suger, in thread "Acrobat Reader 7.0.")

Now I have installed RealPlayer, also via Synaptic32, but can't get it to run. First, I did
```
sudo ln -s /usr/local/bin/do_dchroot /usr/bin/realplay

```
But that just got me an error message that the file exists.

Then I just typed "realplay" from the command line. The screen flickered and it appeared an application was going to appear on the panel, but then it stopped and nothing happened. Ditto for if I clicked on a RealPlayer link on a streaming web site.

So then I read some more and learned I could just type "dchroot" to enter the chroot environment. I did so, and then typed "realplay." This time I got:
```
jjj@Devil5:~$ realplay
** ERROR **: Unable to open display
aborting...
/usr/bin/realplay: line 75: 23444 Aborted                 $REALPLAYBIN "$@"
jjj@Devil5:~$ sudo ln -s /usr/local/bin/do_dchroot /home/jjj/software/RealPlayer/realplay
```
Now I see why it started to appear and then disappeared.

I should add that, when I click on a link in Firefox, not only does RealPlayer go away, but it crashes Firefox too.

Does anyone know what is wrong?

---


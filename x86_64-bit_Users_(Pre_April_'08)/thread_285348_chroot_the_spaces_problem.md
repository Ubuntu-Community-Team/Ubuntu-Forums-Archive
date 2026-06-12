---
title: "chroot: the spaces problem"
date: 2006-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by FedeXX on 2006-10-26
I'd like to use wine and mplayer from my 32bit chroot environment, by directly double clicking the item to open, for example a Windows Media Video. But if I type in the "open with" field only 

```

dchroot -d gmplayer

```

it works only for files where there's NO spaces in their path.

For example a double click on /home/fedexx/video.avi will work, but on /home/fedexx/another test.avi will not work, as it says it can't open "another" and "test.avi" because they doesn't exist.

How can I translate a " " into "\ " like the command line does? Somebody can write a little script? Pleeeeeeease? :KS 

Thank you!!!

(sorry for my BAD english)

---

### Post by kuja on 2006-10-26
Okay, so I wrote you a quick script. I've attatched it to this post.
- It does more or less what you want, but will only accept one filename as an argument, not a list of files.
- Call it like this - gmplayer32 /home/bob/my file.avi

Tell me how it works out.

---

### Post by FedeXX on 2006-10-27
> **kuja said:**
> Okay, so I wrote you a quick script. I've attatched it to this post.
- It does more or less what you want, but will only accept one filename as an argument, not a list of files.
- Call it like this - gmplayer32 /home/bob/my file.avi

Tell me how it works out.

Thank you!!! I really appreciated it :D 

However, it doesn't work :( double clicking on "Another test.wmv" gives:

```

(blahblahblah)
Playing /home/fedexx/Desktop/Personal/Video/Another.
File not found: '/home/fedexx/Desktop/Personal/Video/Another'
Failed to open /home/fedexx/Desktop/Personal/Video/Another.


Playing /home/fedexx/Desktop/Personal/Video/test.wmv.
File not found: '/home/fedexx/Desktop/Personal/Video/test.wmv'
Failed to open /home/fedexx/Desktop/Personal/Video/test.wmv.

```

---

### Post by kuja on 2006-10-27
Hmm, I'll look into it.

Okay, I've got a slightly modified version attatched.

Here's how I made it work: 

Go to a video file, right click, open with...
(I opened with) $HOME/gmplayer32 %u
With the option open in terminal enabled.

---


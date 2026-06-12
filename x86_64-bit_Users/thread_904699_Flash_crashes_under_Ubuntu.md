---
title: "Flash crashes under Ubuntu"
date: 2008-08-29
forum: x86 64-bit Users
---

### Post by rjt_5 on 2008-08-29
I've always found the many complaints about flash under Linux quite puzzling because I've been using Linux and Flash for many years and never had any problems with it. It worked just as well as under any of the other supported OSes.

I was using Gentoo before with Flash working perfectly and switched to Ubuntu because the 64bit packages under Gentoo have essentially stagnated. I installed flash using the package in Add/Remove programs which installed it with nsplugginwrapper. Some sites seem to work okay, such as those that use Flash for navigation or Youtube. But some sites, primarily those that stream video end up crashing flash(or more likely nsplugginwrapper).

It's flash that is crashing, not firefox. The space were the flash video was is left as a grey box. All other pages using flash end up with just grey boxes and flash no longer works until the browser is restarted(sometimes not even then). One site that is guaranteed to crash flash are those that use streaming video supplied by Comedy Central such as the site for The Daily Show. The embedded videos on that site crash while loading the player. Their player always worked perfectly under Gentoo, even better that Youtube's (Which is incapable of resuming the streaming after the connection is dropped).

I tried installing flash manually myself. No change.
I tried installing Flash 10. Had the exact same problem except some sites also now claimed that I didn't have flash (They were specifically looking for Flash 9).

Surely this problem has been encountered before? How is it that Flash could ONLY have problems under Ubuntu? This is driving me absolutely insane.

---

### Post by gjoellee on 2008-08-29
Ooooooo quit "hard" to read your post when it's not "broken up in paragraphs":(

However using flash 10 may be a better option:)

PS: ubuntu Intrepid comes with MAJOR performance and technical improvements

---

### Post by rjt_5 on 2008-08-29
It's kind of hard to judge the line wrapping in these small text widgets in forums. Ends up making the text look messy since the post itself is wider.
I edited it anyway and inserted double spaces.

As I said in my original post, I already tried Flash 10. The result is just simply worse because in addition to the original problem you also can't use sites that do version detection improperly.

---

### Post by Sef on 2008-08-29
Have you followed [Kilz's tutorial]("http://ubuntuforums.org/showthread.php?t=772490")?  Flash is still only made for x86 and not AMD64.   There are also SWFDeck and Gnash that are available in the repositories.  They may or may not work with sites that need flash 9.  With flash 7 sites, they are fully compatible.

---

### Post by rjt_5 on 2008-08-30
Yes I did try those instructions. Like I said, Flash installs fine. But it crashes on certain websites. I suppose it's more accurate to say that nsplugginwrapper crashes:

npviewer.bin[16779]: segfault at 726f7463 rip 726f7463 rsp ff8af4bc error 14

The alternative Flash implementations aren't really of any use to me since I mostly use Flash for streaming video which is the main thing that doesn't work in the alternatives.

Certainly there's a known solution to this? As I said this problem doesn't occur under Gentoo. It still happens with Opera under Ubuntu so it's not Firefox and it's not Flash itself. It has something to do with Ubuntu.

---


---
title: "VNC over SSH on 64-bit systems"
date: 2006-11-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by jehosephat on 2006-11-09
This might be a no-no; I've already posted 2 replies on existing threads, but I haven't seen a comprehensive description of this problem anywhere, so I wanted to see if I could get some expert attention.

Running 6.10 on 64-bit (Dell 9510; Pentium D Smithfield) ... encountered this problem after upgrading from FC4 (to 5 and then 6), then on Ubuntu and Xubuntu 6.06.1 / 6.10 ...

Major symptom: vnc starts a display pid, but X fails with the following text: 
X error *blah blah*: BadLength (polycode *blah blah* ...)
Major opcode *blah blah*: 134
*blah blah*
serial number *blah*: 65
*blah* serial number: 65
(ok so I'm paraphrasing ...)

Bugzilla has a few posts on this ... [here]("http://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=206116")'s one ...
Looking through the VNC and GDM HOWTO [here]("http://ubuntuforums.org/showthread.php?t=122402") on ubuntuforums, Tichondrius (sp?) has posted about where to get the vnc4 packages that are fixed with respect to this bug.  I can't follow his Howto exactly because (apprently since 6.06?) one of these patched .deb files (vnc4server, I think) depends on xserver-common, which is now x11-common, so I have to force the install (dpkg --force-depends).  Nevertheless, I've gotten VNC working over SSH with this and a few other variations.  However (!) if I try to open up anything bigger than a terminal in my VNC client display, it crashes with a segmentation fault that sometimes kills my server!

Now, I finally found some advice here that led me to install X11vnc, which works flawlessly, but of course it has the disadvantage that I'm using display :0 so it's not physically secure.  It's good enough for now, but I was hoping someone could advise me on the overall x86_64 VNC linux bug problem ...
Thanks ...

---


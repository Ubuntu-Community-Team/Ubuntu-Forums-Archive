---
title: "Rhapsody &amp; 64-bit (Firefox 3 B5)"
date: 2008-05-20
forum: x86 64-bit Users
---

### Post by Melk79 on 2008-05-20
Has anyone had any luck installing this subject?  I've tried to install the add-on from their site (which is supposed to support Linux -- maybe not 64-bit) and I get these errors:

1) Malformed File -
Firefox could not install this item because "install-m5c..rdf" (provided by the item) is not well-formed or does not exist. Please contact the author about this problem.

2) Error-
Firefox could not install the file at 

[http://forms.real.com/real/player/download.html?f=unix/rhapx/RhapsodyPlayerEngine_Inst_Linux.xpi](http://forms.real.com/real/player/download.html?f=unix/rhapx/RhapsodyPlayerEngine_Inst_Linux.xpi)

because: Unexpected installation error
Review the Error Console log for more details.
-203

I've tried manually downloading the nprhapengine.so file and installing it at /usr/lib64/firefox-addons/plugins/, but no luck.  Any suggestions?

---

### Post by bigredx24x on 2008-05-21
This may work for you:

[http://ubuntuforums.org/showpost.php?p=5007491&postcount=10](http://ubuntuforums.org/showpost.php?p=5007491&postcount=10)

**From my experience, the plugin is incompatible with the 64-bit Firefox.

---

### Post by Sef on 2008-05-21
> (which is supposed to support Linux -- maybe not 64-bit)

There is one for Fedora, but the [poster]("http://real.lithium.com/real/board/message?board.id=InstallingRhapsody&thread.id=28840") said it was not working.

Note on packaging: Fedora uses .rpm; while Ubuntu uses .deb.  The package managers are not compatible.  You can use alien to change a binary .rpm package to a binary.deb package, but no guarantees that it will work.  

It's available in Synaptic.  System > Administration > Synaptic Package Manager.

---

### Post by Melk79 on 2008-05-21
I liked this approach from the Real forum, but I ran into a snag at the first step.  After copying the firefox file as it said, there was no MOZ_ARCH data to be found to trick it into thinking it was i386.  Seems viable if I can find the equivalent for Firefox 3 b5 (or maybe hold out until the final Firefox 3 is out). Thanks for the link.

---

### Post by Melk79 on 2008-05-21
Thanks for the link bigred.  I'm hesitant to follow it only because I'm finally settling into Firefox 3 and the final release should be out soon.  From what I've read on that Real forum, it doesn't look like they're breaking down doors to help us 64-bit folks out.  That's unfortunate.

---

### Post by Melk79 on 2008-06-25
Real finally released a 64-bit client for Windows Vista and XP.  If anyone learns how to make it work in Ubuntu 64, please pass along.  Thanks

---

### Post by pixel :-) on 2008-06-26
you can try [http://getswiftfox.com/deb.htm]("http://getswiftfox.com/deb.htm").It's actually 32 bits firefox that can run on 64Bit Linux.It's freeware.

You can also use transmission instead :popcorn:

---

### Post by Melk79 on 2008-10-13
In case anyone hits this on Google, Rhapsody works out of the box now on Ubuntu 64.  All I did was go there and hit play.  No problems.

---

### Post by rrm3 on 2009-04-28
In case someone hits this on google, now it doesn't work anymore.  :-)

---


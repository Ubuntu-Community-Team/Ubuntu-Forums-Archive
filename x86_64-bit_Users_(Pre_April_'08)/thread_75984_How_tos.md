---
title: "How tos????"
date: 2005-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by xthaparian on 2005-10-14
Can somene please make the UBuntu 64bit more usable.

We need couple for things to get rolling.

1) We need a good HOW TO for getting the ATI drivers installed.
2) Need a HOW TO to get the 32 bit programs working in 64 bit. (without using chroot32).

3) How to compile JAVA 1.5 on 64 bit machine.

4) How to get FLASH working.

Once there 4 major problems are sorted out. Then the 64 bit will have no problem except for the Software and system based issues.

Moderators or experts in 64bit Systems please have a look at this and try to encourage these HOW tos to be made, or atleast start a thread in this section.

Its hard to search for 64 bit support as 64 bit users are confused as to where to go and search for right answers except for this thread.

Lets make the 64 bit a Success.

---

### Post by newbie2 on 2005-10-14
[http://www.howtoforge.com/](http://www.howtoforge.com/)
;)

---

### Post by DancingSun on 2005-10-15
[QUOTE=xthaparian]Can somene please make the UBuntu 64bit more usable.

We need couple for things to get rolling.

1) We need a good HOW TO for getting the ATI drivers installed.
2) Need a HOW TO to get the 32 bit programs working in 64 bit (without using chroot32).

3) How to compile JAVA 1.5 on 64 bit machine.

4) How to get FLASH working.

Once there 4 major problems are sorted out. Then the 64 bit will have no problem except for the Software and system based issues.

Moderators or experts in 64bit Systems please have a look at this and try to encourage these HOW tos to be made, or atleast start a thread in this section.

Its hard to search for 64 bit support as 64 bit users are confused as to where to go and search for right answers except for this thread.

Lets make the 64 bit a Success.[/QUOTE]
[LIST=1]
[*]There's already a HOWTO for ATI drivers.  It was posted on 5.04's Tip's and Trick forum: [http://ubuntuforums.org/showthread.php?t=65276&highlight=ATI](http://ubuntuforums.org/showthread.php?t=65276&highlight=ATI)
[*]Not sure how reliably we can do that...I guess the best way to go about this is to file a bug/feature request in the Ubuntu bug tracker and have the developers tackle this in problem in a more fundamental way, like implementing dual-architecture for Ubuntu64.  All we can do is hack some work-arounds.
[*]You can't compile Java 1.5 (no source code), but you can install it using Sun's installer.  There's also a HOWTO in Ubuntu's wiki pages: [https://wiki.ubuntu.com/JavaAMD64?highlight=%28java%29](https://wiki.ubuntu.com/JavaAMD64?highlight=%28java%29)
[*]This is somewhat related to 2), as there are no 64-bit Flash at this time.[/LIST]

---

### Post by Stereotypical Rage on 2005-10-15
1) I could swear the ATI drivers were included in XORG.
2) Is it even possible to get 32 bit progs working without modifying them?
3) [http://ubuntuforums.org/showthread.php?t=70428](http://ubuntuforums.org/showthread.php?t=70428)
4) Flash is currently not available for x86_64. There is GPLFlash, but I haven't had that work, yet.

---

### Post by zekolas on 2005-10-15
[QUOTE=xthaparian]
1) We need a good HOW TO for getting the ATI drivers installed.
2) Need a HOW TO to get the 32 bit programs working in 64 bit. (without using chroot32).

3) How to compile JAVA 1.5 on 64 bit machine.

4) How to get FLASH working.
[/QUOTE]

1.) [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
2.) Sorry can't really help you here
3.) I am not sure what you mean about compile java 1.5 on 64 bit machine. Do you mean install the Java Runtime Environment or how to use java to compile programs? 

For the java run time envonment here is what I did. I went to [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp) and downloaded java 1.5 for amd64 linux. Excute the bin file and it will extract a jre-1_5 directory. Then I went into /bin and created a link named "java" and linked it to "java" program in the jre-1_5 directory. Now I can run any program such as limewire or azurus.

4. Check out this page [https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")
scroll down untill you see a section for "Flash for x86_64". Macromedia has not made a flash player compatable for x86_64, but this explains how to use gnuflash what has done a pretty good job for me.

Hopefully you found some of this usefull, I am pretty new to ubuntu as well.

---

### Post by ikd69 on 2005-10-15
[QUOTE=DancingSun][LIST=1]
[*]There's already a HOWTO for ATI drivers.  It was posted on 5.04's Tip's and Trick forum: [http://ubuntuforums.org/showthread.php?t=65276&highlight=ATI](http://ubuntuforums.org/showthread.php?t=65276&highlight=ATI)
[/LIST][/QUOTE]

And it is working.

I just finished a dist-upgrade from 5.04 to 5.10.  In 5.04 i followed the outstanding info in the thread mentioned above and my ATI X700 worked like a charm.   I was concerned that things might not work out in 5.10, but apparently they do.

cheers,

ikd :D

---

### Post by Cashel on 2006-02-06
AMD Athlon 64 X2 3800+ , Ubuntu Breezy... pure heaven... 

Just got this thing running yesterday and so far it's a joy to behold.. Ironic that linux was a fast and confusion free setup compared to windows 64bit :P Still figuring out all this WOW64 nonsense.. Interested in hearing of any native 64 bit apps you folks hear of and experiences using dual SLI cards... I have one now and I'm considering a second... Single SLI (GeForce 6600GT) works great for me.. gotta love nvidia..

Your Java problems arent mine, I have the full SDK works fine. Havent tried the JAVA 3D API tho... wouldnt be suprised if it goes bonkers.. not quite there in Java yet to mess with it tho, hehe... give me perl anyday :)

---


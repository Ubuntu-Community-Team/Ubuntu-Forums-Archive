---
title: "Updating firefox breaks Flash"
date: 2007-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by M$LOL on 2007-08-02
I just updated to Ff 2.0.0.6 because the update dialog kept nagging me, but now when I go to youtube I get the error saying that Flash isn't installed. I copied over the flashplayer.xpt and the libflashplayer.so manually, but it still didn't work, so I re-ran the 3in1 script again, reinstalling the plugin, but still no luck. Is there any way to fix this?

Thanks

---

### Post by Kilz on 2007-08-02
> **M$LOL said:**
> I just updated to Ff 2.0.0.6 because the update dialog kept nagging me, but now when I go to youtube I get the error saying that Flash isn't installed. I copied over the flashplayer.xpt and the libflashplayer.so manually, but it still didn't work, so I re-ran the 3in1 script again, reinstalling the plugin, but still no luck. Is there any way to fix this?

Thanks

You may have to remove the flash files manually before running the script again.

---

### Post by M$LOL on 2007-08-02
Thanks Kilz, I'll try that tomorrow out of curiosity, but I decided to try the nspluginwrapper script, and it's awesome, I haven't had one crash yet :)

Thanks :)

---

### Post by Kilz on 2007-08-02
> **M$LOL said:**
> I just updated to Ff 2.0.0.6 because the update dialog kept nagging me, but now when I go to youtube I get the error saying that Flash isn't installed. I copied over the flashplayer.xpt and the libflashplayer.so manually, but it still didn't work, so I re-ran the 3in1 script again, reinstalling the plugin, but still no luck. Is there any way to fix this?

Thanks

I just reread your post, the firefox 2.0.0.6 that was installed with update recently is the 64bit version. Not the firefox32 32bit version the 3in1 script installs. 32bit flash wont run with the 64bit one without the nspluginwrapper you installed. The only problem is there is no (safe) java for the 64bit browser. So you may still need to run the 32bit version if you need to run java applets in the browser.

---

### Post by michael37 on 2007-08-02
I'll post my take on this issue.

I found that many Java pages don't work with Firefox anyway, possibly because Java was tested only for Windows.  So, my browser picks are
[list]
[*]Main day-to-day browser: 64-bit Firefox 2.0.0.5, directly from Ubuntu repositories, updated regularly, with nspluginwrapper for 32-bit Flash plugin
[*]Special purpose browser: 32-bit Internet Explorer 7 with 32-bit Java inside headless VirtualBox, more info here: [thread]433359[/thread].
[/list]

The combination works perfectly for me.

Sidenote: Internet Explorer runs fine in Wine (using IES4Linux), but only without Java; thus, the VirtualBox approach.

---

### Post by Kilz on 2007-08-02
> **michael37 said:**
> I'll post my take on this issue.

I found that many Java pages don't work with Firefox anyway, possibly because Java was tested only for Windows.  So, my browser picks are
[list]
[*]Main day-to-day browser: 64-bit Firefox 2.0.0.5, directly from Ubuntu repositories, updated regularly, with nspluginwrapper for 32-bit Flash plugin
[*]Special purpose browser: 32-bit Internet Explorer 7 with 32-bit Java inside headless VirtualBox, more info here: [thread]433359[/thread].
[/list]

The combination works perfectly for me.

Sidenote: Internet Explorer runs fine in Wine (using IES4Linux), but only without Java; thus, the VirtualBox approach.

Why on this gods green earth would anyone want to run Windows, Remember that this is a linux forum. The goal of most people running Linux is never to have to run Windoze. I for one dont miss a virus scanner, spybots , malware, or any of the other things I constantly had to deal with on M$ products.
Next, if they did run Windoze, why on earth would they run that spybot, virus gathering, security flaw that is IE? 32bit firefox runs quite well on 64bit Ubuntu, with all plugins thank you. Without the need to fire up Windose.
Lastly, and most important. Never, ever, ever, ever, ever run IE under wine as a browser. It might be good to use to see if a page you have made looks good under IE. But IE is a huge security flaw waiting to happen. You could fubar your home folder and all the files in it. Never use it to browse, never, ever,ever,ever,ever,ever. Wine is a bug for bug, security flaw for security flaw copy of windows.

---

### Post by michael37 on 2007-08-03
> **Kilz said:**
> Why on this gods green earth would anyone want to run Windows, Remember that this is a linux forum. The goal of most people running Linux is never to have to run Windoze. I for one dont miss a virus scanner, spybots , malware, or any of the other things I constantly had to deal with on M$ products.
Next, if they did run Windoze, why on earth would they run that spybot, virus gathering, security flaw that is IE? 32bit firefox runs quite well on 64bit Ubuntu, with all plugins thank you. Without the need to fire up Windose.
Lastly, and most important. Never, ever, ever, ever, ever run IE under wine as a browser. It might be good to use to see if a page you have made looks good under IE. But IE is a huge security flaw waiting to happen. You could fubar your home folder and all the files in it. Never use it to browse, never, ever,ever,ever,ever,ever. Wine is a bug for bug, security flaw for security flaw copy of windows.

I am sorry Kilz, but I am not a religious fanatic.  I live in real world where some programs and some applications and some webpages are simply not designed for Firefox, for Linux, or both.  And no, Firefox 64-bit doesn't have a viable option for a Java plugin.   I am sad that my company uses exchange for the mail and calendar system, but I live with that and I am glad that Evolution doesn't seem to have issues with that.  I wish Thunderbird didn't either -- it's at least twice as fast as Evolution for mail reading.  But maybe if it had exchange support, it wouldn't be as fast ;) 

Is it a Linux forum?  Absolutely.  Wasn't it the same forum that I referenced with instructions for running Windoze in Virtualbox?

Regarding security flaws -- Great comment.  I created a VirtualBox image for my freshly made Windows VM and put it in a tarball.  When spy/virus/rootkit/whatever stuff gets into my VM, I will simply wipe that image and untar my clean VM image back.  That'll take me grand total of 2 minutes.  Beats re-installing OS that most Windows users have to go to?  That's why I run Ubuntu, Kilz.

P.S. You say that 32-bit Firefox is a workable alternative.  It is, but this thread discussed the 64-bit Firefox which I use for my primary browser.

---

### Post by Kilz on 2007-08-03
> **michael37 said:**
> I am sorry Kilz, but I am not a religious fanatic.  I live in real world where some programs and some applications and some webpages are simply not designed for Firefox, for Linux, or both.  And no, Firefox 64-bit doesn't have a viable option for a Java plugin.   I am sad that my company uses exchange for the mail and calendar system, but I live with that and I am glad that Evolution doesn't seem to have issues with that.  I wish Thunderbird didn't either -- it's at least twice as fast as Evolution for mail reading.  But maybe if it had exchange support, it wouldn't be as fast ;) 

Is it a Linux forum?  Absolutely.  Wasn't it the same forum that I referenced with instructions for running Windoze in Virtualbox?

Regarding security flaws -- Great comment.  I created a VirtualBox image for my freshly made Windows VM and put it in a tarball.  When spy/virus/rootkit/whatever stuff gets into my VM, I will simply wipe that image and untar my clean VM image back.  That'll take me grand total of 2 minutes.  Beats re-installing OS that most Windows users have to go to?  That's why I run Ubuntu, Kilz.

P.S. You say that 32-bit Firefox is a workable alternative.  It is, but this thread discussed the 64-bit Firefox which I use for my primary browser.

It isnt religion, that, to me, personally is probably the worst thing anyone has said to me in a bit. To equate running a operating system to ones faith in God is truly sad, and blasphemy. 
The real world is still here. Java runs great on Firefox. Web pages that say they wont work with anything but IE, work with Firefox. Look up a extension called user agent switcher. You dont need IE. You dont need Windose. 
I was scared when I made the switch to Linux, didnt want to let go of Windows and what I was comfortable with. Rationalized a lot. Then I found applications that did the same thing. I deleted windows. Dont miss it one bit. I do exactly the same things I did before, in fact I do more. I have learned a lot more to.
You know, virtualbox runs, surprise, surprise, Linux! you can run different distros to test them out. You can test Gutsy while still having a running setup. But Ubuntu knows that some users need a security blanket, so they point to vm software. Hoping someone will finaly get the idea that they dont need it after not using it for a bit. But some people never do, sadly.
Keep using Windows and you lock yourself in. The proprietary formats, the comfort zone, and simple human laziness will keep you there. Or , give it up. Dont use it for a month. You will never go back.

P.S. If you read the first post again, you will read a reference to a 3in1 script. Heck I even missed it at first. [3in1 is my 32bit Firefox script.]("http://home.comcast.net/~ubuntume/ff32-3in1-4.tar.gz") The original poster wanted to know why after reinstalling the 32bit firefox a plugin wasn't working in the browser ubuntu updated. So this post was in essence about 32bit Firefox. Its a better , viable option, over firing up Windose.

---

### Post by M$LOL on 2007-08-03
Thanks for the info Kilz.

Yeah, I agree with you about Windows, although the one thing I will say is that because of M$' stupid WGA mechanism, I can't get stuff that I need from them (such as the DX SDKs etc) without using Windows, so I have to use a VM. But that brings me to another problem, I don't want to connect my VMs to the internet, so I can't get their updates. IEs4Linux won't work for me either, so my only option seems to be to have two VMs, one connected to the net, and one for actual work.

---


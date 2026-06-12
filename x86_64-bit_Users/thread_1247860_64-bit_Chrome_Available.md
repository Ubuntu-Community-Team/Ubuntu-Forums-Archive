---
title: "64-bit Chrome Available"
date: 2009-08-23
forum: x86 64-bit Users
---

### Post by Thelasko on 2009-08-23
I just recently installed the 64-bit build of Google chrome from [this PPA.]("https://launchpad.net/~chromium-daily/+archive/ppa")

Wow, It's fast!  But how do I get flash working for it?  I have the 64-bit alpha installed on Firefox.  Do I just put a link to it somewhere?  Where do I do that?

Thanks

---

### Post by Thelasko on 2009-08-23
[Found it!]("http://www.ubuntugeek.com/howto-enable-flash-support-for-google-chromium-browser.html")  It looks like it checks in the ~/.mozilla/plugins folder too, so you may not have to do anyting but add the "--enable-plugins" to the start command.

Edit:  I also left the "%U" after "--enable-plugins"  I don't know what it does, but it seemed to make chromium more stable.

---

### Post by Thelasko on 2009-08-23
Correction Chromium not Chrome.

---

### Post by jetpeach on 2009-08-23
i'm wondering if someone could identify the differences between the open source (non-google?) chromium versus google chrome? i kinda want the "google chrome" version if it supports things like the bookmark sync feature that has been added, but will this also be supported/enabled in chromium (maybe already is in the latest version?)?

thanks,
jetpeach

---

### Post by Thelasko on 2009-08-23
> **jetpeach said:**
> i'm wondering if someone could identify the differences between the open source (non-google?) chromium versus google chrome? i kinda want the "google chrome" version if it supports things like the bookmark sync feature that has been added, but will this also be supported/enabled in chromium (maybe already is in the latest version?)?

thanks,
jetpeach

The bookmark sync feature appears to be working in chromium.

---

### Post by Thelasko on 2009-08-23
Sorry, I didn't understand what you were talking about as far as the bookmark sync feature.  I'm not sure if it has it or not.

---

### Post by ken78724 on 2009-08-24
The Lasko, thanks for the Posts! I went to launch pad for the sudo code & got this response: "k78724@Kproductions:~$ deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main 
bash: deb: command not found
k78724@Kproductions:~$ deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main 
bash: deb-src: command not found"

will also report results on launchpad... thanks again! 
Kenneth

---

### Post by ken78724 on 2009-08-24
hmmmm ? can't figure out how to post my results in attempting to install chrome at launchpad. Is it Monday?

---

### Post by bunnyhugh on 2009-08-24
> **ken78724 said:**
> The Lasko, thanks for the Posts! I went to launch pad for the sudo code & got this response: "k78724@Kproductions:~$ deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main 
bash: deb: command not found
k78724@Kproductions:~$ deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main 
bash: deb-src: command not found"

will also report results on launchpad... thanks again! 
Kenneth

Kenneth from what you have posted it appears that you have tried to run the deb lines from a terminal command prompt, if that is the case, that is complete wrong. Those lines need to be added to the sources list either manually or using the third party repository update facilities. If you do not know how to do this there are instructions at the PPA specified by thelesko.

rgds

---

### Post by tomdkat on 2009-08-26
Can this be installed alongside Google Chrome for Linux?

Thanks!

EDIT:  Looks like you can!  :D

Peace...

---

### Post by RTrev on 2009-08-26
How does one tell if the Chromium installed is the 32 versus 64 bit version?  I've been running it for weeks now as my main browser, and waiting for the 64-bit to come out.  Then I saw people saying it's out but offering the same repository I've been using all along:

[http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main

Then, yesterday, I noticed that I had a package installed which Synaptic said was no longer being used: 1a32-libs-chromium-browser.

The version of Chromium Synaptic says is installed is 4.0.203.0~svn20090825r224230-0ubuntu1~ucd2~jaunty

There is no amd64 anywhere in the name.

Can anyone tell me if I'm already running the 64-bit, and if not how to get it?

Thanks much!
Bob

---

### Post by Thelasko on 2009-08-26
> **RTrev said:**
> How does one tell if the Chromium installed is the 32 versus 64 bit version?

Good question.  My guess is to look in your usr/lib64 directory.  If you see chromium-browser in that location you have 64 bit.  If it's in usr/lib32 you have the 32 bit version.

Anybody know another way?

---

### Post by RTrev on 2009-08-26
> **Thelasko said:**
> Good question.  My guess is to look in your usr/lib64 directory.  If you see chromium-browser in that location you have 64 bit.  If it's in usr/lib32 you have the 32 bit version.

Anybody know another way?

Yep, it's in the lib64 directory.  Thanks much!

---

### Post by RTrev on 2009-08-26
> **Thelasko said:**
> The bookmark sync feature appears to be working in chromium.

Can anyone give me a hint about how to get this working?

I'm on Jaunty 64-bit, and using the latest Chromium 64-bit.  I'm using the "--enable-sync" switch in starting the browser.  My understanding is that there should be some sync-related option in the menus, but I sure can't find one.

Thanks.

---

### Post by Thelasko on 2009-08-27
> **RTrev said:**
> Can anyone give me a hint about how to get this working?

I misspoke earlier about the bookmark sync.  What I was referring to is under (wrench)>options and the personal stuff tab.  Under "Browsing Data" you can sync with Firefox.  I don't think you can sync with your iGoogle account yet though.

---

### Post by RTrev on 2009-08-27
> **Thelasko said:**
> I misspoke earlier about the bookmark sync.  What I was referring to is under (wrench)>options and the personal stuff tab.  Under "Browsing Data" you can sync with Firefox.  I don't think you can sync with your iGoogle account yet though.

Ah.  Okay, thanks for clearing that up.

---


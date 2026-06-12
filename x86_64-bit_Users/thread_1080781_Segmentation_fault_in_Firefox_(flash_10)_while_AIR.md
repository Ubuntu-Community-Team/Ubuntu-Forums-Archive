---
title: "Segmentation fault in Firefox (flash 10) while AIR 1.5 is running"
date: 2009-02-25
forum: x86 64-bit Users
---

### Post by cpugeniusmv on 2009-02-25
Ubuntu 8.10 x86_64
Firefox plugin: Shockwave Flash 10.0 d21 (the 64-bit version)
adobeair: 1.5.0.7620

By themselves, AIR and the Flash plugin in Firefox both work great. Though sometimes when I navigate to a page in Firefox with Flash on it while AIR is running, Firefox exits due to a segmentation fault. It doesn't happen for all pages with Flash on them, but here's a reliable way I've been able to reproduce it:

1. Install/run the [Pandora Adobe AIR app](http://www.pandora.com/desktop).
2. Open up Firefox and go to [http://www.pandora.com/](http://www.pandora.com/)

(It's not just the pandora site that makes it crash, other sites do it too, but not as consistently as this combinaton.)

I've been able to reproduce this crash on two different machines with the same software setup. I'm curious to see if others are able to reproduce it, so if you don't mind, give the above procedure a try and see what happens. I'm also curious to know whether this happens on the 32-bit equivalent of this stack.

After I get some responses I hope to submit this to Adobe to see if they'll fix it.

Thanks!

---

### Post by 3Miro on 2009-02-25
It might not be Pandora issue. My irefox just crashes randomly when I am using it. Then again, I am using KDE 4.2 and Firefox does not integrate well yet. What are you using?

---

### Post by Yellow Pasque on 2009-02-25
There's an updated Flash64 Alpha that was released yesterday. I suggest trying that.
I'm also curious as to what video cards/drivers you're using because I've had issues with fglrx segfaulting when running Flash apps. Using open-source drivers solved those issues.

---

### Post by cpugeniusmv on 2009-02-25
I just updated to the new flash plugin for x64 (Shockwave Flash 10.0 r22) and am still able to reliably reproduce the crash.

I'm using Gnome and Firefox has not crashed once since the install except for when I do something like what I described above. That's why I think it's an issue with the flash plugin (not pandora).

I'm using the latest binary nvidia driver from the repository in Intrepid. The only thing that crashes is Firefox, X and all of my other apps continue to run (including AIR).

I'll see what happens when I use the open source drivers.

---

### Post by bjencks on 2009-02-26
It's not just the Pandora AIR app, I can reproduce with twhirl as well (with the Pandora website). Workaround is to stop the air app, load Pandora, then restart the air app. If you do submit a bug report to adobe, can you post a bug # here so we can follow it?

---

### Post by bjencks on 2009-02-26
I created a bug: [https://bugs.adobe.com/jira/browse/FP-1603](https://bugs.adobe.com/jira/browse/FP-1603)

---

### Post by asteffey on 2009-05-17
This problem has been plaguing me as well, but luckily I have been able to find a workaround.  I simply run AIR applications under another user.  The first step is to, of course, create an alternative user with minimal privileges.  Next, I added "xhost +local:" to my list of startup applications (ensures other users can use current x session). Finally, I made a shortcut for "gksu -u <user> <app_path>" to run my AIR app.  Crude but effective.

For the record... I'm running Ubuntu 64 jaunty with 64-bit Adobe Flash Player 10 and Adobe AIR 1.5.1.  Firefox would crash on multiple different websites, the most annoying of which was Gmail.  The only AIR app I use is Pandora. Downgrading to 32-bit Adobe Flash and using the nspluginwrapper would also fix this compatibility issue with AIR, but then I would have other stability issues with Flash websites.

---

### Post by chrisamiller on 2009-05-21
I can confirm this bug as well. Should this be filed as a bug in Ubuntu Launchpad, or is it strictly an Adobe problem?


libflashplayer.so (Shockwave Flash 10.0 d21)
Adobe Air 1.5 (app is TweetDeck)
Always reproducible by signing into gmail with firefox while tweetdeck is running.

---

### Post by wetmonkey on 2009-06-10
WOOAHH!!   
I have been fighting with Flash on 64 Bit (9.04) for awhile.  

I never thought that it could be AIR doing it.  I just closed tweetdeck, viewed gmail.com and it didn't crash.  

There is a definite connection.  I tried starting tweetdeck and visiting gmail and it crashed right away. 

Adobe's bug system sucks so I can't view the submitted bug to add a 'me too'.  

As a random footnote for those finding this thread. 
- I installed the alpha to the ~/.mozilla/plugins/libflashplayer.so
However, still had crashes.  Doing a ln -s in /usr/lib/mozilla/plugins to the file in the home directory allowed me to visit any site with flash except gmail.

It's the tweetdeck (AIR) that seems to be conflict.

---

### Post by wetmonkey on 2009-06-10
So, this is interesting.

Background information: AIR installed with 32libs.  I can't remember the random tutorial used.
Flash installed using 64 bit Alpha for Firefox 3.x

What I found: 

Close tweetdeck (and I suppose any other AIR application)
Close firefox

Start firefox and visit gmail.com.  Works fine for me. 
Start tweetdeck.  Works fine for me.
Close firefox.
Start firefox and visit gmail.com.  Works fine for me.
At this point everything works without issue.  I can visit newgrounds, youtube, gmail without segfault. 

Now try this.
Close firefox
Close tweetdeck
Start tweetdeck.
Start firefox and visit gmail.com.  Seg fault. 

So, for some reason starting AIR before Firefox causes error.  Any Adobe gurus out there that this could help point out what's happening?  I am assuming it's the 32 bit (AIR) and 64 bit versions of the libflashplayer.so causing it. 

I would also note that no matter what order I start these two applications I can visit youtube, and newgrounds without issue.  It's only gmail which crashes the browser.  It's not to say it's exclusive to gmail, but I can say 100% of the time it will crash Firefox if Tweetdeck is started first. 

Will continue to test with Firefox started first to see if it remains stable.  The 64bit alpha is way more responsive than the older nsplugin version.

---

### Post by Lilmarsu on 2009-07-02
Same problem for with DestroyTwitter using AIR.
I can confirm wetmonkey's tests. My DestroyTwitter started with ubuntu. The only solution, close DT, run Firefox, go to gmail, then run DT.

---

### Post by szlwzl on 2009-08-18
I was also able to reproduce this, opening firefox first then air means I can view flash vids.

---

### Post by emmiesix on 2009-09-04
Wow, I'm glad someone noticed it was AIR, I had been running pandora continuously and never made that connection.  Guess I will wait for another update but until then remember not to start AIR first.

---

### Post by lajevardi on 2009-09-22
Same hell here!

---

### Post by d2globalinc on 2009-10-02
I noticed this issue a week or so ago, and I didn't put it together until tonight that it was happening when I had an AIR application open.  I just installed AIR awhile back and usually I didn't have any apps open all the time.  Then I started using Pandora and Tweetdeck via AIR.. I figured it out tonight when my girlfriend was using my computer and able to access her gmail without an issue.  I later rebooted my computer and had pandora open for her to listen too, she logged into her gmail and POOF, all firefox windows crashed.  Thats when it clicked.  I closed pandora AIR app, and no more crashing on gmail.

Gmail would crash btw when the Messenger would load up.  So no more AIR applications open all the time until this can be resolved.  I had about 20 firefox windows open the other day with things I was researching and POOF all of em went away... There were some very colourful words yelled out from my desk area.

Shane Menshik
D2 GLOBAL INC

---

### Post by Hichhiker on 2009-10-16
> **d2globalinc said:**
> I noticed this issue a week or so ago, and I didn't put it together until tonight that it was happening when I had an AIR application open.  I just installed AIR awhile back and usually I didn't have any apps open all the time.  Then I started using Pandora and Tweetdeck via AIR.. I figured it out tonight when my girlfriend was using my computer and able to access her gmail without an issue.  I later rebooted my computer and had pandora open for her to listen too, she logged into her gmail and POOF, all firefox windows crashed.  Thats when it clicked.  I closed pandora AIR app, and no more crashing on gmail.

Gmail would crash btw when the Messenger would load up.  So no more AIR applications open all the time until this can be resolved.  I had about 20 firefox windows open the other day with things I was researching and POOF all of em went away... There were some very colourful words yelled out from my desk area.

Shane Menshik
D2 GLOBAL INC


So.... anyone figure this out? I wonder if this has to do with 32bit Flash AIR uses vs 64bit that Firefox uses?

---

### Post by sammyboy405 on 2009-10-19
Who here thats having the Issue..

Are use AMD Processors?  I think this is tied to some other AMD releated issues Air and Flash has with AMD.

[http://forums.adobe.com/thread/451632?tstart=0](http://forums.adobe.com/thread/451632?tstart=0)

---

### Post by interval1066 on 2009-10-19
Been using ff with flash on an amd dual-core for years and no problems.

---

### Post by Hichhiker on 2009-10-19
> **sammyboy405 said:**
> Who here thats having the Issue..

Are use AMD Processors?  I think this is tied to some other AMD releated issues Air and Flash has with AMD.

[http://forums.adobe.com/thread/451632?tstart=0](http://forums.adobe.com/thread/451632?tstart=0)

Nope, its an Intel XEON in my case. Its pretty clear that the issue is a conflict between Air version of Flash (32bit) and the 64bit plugin that adobe distributes for 64bit linux.

The issue is 100% repeatable - basically if you open Air app first (I use Pandora) and THEN Start Firefox and open a page with Flash (GMail is a good example as it uses Flash for chat) you are guaranteed to get a Segmentation Fault in Firefox flash plugin.

However if you FIRST start Firefox and THEN start Air app - everything is fine. 

Now, on another box I have (also XEONs, though newer model)  I am using npwrapper with 32bit Flash plugin for Firefox - and this seems to work fine - so I am guessing the culprit is the 64bit version of the Flash plugin.  But like I said, everything works fine if Air is not running. I tried to replace Air's Flash with 64bit - but that did not work out so well. Perhaps I should stick to npwrapper and wait until 64bit Air 2.0 comes out.

-HH

---

### Post by lajevardi on 2009-10-20
> Are use AMD Processors? I think this is tied to some other AMD releated issues Air and Flash has with AMD.
1 Plus for AMD Processors.

---

### Post by njdove on 2009-11-05
"Me too." - if I open an AIR app before I open Firefox, a Flash site will inevitably crash Firefox. I have not yet experienced a crash if I open Firefox before I open the same AIR app.

Specs: Ubuntu 9.10 AMD64, Firefox 3.5.4, Adobe AIR 1.5.2 (32-bit), Flash 64-bit Alpha 10.0.32 r18

Thank you @cpugeniusmv for the thread and @wetmonkey for the fix! I've tried so many unrelated workarounds the past several days!

---

UPDATE: I was still having problems (Firefox 3.5.8; Flash 64-bit beta 10,0,45,2; AIR 1.5.3.9130 - specifically TweetDeck), even when I would open Firefox first, it would inevitably crash at some point.

I found a somewhat tedious, but more reliable work-around: running TweetDeck under a different user account. This took a bit of work because TweetDeck relies on GnomeKeyring or KWallet. The following worked for me:

[LIST=1]
[*]Create a new user (e.g. "air").
[*]Log in as that user and run TweetDeck - set it up as desired.
[*]Create the below script in that user's home (e.g. /home/air/tweetdeck). It runs gnome-keyring-daemon and sets the necessary environment variables.
[*]Log in with your primary account.
[*]Open a terminal (e.g. Accessories...Terminal).
[*]Type "xhost +local:" to allow local connections to your X session.
[*]Run your desired app as that user: "sudo -i -u air /home/air/tweetdeck" and Enter the AIR user's password when prompted.
[/LIST]

```
#!/bin/bash

eval $(gnome-keyring-daemon)

export GNOME_KEYRING_PID GNOME_KEYRING_SOCKET
export GNOME_DESKTOP_SESSION_ID=1

/opt/TweetDeck/bin/TweetDeck

kill $GNOME_KEYRING_PID

```

---


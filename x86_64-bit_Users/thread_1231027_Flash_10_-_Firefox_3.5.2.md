---
title: "Flash 10 - Firefox 3.5.2"
date: 2009-08-04
forum: x86 64-bit Users
---

### Post by Ascendancy117 on 2009-08-04
I need help getting flash working on Firefox 3.5.2. I installed the latest version of firefox using Ubuntuzilla ([http://sourceforge.net/projects/ubuntuzilla/](http://sourceforge.net/projects/ubuntuzilla/)). Now I have no more plugins installed. I've tried the steps in the sticky threads and other help threads online, but none of them worked. I'm guessing this is because Ubuntuzilla did something to the Firefox install in the background that these threads didn't anticipate. For example, the process for firefox is now firefox-bin. Anyway, no idea how I'm going to get Flash and Java working now. Anybody have any ideas?

===

Ok nevermind. I got it working with some more googling.

---

### Post by deepdeep on 2009-08-04
Hello, I'm using Jaunty Jackalope AMD64 too, I simply download and extract the 32bit flash and place it into /usr/lib/mozilla/plugins and it works perfectly~

---

### Post by beleth1 on 2009-08-04
thanks deepdeep! it works perfectly with the 32bit version.

---

### Post by deepdeep on 2009-08-04
> **beleth1 said:**
> thanks deepdeep! it works perfectly with the 32bit version.

You're welcome~:D

---

### Post by harry2006 on 2009-08-04
for the novice:
   [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

HIH.

---

### Post by hackel on 2009-08-05
deepdeep, this is impossible.  You can't run a 32-bit plugin in a 64-bit browser without nspluginwrapper!  The solution is to download the 64-bit Flash plugin from Adobe and install it to ~/.mozilla/plugins.  You should never touch any files in /usr orther than in /usr/local.

---

### Post by nanotube on 2009-08-05
> **hackel said:**
> deepdeep, this is impossible.  You can't run a 32-bit plugin in a 64-bit browser without nspluginwrapper!  The solution is to download the 64-bit Flash plugin from Adobe and install it to ~/.mozilla/plugins.  You should never touch any files in /usr orther than in /usr/local.

ubuntuzilla installs the official mozilla build, which is a 32bit build. so yes, it is possible, once you get rid of certain incorrect assumptions underlying your claim of impossibility :D

that said, you're right that it's better to stay out of /usr. deepdeep and others: instead of sticking libflashplayer.so into /usr/ put it in your home directory, into ~/.mozilla/plugins. that will work just as well, without having to mess with /usr.

I have now added a new section to the ubuntuzilla faq talking about the flash issue. see here: [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ)

---

### Post by DiabolusItalicus on 2009-08-05
> **nanotube said:**
> ubuntuzilla installs the official mozilla build, which is a 32bit build. so yes, it is possible, once you get rid of certain incorrect assumptions underlying your claim of impossibility :D

that said, you're right that it's better to stay out of /usr. deepdeep and others: instead of sticking libflashplayer.so into /usr/ put it in your home directory, into ~/.mozilla/plugins. that will work just as well, without having to mess with /usr.

I have now added a new section to the ubuntuzilla faq talking about the flash issue. see here: [https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ](https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ)

Thanks for adding that truly *crystal clear* FAQ tu Ubuntuzilla, nanotube: I did as suggested and put the plugin in my home directory, and now I have again access to all that Flash stuff out there!
(Just correct the link to the FAQ page, though: it's just a plain 'http' web page, not a secured 'https' one)

I'm running 64-bit Jaunty and wasn't aware at all that Ubuntuzilla (that I *had to* install in its 64-bit flavor) had installed 32-bit Firefox, so my first candid attempt to install the Flash downloaded from Adobe smashed against the issue of wrong architecture 'i386' of the sole .deb Flash package available and the disappointment for the lack of any 64-bit Flash on Adobe website.

But now I have an additional question on Firefox and Flash.

Suppose I decide to remove Ubuntuzilla and the Firefox installed through it to get back to the 'official' (?) Firefox 3.5.x available in Ubuntu repository.

Is that 'official' Firefox converted to 64-bit by the Ubuntu crew, or is it still the 32-bit version (in related posts I read that Mozilla only releases 32-bit stuff: is this correct)?

If the 'official' Firefox is converted to 64-bit, how could I get the 32-bit Flash plugin to work?

Thanks, and regards from Italy.

---

### Post by nanotube on 2009-08-06
> **DiabolusItalicus said:**
> Thanks for adding that truly *crystal clear* FAQ tu Ubuntuzilla, nanotube: I did as suggested and put the plugin in my home directory, and now I have again access to all that Flash stuff out there!
(Just correct the link to the FAQ page, though: it's just a plain 'http' web page, not a secured 'https' one)

thanks for the compliments - glad the faq helped. :) 
link corrected. (it's https for logged-in sourceforge users, and i was logged in when i copied the link...)

> 
But now I have an additional question on Firefox and Flash.

Suppose I decide to remove Ubuntuzilla and the Firefox installed through it to get back to the 'official' (?) Firefox 3.5.x available in Ubuntu repository.

Is that 'official' Firefox converted to 64-bit by the Ubuntu crew, or is it still the 32-bit version (in related posts I read that Mozilla only releases 32-bit stuff: is this correct)?

If the 'official' Firefox is converted to 64-bit, how could I get the 32-bit Flash plugin to work?

the firefox from the ubuntu repositories is a 64bit build. mozilla doesn't release 64bit builds, but ubuntu packagers make a 64bit build for the repos. so the "official" repository versions are 64bit. 

So... if you do decide to go back to official repo stuff, just delete the libflashplayer.so from your profile, and install flashplayer from the repos (which will pull a 64bit flash)

> Thanks, and regards from Italy.

you're quite welcome - and greetings from the usa :)

---

### Post by Yellow Pasque on 2009-08-06
> So... if you do decide to go back to official repo stuff, just delete the libflashplayer.so from your profile, and install flashplayer from the repos (which will pull a 64bit flash)

The last time I checked, the Flash in the repo was the 32-bit version that ran in 64-bit browsers with the use of nspluginwrapper. While this should work, many people find it better to use the native 64-bit Flash plugin.

---

### Post by nanotube on 2009-08-06
> **Temüjin said:**
> The last time I checked, the Flash in the repo was the 32-bit version that ran in 64-bit browsers with the use of nspluginwrapper. While this should work, many people find it better to use the native 64-bit Flash plugin.

oh, thanks for that clarification. i thought that since adobe released a 64bit version of flash, the installer from the repos would be pulling that one... but i guess i was wrong. :)

still the instructions remain the same: if you go back, take out the plugin from your home dir, and let the repos installer set stuff up as it likes.

---

### Post by bikerider42 on 2009-08-06
And what about java? How to make that work with the upgrade? tia... matt

---

### Post by nanotube on 2009-08-07
> **bikerider42 said:**
> And what about java? How to make that work with the upgrade? tia... matt

i don't know... in theory, should work the same way as flash...

---

### Post by Yellow Pasque on 2009-08-07
If you want Java to work in a 32-bit browser, install the ia32-sun-java6-bin package

---

### Post by ThotDjehuty on 2009-08-08
None of those tips worked out for me. I just have NO plugins installed on my 3.5.2.

I'm totally lost whats going on. I used Ubuntuzilla to install Firefox 3.5.2 and after that I have NO plugins at all. How in earth can this be so complicated in Ubuntu?

I want to use latest and fastest browser available - but this Ubuntu policy to support only the Firefox version 3.0.x which has been out when final release of Jaunty came out. This is something what I can call idiotism. Whit Ubuntu you just can't have newest Firefox as you default browser. You have to use those legacy versions... This is just very bad policy.

More pain gives me this plugin istallation methods. It seems to be so that 64bit is not really supported fully and you have to use 32bit plugins even there is available 64bit plugins.

Why can't you install Firefox plugins via Browser ? Is it too simple and all the nerds feels stupid to do everything vie cli or too complex or what it is that this must be so difficult? Can' you make anything simple than just click and install or autoinstall needed plugin when needed?

---

### Post by Yellow Pasque on 2009-08-08
There's firefox 3.5.2 in Jaunty, easily installable through Synaptic. You just didn't look very hard: [http://packages.ubuntu.com/jaunty-updates/firefox-3.5](http://packages.ubuntu.com/jaunty-updates/firefox-3.5)

> More pain gives me this plugin istallation methods. It seems to be so that 64bit is not really supported fully and you have to use 32bit plugins even there is available 64bit plugins.
What do you expect when you install a third-party 32-bit browser in a 64-bit distro?

---

### Post by nanotube on 2009-08-08
> **Temüjin said:**
> If you want Java to work in a 32-bit browser, install the ia32-sun-java6-bin package

thanks for the tip - i'll put that into the ubuntuzilla faq :)

---

### Post by ThotDjehuty on 2009-08-10
> **Temüjin said:**
> There's firefox 3.5.2 in Jaunty, easily installable through Synaptic. You just didn't look very hard: [http://packages.ubuntu.com/jaunty-updates/firefox-3.5](http://packages.ubuntu.com/jaunty-updates/firefox-3.5)


What do you expect when you install a third-party 32-bit browser in a 64-bit distro?

I just don't understand why Ununtu must mess up the Firefox browser and don't let it be as it is from Mozilla? Is there some reason for that? It's obvious that any kind of support for 64bit Ubuntu and Firefox is too complex to handle. 

So your Firefox 3.5.2 (firefox-3.5_3.5.2+nobinonly-0ubuntu0.9.04.1_amd64.deb) is actually Shiretoko version and NOT Firefox and yes I did look hard enough!

---

### Post by Yellow Pasque on 2009-08-10
> is actually Shiretoko version and NOT Firefox
Shiretoko is just the code name for Firefox 3.1 or 3.5. It is usually the same thing as FF, just with a different name and icon, because of licensing.

> I just don't understand why Ubuntu must mess up the Firefox browser and don't let it be as it is from Mozilla? Is there some reason for that?
[http://www.asoftsite.org/s9y/archives/161-FAQ-Why-is-my-firefox-3.5-still-called-Shiretoko.html](http://www.asoftsite.org/s9y/archives/161-FAQ-Why-is-my-firefox-3.5-still-called-Shiretoko.html)

Also note that a lot of smaller Linux distros (and even some larger ones, like Debian) have done away with using the FF name/logo because of licensing issues. See [http://en.wikipedia.org/wiki/Iceweasel](http://en.wikipedia.org/wiki/Iceweasel)

---

### Post by ThotDjehuty on 2009-08-10
> **Temüjin said:**
> Shiretoko is just the code name for Firefox 3.1 or 3.5. It is usually the same thing as FF, just with a different name and icon, because of licensing.


[http://www.asoftsite.org/s9y/archives/161-FAQ-Why-is-my-firefox-3.5-still-called-Shiretoko.html](http://www.asoftsite.org/s9y/archives/161-FAQ-Why-is-my-firefox-3.5-still-called-Shiretoko.html)

Also note that a lot of smaller Linux distros (and even some larger ones, like Debian) have done away with using the FF name/logo because of licensing issues. See [http://en.wikipedia.org/wiki/Iceweasel](http://en.wikipedia.org/wiki/Iceweasel)

"Mozilla Foundation owns the trademark “Firefox”[[5]]("http://en.wikipedia.org/wiki/Iceweasel#cite_note-4") and claims the right to deny the use of the name and other trademarks to unofficial builds.[[6]]("http://en.wikipedia.org/wiki/Iceweasel#cite_note-MozillaTrademarkPolicy-5") Unless distributions use the [binaries]("http://en.wikipedia.org/wiki/Binaries") supplied by Mozilla or else have special permission, they must [compile]("http://en.wikipedia.org/wiki/Compile") the Firefox source with an option enabled which gives Firefox the codename of the release version of Firefox on which it is based, and which doesn't use the official logo or other artwork."

jep jep - so this means that Ubuntu mess up whit Firefox code! Why - whats the need for this?

There are sites that uses this Browser User Agent info and gives optimized pages by that. Now like Facebook you just don't get correct set up whit Shiretoko FF you have to use plugins to fake your User agent to get functionalities work as they should. Facebook chat is one of those! Whit Shiretoko Gmail is broken and it crashes after login. Now how's supporting this issue? Not Mozilla!

---

### Post by Yellow Pasque on 2009-08-10
> so this means that Ubuntu mess up whit Firefox code! Why - whats the need for this?
Ubuntu is an open-source project. They don't want to use binaries if avoidable. Also, as the developer said, they only go through the process of getting Mozilla approval for one Firefox version for every Ubuntu release. It doesn't mean they're "messing" with the code.

> here are sites that uses this Browser User Agent info and gives optimized pages by that.
Sites shouldn't be checking the browser name, only the rendering engine if anything.

> Facebook chat is one of those! Whit Shiretoko Gmail is broken and it crashes after login.
Those things work fine for me in "Shiretoko." I wonder if you have sun-java6-plugin installed and set as your default Java plugin.

---

### Post by ThotDjehuty on 2009-08-10
> **Temüjin said:**
> Ubuntu is an open-source project. They don't want to use binaries if avoidable. Also, as the developer said, they only go through the process of getting Mozilla approval for one Firefox version for every Ubuntu release. It doesn't mean they're "messing" with the code.


Sites shouldn't be checking the browser name, only the rendering engine if anything.


Those things work fine for me in "Shiretoko." I wonder if you have sun-java6-plugin installed and set as your default Java plugin.

Thanks for the patience :) I will check that java-plugin and hope that it would be tha case... other vice it's a bug and somethin to report at launcbad..

---

### Post by Yellow Pasque on 2009-08-10
To make Facebook chat work: [http://bbs.archlinux.org/viewtopic.php?id=75312](http://bbs.archlinux.org/viewtopic.php?id=75312)

---

### Post by dannymichel on 2009-08-11
> **hackel said:**
> deepdeep, this is impossible.  You can't run a 32-bit plugin in a 64-bit browser without nspluginwrapper!  The solution is to download the 64-bit Flash plugin from Adobe and install it to ~/.mozilla/plugins.  You should never touch any files in /usr orther than in /usr/local.
i dont see a x64 download

---

### Post by novafluxx on 2009-08-11
> **Temüjin said:**
> The last time I checked, the Flash in the repo was the 32-bit version that ran in 64-bit browsers with the use of nspluginwrapper. While this should work, many people find it better to use the native 64-bit Flash plugin.
^^^Correct^^^

I don't believe that the repos include the 64-bit version of Flash, as it is considered to be in "alpha" stage.

Pulling Flash from the repos only installed the 32-bit version with a wrapper...if it works for you, congrats, enjoy.

> **dannymichel said:**
> i dont see a x64 download

Check here:
[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

This IS an alpha and is in testing, though I've never had a single problem with the previous refreshes

---

### Post by dannymichel on 2009-08-12
putting flash 10 x64 into the .mozilla/plugins(which u have to create) folder doesnt work

---

### Post by nanotube on 2009-08-12
> **dannymichel said:**
> putting flash 10 x64 into the .mozilla/plugins(which u have to create) folder doesnt work

if you are using the ubuntuzilla version of firefox, it is a 32bit build, so you need to use the 32bit version of flash in your .mozilla/plugins.

---

### Post by -=hazard=- on 2009-08-12
The firefox flash thing is pretty simple, you need just to download and install the appropriate flash version for your firefox and system 32/62 bit, but the real problem remain flash for Opera. I have tried all the ways with all flash versions, but till now I cant get it work. Any one knows something how to resolve it for opera?

---

### Post by Slurm on 2009-08-17
Sorry guys to bother you,  but I am also having the exact same problem here.  

Could you point me to some Newbie  "Dick-and-Jane" method to correct this problem?   I have installed flash using different methods and when I type about:plugins it says there is nothing there.  

I probably have 16 different Flashes scattered throughout my file system and will have to start by finding and removing everything.

Thanks in advance.. I hope that where I am pointed to has big bird  walk me through this.  

Slurm

---


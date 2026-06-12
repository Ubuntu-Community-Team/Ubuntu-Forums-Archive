---
title: "Howto install Flash on 64bit Gutsy Gibbon"
date: 2007-09-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kilz on 2007-09-15
[COLOR="Red"][SIZE="6"]This thread was from before Gutsy was released. It is old and outdated. Please do not post here, it needs to die[/SIZE].[/COLOR]




With any flavor of Gutsy you should be able to install flash with apt-get or synaptic/adept and nspluginwrapper should also install and automatically configure the plugin wrapper. 
Open a terminal and type
```
sudo apt-get install flashplugin-nonfree
```
Is all you need to do.
Alternately you should be able to install flashplugin-nonfree with adept or Synaptic and the same should also install and automatically configure the plugin wrapper.

[SIZE="3"]**[COLOR="Red"]You shouldn't need a script or howto to install it.[/COLOR] [COLOR="Purple"]That if it inst automatic, its a bug. Bugs should be reported on launchpad to be fixed.[/COLOR] Did you report your bug? We need everyone to report this, the more people with the problem, the greater the developers will see the need to fix it . [COLOR="Magenta"]Dont just leave it to someone else[/COLOR]. Your voice counts, let the developers know about the problem while Gutsy is still under development.**[/SIZE]
[COLOR="Red"][B][URL="https://bugs.launchpad.net/ubuntu"]
Here is the link to Launchpad![/URL][/B][/COLOR]

---

### Post by Kilz on 2007-09-25
Bump this up

---

### Post by diesel1 on 2007-09-25
Bump!

Diesel1.

---

### Post by jf/ on 2007-09-25
how about on feisty 64bit? There is no 'flashplugin-nonfree'.

---

### Post by John.Michael.Kane on 2007-09-25
> **jf/ said:**
> how about on feisty 64bit? There is no 'flashplugin-nonfree'.

Under feisty you can use this method [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924) which does the work you.

---

### Post by jauhari on 2007-09-26
> **Kilz said:**
> With any flavor of Gutsy you should be able to install flash with apt-get or synaptic/adept and nspluginwrapper should also install and automatically configure the plugin wrapper. 
Open a terminal and type
```
sudo apt-get install flashplugin-nonfree
```
Is all you need to do.
Alternately you should be able to install flashplugin-nonfree with adept or Synaptic and the same should also install and automatically configure the plugin wrapper.

[SIZE="3"]**[COLOR="Red"]You shouldn't need a script or howto to install it.[/COLOR] [COLOR="Purple"]That if it inst automatic, its a bug. Bugs should be reported on launchpad to be fixed.[/COLOR] Did you report your bug? We need everyone to report this, the more people with the problem, the greater the developers will see the need to fix it . [COLOR="Magenta"]Dont just leave it to someone else[/COLOR]. Your voice counts, let the developers know about the problem while Gutsy is still under development.**[/SIZE]
[COLOR="Red"][B][URL="https://bugs.launchpad.net/ubuntu"]
Here is the link to Launchpad![/URL][/B][/COLOR]
Let's Me try ;)

---

### Post by stmiller on 2007-09-27
Very cool!

---

### Post by paradoxni on 2007-09-28
i did this but no flash movies are appearing , doesnt seem to work here.

*EDIT*

Sorry my mistake, I had copied over my home folder from Feisty and my $home/.mozilla/plugins folder had a flash library remnant in there, I deleted that and now flash it working fine... thanks!! :)

---

### Post by Kilz on 2007-09-28
> **paradoxni said:**
> i did this but no flash movies are appearing , doesnt seem to work here.

Did you report the bug on launchpad?

---

### Post by paradoxni on 2007-09-28
updated my post ^^ fixed now

---

### Post by Kobalt on 2007-09-28
I have a question for you Kilz : is it your script that gave the idea to Ubuntu devs to install flash using ndiswrapper in an automated way, or it the other way around?

just out of curiosity :)

---

### Post by Kilz on 2007-09-28
> **paradoxni said:**
> updated my post ^^ fixed now

Even if you fixed it by extra steps, the steps shouldnt be needed. If you did extra steps did you file a bug report so it can be fixed so its completely automatic?

---

### Post by Kilz on 2007-09-28
> **Kobalt said:**
> I have a question for you Kilz : is it your script that gave the idea to Ubuntu devs to install flash using ndiswrapper in an automated way, or it the other way around?

just out of curiosity :)

I dont think it was either. There have been requests for the developers to add flash for a long time. Also my script is based on the instructions from the nspluginwrapper site and an older manual howto on this forum. I just made it click click easy. Sometimes thats just as important to new users. My guess is the Ubuntu developers followed the nspluginwrappers instructions.

---

### Post by Kobalt on 2007-09-28
Gotcha ;)

---

### Post by paradoxni on 2007-09-28
> **Kilz said:**
> Even if you fixed it by extra steps, the steps shouldnt be needed. If you did extra steps did you file a bug report so it can be fixed so its completely automatic?

But it wasnt a bug? it was me that caused it not to work by copying over my home folder from feisty.

---

### Post by Kilz on 2007-09-28
> **paradoxni said:**
> But it wasnt a bug? it was me that caused it not to work by copying over my home folder from feisty.

Anything that stops you automatically installing Flash and the wrapper is a bug. If you copied over your home folder and there were files that the new wrapper did not delete, its a bug. It should just work regardless of whats there or whats not.

---

### Post by Typhoe on 2007-10-03
Hi,

I have a little question for you.

I have Gutsy AMD64 installed since Tribe 5, and I installed the flash plugin with the same command line you gave in the first post:
sudo apt-get install flashplugin-nonfree nspluginwrapper

Flash has worked for a few time and then recently, it doesn't anymore.

I don't really know why and what I'm looking for is where the activity of the plugin should be logged (to be able to see what is wrong with my config and make a report).

Because, when I try an url with a flash animation, all I get is Firefox freezing for a few seconds (it fades to gray) and then, I get my page but with nothing in the flash frame...

For example, on this page, I get:
[http://www.adobe.com/fr/support/flash/ts/documents/test_version/version.swf](http://www.adobe.com/fr/support/flash/ts/documents/test_version/version.swf)



GET /fr/support/flash/ts/documents/test_version/version.swf HTTP/1.1

Host: [www.adobe.com](www.adobe.com)

User-Agent: Mozilla/5.0 (X11; U; Linux x86_64; fr; rv:1.8.1.6) Gecko/20070919 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6

Accept: text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5

Accept-Language: fr,fr-fr;q=0.8,en-us;q=0.5,en;q=0.3

Accept-Encoding: gzip,deflate

Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7

Keep-Alive: 300

Connection: keep-alive

Cookie: redirectURL=; TID=--BIOW



HTTP/1.x 200 OK

Connection: Keep-Alive

Date: Wed, 03 Oct 2007 10:40:00 GMT

Age: 461

Content-Length: 8621

Server: Apache

Last-Modified: Mon, 07 Jun 2004 18:19:11 GMT

Etag: "21ad-4f4865c0"

Accept-Ranges: bytes

Cache-Control: max-age=900

Expires: Sat, 14 Jul 2007 10:12:13 GMT

Keep-Alive: timeout=5, max=500

Content-Type: application/x-shockwave-flash


But no flash animation...

I got the same problem on 2 computers.

Hope for some directions :)
Thank you
Typhoe

---

### Post by Kilz on 2007-10-03
> **Typhoe said:**
> Hi,

I have a little question for you.

I have Gutsy AMD64 installed since Tribe 5, and I installed the flash plugin with the same command line you gave in the first post:
sudo apt-get install flashplugin-nonfree nspluginwrapper



You might want to file a bug report.

---

### Post by Typhoe on 2007-10-03
> **Kilz said:**
> You might want to file a bug report.

Yes indeed, but I don't really know what to fill in the report.... I can find any output in my log (syslog/message....?)

Thus my post here (before submitting a report...) for if someone has an idea.

Regards,
Typhoe

---

### Post by Kilz on 2007-12-05
Bump this thread so that maybe it will be seen and read.

---

### Post by NullHead on 2007-12-06
This is a good guide to have around for those new users! :lolflag:

---

### Post by NullHead on 2007-12-06
WOW :shock: this link that was giver earlier [http://www.adobe.com/fr/support/flash/ts/documents/test_version/version.swf](http://www.adobe.com/fr/support/flash/ts/documents/test_version/version.swf) when you run the page it can detect you're kernel version number!!!! thats kind of scary for me .. I'm not sure who I want to know my kernel version number :shock::shock:

---

### Post by Zack McCool on 2007-12-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/174555](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/174555) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				When I attempt to install, I get an error...

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

I have filed a launchpad bug report 174555.  Any ideas?

---

### Post by zietbukuel on 2007-12-06
I'm still having problems with this installer :( how do I get the latest version? thanks.

---

### Post by zietbukuel on 2007-12-07
> **Zack McCool said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/174555](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/174555) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
                When I attempt to install, I get an error...

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

I have filed a launchpad bug report 174555.  Any ideas?

There is a package for i386 but not for amd64 :(

---

### Post by Kilz on 2007-12-08
> **zietbukuel said:**
> There is a package for i386 but not for amd64 :(

You might want to place that info on the bug report.

---

### Post by John.Michael.Kane on 2007-12-08
> **Kilz said:**
> You might want to place that info on the bug report.

Heres the current standings [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890)
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

### Post by fain on 2007-12-08
> **paradoxni said:**
> But it wasnt a bug? it was me that caused it not to work by copying over my home folder from feisty.

I did this same thing except it was from a Ubuntu studio gutsy install. Did you resolve it? If so how?

---

### Post by borisattva on 2007-12-08
```
    * hardy lpia Successfully built (DONE)
    * hardy i386 Successfully built (DONE)
    * hardy amd64 Needs building
```

amd64 just gets no love it seems..

is building something that a 'person in charge' does or can anyone do it and make it available for others? if latter, then how?

---

### Post by Swmmrman on 2007-12-08
Im seeing something diferent.  Install goes well. F inishes normaly.  HOwever all flash apps continue to say i need the plugin.

---

### Post by John.Michael.Kane on 2007-12-08
> **Swmmrman said:**
> Im seeing something diferent.  Install goes well. F inishes normaly.  HOwever all flash apps continue to say i need the plugin.



Try installing via command line.

First run:
```
sudo aptitude remove flashplugin-nonfree
```

Next run:
```
sudo aptitude install flashplugin-nonfree
```

The end output should still say 

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

Options:
1) You can compile your own. 
2) Wait for the devs to upload the package. 
3) Try the workaround posted in this tread

---

### Post by borisattva on 2007-12-08
> **Swmmrman said:**
> Im seeing something diferent.  Install goes well. F inishes normaly.  HOwever all flash apps continue to say i need the plugin.

thats actually what everyone is reporting.
install only seems to go well. if you tick the more details triangle, in plain text it says

```

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.
```

the solution is out there for 32bit already, but apparently not yet built for amd64

---

### Post by Swmmrman on 2007-12-08
Ah.  Il have to take a lok at the 32 bit install to see if it works there

---

### Post by fain on 2007-12-08
> **paradoxni said:**
> i did this but no flash movies are appearing , doesnt seem to work here.

*EDIT*

Sorry my mistake, I had copied over my home folder from Feisty and my $home/.mozilla/plugins folder had a flash library remnant in there, I deleted that and now flash it working fine... thanks!! :)

Ah i missed this post. I deleted my entire .mozilla folder and let firefox create another and installed flash but it still didn't work.

Is there some where that shows the steps this script does so i can go through and check each step? 
Something somewhere other than my home directory has gotten screwed up.

---

### Post by Swmmrman on 2007-12-08
> **fain said:**
> Ah i missed this post. I deleted my entire .mozilla folder and let firefox create another and installed flash but it still didn't work.

Is there some where that shows the steps this script does so i can go through and check each step? 
Something somewhere other than my home directory has gotten screwed up.

Did that myself once.  Then found this post and felt silly

---

### Post by buntunub on 2007-12-08
Fix is [here]("http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb")

Got it from[ here]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890")

---

### Post by buntunub on 2007-12-08
Would like to thank all the helpful folks who put alot of time and effort into the fix for this incredibly ANNOYING issue.

---

### Post by WiFi Ed on 2007-12-08
> **buntunub said:**
> Fix is [here]("http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb")

Got it from[ here]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890")

I just did a fresh install of Gutsy64bit and had the same flash problem. Thanks for the links to the fix:)

---

### Post by umberleigh on 2007-12-10
> **buntunub said:**
> Fix is [here]("http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb")

Got it from[ here]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890")

Cheers for the fix. I can finally watch youtube on linux!

Unfortunately npviewer.bin consumes all my free CPU cycles until i kill it, at which point I have to restart firefox till flash will work again.

It even does it once I've closed any pages containing flash, or when I open pages containing flash streaming videos without playing them.

---

### Post by buntunub on 2007-12-10
Ya. Its a partial fix at best. disney.com and nick.com wont work for me either, but youtube works fine and the flash test page at adobe.com work. It probably has something to do with nspluginwrapper because ive heard a few things about just forcing the libflash.so works for some. Flash works flawlessly for me in x86-64 Gentoo/Sabayon, so there is something that they are obviously doing right, that Ubuntu is doing wrong. Considering that in Gentoo, you use the stock version of flash + nspluginwrapper, the problem is probably in how either the libflash or the nspluginwrapper is being compiled.

---

### Post by TheLions on 2007-12-10
> **buntunub said:**
> Fix is [here]("http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb")

Got it from[ here]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890")

10x for fix!

---

### Post by daradib on 2007-12-10
See this for more information: [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---

### Post by Paucus on 2007-12-11
> **TheLions said:**
> 10x for fix!
Thank you!!

---

### Post by neotasic1 on 2008-01-14
Unless I am reading it wrong, it seems that Flashplayer for 64bit Gutsy has been broken in latest release from Adobe.  There are a number of active bugs relating to this issue including the "md5sum mismatch install_flash_player_9_linux.tar.gz" error on using the command you refer to.  Do I still submit a new bug report even  though it is an exact duplicate of an existing report? (I am new to this and only just registered in launchpad as I have managed to resolve previous issues with the help of this forum)

Secondly, I take it there is no current fix?

---

### Post by Kilz on 2008-01-14
> **neotasic1 said:**
> Unless I am reading it wrong, it seems that Flashplayer for 64bit Gutsy has been broken in latest release from Adobe.  There are a number of active bugs relating to this issue including the "md5sum mismatch install_flash_player_9_linux.tar.gz" error on using the command you refer to.  Do I still submit a new bug report even  though it is an exact duplicate of an existing report? (I am new to this and only just registered in launchpad as I have managed to resolve previous issues with the help of this forum)

Secondly, I take it there is no current fix?

This thread is ancient, it predates Gutsy's release. We need to let it die. It holds no real good information anymore. [Go here.]("http://ubuntuforums.org/showthread.php?t=476924")

---

### Post by Melcar on 2008-01-14
I can't believe the repos haven't been updated to address this issue, but I guess it's due to the latest flash build being rather bugy.  It's not that hard to get flash working "manually" thought (move the file to the plugins folder and "wrap" it with nspluginwrapper).

---

### Post by Kilz on 2008-01-14
> **jennydai said:**
> I installed it, and the install went well. But flash appears continuing to say that i need the plugin.

[http://www.digitalrev.com/en/product_details.php?item_id=2720](http://www.digitalrev.com/en/product_details.php?item_id=2720)
[http://www.digitalrev.com/](http://www.digitalrev.com/)
[COLOR="Red"][SIZE="6"]
Please let this old outdated thread die!!![/SIZE][/COLOR] if you need help read post 45.

---


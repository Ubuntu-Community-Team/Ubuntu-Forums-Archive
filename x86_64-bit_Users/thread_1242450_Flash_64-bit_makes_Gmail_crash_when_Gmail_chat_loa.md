---
title: "Flash 64-bit makes Gmail crash when Gmail chat loads"
date: 2009-08-17
forum: x86 64-bit Users
---

### Post by WindPower on 2009-08-17
The title pretty much says it all; I've followed the instructions in the sticky and Flash works wonderfully, with the exception of this showstopper bug: when I open Gmail, Firefox crashes (segfault) as soon as the "Chat" section loads. Disabling chat makes it work, and "sudo rm /usr/lib/mozilla/plugins/libflashplayer.so" removes Flash and makes it work, but... no Flash, obviously. :(
Anyone else experiencing this? Any fixes/solutions?
Using Kubuntu 9.04 64-bit.

---

### Post by ikonia on 2009-08-17
contact adobe. Flash is closed source and still in pre-release state. Contact adobe for any problems.

---

### Post by Yellow Pasque on 2009-08-17
I see this complaint pretty frequently, but gmail works fine for me in Ubuntu Jaunty with FF 3.0.x and the native 64-bit Flash plugin. Are you using the latest version of 64-bit Flash? (It was updated in July). Note that I'm using open-source video drivers. I used to get segfaults in Flash using Catalyst/fglrx, and I wonder if nvidia users get them too.

Also, you might want to consider using a Flashblock plugin in Firefox. That's not a perfect solution, but should be a better workaround.

---

### Post by hmjbarbosa on 2009-09-26
Same problem here!

I had some sound issues with youtube-like flash videos and read on some forum that installing the 64bit version of adobe flash should solve it. I installed the version available here:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

released on 30th july. Flash works great, but google chat make firefox crash. 

My system is:

FireFox 3.0.14
x86_64 Kernel 2.6.28-15-server
Ubuntu 9.04 Jaunty

I wonder what is the "native" flash that was mentioned.

---

### Post by manlypain on 2009-10-30
this worked for me
this file was needed libadns1

so run
sudo apt-get install libadns1

i found this on another site and it worked like a charm

---

### Post by Mr_Miyagi on 2009-10-31
Tried installing libadns1 but no luck here :(

---

### Post by SilverWave on 2009-10-31
Nope libadns1 does not work.

---

### Post by fab.head on 2009-10-31
It happened to me as well after a fresh installation of Karmic + 64-bit flash plugin.
I tried to install/uninstall/reinstall the 64-bit flash plugin in several ways:

1. manually (simply downloaded it from the adobe website)
2. with the script which can be found in this forum
3. from the ppa repo

The result was always a crash when accessing gmail from firefox.

Yesterday I installed Virtualbox PUEL. In order to be able to access my USB devices from Virtualbox, I had to check "Use VirtualBox" under System > Administration > Users and Groups > "my user" > User Privileges 

Under "User Privileges" I also checked all the remaining items, then logged out and in again.

Well, I don't know whether this helped in any way but since then the issue with firefox + 64-bit flash + gmail has gone.

Could it be an issue with user privileges?

---

### Post by rokclimb15 on 2009-11-03
Having the same problem myself.  I am using the binary nvidia driver.  Really strange.

---

### Post by atorch on 2009-11-05
> **SilverWave said:**
> Nope libadns1 does not work.

Does not work for me either.  Gmail crashes as soon as chat loads (given flash is installed).  

Changing user privileges did not help either.

---

### Post by bear24rw on 2009-11-05
I am also experiencing this problem and libadns1 did not help :/

---

### Post by ron66 on 2009-11-06
I also had the same problems.  However I was able to fix it.  During the process I came across a web-site that mentioned problems (don't rememver exactly where) with Adoble flash plugin libs and other Adobe libs. After I read this, I remembered that I had installed Pandora One (which depends on Adobe Air) a few days ago. So I uninstalled Pandora (see [http://eatthepath.com/2009/05/29/installing-pandora-under-ubuntu-linux/](http://eatthepath.com/2009/05/29/installing-pandora-under-ubuntu-linux/) for gotchas)  then uninstalled Adobe Air.

After all the uninstalling, I tried a you tube video, and Gmail. Both worked.  No crashing!

Unfortunately I don't recall the exact steps I took, but it seems  that the 32 bit Adobe Air and 64-bit Adobe flash libs somehow are in conflict. Good Luck. YMMV.

---

### Post by efflandt on 2009-11-06
The sticky at the top of the forum had a tidbit about "illegal instruction".  And while I was not sure if that was the case, Firefox with 64-bit flash plugin in both 9.04 and 9.10 would work fine on some websites (like www,foxnews.com), but blow up and disappear just clicking on a link to [www.foxbusiness.com](www.foxbusiness.com) from there.  I have an older Athlon64 3200+.

So the link from the stick post to [http://ubuntuforums.org/showthread.php?t=1263905](http://ubuntuforums.org/showthread.php?t=1263905) helped me identify a problem and got Firefox flash working without blowing up.

---

### Post by ambrosa on 2009-11-07
I've made a fresh Ubuntu 9.10 installation some days ago.
I've no add extra software: this is a clean and simple installation.

CPU Intel Core 2 Duo E6600 (no LAHF problem), Nvidia 7900GT using Nvidia accelerated driver rev. 185

With original Flash player (32bit version), no crash but flash doesn't work for 50% web sites

I've switched to 64 bit flash version and Firefox crash also for me in Gmail while loading chat.

---

### Post by ph0nph0n on 2009-11-08
If you do not have the lahf_lm issue (see efflandt's post above) but are still experiencing issues with Gmail, you may want to consider this solution. This is only a fix for Gmail though.

It appears that Gmail is loading a few flash files to enable chat sounds, even if sounds are disabled in the options.

Preventing those files to load solves the crashing issue, while still leaving the possibility to enjoy Flash, Gmail and Gmail's chat, the only thing being lost is the chat sounds.

I used the [Adblock plus]("https://addons.mozilla.org/en-US/firefox/addon/1865") add-on to block those flash files, and added those three filters:

[LIST]
[*]mail.google.com/mail/im/chatsound.swf
[*]mail.google.com/mail/im/media-api.swf*
[*]mail.google.com/mail/im/sound.swf
[/LIST]

Detailed steps:

1. Install Adblock Plus if you're not already using it: go to [https://addons.mozilla.org/en-US/firefox/addon/1865]("https://addons.mozilla.org/en-US/firefox/addon/1865") and click "add to Firefox". Once the install is complete, you'll be asked to restart Firefox. Adblock will then ask you to select a subscription list (this add-on has been designed to prevent ads by checking a filters list - If you subscribe to any list, you won't see ads anymore).
2. Go to Tools > Adblock Plus Preferences.
3. For each filters I wrote above, click the "Add filter..." button at the bottom left, paste the filter and press enter.
4. Once you're done, click OK.
5. You should now be able to load Gmail without any issues.

---

### Post by gunksta on 2009-11-08
Have any of you tried installing / using FlashBlock? I'm on 64-bit Kubuntu and I can use Gmail's chat function without crashing, but I rarely have any Flash loaded, because I block it. This could lead to occasional problems if you want to watch something with Flash and chat at the same time, but it could at the very least be a step in the right direction.

Just in care it's relevant, I'm using Intel Graphics, so if the driving problem here is Nvidia drivers, my observations could be useless.

---

### Post by ph0nph0n on 2009-11-09
Hi gunksta,

Yes FlashBlock does work, however it changes your whole Flash experience. Hence the idea of using Adblock to block only the relevant flash.

---

### Post by JeffV on 2009-11-09
ph0nph0n:  Thanks for the tip on using Adblock.  It works perfectly!

---

### Post by gunksta on 2009-11-09
I'm certainly glad that it's working for you, although I must confess, I tend to use both.

---

### Post by WindPower on 2009-11-10
OP here, I am not on the same computer anymore and do not have this problem. I think that the recent flow of replies does tend to show that the bug is still there for some users though :o

---

### Post by blueridgedog on 2009-11-10
Until the adobe supplied flash matures, use this link for gmail instead:

[http://mail.google.com/mail/?ui=1&ov=1](http://mail.google.com/mail/?ui=1&ov=1)

It is the version without the chat tool.

---

### Post by blueridgedog on 2009-11-10
I did post this on the gmail support forum...

---

### Post by senorgomez on 2009-11-17
Solution: Restart your computer. Gmail will work then.

I didn't need the wrapper, just moved the adobe lab flash to /usr/lib/mozilla, deleted all other versions of flash, banged my head against a wall when gmail didn't work, then restarted.

Solved my problem.

---

### Post by blueridgedog on 2009-11-17
Ha...worked for me...just a restart.  It shows how little I reboot.

---


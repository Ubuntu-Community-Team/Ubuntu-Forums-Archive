---
title: "Flash won't work in Firefox after upgrade"
date: 2007-05-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by vickistan on 2007-05-22
I recently upgraded my Ubuntu Dapper AMD64 box. I used Update Manager to move to Feisty. [Note: I am unsure how to verify this since all I have to go on is successful run in Update Manager and an /etc/debian-version file which says I am running testing/unstable. I used to be a Slackware user. The kernel hasn't changed, but I expect that that is normal for a distro upgrade.] Now the firefox-32 doesn't run flash anymore. I have different versions on my system:

/usr/lib/firefox/firefox
/usr/lib64/firefox/firefox

but neither of these play flash. There is another installation at /usr/lib32/firefox/, but it doesn't contain an executable called firefox. This worked before the upgrade.

Anyone know how I can get flash working again?

Captain Vic

---

### Post by JSThePatriot on 2007-05-22
Unfortunately Firefox and Flash aren't working well together in Fiesty. What I have had to do is follow the instructions for getting flash to work in Opera, and when I need to view a flash site, I open it in opera. I know that's not the best solution, but it works until the plugins are updated for Firefox.

Here's the instructional link: [http://ubuntuforums.org/showthread.php?t=413040&highlight=flash+opera](http://ubuntuforums.org/showthread.php?t=413040&highlight=flash+opera)

I hope this helps,
JS

---

### Post by shad0w_walker on 2007-05-22
I have fiesty running just fine with firefox + flash 9 player.

If you dont mind having a 32bit version of firefox + libs installed there is a very nice script available which installs it for you and offers you the choice of installing flash, java, etc. I would recommend this way of doing things as flash, java, etc dont have 64bit releases and nspluginwrapper is very flakey.

Link to thread covering firefox32:

[http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)

If you have a problem with firefox not opening files from the download manager (Click on open but nothing happens) then this link should sort you out.

[http://ubuntuforums.org/showpost.php?p=2690318&postcount=14](http://ubuntuforums.org/showpost.php?p=2690318&postcount=14)

Good luck and try not to get sucked into the anti 64bit FUD that lets people shove what ever browser they prefer when there are solutions to your problem.

---


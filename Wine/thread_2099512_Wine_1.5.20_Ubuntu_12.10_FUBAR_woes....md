---
title: "Wine 1.5.20 Ubuntu 12.10 FUBAR woes..."
date: 2012-12-29
forum: Wine
---

### Post by wiebeest on 2012-12-29
Hmmz. Ok, I'm starting to see a pattern here I don't particularly like with the latest Wine update.
 
After I updated Wine to version 1.5.20 today and afterwards my  perfectly working **Far Cry 2** failed to start. And coincidentally also my **Deus Ex: HR** refused to start. 
When trying to install an older game that always used to work perfectly now also failed (**Mass Effect 2**)   

I went to check the forums and lo and behold: 

This problem with the latest wine seems to happen to people  across all different kind of games. 

So now I see problems with **Eve online**: [http://ubuntuforums.org/showthread.php?p=12427861#post12427861]("http://ubuntuforums.org/showthread.php?p=12427861#post12427861") 

Check **Sim city Deluxe SE**: [http://ubuntuforums.org/showpost.php?p=12427629&postcount=95]("http://ubuntuforums.org/showpost.php?p=12427629&postcount=95") 

And **World of WarCraft**: [http://ubuntuforums.org/showpost.php?p=12427887&postcount=2489]("http://ubuntuforums.org/showpost.php?p=12427887&postcount=2489")

[B][U]So, Houston we definitely have a serious problem with the latest wine update. 
So, stay away from it untill there's a solve announced.[/U][/B]

And I especially don't like this myself since I had a gaming evening planned for now!!  ](*,)

Meanwhile, if anybody knows how to reverse to the previous version 1.5.19 I'd be very interested to know.

---

### Post by pioughd on 2012-12-30
Same problems here, almost nothing works under 1.5.20.  

> **wiebeest said:**
> 
Meanwhile, if anybody knows how to reverse to the previous version 1.5.19 I'd be very interested to know.

I just did it successfully.  Presuming you are using the ubuntu-wine PPA like I am, download the following files from:

[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.5/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.5/)

wine1.5-amd64_1.5.19-0ubuntu3_amd64.deb 
wine1.5_1.5.19-0ubuntu3_amd64.deb 
wine1.5-i386_1.5.19-0ubuntu3_i386.deb

then install all 3 at once with sudo dpkg -i

---

### Post by Horrid Troll on 2012-12-30
You can downgrade by going to synaptic - finding wine then going to package->force version..though whether they have 1.5.19 is another thing. If that works for you, you may also need to lock the version (in synaptic also) otherwise you'll be constantly notified that an update is available..or disable the Wine PPA.

I'm sure that Wine used to have older debs on their site, but I can't seem to see them now.

---

### Post by tkmn on 2012-12-30
Not the first time this has happened. :(


I found the previous version in **/var/cache/apt/archives**

Is there a proper way to do this? Other than uninstalling & installing manually.

Force version only works when you have multiple sources I think. (older versions from the same repo are not available)

---

### Post by pimanov on 2012-12-30
> **pioughd said:**
> Same problems here, almost nothing works under 1.5.20.  



I just did it successfully.  Presuming you are using the ubuntu-wine PPA like I am, download the following files from:

[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.5/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.5/)

wine1.5-amd64_1.5.19-0ubuntu3_amd64.deb 
wine1.5_1.5.19-0ubuntu3_amd64.deb 
wine1.5-i386_1.5.19-0ubuntu3_i386.deb

then install all 3 at once with sudo dpkg -i

Great solution. Thanks a lot!

---

### Post by wiebeest on 2012-12-30
> **tkmn said:**
> Not the first time this has happened. :(

I found the previous version in **/var/cache/apt/archives**

Is there a proper way to do this? Other than uninstalling & installing manually.

Succes with a mix of what your retrievings found in **"var/cache/apt/archives"** and the commandline pioughd mentioned.  > **pioughd said:**
> then install all 3 at once with sudo dpkg -i

**Only I found _4 files_ instead of 3 relating to the previous version of Wine:**

[LIST]wine1.5_1.5.19-0ubuntu3_amd64.deb (1.2 mb)[/LIST]
[LIST]wine1.5-amd64_1.5.19-0ubuntu3_amd64.deb (23.0 mb)[/LIST]
[LIST]wine1.5-i386_1.5.19-0ubuntu3_i386.deb (21,5 mb)[/LIST]
[LIST]wine_1.5.19-0ubuntu3_amd64.deb (918 bytes)[/LIST]

Copy those to your desktop.
Now open up a Terminal and type: 
"sudo dpkg -1" as **pioughd** mentioned, then select and then drag the older Wine version files on your desktop (copied from "var/cache/apt/archives") to the Terminal.  

**Enter Your Password **
 
And you'll get a warning: "dpkg: warning: downgrading wine from 1.5.20-0ubuntu1 to 1.5.19-0ubuntu3"

**ENTER**

In the [Terminal] then type: "winecfg" to open ***Wine Configuration*** and then go to the "About"-Tab to check if the version was indeed downgraded to version 1.5.19.

---

### Post by wiebeest on 2012-12-30
Thanks all for the help!!! :popcorn:

---

### Post by rdpascua on 2012-12-30
Hey I got this problem too, my starcraft won't run after wine update :confused:

---

### Post by Butthead on 2012-12-30
I'm sure that a fix will be released soon if you're just a little bit patient. :-\"

Funny, the fubared Wine upgrade had to be released on a Saturday. ](*,)

---

### Post by sirtoast on 2012-12-31
I tried the steps above, but I don't run 64bit, and when I tried to go with the i386 packages, I got a broken package manager, and spend 45 minutes fixing that manually.  I wouldn't consider the problem solved, as much as worked around :)

I'm just going to wait until the wine build gets updated and fixed.  (and I'm getting a new video card this week, so not sweating it too much until then)

Until then, I'll be playing Rochard from my Humble Bundle:)

---

### Post by dino99 on 2012-12-31
hey guys,

if a problem is not reported then no needs to wait a fix for an unknown issue.

Where are the reported bugs ?

Have you installed the wine debug package ? then ran your game with winedebug into a terminal ?

---

### Post by dino99 on 2012-12-31
bugs opened: [https://bugs.launchpad.net/ubuntu/+source/wine/+bug/1094870](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/1094870)

---

### Post by MrRtd on 2012-12-31
I successfully downgraded to 1.5.19, but I just wanted to comment that this doesn't actually solve the problem with 1.5.20. Now that I know that a bug report has been made, I look forward to seeing this problem being fixed. 
I've been using the latest wine releases for a few years and this has been the first time I've ran into a serious problem, which required a downgrade.

---

### Post by nu2linux6 on 2012-12-31
A new ppa release, 1.5.20-0ubuntu2, fixes the problem. Seems to have been either a faulty patch or build.

---

### Post by wiebeest on 2012-12-31
> **nu2linux6 said:**
> A new ppa release, 1.5.20-0ubuntu2, fixes the problem. Seems to have been either a faulty patch or build.

Scared to use it now that I'm so happy my games work again under 1.5.19. ;-) But, now I know how to downgrade succesfully I'll check it out soon.

For now: Happy New Year every body! :biggrin:

---

### Post by False_Karma on 2013-01-01
> **nu2linux6 said:**
> A new ppa release, 1.5.20-0ubuntu2, fixes the problem. Seems to have been either a faulty patch or build.

*-0ubuntu2 didn't fix it for me, Deus Ex still refused to launch.  But I got what I wanted, a quick way to revert, thanks to:

> **pioughd said:**
> Same problems here, almost nothing works under 1.5.20.  



I just did it successfully.  Presuming you are using the ubuntu-wine PPA like I am, download the following files from:

[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.5/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.5/)

wine1.5-amd64_1.5.19-0ubuntu3_amd64.deb 
wine1.5_1.5.19-0ubuntu3_amd64.deb 
wine1.5-i386_1.5.19-0ubuntu3_i386.deb

then install all 3 at once with sudo dpkg -i

Now everything works as well as it should, as far as I can tell. Huge thanks!

---


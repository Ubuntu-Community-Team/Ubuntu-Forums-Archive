---
title: "flashplugin-nonfree works fine but stops after a while FF3b5"
date: 2008-05-23
forum: x86 64-bit Users
---

### Post by rikhard.fsoss on 2008-05-23
hi all,

i have a problem with FF3b5 using amd64 hardy, i installed flashplugin-nonfree and nspluginwraper, it works fine, but if after a while i don't watch any flash video, flash stop working with a grey box.

but with konqueror everything is ok?!!!

does anyone have a clue?

thanks

rj

---

### Post by philinux on 2008-05-23
It's been reported at launchpad. Close FF and restart it gives flash again.

---

### Post by Tsukasah on 2008-05-23
> Close FF and restart it gives flash again. 

I have the same problem, but I really don't want to close out firefox if I'm in the middle of something. Sure, after you're done with what ever you're doing you can restart it, but I'm too lazy to do that. Also I'm a super multi-tasker and I usually have about 10 or 11 tabs open, and though firefox will reopen those after closing it. I sometimes have to relogin to them, just an assortment of things. 

But yeah if you do restart FF you can get flash again for a period of time. When I had this problem the first time(it fixed until my HDD crapped out) I tried gnash and went here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Just follow the instructions. It worked for me before. Now it doesn't. Wow, my first time helping someone with Ubuntu! Or atleast an attempt to helping someone.

Oh, also I guess you can go here [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924) but that's also flashplugin-nonfree and nspluginwrapper. And the bell rang(school) so I have to go, cant check.

---

### Post by rikhard.fsoss on 2008-05-23
restart???!! that's quite st**** it's like reboot in m$-windows world.

and i'm a hugeeeeeeeee user of tabs, right now i have 64 open, and i need them, so it's not the good solution to this problem.

i really don't know where is the problem, but i suspect firefox, since konqueror works fine.

i tried with swiftfox3pre, it seems to work a litle better, but the same grey boxes continues after a while.

thanks

rj

---

### Post by Zorael on 2008-05-23
It's the new flash player, nspluginwrapper and FF3b5 not playing well together. You could try the new Flash 10 beta and see if it works better, alternatively change back to FF2. I did the latter.

A fresh build of nspluginwrapper might also do the trick. See [http://gwenole.beauchesne.info/en/blog/2007/12/25/nspluginwrapper_and_new_flash_player](http://gwenole.beauchesne.info/en/blog/2007/12/25/nspluginwrapper_and_new_flash_player).

---

### Post by rikhard.fsoss on 2008-05-24
ohh well, i think i'm gonna try flash10, but swiftfox seems to work better, could swiftweasel work well?!!

---

### Post by rikhard.fsoss on 2008-05-24
well f10 is even worst........what a crap plugin.

adobe those idiots, how about a flash for amd64?


rj

---

### Post by pixel :-) on 2008-05-24
don't restart,try reload the page several times,also try go back and forth in the history.Also try "killall npviewer.bin".

---

### Post by philinux on 2008-05-24
> **pixel :-) said:**
> don't restart,try reload the page several times,also try go back and forth in the history.Also try "killall npviewer.bin".

Tried the reload and back forth, does not work. Might try the killall option though.

---

### Post by pixel :-) on 2008-05-24
npviewer.bin is just the wrapper for the 32 flash for the 64 firefox,firefox it's self will not be affected.Hopefully it will reload npviewer correctly,at worse you'll stay with a white scare.

---

### Post by philinux on 2008-05-24
Damn thing wont crash, flash been working for ages now. :lolflag:

---

### Post by philinux on 2008-05-24
> **pixel :-) said:**
> don't restart,try reload the page several times,also try go back and forth in the history.Also try "killall npviewer.bin".

Comes back with no process killed.

It's not listed in system monitor

---

### Post by pixel :-) on 2008-05-24
yea, i tryed killal, and it doesn't fix anything,but it reproduces your problem, now i have too a white scare and it dosn't whant to go away no mater what.

I restarted firefox in a terminal,i killed np..And know it gives me a deluge of


*** NSPlugin Wrapper *** ERROR: NPClass::HasProperty() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::HasMethod() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::Invoke() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::HasProperty() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::HasMethod() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::Invoke() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::HasProperty() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::HasMethod() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::Invoke() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::HasProperty() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::HasMethod() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::Invoke() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::HasProperty() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::HasMethod() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::Invoke() invoke: Connection closed

maybe it's good for the developers

"It's not listed in system monitor" click "Tree" for the tree view in kde system guard,it depends from the proses firefox.

"no process killed" you mean this?
$ killall rgjioj
rgjioj: no process killed

or this,here it did kill something
$ killall npviewer.bin
$                  
You mean that now it gives you "no process killed" or it never killed anything?With me it sticks even if a close the pages with flash

Next time restart firefox in a terminal and see what errors it gives you.

just for fun, try this "killall -s STOP npviewer.bin" and then "killall -s CONT npviewer.bin"

---

### Post by pixel :-) on 2008-05-24
i think i found it.Go in tools-->add-ons-->plugins
disable flash,reenable it, reload your page.It gets unblocked after i did killall npv..

---

### Post by philinux on 2008-05-25
Just disabling and then enabling flash plugin followed by reload gets it going again.

Weird

---

### Post by Yellow Pasque on 2008-05-25
> **rikhard.fsoss said:**
> adobe those idiots, how about a flash for amd64?
As I said in the Flash sticky:
> If you want 64-bit Flash, I suggest taking the time to send Adobe feedback. Adobe has stated that they will consider a native 64-bit version of Flash with enough "customer demand". Whether this is true or an empty corporate promise, I don't know. I would like to believe it's true, so I made my demand known, like so: [http://ubuntuforums.org/showpost.php?p=5031885&postcount=6](http://ubuntuforums.org/showpost.php?p=5031885&postcount=6)

---

### Post by of_darkness on 2008-05-25
> **rikhard.fsoss said:**
> restart???!! that's quite st**** it's like reboot in m$-windows world.

and i'm a hugeeeeeeeee user of tabs, right now i have 64 open, and i need them, so it's not the good solution to this problem.

i really don't know where is the problem, but i suspect firefox, since konqueror works fine.

i tried with swiftfox3pre, it seems to work a litle better, but the same grey boxes continues after a while.

thanks

rj

 use [https://addons.mozilla.org/en-US/firefox/addon/2324](https://addons.mozilla.org/en-US/firefox/addon/2324) (session manger) and ther is no prob to restart whit alooot of tabs, and if ther sub tabs of comunitys req login etc to show, then start whit no net and then login to the sites and then reload all the others tabs:)  and thers a new beta of flash -flash 10 and it seams to work kinda fine, better then flash 9..

---


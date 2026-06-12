---
title: "Facebook"
date: 2009-01-10
forum: x86 64-bit Users
---

### Post by mr_skater99 on 2009-01-10
Hi all,

Here's my issue - and I'm not sure if this is jut 64bit (but I would assume it is).

I have 8.10 installed with the latest java jre 1.6.12 plugin for firefox installed (manually as per another thread on here atm)as well as the flashplugin-nonfree from the repo's installed.

Both of these work on separate sites.  HOWEVER with Facebook, I can login and get the initial news page, but as soon as I click on a link anywhere on that page for anything, it just sits there and goes no where.  Firefox shows errors on the page in different iframes (I think the web developer plugin).

Facebook works fine on all other computers in the house.  Just this 8.10 64bit box that fails.

Any suggestions from anyone as to what this might be.  I've been trying heaps of different things with java or flash plugin to get this to work.  Am I on target or would it be something completely different?

Cheers.

---

### Post by tuxxy on 2009-01-10
> **mr_skater99 said:**
> Hi all,

Here's my issue - and I'm not sure if this is jut 64bit (but I would assume it is).

I have 8.10 installed with the latest java jre 1.6.12 plugin for firefox installed (manually as per another thread on here atm)as well as the flashplugin-nonfree from the repo's installed.

Both of these work on separate sites.  HOWEVER with Facebook, I can login and get the initial news page, but as soon as I click on a link anywhere on that page for anything, it just sits there and goes no where.  Firefox shows errors on the page in different iframes (I think the web developer plugin).

Facebook works fine on all other computers in the house.  Just this 8.10 64bit box that fails.

Any suggestions from anyone as to what this might be.  I've been trying heaps of different things with java or flash plugin to get this to work.  Am I on target or would it be something completely different?

Cheers.

Firstly I would remove the flashplugin-nonfree you have installed from the repos and install the new native 64-bit browser plug-in, this isnt in the repos yet but is much better than the 32-bit one you are currently having to use.  This improved Flash for me considerably however I dont use Facebook so cannot confirm this makes it work.

[http://ubuntuforums.org/showthread.php?t=999313](http://ubuntuforums.org/showthread.php?t=999313)

---

### Post by mr_skater99 on 2009-01-11
Thanks for the suggestion Tuxxy, just tried that and didn't make a difference.

Cheers though.

---

### Post by tuxxy on 2009-01-11
hmm ok then I noticed you installed Java manually? this is not recommended as it can be easily installed along with Flash, codecs and much more by installing the package ubuntu-restricted-extras

```

sudo apt-get install ubuntu-restricted-extras
```

[http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras](http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras)

---

### Post by mr_skater99 on 2009-01-11
Uninstalled what i had installed manually and tried just this package.

Facebook is still no different.

Is it only me having this problem???

---

### Post by Spr0k3t on 2009-01-11
The problem has to be something completely different from Java or Flash.  I disabled both of the plugins and had no problems.

Here's what I would do to start.

Go into your home directory and rename the ".mozilla" directory.  This will remove any added functionality which you may have activated for Firefox.  This will also remove any plugins you currently have running.  Close out of Firefox first, rename the directory, launch Firefox.  You should have a completely clean Firefox of all elements and plugins.

Post up your results.

---

### Post by mr_skater99 on 2009-01-11
Just tried it.  Got a clean firefox with no bookmarks etc.  Same thing though.

Facebook loaded, i could log in and got the main news page - but as soon as i clicked on something, firebug showed errors on the page and nothing loaded.

Any other suggestions?

I have also tried disabling all plugins i have installed (only 3 - 4) but made no difference.

---

### Post by nikgare on 2009-01-11
What happens when you disable/remove firebug?
Do you have javascript enabled in Firefox's choices?

---

### Post by mr_skater99 on 2009-01-11
Hi,

Just removed every plugin that i have installed.  all i had left was the default ubuntu firefox extension.

Still the same.

Checked firefox's options and javascript is enabled.

Cheers.

---

### Post by mr_skater99 on 2009-01-11
What i find most weird is that if i click on something on the news page it fires off the request - and just sits there.  It doesnt timeout like any other page, i left it sitting here for almost 20 mins and it just sat here.

Cheers.

---

### Post by Arup on 2009-01-11
Have you removed nsplugin?

---

### Post by Spr0k3t on 2009-01-11
> **mr_skater99 said:**
> Just tried it.  Got a clean firefox with no bookmarks etc.  Same thing though.

Facebook loaded, i could log in and got the main news page - but as soon as i clicked on something, firebug showed errors on the page and nothing loaded.

Any other suggestions?

I have also tried disabling all plugins i have installed (only 3 - 4) but made no difference.

Need a screenshot of these errors you are seeing.  Do they pop up on their own or do you have to actively go and find them.  There are hundreds of javascript errors on Facebook but no Java that I've been able to find.  So take a shot of the before and after and describe (in as much detail as you can) what steps you take to produce the error messages.

---

### Post by hyperdude111 on 2009-01-11
If you want try another browser like opera or if you need firefox it runs great in wine.

---

### Post by mr_skater99 on 2009-01-12
I double checked and nsplugin inst installed.

Here's something funny i have just found.  If i disable javascript in firefox preferences, the facebook login page says javascript is disabled but still lets me login and see the main news page - and i can then click on somethings (that dont require javascript) like someones name and it takes me straight to their profile page. 

If i re-enable javascript it goes back to just doing nothing when i click something.

The errors i was getting previously were in firebug.  I just re-installed firebug and for some reasons the errors are not showing up now.  If they do again i will post them up.

Is there anyway javascript in my firefox install can be miffed up?

Cheers.

P.S

i just tried to submit this post on the ubuntu box - i have been doing most of my posting from my mac as i am playing leave it open on people suggestions and play with settings on the ubuntu box.  

Anyway, when i clicked submit post below it waited for sometime and eventually popped up a save dialogue box and asked me if i wanted to save newreply.php

Something is definitely screwy with my firefox....

---

### Post by nikgare on 2009-01-12
Then rename your profile and create a new one to see if your firefox profile is corrupt.
ie: Rename the folder **.mozilla** in your home directory

---

### Post by mr_skater99 on 2009-01-12
That was the first thing i tried - but tried it again, just in case.

Gives me a clean firefox - but with the same issues.

Cheers.

---

### Post by mr_skater99 on 2009-01-14
SOLVED!!!!

In firestarter i had enable ICMP filtering checked and none of the boxes below ticked (so none allowed).

Unticked this box and restarted firefox and facebook works perfectly.  Tried this a few times un-ticking and re-ticking the box and restarting firefox and this has solved it!!!!

Can someone explain why?  My knowledge of ICMP is severely limited.

Cheers.

---

### Post by mr_skater99 on 2009-01-14
I'm trying to mark this as solved - but when i go edit and go advanced - i change the title of the thread to include [SOLVED] and when i hit save i get a database error.

Am i doing this right?

---

### Post by Spr0k3t on 2009-01-14
Glad to hear the problem was nothing to do with Firefox but rather a separate application causing the problem.  Have you reloaded your configuration (~/.mozilla/) files back in to test everything to make sure it was okay?

---

### Post by mr_skater99 on 2009-01-14
Yep- using my original profile now (copied .mozilla back) and all is well :)

---

### Post by nishv on 2009-01-23
> **mr_skater99 said:**
> SOLVED!!!!

In firestarter i had enable ICMP filtering checked and none of the boxes below ticked (so none allowed).

Unticked this box and restarted firefox and facebook works perfectly.  Tried this a few times un-ticking and re-ticking the box and restarting firefox and this has solved it!!!!

Can someone explain why?  My knowledge of ICMP is severely limited.

Cheers.

Hi,

This issue is nothing to do with ICMP, It is to do with with the MTU setting where the packets are getting chopped off while leaving your network.

Call your ISP and ask for the MTU setting, then apply it on your Router / NIC Device.

---


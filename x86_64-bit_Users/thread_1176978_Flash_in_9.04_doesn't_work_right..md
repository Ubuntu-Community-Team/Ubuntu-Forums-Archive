---
title: "Flash in 9.04 doesn't work right."
date: 2009-06-02
forum: x86 64-bit Users
---

### Post by The Funkbomb on 2009-06-02
Sorry for cross posting this with the Multimedia forum but I think this might be just a 64bit problem.

As you may have figured out, I'm running 9.04 64bit.  I have two issues with Flash.  The second issue is the result of trying to fix the first issue.

Issue 1:  I was trying to visit this Wired.com article and it had a video.  When I tried to view the video, it would try to load but then the firefox screen would just gray out.  If I go into System Monitor, npviewer.bin is using up all my CPU.  If I kill it, firefox unfreezes but the video doesn't play.

I ran firefox through terminal.  When it closes, this is what I get:

```
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() wait for reply: Connection closed
*** NSPlugin Wrapper *** ERROR: NPObject 0x2e09a90 is no longer valid!
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1854):invoke_NPP_Destroy: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** ERROR: NPObject 0x480c420 is no longer valid!
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1923):invoke_NPP_SetWindow: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2533):invoke_NPP_HandleEvent: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1923):invoke_NPP_SetWindow: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2533):invoke_NPP_HandleEvent: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1923):invoke_NPP_SetWindow: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2533):invoke_NPP_HandleEvent: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1923):invoke_NPP_SetWindow: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2533):invoke_NPP_HandleEvent: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1854):invoke_NPP_Destroy: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** ERROR: NPObject 0x37a8600 is no longer valid!
```

That is the flash player.

This brings me to issue 2.

I went into the IRC channel and some folks said I should install the 10.0 r22 straight from Adobe.  One guy even gave me a link to the ubuntu site that walked me through it.  It was three steps.  Step one removes all the flash stuff you may have installed.  Step two gets the tar from adobe and untars it.  Step three moves it to /usr/lib/mozilla/plugins.

All well and good.  I open up firefox and go to youtube.com to see if it works.  Firefox closes.  It doesn't gray out, it just closes.

I ran firefox through terminal again.  When it closes, it just says segment fault.

I tried moving the plugins to ~/.mozilla/plugins (even creating a folder called plugins) and the same behavior happens.

I don't know how to fix this.

---

### Post by The Funkbomb on 2009-06-02
I fixed it all on my own. :D

This is what I had to do.  The standard set up is to place the plugin into /usr/lib/firefox/plugins which I had done.

This time, I actually looked through /usr/lib/ and saw there were multiple firefox folders.  There was the standard /usr/lib/firefox/ but there was also firefox-3.0.10/plugins.  With nothing to lose, I threw it in there.

Bingo bango, success!

---

### Post by The Funkbomb on 2009-06-02
Actually, looking at about:plugins, it shows that it's really in /usr/lib/firefox-addons/plugins/libflashplayer.so

It works though.  Youtube works.  The wired.com video works.  Success.

---

### Post by Anubis on 2009-06-03
Please DELETE this thread?

---

### Post by The Funkbomb on 2009-06-03
Why?  What if someone else has the same problem?  I searched and asked all over for help and couldn't find any that worked.  My way worked.  I'm happy with the results.  I hope it helps someone else too.

---

### Post by mrskimmyl on 2009-06-03
> **The Funkbomb said:**
> Why?  What if someone else has the same problem?  I searched and asked all over for help and couldn't find any that worked.  My way worked.  I'm happy with the results.  I hope it helps someone else too.
Please don't delete! Thank you so much for posting this - I'm having the same problem. I just had 1 question. I'm still very new to Ubuntu, so I'm sorry if this is actually a dumb question. Did you just do to the Adobe website, download the plugin onto your desktop (or wherever) & then do a drag & drop & move that into /usr/lib/firefox/ ?

---

### Post by The Funkbomb on 2009-06-03
Yes and no.  First, let's make sure we're on the same page here.  I'm running 9.04 x64.  The plugin I used is only for 64bit.  If you're using 32bit, I haven't heard too many complaints about their flash.

If you're using 64bit, let's continue. :)

You can't download this plugin directly from the Adobe site.  It's an Alpha or maybe even a release candidate at this point.  I don't know.

We can do all this in three easy steps.  Write these down because you'll want to close out Firefox while you do this.

You say you're new to Ubuntu so I'll show you the easiest way to do this... through Terminal.  Open Terminal by going to Applications>Accessories>Terminal.

First thing we need to do is make sure we've removed all existing flash stuff.  In Terminal type this:

```
sudo apt-get purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash nspluginwrapper swfdec-mozilla
```

If done correctly, you can go into Firefox and flash won't load.  Also, if you go into about:plugins, it shouldn't have anything for flash.  After checking, close Firefox again.

Step two.  We need to get the alpha release.  The latest release is 10.0 r22.  In Terminal, enter this:

```
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz && tar xvfz libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz
```

This will download libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz and untar it.  If you're coming from Windows, tar is sorta like a zip.  They're not the same thing, they're just similar in how we treat them.

Step three.  We need to move your extracted file to the correct folder.

The correct command for this is:

```
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so
```

Actually, I just tried in /usr/lib/mozilla/pluggins and it does indeed work so far.

---

### Post by mr PUG on 2009-06-04
all you need to do to make flash work properly in ubuntu 9.04:

```
$ sudo apt-get remove --purge flashplugin-*
$ sudo apt-get remove --purge swfdec-mozilla swfdec-gnome mozilla-plugin-gnash gnash
$ sudo apt-get install flashplugin-nonfree
```enjoy

---

### Post by ken78724 on 2009-06-04
mr PUG
   running 64 bit 9.04 Jaunty, I get the following terminal response
k78724@Kproductions:~$ $ sudo apt-get remove --purge flashplugin-*
bash: $: command not found
k78724@Kproductions:~$ $ sudo apt-get remove --purge swfdec-mozilla swfdec-gnome mozilla-plugin-gnash gnash
bash: $: command not found
k78724@Kproductions:~$ $ sudo apt-get install flashplugin-nonfree

Have I failed to understand how to apply your note? Or, must I go back to the prior post?

---

### Post by HarleyJoel on 2009-06-04
After following numerous instructions on how to improve Flash's performance, on five different computers, I'm getting about 9 fps using Flash 10. I guess I'm going to have to live with it.

---

### Post by HarleyJoel on 2009-06-04
> **ken78724 said:**
> mr PUG
   running 64 bit 9.04 Jaunty, I get the following terminal response
k78724@Kproductions:~$ $ sudo apt-get remove --purge flashplugin-*
bash: $: command not found
k78724@Kproductions:~$ $ sudo apt-get remove --purge swfdec-mozilla swfdec-gnome mozilla-plugin-gnash gnash
bash: $: command not found
k78724@Kproductions:~$ $ sudo apt-get install flashplugin-nonfree

Have I failed to understand how to apply your note? Or, must I go back to the prior post?
Remove the "$" - just start with "sudo"

---

### Post by mr PUG on 2009-06-04
@Ken78724

it appears you copied the "$" into the command. I put the $ symbol there to illustrate the start of a new command line..
Leave out the "$" and it should work.

So type the following 3 commands in Terminal (and hit Enter after each line):

```
sudo apt-get remove --purge flashplugin-*
sudo apt-get remove --purge swfdec-mozilla swfdec-gnome mozilla-plugin-gnash gnash
sudo apt-get install flashplugin-nonfree
```

---

### Post by The Funkbomb on 2009-06-04
The plugin you are telling people to install was the one that caused all my problems.

---

### Post by Yellow Pasque on 2009-06-04
> You can't download this plugin directly from the Adobe site.
You can, but they hide it [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by FTL_Diesel on 2009-06-04
mr PUG, I agree with The Funkbomb that what you suggested will just reinstall the plugin that people seem to be having problems with. I believe that this is occurring because installing flash through 'flashplugin-nonfree' gets flash working by wrapping the 32-bit version.

The native 64-bit version that The Funkbomb used dodges this problem. I also was having problems with Firefox freezing for periods of time when I navigated to or from pages with flash. Installing the native 64-bit version fixed this completely for me.

---

### Post by ken78724 on 2009-06-04
Very interesting Gents! I just followed Mr. PUG and got this terminal message: 2009-06-04 21:17:41 (77.7 KB/s) - `./adobe-flashplugin_10.0.22.87.orig.tar.gz' saved [3968445/3968445]

Download done.
Flash Plugin installed.

Setting up flashplugin-nonfree (10.0.22.87ubuntu2) ...

Am I in for problems? If so, how does one do the Funkbomb advantage mentioned here? Would you expect this to also affect Opera 10 beta; just installed it at 7 PM Texas time. 

> **FTL_Diesel said:**
> mr PUG, I agree with The Funkbomb that what you ..... 

The native 64-bit version that The Funkbomb used dodges this problem. I also was having problems with Firefox freezing for periods of time when I navigated to or from pages with flash. Installing the native 64-bit version fixed this completely for me.

as you'd expect, I have no exp with the newly installed flash... Give me a leg up to go by. Must eat and try to finish an unrelated project before going to bed. Back to you when I can. 
Ken

---

### Post by The Funkbomb on 2009-06-04
Here's the thing.  The -nonfree plugin, aka the one from the repositories, does work most of the time.  Major sites like Youtube did fine with it because their flash players tend to be on the lightweight side.  Heavier flash players such as ones that allow full aspect control or sites that rely heavily on flash (ones with multiple flash widgets) locked my browser up.

As someone who visits tons of websites, this was unacceptable for me.  Plus, I'm one of those people who want everything to work 100% of the time.

If you just want to casually browse, the plugins from the repository may be fine for you.  Hopefully, once Adobe releases the alpha, Canonical will add it to the repos so folks like me can get updates like the rest of you folks through update manager.  Until then, I have no issue manually updating.

---

### Post by Kareeser on 2009-06-04
Interesting post. My flash x64 installation also crashes firefox with a segmentation fault. I had just given up and reverted back to the npwrapper'd 32-bit version installed by the Ubuntu repos.

I don't see how changing the folder of a plugin should make any sort of difference, since firefox reads plugin information from all of the folders regardless.

In any case, perhaps it's a permissions problem... a bug report could be in order here.

---

### Post by The Funkbomb on 2009-06-05
> **Kareeser said:**
> Interesting post. My flash x64 installation also crashes firefox with a segmentation fault. I had just given up and reverted back to the npwrapper'd 32-bit version installed by the Ubuntu repos.

I don't see how changing the folder of a plugin should make any sort of difference, since firefox reads plugin information from all of the folders regardless.

In any case, perhaps it's a permissions problem... a bug report could be in order here.

Because the folder that I was told to put the plugin into wasn't there before.

I was told to put it into /usr/lib/firefox/plugins.  There is no /usr/lib/firefox/... until you try to move a file there.  Once you do, it creates that folder I guess.  Firefox doesn't know to look in that folder because it isn't part of the program's places to look.

If you move it into /usr/lib/mozilla/plugins, that folder has always been there and the program knows to look in there.

---

### Post by mrskimmyl on 2009-06-07
> **The Funkbomb said:**
> Yes and no.  First, let's make sure we're on the same page here.  I'm running 9.04 x64.  The plugin I used is only for 64bit.  If you're using 32bit, I haven't heard too many complaints about their flash.

If you're using 64bit, let's continue. :)


I didn't know whether I was using 32bit or 64bit, but because I was having the exact same problem as you were, I assumed (correctly) that I was using 64bit. I followed the instructions you provided & it worked perfectly! All of the flash videos/files that weren't working for me before are now working. Thank you so much for your help! :D

---

### Post by Entropy_Sam on 2009-06-09
Dont know why anyone would want to delete this thread...
 
Thanks, FunkBomb, I've been experiencing flash problems that completely seize my system up. Here's hoping this solves it when I get hoje ttonight and try it out...

---

### Post by Entropy_Sam on 2009-06-09
Alas, no joy.

Flash still caused a complete system freeze after installing 64 bit Flash... :-(

---

### Post by pouyan_afshin on 2009-07-09
In fact I had the same problem as [The Funkbomb]("http://ubuntuforums.org/member.php?u=744323") mentioned in the first place, that is what I did and now it works perfectly:

Do everything [The Funkbomb]("http://ubuntuforums.org/member.php?u=744323") mentioned in the 7th reply.

I did all of those but then as soon as I opened a clip in youtube firefox grayed.

That is what I did to fix it, run the following script and then everything will work fine:

$ wget [http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh)
$ sudo bash ./flash10_en.sh

reference: [http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html)

I hope it helps, thanks again to [The Funkbomb]("http://ubuntuforums.org/member.php?u=744323").

---

### Post by iakovos on 2009-07-22
Post #7 's advice made flash work perfectly - thanks!

---

### Post by 7th-time on 2009-07-28
Of course Flash does not work well or easily in 9.04. When was it ever easy to watch youtube, google vids, etc. on any UBUNTU machine? Believe me; I've been trying since release 6.06. 
Since this is one of the most popular uses for a P.C., you would think, given all the man and woman hours devoted to developing UBUNTU and the surrounding software, that they could have come up with an easy foolproof install by now?
Still, I remain optimistic. If you pray very hard, spend several hours a day learning the in's and out's of the Linux OS, and start dating a local geek, you just may be watching those 'flash' vids before the Zippy Zebra rlease.

---

### Post by Opti_Rick on 2009-07-31
```
sudo apt-get remove --purge flashplugin-*
sudo apt-get remove --purge swfdec-mozilla swfdec-gnome mozilla-plugin-gnash gnash
sudo apt-get install flashplugin-nonfree
```

The above worked wonders on my celeron based Toshiba Satellite laptop.

---

### Post by JoeEndUser on 2009-08-04
I also have a satellite. Unfortunately Opti-Rick's suggestion didn't work for me, but did partially. I used the first removal line:

sudo apt-get remove --purge flashplugin-*

Then went back to you tube and tried a video.

I was prompted to save and install the Adobe flash plug-in, which I did.

I rebooted the computer just in case.

Woo-hoo, you tube! Not even choppy!

---


---
title: "A few questions about Swiftfox"
date: 2007-01-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by MysticAurora on 2007-01-18
Hi. I'm currently using firefox32 with some minimal media functionality (read: only Flash works). What I'd like to do is have it to where Flash, mplayer, and Java all work within my browser along with all of my extensions:

Adblock-Plus
Linkification
Sage
Greasemonkey
ImageZoom
Web Developer
Download Statusbar
TabMixPlus
SessionManager
downTHEMall
DOM Inspector
Gmail Notifier

If I switch to Swiftfox, will I be able to reinstall my extensions and get them to work just as well as before? I'd like to get my web browsing mastered before I get to work on the other problems with my system.

---

### Post by theslut on 2007-01-18
if you isntall swiftfox it should automatically pick up your firefox profile and run everything just as it was before, extensions included.

---

### Post by slicker on 2007-01-18
> **theslut said:**
> if you isntall swiftfox it should automatically pick up your firefox profile and run everything just as it was before, extensions included.

But if the original poster doesn't have something working, it will still not work with Swiftfox. All Swiftfox is, is a build of the Firefox code with a different name. 
Lastly, Swiftfox is a proprietary, non-free as in freedom application that has free alternatives. While the original poster wants to install non-free plug-ins it may be because they don't have free plug-ins that work. They may not realize the application takes away freedoms that the parent (Firefox) gives them.

---

### Post by Unterseeboot_234 on 2007-01-18
Swiftfox uses its own file structure to manage the links for the plug-ins: java, MPlayer, flash-6, and this can get somewhat confusing with the java plug-in. I tried both the "64-bit Firefox with wrappers", and I tried the "run 32-bit Firefox with Flash, with MPlayer, with java". It's the download speed. I like fast downloads. For whatever reason, Swiftfox lets me download at the max possible speed with DSL. If you do a Swiftfox/Automatix2 install with the plug-ins and nothing else on top of a fresh ubuntu, no problems.

If you try the recipes for the other Firefox browsers, well, you're going to have to do some file surgery to make Swiftfox/java connect again. The Bookmarks, personal preferences, etc. will stay the same in all variations of Firefox/Swiftfox. You will have to look for the sym-links inside opt/swiftfox/plug-ins and evaluate if the links connect to /usr/lib/jvm/ia32-java-1.5.0-sun/jre/plugin.

Have you ever used the Flash IDE? It's a customized Windows Internet Explorer, licensed from Microsoft. I don't plan to make any kind of software with the Swiftfox browser. I do plan to download with the Swiftfox browser.

---

### Post by MysticAurora on 2007-01-18
In that case, should I just seek some help with my current setup instead? I like using free (as in freedom) software whenever possible, and since I went through the trouble of installing firefox32, I suppose I should use it. :)

All I need to do is get Java and Mplayer working, and I have no idea where to start. I've tried downloading the official JRE, and my system says that it's installed, but apparently it's not connected to firefox32 like it should be. It's the only web browser on my system outside of lynx.

---

### Post by Kilz on 2007-01-18
> **MysticAurora said:**
> In that case, should I just seek some help with my current setup instead? I like using free (as in freedom) software whenever possible, and since I went through the trouble of installing firefox32, I suppose I should use it. :)

All I need to do is get Java and Mplayer working, and I have no idea where to start. I've tried downloading the official JRE, and my system says that it's installed, but apparently it's not connected to firefox32 like it should be. It's the only web browser on my system outside of lynx.

Did you install my howto for firefox32?

---

### Post by Kilz on 2007-01-18
> **Unterseeboot_234 said:**
> Swiftfox uses its own file structure to manage the links for the plug-ins: java, MPlayer, flash-6, and this can get somewhat confusing with the java plug-in. I tried both the "64-bit Firefox with wrappers", and I tried the "run 32-bit Firefox with Flash, with MPlayer, with java". It's the download speed. I like fast downloads. For whatever reason, Swiftfox lets me download at the max possible speed with DSL. If you do a Swiftfox/Automatix2 install with the plug-ins and nothing else on top of a fresh ubuntu, no problems.

If you try the recipes for the other Firefox browsers, well, you're going to have to do some file surgery to make Swiftfox/java connect again. The Bookmarks, personal preferences, etc. will stay the same in all variations of Firefox/Swiftfox. You will have to look for the sym-links inside opt/swiftfox/plug-ins and evaluate if the links connect to /usr/lib/jvm/ia32-java-1.5.0-sun/jre/plugin.

Have you ever used the Flash IDE? It's a customized Windows Internet Explorer, licensed from Microsoft. I don't plan to make any kind of software with the Swiftfox browser. I do plan to download with the Swiftfox browser.

If you install the fasterfox extension you will get the same download speeds in Firefox. Swiftfox automatically sets these settings

---

### Post by MysticAurora on 2007-01-18
> Did you install my howto for firefox32?

Yeah, I followed the instructions when I first installed firefox32 and Flash worked perfectly, but embedded media (for Mplayer to handle) will not work, and neither does Java (just tested Yahoo!'s Pool and it spat the "click here to download plugin" message at me). I'm not sure what screwed up and/or where. If there's anything I can do to help diagnose the problem, I'd be more than willing to do it.

---

### Post by Kilz on 2007-01-18
> **MysticAurora said:**
> Yeah, I followed the instructions when I first installed firefox32 and Flash worked perfectly, but embedded media (for Mplayer to handle) will not work, and neither does Java (just tested Yahoo!'s Pool and it spat the "click here to download plugin" message at me). I'm not sure what screwed up and/or where. If there's anything I can do to help diagnose the problem, I'd be more than willing to do it.

Mplayer plugin will not work on Edgy if you are running it because of missing libraries. But the java plugin will. If you are running Dapper everything should work. You may want to run the install script if you used the manual howto as it will make sure everything gets set up correctly. 
I never installed Edgy so im not sure what ones they are if you are running it. After installing the script, open up a terminal and type in 
```
mplayer 
``` to see whats missing, it should give you an error code. I will try and help you install what it needs.

---

### Post by MysticAurora on 2007-01-19
> **Kilz said:**
> Mplayer plugin will not work on Edgy if you are running it because of missing libraries. But the java plugin will. If you are running Dapper everything should work. You may want to run the install script if you used the manual howto as it will make sure everything gets set up correctly. 
I never installed Edgy so im not sure what ones they are if you are running it. After installing the script, open up a terminal and type in 
```
mplayer 
``` to see whats missing, it should give you an error code. I will try and help you install what it needs.

Does that mean I should uninstall all the stuff I have and retry the entire installation, or just retry the mplayer and java installations through the install script? I'm not exactly following you; despite using Xubuntu since last July, I'm still relatively new to setting packages up properly.

[EDIT] I'm using Xubuntu 6.06 Dapper, AMD64

---

### Post by Unterseeboot_234 on 2007-01-19
Kilz, you've posted ...
```
If you install the **fasterfox extension **you will get the same download speeds in Firefox. 
```

I'm not 100% happy with Swiftfox. My goal was to try to have everything 64-bit software. Let's say I wanted to stay 64-bit Firefox, get rid of Swiftfox. Where do I find fasterfox, and is it something for the 64-bit Firefox? If I could get 64-bit Swiftfox to just do file download comparably, then I'd hack around for the other extensions. And, BTW, I still refer to your excellent HowTo when I'm trying to resolve browser problems I'm having. The HowTo is in my Bookmarks.

As far as java. This post has been insightful for me.

[**HowTo Custom Install Sun Java**]("http://www.ubuntuforums.org/showthread.php?t=319138")

64-bit java does not have everything java that 32-bit does, including the plugin. I had to evaluate what is needed for development and what is needed for web pages. Automatix2 can make a mess of everything installing an un-needed SDK and a duplicate java plugin. Pile on some of these other recipes for the HowTo 32-bit, HowTo 64-bit Firefox with extensions and you've got multiple plugins and multiple sym-links.

---

### Post by Kilz on 2007-01-19
> **MysticAurora said:**
> Does that mean I should uninstall all the stuff I have and retry the entire installation, or just retry the mplayer and java installations through the install script? I'm not exactly following you; despite using Xubuntu since last July, I'm still relatively new to setting packages up properly.

[EDIT] I'm using Xubuntu 6.06 Dapper, AMD64

No you dont need to uninstall anything. Just run the install script. It should replace everything and install anything that is missing.

> **Unterseeboot_234 said:**
> Kilz, you've posted ...
```
If you install the **fasterfox extension **you will get the same download speeds in Firefox. 
```

I'm not 100% happy with Swiftfox. My goal was to try to have everything 64-bit software. Let's say I wanted to stay 64-bit Firefox, get rid of Swiftfox. Where do I find fasterfox, and is it something for the 64-bit Firefox?

64-bit java does not have everything java that 32-bit does, including the plugin. I had to evaluate what is needed for development and what is needed for web pages. Automatix2 can make a mess of everything installing an un-needed SDK and a duplicate java plugin. Pile on some of these other recipes for the HowTo 32-bit, HowTo 64-bit Firefox with extensions and you've got multiple plugins and multiple sym-links.

Fasterfox is available at the Firefox extensions site. [Here is its page,]("https://addons.mozilla.org/firefox/1269/") and it should work with all versions of Firefox including the 64bit versions.
The last versions of the Firefox32 script changed the location of the 32bit plugins to /usr/lib32/firefox32/plugins to avoid the problem of multiple plugins that may be named the same. Installed 64bit plugins should go be installed to /usr/lib/firefox/plugins automatically so they shouldnt effect your 32bit install.

---

### Post by MysticAurora on 2007-01-20
Great! Everything worked out AOK. Should I make a check for any Java or Mplayer stuff that I installed before that isn't needed? Or rather, which packages in particular does the Fx 2.0 w/plugins rely on?

---

### Post by Kilz on 2007-01-20
> **MysticAurora said:**
> Great! Everything worked out AOK. Should I make a check for any Java or Mplayer stuff that I installed before that isn't needed? Or rather, which packages in particular does the Fx 2.0 w/plugins rely on?

If you followed my howto before, there is nothing you will need to remove. The script installs everything to the same places and overwrites whats there. The howto and script basically do the same thing.  You may have missed something the script installed, not replaced, or added extra. The only thing you will do by removing something is mess it up.

---


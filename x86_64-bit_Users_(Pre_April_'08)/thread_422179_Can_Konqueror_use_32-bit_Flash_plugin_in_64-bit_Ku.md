---
title: "Can Konqueror use 32-bit Flash plugin in 64-bit Kubuntu Feisty?"
date: 2007-04-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by monstermunch on 2007-04-24
Hi,

I just upgraded from Kubuntu Edgy to Feisty, both being the 64 bit versions. In Edgy, I had Firefox and Konqueror both working with the Flash plugin. I'm fairly sure I was using the 64-bit Firefox but I can't remember. I used automatix to install Flash and it I don't recall having to tinker with anything.

I installed Feisty and ran automatix to install the Flash plugin. This did not work with 64-bit version of Firefox but did with the 32-bit version. Konqueror seemed to refuse to load the plugin when I told it to rescan for new plugins as it would not list it as a new plugin. I don't recall having this problem with Edgy.

After trying a lot of dead-ends, I found a blog post about installing nspluginwrapper and then running:
nspluginwrapper --install /opt/flash32/libflashplayer.so

I think this creates a 64-bit plugin from a 32-bit one. This means Firefox and Konqueror can both use it. It seems to be working fine except for the odd thing. For instance, in Konqueror, it will load youtube OK videos but not this game [http://www.flash-game.net/game/2805/ping-pong.html](http://www.flash-game.net/game/2805/ping-pong.html), yet these both work in Firefox. Occasionally, the plugin box will go grey and unresponsive in both, but a reload fixes this. Can anyone suggest what the problem might be?

Also, am I mistaken somehow about the ease in which I got 32-bit Flash working with Konqueror in Edgy? It seemed to take no effort at all and I've read in several places that Konqueror can load 32-bit plugins, yet it doesn't seem to work. Is there a way to make it load the 32-bit Flash plugin?

I don't really mind using 32-bit Firefox as I only use it when Konqueror has trouble rendering a page, but not having reliable Flash in Konqueror is very frustrating. Is there an easy way to resolve this?

Thanks.

---

### Post by kuja on 2007-04-25
You'll need to use nspluginwraper, but yeah, it can be done. Make sure you're pointing Konqueror at the proper plugin folder (seems like you're putting it in /opt/flash32) It should be able to pick it up okay.

---


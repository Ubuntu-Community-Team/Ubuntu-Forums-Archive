---
title: "Problem with Flash Player with both Firefox 1.0.6 and Mozilla"
date: 2005-08-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by richpull on 2005-08-01
Hi everyone!
I am having a problem with my flash. I tried to install flash from the macromedia site but it told me that it didnt have a package for my kernel (2.6.11 - AMD64) I tried to search for a plugin in Synaptic Package Manager and found one and installed it. However now whenever when i try to see a website with Flash content both browsers (Mozilla and Firefox) just close.

Can anyone help me cause I really need this ?

Thanks
Richard

---

### Post by DancingSun on 2005-08-01
Wow...I didn't know there was Flash on the 64-bit repositories...and a GPL one to boot!  I'll try it out when I get the chance.  Does anyone know about this?  Are these GPL Flash libraries reversed engineered products?

Now, if you search around the forum, you'll see that you can't get the official Flash to work in 64-bit browsers, because Macromedia doesn't make a 64-bit version of Flash.  There's a thread to petition for 64-bit support, look for it, and sign the petition and fill in the wish form.

Update:
Just found the website to the GPL Flash libraries, it states that it is not compatible with all Flash versions, so maybe that's why it is crashing.

---

### Post by Tamir on 2005-08-01
[QUOTE=DancingSun]Wow...I didn't know there was Flash on the 64-bit repositories...and a GPL one to boot!  I'll try it out when I get the chance.  Does anyone know about this?  Are these GPL Flash libraries reversed engineered products?

Now, if you search around the forum, you'll see that you can't get the official Flash to work in 64-bit browsers, because Macromedia doesn't make a 64-bit version of Flash.  There's a thread to petition for 64-bit support, look for it, and sign the petition and fill in the wish form.

Update:
Just found the website to the GPL Flash libraries, it states that it is not compatible with all Flash versions, so maybe that's why it is crashing.[/QUOTE]
 Can someone explain? I don't understand.

---

### Post by etitor on 2005-08-01
I can. Ubuntu AMD64 has somewhere in its repositories a flash plugin that doesn't work. It is called libflash-mozplugin and libflash-swfplayer. Version 0.4.11-2 in my system.

They are useless AFAIK for playing flash content at least under Firefox.

---

### Post by Jet2k5 on 2005-08-01
lol I'm not surprised :P

---

### Post by DRF on 2005-08-05
I've got some flash content to work with those plugins. In an attempt to get flash to work I looked around synaptic also and installed: (or allready had installed)

libflash0
libflash-mozplugin
libflash-swfplayer
libswfdec0.3
swf-player
gstreamer0.8-swfdec

After getting all those and reloading a couple of webpages with flash I could see the flash animations but unfotunatly the links embedded in the flash wouldn't work, but it's better than nothing.

Daniel

---

### Post by etitor on 2005-08-06
[QUOTE=DRF]After getting all those and reloading a couple of webpages with flash I could see the flash animations but unfotunatly the links embedded in the flash wouldn't work, but it's better than nothing.[/QUOTE]

Daniel, can you please give us one or two URLs that you know for sure have flash you can see (with AMD64 and those packages installed)?

---

### Post by wmcbrine on 2005-08-06
If you really want Flash, for now, the easiest thing to do is install a 32-bit browser, so you can in turn install the official plugin. I have a 32-bit Firefox in a chroot for this purpose. I still use the 64-bit Firefox as my main browser.

In the 64-bit browser, I have a dummy Flash plugin to supress Firefox's nag messages, as well as the Flashblock extension, which dirties the screen less than the dummy plugin alone. (I tried Flashblock without the plugin, but that didn't work.)

---

### Post by Corbelius on 2005-08-06
I have installed gplflash version 0.4.12 and work fine with Epiphany, but with 0.4.13 crash all time.

---

### Post by kao on 2005-08-07
[QUOTE=Corbelius]I have installed gplflash version 0.4.12 and work fine with Epiphany, but with 0.4.13 crash all time.[/QUOTE]

gplfash freezed my ff with gnome untill ctrl-alt-bkspace

---

### Post by Corbelius on 2005-08-08
[QUOTE=kao]gplfash freezed my ff with gnome untill ctrl-alt-bkspace[/QUOTE]

Do u have 0.4.12 or 0.4.13?

[http://www.steiner-web.info/rafael/flash/](http://www.steiner-web.info/rafael/flash/)

---


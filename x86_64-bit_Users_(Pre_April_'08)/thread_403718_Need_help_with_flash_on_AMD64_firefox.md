---
title: "Need help with flash on AMD64 firefox"
date: 2007-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by webmaren on 2007-04-07
I'm running the Feisty AMD64 beta, and I can't seem to get flash to work on sites like youtube and others. But on other sites like addicting games and some movies, it will work. Does anybody have a solution?

I already looked at the 64-bit howto stickied on here. I also have tried to install 32bit Firefox with no success.

---

### Post by Kernel_Krunch on 2007-04-07
i just posted a solution to the guide thread... cut and paste it

---

### Post by webmaren on 2007-04-07
I looked at the solution, but all it did was make youtube movies appear broken. Newgrounds, sort of works now, but the sound is all discconnected from the movie.

---

### Post by Kilz on 2007-04-07
> **webmaren said:**
> I looked at the solution, but all it did was make youtube movies appear broken. Newgrounds, sort of works now, but the sound is all discconnected from the movie.


Nspluginwrapper is ok, but it can be hard to set up. It also lacks java plugin support. Try 32bit firefox. Look in my signature, go to the firefox howto, download the install script, right click on it and choose extract here, open the folder it will make, double click on the base-plugins script and choose run in terminal. Answer yes or no to a few questions.

---

### Post by webmaren on 2007-04-07
> **Kilz said:**
> Nspluginwrapper is ok, but it can be hard to set up. It also lacks java plugin support. Try 32bit firefox. Look in my signature, go to the firefox howto, download the install script, right click on it and choose extract here, open the folder it will make, double click on the base-plugins script and choose run in terminal. Answer yes or no to a few questions.

As I stated in my first post, the 32bit installation does not work for me.

---

### Post by Kilz on 2007-04-07
> **webmaren said:**
> As I stated in my first post, the 32bit installation does not work for me.

I have yet to have anyone that could not run 32bit firefox. The script and application work in the Feisty beta. Have you enabled the required repositories and ran the script? I also notice that you have 3 posts, all of them in this topic. What have you done or posted trying to get it to work?

---

### Post by Kernel_Krunch on 2007-04-07
> **webmaren said:**
> but all it did was make youtube movies appear broken.
what does broken mean?  i have no problems at youtube.
> Newgrounds, sort of works now, but the sound is all discconnected from the movie.
I was just there and it works fine.  

I think your install of firefox32 has wreaked your system, i suggest you reinstall and try again from scratch.  its interesting you didn't need the sys links either.. anyways, i updated the script in case you get a missing plugin notice.

---

### Post by Kilz on 2007-04-07
> **Kernel_Krunch said:**
> .  
**I think your install of firefox32 has wreaked your system, i suggest you reinstall and try again from scratch. ** its interesting you didn't need the sys links either.. anyways, i updated the script in case you get a missing plugin notice.

I think you have absolutely no idea what you are talking about. If you did you would never suggest wiping and reinstalling an install over an installed .deb file. One that has been installed in a lot of systems since Dapper.

---

### Post by Kernel_Krunch on 2007-04-07
you don't know what this guy did... you said yourself there should be no problem with his install since everyone else can do it... yet his doesn't work so he messed something up... and his system at the same time since the plugin 'kinda' works.  

you attack my words when all i'm trying to do is help this person, sad.

---

### Post by Kilz on 2007-04-08
> **Kernel_Krunch said:**
> you don't know what this guy did... you said yourself there should be no problem with his install since everyone else can do it... yet his doesn't work so he messed something up... and his system at the same time since the plugin 'kinda' works.  

you attack my words when all i'm trying to do is help this person, sad.

Im against the "just wipe it down" without finding out any information at all mentality. You dont know what happened , so suggesting to just reinstall may be a bad idea. I would never suggest that with just the posts in this thread.

---

### Post by webmaren on 2007-04-08
I finally fixed my 64bit version by taking one of the suggestions in the install thread

I force-architectured the flash install package and now everything works.

---

### Post by yelserpdog on 2007-04-08
I'm running an AMD 64 and can't get the 32 bit firefox working, it just hangs! This is now the one thing stopping me canning windows

---

### Post by Kilz on 2007-04-08
> **yelserpdog said:**
> I'm running an AMD 64 and can't get the 32 bit firefox working, it just hangs! This is now the one thing stopping me canning windows

First off what version of Ubuntu are you using? Second, please open a terminal and type in firefox32 , copy the contents of the terminal when firefox freezes and paste it into a reply here.

---

### Post by Kilz on 2007-04-08
> **webmaren said:**
> I finally fixed my 64bit version by taking one of the suggestions in the install thread

I force-architectured the flash install package and now everything works.

I am glad everything worked out without you reinstalling everything. If you ever need a java plugin we can get 32bit firefox working. Nspluginwrapper dose not support the java plugin.

---

### Post by kelsos on 2007-04-11
i have installed the flash plugin in 64bit firefox using the nspluginwrapper. well for a period of time everything was really fine, however after disabling the OnBoard soundcard (realtek alc850 on a nforce 3 based mobo) and i made the audigy 2 zs my default soundcard i stopped having sound form the flash plugin. I tried the some videoplaying plugins and the sound was just fine, i also tried a few solutions i found on various forums but nothing worked for me. I also tried starting firefox through console to see what i get during the video playing

It was something like this:

> LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/libflashplayer.so [/usr/lib/firefox/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/libflashplayer.so [/usr/lib/firefox/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:7965): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(npviewer.bin:7965): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: wrong ELF class: ELFCLASS64
ALSA lib ../../../src/pcm/pcm_dmix.c:862:(snd_pcm_dmix_open) unable to open slave....


the ALSA lib ..... unable to open slave.... line continues to repeat along with the video playback... does anyone knows anyway to fix the sound?

---

### Post by kelsos on 2007-04-12
Today after searching a little more... i tried to check the devices too. After searching for a while i realized that after disabling the OnBoard sound through BIOS my tvtuner was loaded as primary sound device... so it was impossible to have sound that way.. i tried removing the tvtuner and no sound plays just fine :)

---


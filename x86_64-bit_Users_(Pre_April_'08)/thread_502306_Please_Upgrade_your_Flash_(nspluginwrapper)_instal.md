---
title: "Please Upgrade your Flash (nspluginwrapper) install"
date: 2007-07-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kilz on 2007-07-16
Macromedia has [issued a security warning]("http://www.adobe.com/support/security/bulletins/apsb07-12.html") for Flash 9 for version 9.45 and below. It has to do with a possible key logging flaw. 
If you installed Flash with my install script or one of the other nspluginwrapper howto's before today (July 16, 2007)it is possible you have this version, there will be no automatic upgrade notifications.
[My script]("http://ubuntuforums.org/showthread.php?t=476924") will download and install the new version just by running it again. Here is also a link to the other [popular manual howto]("http://ubuntuforums.org/showthread.php?t=341727") if you prefer to do it that way.

---

### Post by sel on 2007-07-16
Thanks :)

---

### Post by jrocket on 2007-07-17
Thanks for your work.

---

### Post by jamesford on 2007-07-17
thanks but this versino of firefox only works now and then for me. like i play a youtube video, do other stuff and 30 mins later i wanna view some flash agian and it simply isnt loading

---

### Post by Kilz on 2007-07-17
Just to make sure its all good you may want to delete the 
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so  libflashplayer.so and flashplayer.xpt. Then rerun the script. Let me know if this helps and Ill change the script to delete the files before install.

---

### Post by crjackson on 2007-07-17
Worked like a charm.

---

### Post by jamesford on 2007-07-17
ok done that. working so far but its too early to tell. ill report back (hope i dont forget)

btw are u sure this really gets the latest flash player? about:plugins says Shockwave Flash 9.0 r48
i was messing around earlier with some manual install after i got the problem mentioned above and i could have sworn that about:plugins then said Shockwave Flash 9.0 r60

---

### Post by jamesford on 2007-07-17
nope the problem still persists. now all flash is dead, just empty white space where videos are supposed to be on youtube. restarting firefox and itll work

i notice npviewer.bin isnt in the task manager when this happens

---

### Post by Kilz on 2007-07-17
> **jamesford said:**
> nope the problem still persists. now all flash is dead, just empty white space where videos are supposed to be on youtube. restarting firefox and itll work

i notice npviewer.bin isnt in the task manager when this happens

It looks like you had a beta version of flash installed, did you at one time do a manual nspluginwrapper install? If so look for a flash plugin in your ~/.mozilla/plugins folder and remove it.

---

### Post by jamesford on 2007-07-17
yeah i alraedy looked there, its empty

---

### Post by Kilz on 2007-07-17
> **jamesford said:**
> yeah i alraedy looked there, its empty

is /usr/lib/mozilla-firefox a symlink to /usr/lib/mozilla on your system? there may be a  plugin hiding there if not. You might also want to search for the flash plugin to see where they are all hiding.

---

### Post by jamesford on 2007-07-17
[[img]http://bildr.no/thumb/86000.jpeg[/img]](http://bildr.no/view/86000)

usr/lib/mozilla-firefox is a symlink to /usr/lib/firefox

---

### Post by Kilz on 2007-07-17
> **jamesford said:**
> [[img]http://bildr.no/thumb/86000.jpeg[/img]](http://bildr.no/view/86000)

usr/lib/mozilla-firefox is a symlink to /usr/lib/firefox

I see you have 2 npwrapper.libflashplayer.so files installed. try and remove the symlink in your firefox/plugins folder

---

### Post by sel on 2007-07-18
Bump

---

### Post by jamesford on 2007-07-18
hey

i had to reinstall due to hdd failure and had to  buy new. installed using your script, and no other method this time. too early to tell but there shouldnt be any flash files anywhere other than those installed by your script. will let u know how it goes

---

### Post by jamesford on 2007-07-19
nope the problem is still there :(
this is after a fresh install where ive used no other flash install method other than your script

---

### Post by cprofitt on 2007-07-19
Adobe and flash are evil -- I refuse to run the product. Apple is about the only company I feel is worse than Adobe right now.

---

### Post by Kilz on 2007-07-19
Is this the happening on any specific site, do you have compiz, beryl, or any other desktop effects enabled? Have you ever had problems running Flash before? Why were you using the r60 beta version?

---

### Post by Kilz on 2007-07-19
> **PrivateVoid said:**
> Adobe and flash are evil -- I refuse to run the product. Apple is about the only company I feel is worse than Adobe right now.

Thats interesting, and in a perfect world no one would need proprietary "evil" software. But the world is far from perfect. No one is being forced to install flash, if you choose not to, its your choice.

---

### Post by jamesford on 2007-07-19
compiz-fusion, no trouble before the recent flash update. the r60 cos i did a manual install after i had the problems with your script, and r60 was th eonly one i could find
no specific site, happens on every site, like youtube for example

---

### Post by Kilz on 2007-07-19
> **jamesford said:**
> compiz-fusion, no trouble before the recent flash update. the r60 cos i did a manual install after i had the problems with your script, and r60 was th eonly one i could find
no specific site, happens on every site, like youtube for example

Please disable compiz and see if the problems continue.

---

### Post by fonsocm on 2007-07-19
I have the same problem in gnome with firefox and in kde with konqueror. In kde I'm using compiz fusion, in gnome no.

---

### Post by jamesford on 2007-07-19
nah i cant live without fusion for that long, it sometimes takes hours and hours for it to occur, thne id rather restart my firefox once in a while ;)

---

### Post by fonsocm on 2007-07-19
In konqueror if you wait 10 or 15 minutes, it works again without you have to close the browser.

---

### Post by Kilz on 2007-07-19
Ok, but it would be nice if someone would run without compiz who is experiencing the problem. That way we would know 100% for sure what needs to be fixed and where it needs to be reported to to be fixed.

---

### Post by fonsocm on 2007-07-19
I have the problem with and without compiz. In gnome I don't use compiz.

---

### Post by Kilz on 2007-07-19
> **fonsocm said:**
> I have the problem with and without compiz. In gnome I don't use compiz.

But, is it isntalled to that partition?

---

### Post by fonsocm on 2007-07-19
I have only two partitions / and /home.

I thought if I didn't have configured compiz in gnome, it didn't affect gnome. I don't use aixgl. I use xorg with gnome and xgl with kde.

---

### Post by Kilz on 2007-07-19
Im not sure, its just that the people having problems (the exact same one) both have compiz installed. While the vast majority of users have no problems.

---

### Post by jamesford on 2007-07-24
i dumped the whole flash crap for gnash. its not perfect but...ah well, one less proprietary piece of junk that doesent even come with 64 bit support natively

---

### Post by Midahed on 2007-07-29
I'm running Ubuntu 7.04 Feisty and the 64-bit version of Firefox 2.0.0.5.  I had flash working, having done a manual install of nspluginwrapper, etc., a few weeks ago.   I've just run your script and flash no longer works.

I suspect it might be something to do with the earlier version still being present, because if I do about: plugins I get two sections displayed that relate to Flash.  The first, at the top of then page, is for 9.0 r31 while the last entry in the list is for 9.0 r48.  Both reference the same filename - npwrapper.libflashplayer.so

Can anyone give me a clue as to how to fix this?

[Edit]  Just done a 'find' and there are two references to npwrapper.libflashplayer.so:-

/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so

Should one of these be removed?

Thanks,

Mike

---

### Post by michaelfitzi on 2007-07-29
OMG!! Thank you! Now as I am a complete idiot when it comes to Linux (just started 2 days ago), I need one of those for getting my video card configuration set up!!

Thanks again!!

---

### Post by Kilz on 2007-07-29
> **Midahed said:**
> I'm running Ubuntu 7.04 Feisty and the 64-bit version of Firefox 2.0.0.5.  I had flash working, having done a manual install of nspluginwrapper, etc., a few weeks ago.   I've just run your script and flash no longer works.

I suspect it might be something to do with the earlier version still being present, because if I do about: plugins I get two sections displayed that relate to Flash.  The first, at the top of then page, is for 9.0 r31 while the last entry in the list is for 9.0 r48.  Both reference the same filename - npwrapper.libflashplayer.so

Can anyone give me a clue as to how to fix this?

[Edit]  Just done a 'find' and there are two references to npwrapper.libflashplayer.so:-

/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so

Should one of these be removed?

Thanks,

Mike
What is the result of the command 
```
ls -al /usr/lib/firefox/plugins/
```
It should tell us what version we need to remove if any. Its also possible to have the wrapped plugin in ~/.mozilla/plugins

---

### Post by Midahed on 2007-07-30
Hi,

**[EDIT]  Please see my next post before taking too much notice of this!** :)

Here's the result of doing ls -al /usr/lib/firefox/plugins/

```
root@homepc:/# ls -al /usr/lib/firefox/plugins/
total 96
drwxr-xr-x 2 root root  4096 2007-07-30 10:48 .
drwxr-xr-x 5 root root  4096 2007-07-20 17:11 ..
lrwxrwxrwx 1 root root    36 2007-07-16 15:44 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2007-07-16 15:44 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2007-07-16 15:44 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2007-07-16 15:44 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2007-07-16 15:44 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2007-07-16 15:44 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2007-07-16 15:44 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2007-07-16 15:44 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 11072 2007-07-18 13:28 libunixprintplugin.so
lrwxrwxrwx 1 root root    37 2007-07-16 15:44 libvlcplugin.so -> ../../mozilla/plugins/libvlcplugin.so
lrwxrwxrwx 1 root root    42 2007-07-16 15:44 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root    43 2007-07-16 15:44 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root    42 2007-07-16 15:44 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root    43 2007-07-16 15:44 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root    39 2007-07-16 15:44 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root    43 2007-07-16 15:44 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root    44 2007-07-16 15:44 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root    40 2007-07-16 15:44 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
-rwxr-xr-x 1 root root 69696 2007-06-02 13:20 npwrapper.libflashplayer.so
```

Thanks for your help!

Mike

---

### Post by Midahed on 2007-07-30
Ooops....

It looks as though that was a false alarm.

After replying to your post, I revisited the Adobe page for testing Flash and Shockwave plugins [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

Flash is working fine - and it reports version 9.0.48.0.  Yet it wasn't working after running your script yesterday (and, yes, I did close and re-open Firefox several times).  The only thing I can think is that the system has now had a reboot since running the script.  Does that make any sense?

[Edit]  ...and about: plugins now only shows one entry for Shockwave Flash:-

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r48

Mike

---

### Post by Kilz on 2007-07-30
> **Midahed said:**
> Ooops....

It looks as though that was a false alarm.

After replying to your post, I revisited the Adobe page for testing Flash and Shockwave plugins [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

Flash is working fine - and it reports version 9.0.48.0.  Yet it wasn't working after running your script yesterday (and, yes, I did close and re-open Firefox several times).  The only thing I can think is that the system has now had a reboot since running the script.  Does that make any sense?

[Edit]  ...and about: plugins now only shows one entry for Shockwave Flash:-

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r48

Mike

Hard to tell, but you might want to remove that plugin in /usr/lib/firefox/plugins, its an older one and may cause problems down the road, if you want copy it some place just in case.

---

### Post by Midahed on 2007-07-30
Thanks for all your help!  Much appreciated.

I've renamed **/usr/lib/firefox/plugins/npwrapper.libflashplayer.so** just in case something stops working and I have to recover it.  I'll get rid of it altogether in a few days assuming there are no problems.

Mike

---

### Post by Midahed on 2007-07-31
Just to complete the story, renaming **/usr/lib/firefox/plugins/npwrapper.libflashplayer.so** caused Flash to stop working again, so I just replaced it with a symbolic link to the later version of the same file that your script installed in **/usr/lib/mozilla/plugins**

All working now.

Thanks,

Mike

---


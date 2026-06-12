---
title: "Firefox 3 RC1 with flashplugin in hardy AMD64"
date: 2008-05-29
forum: x86 64-bit Users
---

### Post by PeeZz on 2008-05-29
[B][SIZE=5]Firefox is available via the repositories. This guide isn't useful anymore. Sorry!
[/SIZE] 

[/B]Hi all

I'm about to write my first "tutorial". So if anything is missing, wrong, etc.. _PM me!!_ If something can be done in a faster/better way _PM me!!_ Or you could just answer to this post.

[SIZE=3]I also want to thank [Kilz]("http://ubuntuforums.org/member.php?u=78588") for _[this thread]("http://ubuntuforums.org/showthread.php?t=772490")_!![/SIZE]

**_STEP 1: backup your firefox profile_**

For this I refer to this website: _[Profile backup]("http://kb.mozillazine.org/Profile_backup")_;
Or this one if you just like to backup several parts of your profile: _[Transferring data]("http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox")_.

Your firefoxprofile is located in"HOME DIR"/.mozilla/firefox/.

I hope you can do this without my help.

_**STEP 2: download firefox 3 RC1**_

_[Download]("http://www.mozilla.com/en-US/firefox/all-rc.html")_ (<-- follow this link to download)

save the tar.bz2 in your home folder

_**STEP 3: remove FF3b5 and flash**_

So now you have to remove FF3b5.
I just deleted the /usr/lib/firefox 3.0 and /usr/lib/firefox-addons folder.
To do this, open a terminal
```
sudo rm -r /usr/lib/firefox 3.0
sudo rm -r /usr/lib/firefox-addons

```But the "firefox-gnome-support" also have to leave:
```
sudo apt-get remove
sudo apt-get purge firefox-3.0-gnome-support
```and flash too:
```
sudo apt-get purge nspluginwrapper
sudo apt-get purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper

```_**STEP 4: install FF3 RC1 and flash**_
Now open a new terminal and enter these lines:

```
sudo tar -jxvf firefox-3.0rc1.tar.bz2 -C /usr/lib/
sudo ln -s -T /usr/lib/firefox/firefox /usr/bin/firefox

sudo apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox/plugins/

```_**STEP 5: Final touch**_

I don't know how to do this in a terminal so..

Right-click on the Ubuntu-menu and chose "edit menus" (I don't know if this is correct in English, I'm using a dutch version..)

Then **Internet** and remove the Firefox 3 beta 5 entry.
Add a new item, call it whatever you want, I named it Firefox ;).
The command is just "firefox".
Click on the icon and type in: "/usr/lib/firefox/icons/mozicon128.png".

See attachments for step 5.

I hope this works for everyone using Hardy AMD64.

---

### Post by OoooMatron on 2008-05-29
Thanks, this looks good. I will give it a shot later.

however, i have to say i tried Linux Mint rc with the latest firefox and flash and it poofed out all the time.

---

### Post by Jouke74 on 2008-05-29
Uhh, why don't you remove Firefox 3.0 Beta5 itself through synaptic with sudo apt-get remove Firefox bla bla? 

Furthermore Flash is currently vulnerable for an exploit using SQL injection (just as a side-note).

---

### Post by PeeZz on 2008-05-29
> **Jouke74 said:**
> Uhh, why don't you remove Firefox 3.0 Beta5 itself through synaptic with sudo apt-get remove Firefox bla bla? 

Furthermore Flash is currently vulnerable for an exploit using SQL injection (just as a side-note).

I tried many different things.. install/remove/delete/reinstall/... and i ended up like this. :p.
You can try it with synaptic..
But I cannot say it'll work.

And I know about the exploit, but when there's a security update, it will be available as update, I think. This won't touch this tutorial.

---

### Post by philinux on 2008-05-29
Profile manager is neat.

[http://support.mozilla.com/en-US/kb/Managing+profiles](http://support.mozilla.com/en-US/kb/Managing+profiles)

---

### Post by Sef on 2008-05-29
Have you read this [sticky]("http://ubuntuforums.org/showthread.php?t=677396")?

Also I would provide how to do it through Synaptic.  It is much easier for some people to use it than the command line.

---


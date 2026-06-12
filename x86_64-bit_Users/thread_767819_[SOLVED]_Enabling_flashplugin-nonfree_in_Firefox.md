---
title: "[SOLVED] Enabling flashplugin-nonfree in Firefox"
date: 2008-04-25
forum: x86 64-bit Users
---

### Post by Johnny K on 2008-04-25
I'm using Hardy Heron. I am amazed by the progress gnash has made and congratulate the developers on all their great work. I can't wait until gnash reaches the point where it is just as, if not more functional than Adobe's flash plugin.

That being said, I would still at this time prefer to user Adobe's plugin. Although it is notoriously glitchy and under-developed, it can play most videos well.

I installed the package flashplugin-nonfree from the repositories, but Firefox still uses gnash to display flv videos like those on YouTube. How do I tell Firefox to use flashplugin-nonfree instead?

---

### Post by ajmorris on 2008-04-25
hi there,
if you go to about:plugins from Firefox's URL bar, does it say that both are installed?

---

### Post by FredB on 2008-04-25
```
sudo update-alternatives --config flash
```

---

### Post by Johnny K on 2008-04-25
> **FredB said:**
> ```
sudo update-alternatives --config flash
```
The result of that command was "No alternatives for flash." After restarting Firefox, gnash is still used.

> **ajmorris said:**
> hi there,
if you go to about:plugins (weird spacing because of smiley format) from Firefox's URL bar, does it say that both are installed? about:plugins contains an entry for libgnashplugin.so, but I do not see anything about Adobe flash.

---

### Post by Johnny K on 2008-04-26
I found the solution on [this Launchpad discussion]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/195422"). After installing flashplugin-nonfree, do
**sudo ln -s /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so /usr/lib/xulrunner-addons/plugins/**

---

### Post by Amish_Gramish on 2008-04-26
I don't even have the /var/lib/flashplugin-nonfree/ folder, is there any way to install it again?
/usr/lib/xulrunner-addons/plugins/ says that npwrapper.libflash.so and npwrapper.libflashplayer.so don't exist.  (Well, because they both lead to /var/lib/flashplugin-nonfree/ doesn't exist.)

---

### Post by Julius on 2008-04-26
remove gnash and then re-install flashplugin-nonfree?

---

### Post by Amish_Gramish on 2008-04-26
I tried to uninstall gnash, but it wasn't installed in the first place, and when I reinstalled flashplugin-nonfree, it made the folder, but not the files.

---

### Post by Johnny K on 2008-04-27
> **Julius said:**
> remove gnash and then re-install flashplugin-nonfree?

You don't need to uninstall gnash. I didn't, and was still able to use the Adobe flash plugin.

> **Amish_Gramish said:**
> I don't even have the /var/lib/flashplugin-nonfree/ folder, is there any way to install it again?
/usr/lib/xulrunner-addons/plugins/ says that npwrapper.libflash.so and npwrapper.libflashplayer.so don't exist.  (Well, because they both lead to /var/lib/flashplugin-nonfree/ doesn't exist.)

Go to Synaptic and install both **flashpulgin-nonfree** and **nspluginwrapper**, or just do from terminal:
*sudo apt-get install flashplugin-nonfree nspluginwrapper*

Then, do from terminal:
*sudo ln -s /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so /usr/lib/xulrunner-addons/plugins/*

If that doesn't work, let us know and we can try to figure it out.

---

### Post by scarboni on 2008-04-27
I have both flashplugin-nonfree as well as nspluginwrapper but i don't have any flash* (anything starting with the word 'flash') in /var/lib in amd64-bit hardy.  How can that be?

EDIT: So i apt-get remove flashplugin-nonfree then immediately apt-get install flashplugin-nonfree immediately after & now I get /var/lib/flashplugin-nonfree... trying the sudo ln -s /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so /usr/lib/xulrunner-addons/plugins/ & restarting firefox now...

FINAL UPDATE:  it worked!!  Thank you Johnny K.  May all your flash web pages display with precision!

---

### Post by sirzepp on 2008-04-28
I can't get flash working using any of these techniques.

I've completely deleted and re-installed firefox and then reinstalled flash...and nspluginwrapper.  I've created the symbolic link.  I still can't get flash to appear in my "about:plugins".

Bummer.

I'm thinking I'll just format and re-install with 32 bit Hardy.  This flash thing is quite frustrating(I KNOW it's not anyone in the open source community's fault...it's adobe).

thanks for any help you can offer.

---

### Post by Johnny K on 2008-04-28
> **sirzepp said:**
> I can't get flash working using any of these techniques.

I've completely deleted and re-installed firefox and then reinstalled flash...and nspluginwrapper.  I've created the symbolic link.  I still can't get flash to appear in my "about:plugins".

Bummer.

I'm thinking I'll just format and re-install with 32 bit Hardy.  This flash thing is quite frustrating(I KNOW it's not anyone in the open source community's fault...it's adobe).

thanks for any help you can offer.
Don't install 32-bit quite yet. We can figure this out.

When you try to create the symbolic link, do you get an error? Or is the link created as it should be?

Also, does the file /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so exist?

---

### Post by vishalrao on 2008-04-28
I did it the easy way...

To get Flash on Hardy amd64, I just visited a Flash-enabled page in Firefox where it asked to install the plugin and I clicked that (might have also clicked allow popup/install), I believe Ubuntu's FF plugin takes care of installing your choice of Adobe Flash or one of the other Free versions via the apt machinery... works fine for me.

---


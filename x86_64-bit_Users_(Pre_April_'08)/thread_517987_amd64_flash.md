---
title: "amd64 flash"
date: 2007-08-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Gremlinzzz on 2007-08-05
Just looking gutsy packages and found a flashplayer for amd64
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Fmultiverse%2Ff%2Fflashplugin-nonfree%2Fflashplugin-nonfree_9.0.48.0.0ubuntu4_amd64.deb&md5sum=8b1394475334e909061e4ab84d1d8401&arch=amd64&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Fmultiverse%2Ff%2Fflashplugin-nonfree%2Fflashplugin-nonfree_9.0.48.0.0ubuntu4_amd64.deb&md5sum=8b1394475334e909061e4ab84d1d8401&arch=amd64&type=main)
:guitar:
the list of whats in package
[http://packages.ubuntu.com/gutsy/web/flashplugin-nonfree](http://packages.ubuntu.com/gutsy/web/flashplugin-nonfree)

---

### Post by Gremlinzzz on 2007-08-05
> **Gremlinzzz said:**
> Just looking gutsy packages and found a flashplayer for amd64
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Fmultiverse%2Ff%2Fflashplugin-nonfree%2Fflashplugin-nonfree_9.0.48.0.0ubuntu4_amd64.deb&md5sum=8b1394475334e909061e4ab84d1d8401&arch=amd64&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Fmultiverse%2Ff%2Fflashplugin-nonfree%2Fflashplugin-nonfree_9.0.48.0.0ubuntu4_amd64.deb&md5sum=8b1394475334e909061e4ab84d1d8401&arch=amd64&type=main)
:guitar:
the list of whats in package
[http://packages.ubuntu.com/gutsy/web/flashplugin-nonfree](http://packages.ubuntu.com/gutsy/web/flashplugin-nonfree)

anyone uses the packages and it works for them report back so others will  know, i dont  have amd64
:guitar:

---

### Post by stmiller on 2007-08-05
Interesting! Includes

```
#

[dep] nspluginwrapper (>= 0.9.91.4-2ubuntu1) [amd64]
    A wrapper to run Netscape plugins on other architectures 
```

So the Ubuntu team has perhaps packaged x86 Adobe flash with nspluginwrapper in a single deb for 64bit users? This would be pretty sweet...

---

### Post by Kilz on 2007-08-05
> **stmiller said:**
> Interesting! Includes

```
#

[dep] nspluginwrapper (>= 0.9.91.4-2ubuntu1) [amd64]
    A wrapper to run Netscape plugins on other architectures 
```

So the Ubuntu team has perhaps packaged x86 Adobe flash with nspluginwrapper in a single deb for 64bit users? This would be pretty sweet...

[You dont have to wait for Gutsy, ]("http://ubuntuforums.org/showthread.php?t=476924")

---

### Post by allartk on 2007-08-19
installed, you have to run nspluginwrapper -v -a -i and it will work!

---

### Post by Kilz on 2007-08-19
> **allartk said:**
> installed, you have to run nspluginwrapper -v -a -i and it will work!

So its the 32bit Macromedia Flash plugin. Its not a 64bit plugin, otherwise you wouldnt need to use the wrapper.

---

### Post by Scotty562 on 2007-08-19
Ok, so I downloaded the flash plugin thing from synaptic and when I go to a webpage that has flash it asks me if I want to run the flash installer. I click next and the loader bar just goes back and forth across the screen seemingly endlessly. It just sits there and looks at me stupid. Am I missing something?

---

### Post by Kilz on 2007-08-19
> **Scotty562 said:**
> Ok, so I downloaded the flash plugin thing from synaptic and when I go to a webpage that has flash it asks me if I want to run the flash installer. I click next and the loader bar just goes back and forth across the screen seemingly endlessly. It just sits there and looks at me stupid. Am I missing something?

You might want to read this whole thread.

---

### Post by Scotty562 on 2007-08-20
> **Kilz said:**
> You might want to read this whole thread.

= P harsh

> **allartk said:**
> installed, you have to run nspluginwrapper -v -a -i and it will work!

That indeed did make it work.

Thanks for the info!

---

### Post by Kilz on 2007-08-20
> **Scotty562 said:**
> = P harsh


Not harh, accurate. This topic contains more than enough information to get flash running, As you proved. Heck it even contains a link to a setup script.
Secondly, it looks to me like you may be running Gutsy. As was the person who started this topic. The 64bit sub forum is for released versions. If you are running Gutsy please post in the Gutsy development forum.

---

### Post by penguin steve on 2007-08-20
how do i get the dependency "nspluginwrapper" i tried synaptic and its not there, i tried pasting the command "nspluginwrapper -v -a -i"  in the terminal like i saw in a previous post with no luck.

im a noob at linux.

thanks.

EDIT: sorry i think i found it.
EDIT 2: Yay! it works!

---

### Post by litemotiv on 2007-08-22
83mb of dependencies... :(

---


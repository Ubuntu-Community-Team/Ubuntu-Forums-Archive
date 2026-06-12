---
title: "64bit Flash in Jaunty - There, but not."
date: 2009-04-23
forum: x86 64-bit Users
---

### Post by joey-elijah on 2009-04-23
Okay, weird title. Sorry.

Basically iv'e installed Flash 64 bit thanks to the handy dandy scripts in the sticky.

Youtube doesn't give me the 'you have javascript turned off etc blah blah" error anymore, so Flash is installed and doing something... however all i'm getting are big blank white spaces inplace of the videos.

I've rebooted, restarted etc but still... they won't play in the browser. 

embedded videos also display just big blank white space. 

I think this is common?

---

### Post by ubuser_7 on 2009-04-23
which web browser are you using? 

mine works just fine on firefox, sea monkey, epiphany. however opera draws a big white space as you said. that has been the case with me for a long time now. jaunty didnt change anything for me. 
however I must say that my crashes have gone down after the adobe's 64 bit flash plugin. however it still has its own set of problems :(.

---

### Post by zero777zero on 2009-04-24
i had this issue

go to Tools->Add-ons

disable Iced-Tea and Flash 10.0 d21, leave only Flash 10.0 r22. maybe just disabling Iced Tea will work, idk.

---

### Post by brandon88tube on 2009-04-24
There really is no need to follow that sticky. Just go to a site that requires flash a bar will pop up asking you to install additional plugins. Click it and it will search for the plugins, install them and you're done. If you have any problems with it that is when I would suggest using the info from the sticky.

---

### Post by konungursvia on 2009-04-24
Rebooting the app sometimes solves this. In 64-bit, I sometimes notice flash disables multi-threaded sounds, and vice-versa.

---

### Post by cariboo on 2009-04-24
Flash 10.0 r22 is installed from the Jaunty repositories by default.

---

### Post by brandon88tube on 2009-04-24
> **cariboo907 said:**
> Flash 10.0 r22 is installed from the Jaunty repositories by default.

Really? I had to install the plugin still.

---

### Post by cariboo on 2009-04-24
I have to apologize, the version in the repositories is still 32-bit, I wasn't paying attetion when I installed it last night, I just assumed that because it had the right version number that it was 64-bit.

---

### Post by arashiko28 on 2009-04-24
I've just used it, by the first script of the sticky, followed the directions and tried youtube, works like a charm. try to restart or reinstall.

---

### Post by Arup on 2009-04-24
> **ubuser_7 said:**
> which web browser are you using? 

mine works just fine on firefox, sea monkey, epiphany. however opera draws a big white space as you said. that has been the case with me for a long time now. jaunty didnt change anything for me. 
however I must say that my crashes have gone down after the adobe's 64 bit flash plugin. however it still has its own set of problems :(.

Opera has worked fine here with the x64 Flash 10 alpha plugin, all I do is move the libflashplayer.so to /usr/lib/mozila/plugins and Opera picks the plugin up from there without any hitch. Youtube and all Flash sites work fine under Opera. Also the hang issue is far more minimal in Jaunty as compared to older releases when viewing Youtube etc. with Opera. The only time I saw Opera having problems was when Flash x32 was installed along with ndis wrapper.

---

### Post by joey-elijah on 2009-04-25
> **zero777zero said:**
> i had this issue

go to Tools->Add-ons

disable Iced-Tea and Flash 10.0 d21, leave only Flash 10.0 r22. maybe just disabling Iced Tea will work, idk.

That worked! Thanks!

---

### Post by leohartx on 2009-04-26
this is from cooliris, i solved flash problems by using this, everything is fine now
> 
64-bit Adobe Flash®.
Your distribution, especially if you are using Ubuntu, may use nspluginwrapper to run 32-bit Adobe Flash® because 64-bit Adobe Flash® is not officially released yet. 
Follow these steps: 
1.Download Adobe Flash® 10 Pre-release for Linux 64-bit to your desktop 
2.Create Mozilla's plugins directory if it doesn't already exist:
mkdir ~/.mozilla/plugins 
3.Extract the Adobe Flash® archive into the plugins directory:
tar -xzf ~/Desktop/libflashplayer*.so.tar.gz -C ~/.mozilla/plugins 
4.Restart Firefox 


here is the link for flash 10 pre-release :
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by foripepe on 2009-05-04
If you use Opera under Linux 64:
- Download the Flash:
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
- Untar it
- Copy to /usr/lib64/opera/plugins

---

### Post by foripepe on 2009-05-04
PS. Download this version from the bottom of the page:
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

---

### Post by Laibcoms on 2009-05-04
You can also follow this: [http://monespaceperso.org/blog-en/2009/05/01/how-to-install-flash-64-bit-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/01/how-to-install-flash-64-bit-on-ubuntu-jaunty-904/)

^_^  There, we should have enough information.  Maybe someone can create a new thread for sticky?

---

### Post by purplepup on 2009-05-06
Well, I have the same problem (youtube showing : Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. ) 
I'm running Kubuntu 9.04 amd64, recently upgraded from 8.10.

so I uninstalled any previous version using :
sudo apt-get remove flashplugin-nonfree flashplugin-installer
made sure no libflashplayer.so's lurked about, then copied the new libflashplayer.so to both ~/.mozilla/plugins and /usr/lib/mozilla/plugins

Restarted Firefox and still get the same message on youtube.
Any ideas?

If I can't get this working I think I'll install the 32bit 9.04 as I'm getting fed up with constant problems trying to get stuff to work in 64bit.

Thanks

---

### Post by stchman on 2009-05-06
Here is my 64 bit Flash 10 page.

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

Works well.

---

### Post by purplepup on 2009-05-06
Thanks stchman, I tried your steps, which are just a minor variation on previous steps taken, but the .so is still the same version I used and placed in the same dir, and on reloading FF it was exactly the same problem.

downloading Kubuntu 32bit now I think...

---

### Post by tonyshangrila on 2009-05-07
I tried the various solutions offered in this thread and none of them worked for me.  I followed the steps to install 64-bit flash, and it turned out I also needed to remove the open-source plugin(s):

```
sudo apt-get remove --purge swfdec-mozilla swfdec-gnome mozilla-plugin-gnash gnash
```

Found this tip under "Solution 2" here:
[http://www.ubuntugeek.com/fix-for-flash-not-working-after-jaunty-upgrade-64bit.html](http://www.ubuntugeek.com/fix-for-flash-not-working-after-jaunty-upgrade-64bit.html)

---

### Post by purplepup on 2009-05-07
Thanks tonys, I tried that too (and again just now) and nothing was removed or modified, and FF/flash still broken.

burning 32bit iso now....

---


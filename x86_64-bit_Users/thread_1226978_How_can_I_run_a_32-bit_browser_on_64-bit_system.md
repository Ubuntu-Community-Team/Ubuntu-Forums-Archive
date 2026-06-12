---
title: "How can I run a 32-bit browser on 64-bit system?"
date: 2009-07-30
forum: x86 64-bit Users
---

### Post by gshockxc on 2009-07-30
Still pretty much a noob, but I'm figuring out how to figure things out... if that makes any sense.  Anyway, I've been having some issues with my sound, then with browsers - Firefox and Konqueror.  At first, I thought it was me, and I just don't know what I'm doing.  That could still be the case, but I also found out that part of the issue with my browsers is because I'm running a 64-bit system, and there aren't a lot of flash plugins for those.  

I found some documentation about running 32-bit browsers on a 64-bit system.  But there wasn't enough information to tell me how to do it.  Can anyone help me get started?

Thanks.

---

### Post by Raffles10 on 2009-07-30
You don't need a 32 bit browser for flash.

Download flashplayer10 from the adobe site:

[flashplayer10]("http://labs.adobe.com/downloads/flashplayer10.html")

tar xf libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz

cd to the folder it extracted to

cp libflashplayer.so .mozilla/plugins/

You may have to create .mozilla/plugins/ if it doesn't already exist.

---

### Post by gshockxc on 2009-07-30
> **Raffles10 said:**
> You don't need a 32 bit browser for flash.

Download flashplayer10 from the adobe site:

[flashplayer10]("http://labs.adobe.com/downloads/flashplayer10.html")

tar xf libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz

cd to the folder it extracted to

cp libflashplayer.so .mozilla/plugins/

You may have to create .mozilla/plugins/ if it doesn't already exist.

Great, thanks for your help.  I still have some improvements to make, but that seems to resolve a large portion of the problems I'm having.

---

### Post by Rody on 2009-08-01
#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba [email]romeo.cioaba@spotonearth.com[/email]

echo "Stopping any Firefox that might be running"
sudo killall -9 firefox

echo "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper


echo "Installing Flash Player 10"
cd ~
wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)
tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 

echo "Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

# now doing some cleaning up:
sudo rm -rf libflashplayer.so 
sudo rm -rf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz



modified script from the sticky with  the new 64bit flash update from july 30

---

### Post by theremper on 2009-08-02
Here are the instructions I used to get the 64 bit version of flash really easy to follow.

[http://ubuntu64.today.com/](http://ubuntu64.today.com/)

---

### Post by gshockxc on 2009-08-02
> **theremper said:**
> Here are the instructions I used to get the 64 bit version of flash really easy to follow.

[http://ubuntu64.today.com/](http://ubuntu64.today.com/)

I followed the instructions, and got as far as Step 3.  When I double-click on the extracted file, nothing happens.

---

### Post by theremper on 2009-08-03
you can right click and click on open. I don't know it worked for me

---

### Post by gshockxc on 2009-08-03
> **theremper said:**
> you can right click and click on open. I don't know it worked for me

Yeah, I don't know either.  I had to follow Rody's instructions above.  That worked, but I'm not sure why.  Oh well, either way, I learned something new, so thanks for your help.

---

### Post by sdlinux on 2009-08-03
I got the flash player from the ubuntu repository this weekend and I haven't experienced any problems yet. Should I update my flash?

---


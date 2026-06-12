---
title: "HowTo: Spruce up your Desktop, for x64 users."
date: 2007-08-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by s_spiff on 2007-08-20
**HowTo: Spruce up Your Desktop for x64 users.**

*Ok firstly, this if for newbs like me who'll install Ubuntu and look at all the screen shots on Monthly Desktop Thread and drool, hoping that they can get theirs done up too! But since it ain't easy to go around looking for what you want, I thought I'll compile all the info in one place.*

**Note 1**: I'm using a [COLOR=RoyalBlue]AMD3500+ x64, on board NVidia Geforce 6100 graphic card[/COLOR] having [COLOR=RoyalBlue]Feisty Fawn[/COLOR] installed. So whatever I'm publishing here has worked on my system and [COLOR=Red]MAY/MAY NOT[/COLOR] work on yours. This howto is intended [COLOR=RoyalBlue]for x64 systems[/COLOR]. 

**Note 2**: I'm a noob [ read newb ] too, hence I wouldn't really be able to solve your issues if you had any, best to look up to the pro's in the community and irc channel [ #desktop-effects ]
[B]
Note 3[/B]: This is my first howto, so please be nice. And in case I've posted this is the wrong forum, moderators, apologize for the inconvenience  caused. 

**Part 1** :
[COLOR=RoyalBlue]Getting your Composite Manager[/COLOR] :
There are several out there, *compiz comes by default*, there's beryl ( which I prefer ) and then there is compiz-fusion ( which is the new one, and is a 'fusion' of beryl and compiz official ) and many more, but I'll stick to Beryl, Compiz and Compiz Fusion.

1. To get compiz running on your desktop, first enable the restricted driver for your graphic card by System > Administration > Restricted Drivers Manager.

           **a.** You may already have your drivers installed, or You may want to know how to go about *installing your driver*? 
Well there are several ways out there, most of them on Ubuntu forums itself, but I've tried about 3 methods, and the best one which worked for me was installing Envy, and using Envy installing my nvidia drivers. 

          **b.** *HowTo for Drivers:* [http://ubuntuforums.org/showthread.php?t=514161](http://ubuntuforums.org/showthread.php?t=514161)  
Worked for me initially, but somehow broke my GUI later on after a restart. But if you follow the thread, you'll see that it's working like a charm for most of the people.
    
    [http://ubuntuforums.org/showthread.php?t=496103&highlight=nividia ]("http://ubuntuforums.org/showthread.php?t=496103&highlight=nividia") 
Similar to above, but has a couple of instructions less, nonetheless is working for users.

   [ http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")  
This is a Python based script that'll install all the dependencies and the latest drivers. It called Envy, and don't go by the link, it installs ATI drivers too! Kudos to ***tseliot***.

Would suggest that any errors you get, please don't PM the pro's on the forum, instead create a new thread, that way, anyone else having the same issue can use the same process to resolve the issue as you did.

          **c.** Now that you have your drivers installed, first enable Desktop Effects by System > Preferences > Desktop Effects.
To enable the cube, open the terminal and copy paste : 
```

 gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
 gconftool-2 --type int--set/apps/compiz/general/screen0/options/number_of_desktops 1
 
``` More on this at : [http://ubuntuforums.org/showthread.php?t=359367](http://ubuntuforums.org/showthread.php?t=359367) 
Thanks to ***Amaranth*** for this. 

Another howto on this is at : 
    [https://help.ubuntu.com/community/CompositeManager/InstallingCompiz?highlight=%28compiz%29](https://help.ubuntu.com/community/CompositeManager/InstallingCompiz?highlight=%28compiz%29)
    
To edit the settings and key bindings for Compiz, go to :
    [https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz?highlight=%28compiz%29](https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz?highlight=%28compiz%29)

          **d.** Not satisfied with Compiz? How about *Compiz Fusion?*
    I've tried installing Compiz Fusion, again using two or three methods which I shall give the links to :

    Compiz-Fusion Mini-HowTo :

    [http://ubuntuforums.org/showthread.php?t=481615 ]("http://ubuntuforums.org/showthread.php?t=481615") 
Personally, not used this. You can give it a shot and post your issues on the same thread.

    [http://ubuntuforums.org/showthread.php?t=508769](http://ubuntuforums.org/showthread.php?t=508769)  
***CF-Installer/Updater Script***. This I think is a awesome method for a hassle free, newb friendly way to install compiz-fusion, and the author mentions the following : 
 > 
        It has been reported (and from personal experience too) that by following this way (either using my script or compiling by yourself) Compiz Fusion responses much better and it is way faster, comparing with installing it through repositories/.deb packages.
 The thread is pretty much regularly updated, and he keeps posting new versions of his script on a very regular basis. Thanks to ***ElemonGW*** for the same.

[http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314) 

Compiz-Fusion Guide on Ubuntu Feisty Fawn 7.04. Another howTo. Concise and uses precompiled .debs for the archtype. Thanks to ***Vorian*** for the same.

For ***ATI users***, there is a thread : [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385) 

Although, *I've never used it*, ATI users can give it a shot.

**          e.** Next option is ***Beryl***! And I love this, although the development has stopped, it is still supported, and I'm always attracted to this, don't ask why. There are several howto's for this, and since beryl has been put on the repo's, life has become much much more easy! One note of caution though : [COLOR=Red]Beryl and even Compiz for that matter are quite unstable[/COLOR]. So its quite possible that instead of making your desktop look great, it might break your system! So please be advised with regards to this.
    
    [http://ubuntuforums.org/showthread.php?t=357501](http://ubuntuforums.org/showthread.php?t=357501)  

One of the most concise howto's and gets the job done in just two cmdline   entries I think :P. Thanks to ***PriceChild*** for this.

    h[ttp://wiki.ubuntu.com/BerylOnFeisty](ttp://wiki.ubuntu.com/BerylOnFeisty)    

 A wiki entry, and also pretty much similar, and gives some troubleshooting tips. Would suggest you read the whole document before trying it out. Also, since the development has stopped, the latest version .2.1 has been uploaded in the repos, hence using this method will probably be the safest!.

    [http://ubuntuforums.org/showthread.php?t=279456](http://ubuntuforums.org/showthread.php?t=279456)  
Haven't used this method either, but looks great to me. Do try it out, and post your issues.

***Part 2 : **[COLOR=RoyalBlue]Building up on everything you've got.[/COLOR]*[B]
        a.[/B] Check this out : [http://ubuntuforums.org/showthread.php?t=515076](http://ubuntuforums.org/showthread.php?t=515076)  
This is the monthly thread for desktop screenshots. Posted in Ubuntu         Cafe. The screenshots there are posted along with the info such as what theme is being used, what wallpaper, fonts etc. and many times the links to them. So this is the first place you check out. 

**         b.** Kiba Dock - This is one of those launchers/panel programs. Pretty funky with all the effect. But again, pretty much under continous dev. As for installing it, x64 users have to install using SVN, and it pretty much does get installed. I had issues, as it was asking for a package called pygtk-2.0 which I couldn't find on the repo's and hence just dumped the idea of installing the dbs-plugins. I'll be working on that too, incase anyone knows how to compile from source, or has a deb for the package found at :   [http://www.pygtk.org//downloads.html](http://www.pygtk.org//downloads.html)  please post on this thread. 
Although there is a howTo, its broken, due to shift of the svn to launchpad. I kinda used noob logic and got kiba-dock, kiba-dock-plugins working atleast.

The howTo was made by PriceChild at [http://ubuntuforums.org/showthread.php?t=268645&highlight=kiba-dock](http://ubuntuforums.org/showthread.php?t=268645&highlight=kiba-dock)
The following howto is slightly changed. 
Run the following in the terminal. 
```
    
    sudo aptitude remove automake1.4
    sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev  libglitz-glx-dev  librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev

    mkdir Installs
    cd Installs

```Then run :
```

 svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk kiba-dock

```This will check out the svn and you'll see about 5 folders in the Installs/kiba-dock folder. 
    
Then via the terminal, make install for all the folders downloaded.
eg:
```

    cd ~/Installs/kiba-dock/kiba-dock
    ./autogen.sh
    make
    sudo make install

```Similarly go on for all the folders in the sequence : akamaru, kiba-dock, kiba-plugins, kiba-dbus-plugins, kiba-ephy-extension, kiba-gaim-plugin. And this will give you two new items in Applications>Accesrories, namely Kiba Dock, and Kiba Dock Settings. How to use is? Well check out : [http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Using_Kiba_Dock](http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Using_Kiba_Dock)   This gives a comprehensive introduction to all the features.

c. AWN - Avant-Window-Navigator. Another taskbar/launcher. Under development, but is ubercool to use. Installion is pretty much simple too! Again, for 64 users, you have to compile from svn. So open up that terminal and get copy pasting :P

```

sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common

``` This will get you all the dependencies. With that out of the way, run the following in the terminal :
```

cd ~/Installs/
bzr co http://bazaar.launchpad.net/~awn-core/awn/trunk avant-window-navigator
cd avant-window-navigator
./autogen.sh
make
sudo make install

```With that, you'll have a new entry in Applications > Accessories : Avant Windows Navigator.

For more info on this please go to : [http://awn.wetpaint.com/](http://awn.wetpaint.com/)    On the left, there are links to HowTo's, downloads, plugins etc.

There's also Affinity, but since I haven't installed it, I shall not write it up. Incase you do try it, and get it to work, do post the HowTo. But the previous Reacocard's howto's there for you to check out at : [http://ubuntuforums.org/showthread.php?t=385981&highlight=kiba-dock](http://ubuntuforums.org/showthread.php?t=385981&highlight=kiba-dock)

With this you have a comprehensive HowTo to make your desktop look stunning along with that effects, which none of ur MS using friends can brag of! Certain good links which you should go through are :

[Deviant Art]("http://www.deviantart.com/") : You get excellent wallpapers, icon sets, and even themes here!

[Ubuntu Forums - Desktop Effects & Customization]("http://ubuntuforums.org/forumdisplay.php?f=223") : This is where you'll get to see some of the best HowTo's and threads explaining how to resolve desktop effects related issues.

[Ubuntu Community Cafe]("http://ubuntuforums.org/forumdisplay.php?f=11") : Keep a track of the top most thread, the monthly Desktop thread, where users post their desktop screen shots. The guys here are pro's at this, and some of the desktop are simply stunning! 

[Gnome Look]("http://www.gnome-look.org") : The place where you'll get everything right from themes, gtk based, metacity, beryl, compiz and icon sets. Basically a one stop shot sorta thing :P

[Interfacelift]("http://interfacelift.com/") : This is another one of those places where you'll get stunning wallpapers! 

[GnomeStyle]("http://gnomestyle.blogspot.com/") : Someone's blog, but has pretty neat designs, and you can check them out. She/He has put it up for grabs, his own modifications and themes.


P.S. There may be mistakes / errors in this HowTo, please feel free to point out the mistakes along with the corrections, I shall duly edit the post. Also, I may have missed out on several programs out there, but thats because I haven't installed them, I shall add them as and when I have successfully used them on my system.

---

### Post by volksolwagen57 on 2007-08-22
I followed your how to and found the installation process pain free. I was amazed that the self-installer even included emerald. Awesome. So after a lot of activity in the terminal and 10-15 minute install, I don't think Fusion is working. I click on the Fusion icon in Applications and nothing happens. I tried to run it with Alt+F2 and still nothing. Did I miss something? Could you help me with this? Thank you for your time.

---

### Post by s_spiff on 2007-08-23
Well unfortunately, the two times that i did try compiz fusion, it didn't work for me as my desktop effects weren't gettin enabled. So I can't really comment on this. If you've used any of the threads that i've mentioned in the howto, you should follow those, you may find someone experiencing the same issue, or then just post your issue in the forums, or you can post here too, just include your terminal output/error.

---

### Post by bluemech on 2007-09-01
Hmm... nice guide. Beryl works fine. AWN works fine. Both on quite an underpowered system (graphics card wise).

A while ago though, I installed Kiba just to see how it compared against AWN. Unfortunately for me, I don't like it that much, and now I want to remove it from my system. However, it didn't come through a deb or Synaptic so I can't just apt-get my problems away.

How do you uninstall something you installed from make install?

EDIT: Never mind. Apparently the answer is a simple ```
sudo make uninstall
``` for every one I installed. :P

---


---
title: "Swiftfox and flash 64-bit not working"
date: 2009-04-14
forum: x86 64-bit Users
---

### Post by skintythe1andonly on 2009-04-14
I have installed swiftfox-athlon64 even though I am using a AMD turionX2. I read somewhere else that i was to do this.

I find swiftfox much faster but cannot get flash working. In firefox I had installed flash using the official 64-bit plugin available at [http://labs.adobe.com/technologies/flashplayer10/]("http://labs.adobe.com/technologies/flashplayer10/"), where I just copied the plugin to ~/.mozilla/plugins. This did not seem to work when I copied it to /usr/lib/mozilla/plugins like some other tutorials said to do

I am now trying to get this plugin working in swiftfox. This does not seem to work. I have made symlinks from ~/.mozilla/plugins/libflashplayer.so to /usr/lib/swiftfox/plugins and /usr/lib64/swiftfox/plugins/

The plugin still seems to work in firefox but it is not working in swiftfox. I am not getting told that it is not installed or anything. Where players would be are just blank. Is this because swiftfox is a 32-bit build as says on [http://getswiftfox.com/]("http://getswiftfox.com/")

Any ideas how best to install this?

---

### Post by mendres on 2009-04-14
I tried to install Swiftfox, because of your question. Just to see if Swiftfox really is faster than Firefox. I had the same problem with flash so far, this seems to be because it still is 32-Bit software, although I installed AMD64 package for my AMD Athlon64.

Now I'm running Swiftweasel, which is fully 64-Bit with PGO compiled. By the way, it is based on actual Firefox 3.0.8 builds, not like Swiftfox still messing around with 3.0.4 source.

---

### Post by skintythe1andonly on 2009-04-15
Can you point me in the direction of a .deb for the 3.08 build. The debs there seem to be be 3.01 versions.... even better if you could give me the repos. I cant seem to find one for intrepid.

If I have to build it, how do I go about it. I have the swiftweasel-3.0.8_amd-pgo_x86_64_ubuntu.tar.gz but am unsure how to install it

---

### Post by fooman on 2009-04-15
there is nothing to "build" or "install" there....all you have to do is right-click on the *swiftweasel-3.0.8_amd-pgo_x86_64_ubuntu.tar.gz* file and choose "extract here".

that will extract a directory called simply "swiftweasel".

in that directory,  you will find a *file* called simply "swiftweasel"....if you click on that it should open a dialog box asking how you would like to open the file....choose "run" and swiftweasel should open.  flash, java and everything else that worked in firefox,  seems to be working fine in swiftweasel for me.

i placed the extracted swiftweasel directory in my home folder and made an entry for swiftweasel in my applications > internet menu.

---

### Post by skintythe1andonly on 2009-04-15
Ah ok, I was wondering that. This is exactly how /usr/lib/swiftfox looked when I had it installed and was trying to get flash working. I actually tried moving it to /usr/lib to see if I could arrange it like a proper installed file but it did throw back some error when I tried to run it from there. This will do until intrepid repos gets put up or a proper deb but by then I will prob be using jaunty. It is much faster than firefox, I couldnt bear it anymore.

---

### Post by mnial on 2009-05-06
so, guys, did you get firefox plugins (such as flash & java) running under swiftweasel?

I followed [http://swiftweasel.wiki.sourceforge.net/Plugins](http://swiftweasel.wiki.sourceforge.net/Plugins) instructions, but... nothing =(

I'm running 9.04

---

### Post by skintythe1andonly on 2009-05-07
I have since switched back to 32-bit with my update to jaunty as there were some bugs with some other programs I was just not getting to the bottom of. I had it all working and that link was pretty much the same thing as what i did. I just did it using nautilus.

Where is your swiftweasel installed or are you using swiftfox? I could only get flash to work with swiftweasel. The version I used was pre-built, there seems to have been some updates since. I saved it to my home directory and used the launch script to start it. If i moved it to /usr/share/  it would fail.

To get flash working i created a link of /usr/share/mozilla/plugins/libflashplayer.so (are you using the official adobe plugin?) and placed it in the siwftweasel plugins folder in my home directory. Good luck

---

### Post by Nohajc on 2009-09-16
Well, since Swiftfox is in fact 32-bit (even in the amd64 package) I was able to setup flash in these two simple steps:
1) uninstall flashplugin-installer (the one from repositories, which is used for 64-bit Firefox)
2) Download .tar.gz from adobe and copy libflashplayer.so to /usr/lib/swiftfox/plugins

It works fine for me.
I believe it has something to do with the nspluginwrapper, because it should be disabled when running flash in a 32-bit browser.

---

### Post by marcoslai on 2009-09-27
Flash working fine in my Swiftfox 3.5.3-1 athlon64. 
I'm using Ubuntu 9.04 amd64,was struggling with flash after switched to Swiftfox,after few tried,I found the way:
-Remove 64bit libflashplayer.so.
-Download 32bit libflashplayer.so from Adobe site.
-Put it into usr/lib/mozilla/plugin
-Change its permission to - Owner : 'your username'(default is root),Access : Read & Write.
Done.

---


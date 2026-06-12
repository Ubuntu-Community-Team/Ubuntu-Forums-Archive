---
title: "Plugins for Seamonkey"
date: 2007-03-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by AllesMeins on 2007-03-05
Because the mozilla-suite in the rpositories is a little old (was it 2005 when they stopped the development?) i prefere to use seamonkey. Because of that i downloaded the x86_64-build from mozilla.com. My problem is: I can't get any plugins to work. I tried the plugins from mozilla-suite (64 bit), the plugins from my 32bit firefox, the files from the mozplugger package, self compiled mozplugger,...
The result is always the same for every installed plugin:

LoadPlugin: failed to initialize shared library /home/gedinixan/.mozilla/plugins/mozplugger.so [/home/gedinixan/.mozilla/plugins/mozplugger.so: wrong ELF class: ELFCLASS64]

Any ideas how to use plugins in an 64bit seamonkey?

---

### Post by Kilz on 2007-03-05
> **AllesMeins said:**
> Because the mozilla-suite in the rpositories is a little old (was it 2005 when they stopped the development?) i prefere to use seamonkey. Because of that i downloaded the x86_64-build from mozilla.com. My problem is: I can't get any plugins to work. I tried the plugins from mozilla-suite (64 bit), the plugins from my 32bit firefox, the files from the mozplugger package, self compiled mozplugger,...
The result is always the same for every installed plugin:

LoadPlugin: failed to initialize shared library /home/gedinixan/.mozilla/plugins/mozplugger.so [/home/gedinixan/.mozilla/plugins/mozplugger.so: wrong ELF class: ELFCLASS64]

Any ideas how to use plugins in an 64bit seamonkey?

Did you use my howto or script to install Firefox32 ?

---

### Post by AllesMeins on 2007-03-05
I've already a 32bit Firefox with plugins working (mostly) fine. But i'd like to use a seamonkey 64 bit as well. I'm aware that i won't be able to use all plugins (java, flash...) but at least a mplayer-plugin should be possible, shouldn't it?

---

### Post by Kilz on 2007-03-05
> **AllesMeins said:**
> I've already a 32bit Firefox with plugins working (mostly) fine. But i'd like to use a seamonkey 64 bit as well. I'm aware that i won't be able to use all plugins (java, flash...) but at least a mplayer-plugin should be possible, shouldn't it?

The reason I asked if you used my howto (linked in my signature) to set it up is so I could help you on how to make the plugins you already have installed work with seamonkey. Can you tell me what instructions or script you used?

---

### Post by AllesMeins on 2007-03-05
I'm afraid i'm not sure what i used. I used a howto, but I don't know if it was yours. But most likely it was this: [https://help.ubuntu.com/community/FirefoxAMD64FlashJava](https://help.ubuntu.com/community/FirefoxAMD64FlashJava)

---

### Post by Kilz on 2007-03-06
> **AllesMeins said:**
> I'm afraid i'm not sure what i used. I used a howto, but I don't know if it was yours. But most likely it was this: [https://help.ubuntu.com/community/FirefoxAMD64FlashJava](https://help.ubuntu.com/community/FirefoxAMD64FlashJava)

That helps, your 32bit firefox plugins are installed to /usr/local/firefox32/plugins. Depending where you installed seamonkey, or how you installed seamonkey it will be easy. 
If you went to the seamonkey project and got their installer, it installs to /usr/local/seamonkey.
We then remove the plugin folder in seamonkey
```
sudo rm -dfr /usr/local/seamonkey/plugins
```
Then we symlink in the plugins from firefox
```
sudo ln -s /usrlocal/firefox32/plugins /usr/local/seamonkey
```

Now each time you add a plugin to the 32bit firefox plugins direcory it will install it for both.

---

### Post by AllesMeins on 2007-03-06
Thanks for the help - it works just fine. But can you explain to me why it is working? Why does it use the 32bit plugins an what is wrong with the 64bit? At least seamonkey claims to be a x86_64 build.

---

### Post by Kilz on 2007-03-06
> **AllesMeins said:**
> Thanks for the help - it works just fine. But can you explain to me why it is working? Why does it use the 32bit plugins an what is wrong with the 64bit? At least seamonkey claims to be a x86_64 build.

If you got the package from the seamonkey site , it is advertised as a i686 version. i686 is 32bit. Even if it were there are no 64bit plugins for flash, java, or mplayer. 64bit browsers cant use 32bit plugins.
The best thats avilable for 64bit is nspluginwrapper, and that doesnt work with java, only flash and mplayer. There is a 64bit blackdown  java plugin , but it makes most modern browsers crash when loading applets.

---


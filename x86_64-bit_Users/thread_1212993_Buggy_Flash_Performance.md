---
title: "Buggy Flash Performance"
date: 2009-07-14
forum: x86 64-bit Users
---

### Post by Martin Marshalek on 2009-07-14
I just made the switch from my Intrepid 32bit to Jaunty 64bit and, although I really like Jaunty (especially the new default wallpaper and dust theme) I have been having problems with flash. 

First off, I installed flash through the ubuntu-restricted-extras package and its performance is intermittent. Often times Youtube works great as does Hulu and many other video sites but other times videos or flash items won't load at all. Also, flash seems to be laggy on sites like adobe's own site and syfy.com. Any suggestions? 

Thanks

---

### Post by masux594 on 2009-07-14
For flash i run this command and everything works fine.. ```
sudo apt-get install flashplugin-installer flashplugin-nonfree
```Sysc, A

P.s. Don't create a new thread about flash in jaunty.. There's a long list of thread with the same subject!

---

### Post by Martin Marshalek on 2009-07-14
Sorry about the new thread but, the ones I found contained issues I don't actually have. I was going to install the plugin that way now but, I'm not sure how to completely uninstall flash so I can reinstall.

---

### Post by masux594 on 2009-07-14
If u go to "about:plugins" of your firefox, u can see the pluging currently installed for flash.. then you can uninstall the plugin currently installed.. [U][URL="http://about%3Cb%3E%3C/b%3E:plugins"]
[/URL][/U] 
Sysc, A

---

### Post by Martin Marshalek on 2009-07-14
Okay, I now have Flash 64bit installed and I am looking towards finding Java 64, are the Icedtea OpenJDK packages (the ones in Add/Remove) in 64bit?

---

### Post by philinux on 2009-07-14
> **Martin Marshalek said:**
> Okay, I now have Flash 64bit installed and I am looking towards finding Java 64, are the Icedtea OpenJDK packages (the ones in Add/Remove) in 64bit?

I'd install sun-java6-jre  which will pull in sun-java6-bin and install the sun-java6-plugin. Seems to work well.

---

### Post by QIII on 2009-07-15
When you have installed Sun's Java, run the following in the terminal to make sure that it is preferred over OpenJDK:

sudo update-java-alternatives -s java-6-sun

---

### Post by Yellow Pasque on 2009-07-15
You're using the 32-bit version of Flash through ndiswrapper (this is the one installed by restricted-extras and flashplugin-installer). Uninstall that one and try the native 64-bit Flash plugin.

---


---
title: "Firefox Freezes. Often."
date: 2009-03-05
forum: x86 64-bit Users
---

### Post by Matthileo on 2009-03-05
Firefox often freezes (goes dark).
Sometimes when it does my other running programs also go dark, and my system monitor applet on my panel stops moving.

I ran firefox from the command line and after two major freezes it output npviewer.bin errors

I'm running Intrepid x64.
This is a serious issue and it's driving me crazy.

```
matt@matt-laptop:~$ firefox
ICEDTEAPLUGIN_DEBUG = (null)

(npviewer.bin:9985): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:9985): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:10419): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:10419): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
```

Just to see if it would help I uninstantiated flashplugin-nonfree
After that firefox still freezes but now I only get the IcedTea error.

```
matt@matt-laptop:~$ firefox
ICEDTEAPLUGIN_DEBUG = (null)
ICEDTEAPLUGIN_DEBUG = (null)
ICEDTEAPLUGIN_DEBUG = (null)
ICEDTEAPLUGIN_DEBUG = (null)
ICEDTEAPLUGIN_DEBUG = (null)
ICEDTEAPLUGIN_DEBUG = (null)
ICEDTEAPLUGIN_DEBUG = (null)
ICEDTEAPLUGIN_DEBUG = (null)
ICEDTEAPLUGIN_DEBUG = (null)
ICEDTEAPLUGIN_DEBUG = (null)
```

---

### Post by x33a on 2009-03-05
try uninstalling icedtea too. or disable the plugin.

---

### Post by Matthileo on 2009-03-05
> **x33a said:**
> try uninstalling icedtea too. or disable the plugin.

I tried to disable the plugin, but still got the error.
I'll try uninstalling it later as a test, but I kinda need java.

---

### Post by x33a on 2009-03-05
install the sun java plugin instead of icedtea.

---

### Post by Matthileo on 2009-03-05
> **x33a said:**
> install the sun java plugin instead of icedtea.

Is it in apt, or will I have to download it manually?

If it is in apt, what's the package called?
If not, where can I get it?

EDIT

Confirmed, the issue is with IcedTea.

EDIT::EDIT

It seems that the sun plugin isn't available for x64...
At least not in the repos...

---

### Post by x33a on 2009-03-05
you can install it through synaptic.

search for java in synaptic and install the sun-java-6 plugin.

---

### Post by Matthileo on 2009-03-05
> **x33a said:**
> you can install it through synaptic.

search for java in synaptic and install the sun-java-6 plugin.

It isn't there.
It looks like it's only available for 32bit.

---

### Post by x33a on 2009-03-05
hmm.. i don't notice you were using 64 bit version, but you can try this:

[http://ubuntuforums.org/showthread.php?t=1016014](http://ubuntuforums.org/showthread.php?t=1016014)

---

### Post by Matthileo on 2009-03-05
> **x33a said:**
> hmm.. i don't notice you were using 64 bit version, but you can try this:

[http://ubuntuforums.org/showthread.php?t=1016014](http://ubuntuforums.org/showthread.php?t=1016014)

Thanks.
It seems to have worked...

Firefox still freezes some time though...
I'm back to thinking it's an issue with flash.

---

### Post by x33a on 2009-03-05
you can try creating a new profile. load all your addons and plugins one-by-one, and see which is causing the problem.

to create a new profile
```
firefox -ProfileManager
```

---

### Post by jwbrase on 2009-03-06
I had similar problems (though for me the browser would just CTD randomly), and from what I understand, it's a known and widespread issue that Firefox and its Flash plugin cause lots of problems on 64-bit Ubuntu. I think people have managed to solve the problem, but I never really managed to get Firefox working. I found it much simpler to switch to Opera, which hasn't yet crashed on me once that I can recall, and which I have found I like better than Firefox even when Firefox *is* working properly.

---


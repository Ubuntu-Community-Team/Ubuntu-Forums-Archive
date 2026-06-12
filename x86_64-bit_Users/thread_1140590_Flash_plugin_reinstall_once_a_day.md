---
title: "Flash plugin reinstall once a day"
date: 2009-04-27
forum: x86 64-bit Users
---

### Post by ryanferreri on 2009-04-27
Running Jaunty x64...

I tried several methods for getting Flash to work, and the one that seems to have worked is simply pasting the x64 libflashplayer.so in ~/.mozilla/plugins. The catch is that it will work for a while (usually a few hours, or 2 or 3 opens/closes of Firefox), then it will stop working (gray/black/blank screen on online Flash videos). So far the "fix" has been to delete the .mozilla folder, restart Firefox, and put the libflashplayer.so back in when .mozilla is created. 

I'm puzzled as to why it would stop working after working beautifully for a while.

Any ideas?

---

### Post by John.Michael.Kane on 2009-04-27
I am not sure why you have to reinstall flash every few hours.

Was any other methods of installing flash used before simply placing the libflashplayer.so in ~/.mozilla/plugins.

---

### Post by ryanferreri on 2009-04-27
I have tried flashplugin-nonfree before this, but I removed it and nspluginwrapper before just adding the libflashplugin.so.

---

### Post by ryanferreri on 2009-04-28
Ok I found a solution to the issue that seems to work, but again, I'm not sure why it keeps coming back...

In ~/.mozilla/firefox/randomchars.default there's a file called pluginreg.dat. It says it's auto-generated and that it shouldn't be edited. Nonsense!

At the top of the file is this little snippet:

```
[PLUGINS]
/usr/lib/adobe-flashplugin/libflashplayer.so:$
:$
1233633833000:1:5:$
Shockwave Flash 10.0 r22:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
/usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so:$
```

I changed that second line in the path to point to ~/.mozilla/plugins/libflashplayer.so and it seems to work. But that got me thinking: if the file is telling me not to edit it, my change will probably be replaced at some point. So I checked the timestamps and sizes of the libflashplayer.so files in both directories and found that they are different (A-HA!), backed up the one in /usr/lib/adobe-flashplugin and copied the one from ~/.mozilla/plugins in there. Hopefully this does the trick.

---


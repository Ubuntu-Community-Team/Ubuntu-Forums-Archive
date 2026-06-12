---
title: "Opera 9 (32-Bit) ... any chance to get video going ... ?!"
date: 2006-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Stormbringer on 2006-08-12
Hello.

So I installed the 32-Bit version of Opera 9.01 in order to have a secondary browser where all the bells and whistles that don't work in Firefox 64-bit will finally work ---

- I got Flash working by downloading the player and copying the required files into Opera's plug-on directory.
- I got JAVA working in Opera by simply installing ia32-sun-java5-bin and setting up the correct JVM path in the preferences.

... but ...

What about video playback?

- The 32-Bit plugin for VLC gets refused (Opera reports the pluggie as banned).
- The 32-Bit plugin for mplayer loads (I needed to copy the 32-bit libxpcom.so and libxpcom_core.so libraries, ripped out of 32-bit Firefox, into /usr/lib32 to make it work) ... but does a crash and burn as I try to watch a streaming video.

Hell ... I hate this "everlasting construction area" ...

Anyone got an idea on how to get streaming video going in Opera?

Thanks for any helpful ideas.

-Storm

---

### Post by adka on 2006-12-02
(Anyone got an idea on how to get streaming video going in Opera?)

I know the gxine plugin works well streamming video with opera.  However im only running 32 bit on 32 bit... 

(I got Flash working by downloading the player and copying the required files into Opera's plug-on directory.)

Opera should locate all the installed plugins by its itself.  You shouldn't have to set plugin paths, or pull the plugins from firefox plugin dir to opera plugin dir.   

Hope this helps

---


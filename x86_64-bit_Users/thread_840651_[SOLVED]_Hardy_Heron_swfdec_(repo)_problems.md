---
title: "[SOLVED] Hardy Heron swfdec (repo) problems"
date: 2008-06-25
forum: x86 64-bit Users
---

### Post by Tom Mann on 2008-06-25
Hi Guys

I am trying to get swfdec working on my 64-bit Hardy Heron. I have tried apt-get install swfdec-common form the command line, and installing swfdec via Firefox's autoinstall.

I've started to debug what hasn't happened and found that

```
sudo ln -s /usr/lib/swfdec-mozilla/libswfdecmozilla.so /usr/lib/firefox-3.0/plugins
```

has brought the plugin to life, however I have no sound.

Anyone have any experience with this and what I may need to do?

Thanks,
Tom

EDIT: Removed the shortcut I added as it comes up without it now, Firefox must not have restarted properly, but still no sound...

---

### Post by Tom Mann on 2008-06-25
Never mind - I was using the rt kernel, and added --realtime=TRUE to my /etc/init.d/pulseaudio, run ```
/etc/init.d/pulseaudio stop; sudo killall pulseaudio
``` then ```
/etc/init.d/pulseaudio start
```

Now it works :D

---


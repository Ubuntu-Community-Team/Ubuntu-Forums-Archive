---
title: "communication error.  (Code C)"
date: 2009-04-04
forum: x86 64-bit Users
---

### Post by old_salt on 2009-04-04
Cannot establish communication with the video server.

(Code C)

I get this error only on 64 bit versions of E/M/K/Ubuntu when trying to view videos from local news station. Seems that any video except Flash has this issue.

Any ideas? The link I'm going to is this

[http://www.wral.com](http://www.wral.com)

Thanks

---

### Post by cariboo on 2009-04-04
I just tried you link and it works for me. Which version of flash are youy using? I'm using the 64-bit alpha from [here]("http://labs.adobe.com/downloads/flashplayer10.html"). Just download the file and then double click it to extract libflashplayer.so. Once extracted copy the file to /usr/lib/mozilla/plugins:

```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins
```

jim

---

### Post by old_salt on 2009-04-05
Thanks cariboo907, that did the trick.

How may I recommend or suggest this get added to the Ubuntuguide specifically for 64 bit versions?

I'm perplexed why the install from the repos doesn't already do this.

Thanks,):P

---


---
title: "Install Flash 10 on 64 bit Hardy??????"
date: 2008-12-19
forum: x86 64-bit Users
---

### Post by stchman on 2008-12-19
I have looked all over and there seems to be no easy way to install Flash 10 in 64 bit Hardy.

---

### Post by Spr0k3t on 2008-12-19
1: download the tar.gz file.
2: copy the libflashplayer.so to ~/.mozilla/plugins/
3: restart firefox.
4: ???
5: WIN!

It really doesn't get much easier outside of someone packaging the plugin for you.  Here's the link to the file: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by cariboo on 2008-12-20
You can download the 64bit flash [here]("http://labs.adobe.com/downloads/flashplayer10.html").

Jim

---

### Post by jmszr on 2008-12-20
Edit: Above advice supersedes what I had.

---

### Post by Kilz on 2008-12-20
> **stchman said:**
> I have looked all over and there seems to be no easy way to install Flash 10 in 64 bit Hardy.

The little white box with Go beside it in the upper right hand corner may have helped you. You could also have read the sticky posts.

---

### Post by lazman on 2008-12-20
I just installed Ubuntu 8.1 and went to add/remove and typed in flash player and installed it with that. It seems to be working great. YouTube works. 

I do have a question however, I have been reading on these forums about the flash player and 64 bit Ubuntu and have seen this hardy and gusty. What is hardy and gusty? I'm assuming it's a stable(hardy) and beta(gusty) release but, I did not see any mention of hardy or gusty on the download page. Some clarification please?

As you can tell I'm totally new to linux and ubuntu, but I'm totally impressed so far!

Thanks
~laz

---

### Post by danirolo7 on 2008-12-20
Hi, there's a script that automatise the whole thing,even you can make it with a single command:

```
wget http://queleimporta.com/downloads/flash10_en.sh && sudo chmod +x flash10_en.sh && sudo sh ./flash10_en.sh
```

Remember to uninstall every previous version of flashplayer.

[http://dabuntu.wordpress.com](http://dabuntu.wordpress.com)

---

### Post by hotbit on 2008-12-20
Hardy / Flash 10 / Firefox 3.0.5

Flash 10  - does it work properly?

My Firefox has updated to 3.0.5 a few days ago and now there are a few problems with flash.

I had nspluginwrapper (flash9) in previous ver of Firefox; It worked with updated firefox as well, but sites like youtube and veoh did not work in FULL screen mode any more. Than I tried Flash 10. It works, as well in full screen mode, but screen is blinking - for example weoh.com - where is sth like menu in flash window.

I wonder if the problem is with flash plugins or firefox.

---

### Post by slideking on 2008-12-20
> **hotbit said:**
> Hardy / Flash 10 / Firefox 3.0.5

Flash 10  - does it work properly?

My Firefox has updated to 3.0.5 a few days ago and now there are a few problems with flash.

I had nspluginwrapper (flash9) in previous ver of Firefox; It worked with updated firefox as well, but sites like youtube and veoh did not work in FULL screen mode any more. Than I tried Flash 10. It works, as well in full screen mode, but screen is blinking - for example weoh.com - where is sth like menu in flash window.

I wonder if the problem is with flash plugins or firefox.

In my case flash sites worked ok but firefox kept crashing every minute or two.

It's the 64bit flash plugins that cause the problem and not firefox.

---

### Post by 73ckn797 on 2008-12-20
> **lazman said:**
> I do have a question however, I have been reading on these forums about the flash player and 64 bit Ubuntu and have seen this hardy and gusty. What is hardy and gusty? Some clarification please?

As you can tell I'm totally new to linux and ubuntu, but I'm totally impressed so far!

Thanks
~laz

Gutsy was an earlier version of Ubuntu then came Hardy 8.04 which is still the current Long Term Support (LTS) version of Ubuntu. Support through 2011.

---

### Post by 73ckn797 on 2008-12-20
> **stchman said:**
> I have looked all over and there seems to be no easy way to install Flash 10 in 64 bit Hardy.


I have installed the Flash non-free plugin from the repositories into 64 bit Intrepid and all works just fine.

---

### Post by stchman on 2008-12-20
> **Spr0k3t said:**
> 1: download the tar.gz file.
2: copy the libflashplayer.so to ~/.mozilla/plugins/
3: restart firefox.
4: ???
5: WIN!

It really doesn't get much easier outside of someone packaging the plugin for you.  Here's the link to the file: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

That was pretty easy.  Thanks.  Flash 10 works very well.  No more annoying menu coverup.

---


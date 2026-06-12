---
title: "Flash no longer working in Firefox"
date: 2007-05-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by sprice on 2007-05-06
I initially had been running Firefox 32bit so I could use flash but then I used a tutorial that used nspluginwrapper on the plugins so I could see flash in 64bit firefox. Everything worked fine.. until now.

I'm not sure what I've done but flash doesn't work in either 32bit or 64bit firefox. typing 'about plugins' in both reveals that they are both installed, which is very strange.

any help is appreciated.

---

### Post by Kilz on 2007-05-07
Nspluginwrapper is not compatible with Firefox32. You must remove it and the files it makes for Flash to start working again in Firefox32 . Did you manually install nspluginwrapper?

---

### Post by sprice on 2007-05-07
Yes I manually installed it.

I don't want to run firefox32... i was happy using the 64bit version once I got flash working for it.

---

### Post by sprice on 2007-05-07
I ended up wiping off firefox32. I was about to do the same with firefox64.

I noticed that flash was working in epiphany so i wiped my /firefox/plugins directory and then made a link to it with /mozilla/plugins and everything works.

i'm still baffled... though satisfied.

---

### Post by Kilz on 2007-05-07
> **sprice said:**
> I ended up wiping off firefox32. I was about to do the same with firefox64.

I noticed that flash was working in epiphany so i wiped my /firefox/plugins directory and then made a link to it with /mozilla/plugins and everything works.

i'm still baffled... though satisfied.


Firefox32 is installed by a .deb file. You could just as easily uninstalled the package with apt or synaptic. I am also glad the 64bit version is working for you. Have you tried the java plugin on the 64bit browser? How about the mplayer plugin?

---

### Post by rmfought on 2007-05-08
This happened to me too, I just recopied the nspluginwrapper-created file to the mozilla-firefox  plugin folder again and it magically started working again.  Weird.

---


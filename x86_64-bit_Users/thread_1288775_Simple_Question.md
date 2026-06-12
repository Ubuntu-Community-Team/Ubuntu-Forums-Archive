---
title: "Simple Question"
date: 2009-10-11
forum: x86 64-bit Users
---

### Post by BigCityCat on 2009-10-11
I am using 64 bit. There is one site that Java will not completely load. I'm wondering if anyone else can get this site to work and if there is anything I can do to make it work.

Here is the site. I'm trying to play spades but not all the page will load.

[http://www.games.com/game/spades](http://www.games.com/game/spades)

If not maybe someone knows a good way to play spades online.

---

### Post by falconindy on 2009-10-11
It's using Flash not Java -- and it loads just fine for me using Chromium. Are you using the 64 bit flash plugin from Adobe Labs? Have you tried launching your browser from a terminal window to see if there's any debug/error output when you try and load the game?

---

### Post by BigCityCat on 2009-10-11
No, how do you run the browser from a terminal? What is chromium? Can you help me with your suggestions?

---

### Post by BigCityCat on 2009-10-11
Not sure what my plugin is.

---

### Post by BigCityCat on 2009-10-11
It says shockwave 10.0 r32.

---

### Post by falconindy on 2009-10-11
Assuming you're running Firefox, open a terminal and then type 'firefox &' (without the quotes). Leave the terminal window open and any errors, warnings, or other miscellaneous debug output that gets thrown by Firefox will be printed to that window. This applies to any program and can be useful for troubleshooting.

Sounds like you're already using the 64-bit flash plugin. It does mention it by name: 'libflashplayer.so', right?

[Chromium](http://code.google.com/chromium/) is a browser in development. I used to think Firefox was fast. Then I met Chromium. It's still very much in development and is missing a lot of features, though.

---

### Post by BigCityCat on 2009-10-11
maybe my firefox 3.5 is 32bit.

---

### Post by BigCityCat on 2009-10-11
okay the only output is

[1] 14803

---

### Post by BigCityCat on 2009-10-11
not sure about libflashplayer.so. How can I check?

---

### Post by falconindy on 2009-10-11
> **BigCityCat said:**
> okay the only output is

[1] 14803
Not useful. The Help->About window will tell you whether your Firefox is x86_64 (64-bit) or i386/i686 (32-bit). I suspect if you've been trying to run a 32-bit browser with a 64 bit flash plugin, this wouldn't be the first time you've had problems with a flash based site.

Just tested on 64-bit Firefox 3.0.14, works fine.

---

### Post by BigCityCat on 2009-10-11
This is what it says.

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.3) Gecko/20090910 Ubuntu/9.04 (jaunty) Shiretoko/3.5.3

---

### Post by BigCityCat on 2009-10-11
I guess I'm just having a problem with this plugin. I did the tutorial on this site in the 64 bit section with regards to 64bit flash. Not sure if I got it right cause its not completely working. kit does work on some things just not completely. when I test it on adobes page it asks me to install missing plug in.

---

### Post by BigCityCat on 2009-10-11
I have 2 amd processors, and nvidia graphics if that helps.

---

### Post by falconindy on 2009-10-11
CPU/gfx are irrelevant. I don't know offhand which tutorial you followed. There's a few that involve unnecessary scripts. All you need to do to install 64-bit flash in Firefox is this:

1) Download the [64-bit alpha plugin](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz) from Adobe Labs.
2) Make a directory: $HOME/.mozilla/plugins
3) Extract the contents of the archive you downloaded to the directory you just made.
4) Restart Firefox (if it was running when you did this).

Is this the only site you have issues running Flash on?

---

### Post by BigCityCat on 2009-10-11
is the command mkdir mozilla/plugins

and does it matter if the browser is being called shiretoko

---

### Post by falconindy on 2009-10-11
> **BigCityCat said:**
> is the command mkdir mozilla/plugins

and does it matter if the browser is being called shiretoko
Shiretoko is the development name for 64-bit Firefox 3.5. The name doesn't matter because the code behind it looks an **awful** lot like Firefox...

The command is ```
mkdir $HOME/.mozilla/plugins
```

---

### Post by bosbeemer on 2009-10-11
try this thread ..
[http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

---

### Post by BigCityCat on 2009-10-11
it's installed, not workin yet.

---

### Post by BigCityCat on 2009-10-11
> **bosbeemer said:**
> try this thread ..
[http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

did all of that. Still not working.

---


---
title: "Help with idesk on Afterstep 2.0"
date: 2005-07-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by docmur on 2005-07-05
Hello

I'm not new to idesk and have started work on a new theme.  However I'm having diffuculty getting the theme to work right.  I have as of now 2 icons.  One which links to XMMS and one to my Home directory.  The problem that I'm having is that are appearing transparent on the background.  I want to be 90 opaque.  The second problem is that I when I click them the system open Gnome and loads gnome.  I doesn't even load the app.  So What I need help with is.

1.  How to I make the Icons much more opaque 
2.  How to I make it so when I click the icons they open only there assigned app's     and not load gnome.  

To help you guys out I will post the files that I use for the Icon's and the Config file for idesk.  

Thanks for any help u can give.

---

### Post by FluffyElmo on 2005-07-05
You'll probably get more help on a more general forum, such as 'Desktop Support' or 'Other Applications'. This forum doesn't get as much traffic as others and is best for issues specific to amd64.

That said, it seems you are calling nautilus for your shortcuts which is why gnome is loading. Instead, try linking directly to the application or for browsing files install a lightweight file browser like 'xfe'.

In other words maybe try: *Command[0]: /usr/bin/xmms* instead of *Command[0]: nautilus /usr/bin/xmms* and *Command[0]: xfe /home/docmur* instead of *Command[0]: nautilus /home/docmur*.

As for icon transparency, there is a transparency option in your ideskrc.txt (*Transparency: 150*) file, try changing the value to a lower (or higher?) number.

I don't use iDesk myself so these are guesses...but they seem sensible to me:)

---

### Post by docmur on 2005-07-05
Well if I can just ask what is nautilus??

---

### Post by FluffyElmo on 2005-07-05
Sure, and I should apologise, I didn't mean to be so abrupt earlier. You can ask anything you want and I'll do my best to help. There's just less traffic here though so fewer people who might know what you need.

Basically, nautilus is the gnome file manager/browser. It's also the primary part of gnome you see as it manages the desktop, runs scripts, etc. So when you run nautilus, gnome starts because nautilus pretty much is gnome.

xfe is meant as a lightweight replacement for much of nautilus, it doesn't show thumbnails in directories for instance but then it uses far fewer resources. You can install it by enabling Universe in */etc/apt/sources.list* and typing *apt-get install xfe* (or use Synaptic). 

You can then use it by relacing 'nautilus' with 'xfe' in your scripts. There are probably other lightweight file managers out there, this is just the one I know of offhand.

---

### Post by docmur on 2005-07-06
Well now that I think of it how would I uninstall gnome and kde.

---

### Post by FluffyElmo on 2005-07-06
That's actually more than I know...you would have to install another window manager like icewm and configure gdm to use it. Then you could likely just use Synaptic to remove gnome/kde...though if you're using a different window manager then they'd just be using disk space, shouldn't affect performance.

A search of these forums for 'icewm' should probably turn up more information, I've never used it myself so just know the theory :(

---

### Post by docmur on 2005-07-07
Okay last question. 

I got Gnome uninstalled but now my question is how do I save what I've done to fluxbox so that it loads when I load fluxbox.  Heres what I did.

1.  Set a background that I want to appear every time I start fluxbox it's called think_linux.jpg and it in ~/think_linux.jpg

2.  Load my idesk theme.   On startup 

Thanks

---

### Post by FluffyElmo on 2005-07-07
I don't know, I haven't used fluxbox...a quick search turned these up thouigh which may help.

1. [http://fluxspace.sourceforge.net/](http://fluxspace.sourceforge.net/) 

2. [http://fluxbox.sourceforge.net/docs/en/faq.php#startup](http://fluxbox.sourceforge.net/docs/en/faq.php#startup)

---


---
title: "Flash no sound"
date: 2008-06-06
forum: x86 64-bit Users
---

### Post by peakshysteria on 2008-06-06
For some unknown reason I've suddenly lost all sound from flash sites. Sound is working for music and movies. The problem seems to be with flash alone. I know this have been up in the forums before a few times. But I can't find the threads. Anyway, only new thing in my end is that I've checked hardy-proposed. And this morning there there where an java-6 update though I use Icedtea as default for Firefox.

edit:

found temporary fix:

sudo update-alternatives --config

and:

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/bin/gij-4.2
 +        2    /usr/lib/jvm/java-6-openjdk/jre/bin/java

Press enter to keep the default[*], or type selection number: 

______

Seems IcedTea is gone. Not sure why. It's installed according to synaptic. How can this be??

---

### Post by Plasma_NZ on 2008-06-06
I'll add my 2-cents to attempt to fix your sound.. More or a work-around kinda

Menu > System > Pref's > Sound 

Set all to alsa

Change to the "sounds" tab - and untick ESD - Reboot - "might" fix your problem...

Alternatively if you have 2 soundcards, u should check to see which cards are seen...

```
asoundconf list
```

this should list your cards, to set a certian card as default do..

```
 asoundconf set-default-card name_as_listed_with_previous_card
```

u might need to reboot once or twice for it to take effect..

Hope this helps..

---

### Post by peakshysteria on 2008-06-06
Hmm, I got the sound back by:
```
sudo update-alternatives --config

```
And choosing the other one than the one which is marked as default. But the java I have installed by default is iced tea. Which isn't in the list ehn running the sudo update-alternatives --config command.

It seems that an update have somehow overwritten and removed IcedTea. Which by the way still is marked as installed in synaptic.

So thanks for the trouble anyway man.

---

### Post by Yellow Pasque on 2008-06-06
icedtea is now called openjdk (#2 in your menu).

I had to specify java after the command you gave.
```
sudo update-alternatives --config java
```

```
dan@harvest:/dev$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-4.2
*+        3    /usr/lib/jvm/java-6-openjdk/jre/bin/java

```

EDIT: You can remove the packages with 'icedtea' in the name
> Java runtime based on OpenJDK (transitional package)
This is a transitional package. It can safely be removed after an upgrade
to Ubuntu 8.04 (hardy).

---


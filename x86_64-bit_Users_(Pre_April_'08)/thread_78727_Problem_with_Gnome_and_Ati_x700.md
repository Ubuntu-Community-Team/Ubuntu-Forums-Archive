---
title: "Problem with Gnome and Ati x700"
date: 2005-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Eleka on 2005-10-18
Hello!

I'm tring to install completly Ubuntu 5.10 for AMD64 in my desktop. I have the issue of ubuntu did't recognize my graphic card and I've to use the vesa controller.

For now it's ok, because I want first configure all the rest ofthe hardware, because I don't play very much and don't use 3D dessigners for now.

But, I have a little (but exasperating) problem with the gnome language. I follow all the instructions detailed on my country's ubuntu guide. I installed all the recquierd packages, and in the language selector it's only marked my language, but the Gnome (and the entire system) is in english! I edited the /etc/enviroment but it's all equal ...

Can you help me?

---

### Post by jecos on 2005-10-19
Thats what your typing in whats wrong??  try to re-install the language in synaptic or make sure its there..

for the X700
Search fglrx in synaptic and install: fglrx-control, xorg-driver-fglrx and linux-restricted-modules from the search results fglrx comes up with.. and 
sudo dpkg-reconfigure xserver-xorg 
and set to driver to fglrx

---

### Post by Eleka on 2005-10-20
I explain:

When I do 
```
sudo aptitude install XXX
```

when it finish the work, it always say me this:
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "es_ES:es",
        LC_ALL = "es_ES.ISO-8859-15@euro",
        LC_TYPE = "es_ES.ISO-8859-15@euro",
        LC_MESSAGES = "es_ES.ISO-8859-15@euro",
        LANG = "es_ES.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
```

I'm tring now with the Ati :)

---

### Post by Eleka on 2005-10-25
Anybody can help me? I question the language probem in many forums and I haven't any answers ... :(

Anybody knows why it happens?

---

### Post by ToastedToad on 2005-10-25
$ sudo dpkg-reconfigure locales

Select the proper locales for your language.

---

### Post by Eleka on 2005-10-25
I did it and select all the locales for my language, and when I accept and finished the script, it have a segmentation fault and didn't write any change in configuration files ...

Some idea of whar are happening?

---

### Post by ToastedToad on 2005-10-26
Have you tried to edit /etc/locale.gen manually?

---

### Post by Eleka on 2005-10-26
I tried it this morning ... at the final of the script, when it make a while loop with this sintaxis:

```
while read locale charset; do \
	case $locale in \#*) continue;; "") continue;; esac; \
	is_entry_ok || continue
	if [ "$KEEP" ] && PERL_BADLANG=0 perl -MPOSIX -e \
	    'exit 1 unless setlocale(LC_ALL, $ARGV[0])' "$locale"; then
		continue
	fi

	echo -n "  `echo $locale | sed 's/\([^.\@]*\).*/\1/'`"; \
	echo -n ".$charset"; \
	echo -n `echo $locale | sed 's/\([^\@]*\)\(\@.*\)*/\2/'`; \
	echo -n '...'; \
        if [ -f $LOCALES/$locale ]; then input=$locale; else \
        input=`echo $locale | sed 's/\([^.]*\)[^@]*\(.*\)/\1\2/'`; fi; \
	localedef -i $input -c -f $charset -A /etc/locale.alias $locale; \
	echo ' done'; \
done < $LOCALEGEN
```

I don't understand it very well, but I think that it crash when read the "locale charset". I don't know what is the normal output of this command, but in my case, the output of run "locale charset" in a terminal is this:

```
joseluis@eleka-gaming:~$ sudo locale charset
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
```

Some idea? I'm going to the desesperation :D

---

### Post by Wloxen on 2006-03-31
I think you cannot set any locale to "es_ES.ISO-8859-15@euro", but to "es_ES@euro". The equivalences are:
.- es_ES@euro -> ISO-8859-15
.- es_ES -> ISO-8859-1
.- es_ES@UTF8 -> UTF8

---


---
title: "Evolution Spellcheck Language List Empty"
date: 2007-09-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by mmxbass on 2007-09-03
While using Kubuntu Gutsy, I notice that after I install Evolution, the spell check isn't working. So I go and check under composer preferences. It turns out the language selection list is empty! I have aspell-en and myspell-en-us installed so I'm not entirely sure why the list would possibly be empty.

---

### Post by onehotcutey on 2007-09-14
I am having the same issue in plain ole ubuntu as well.  Any solutions out there?

---

### Post by pappo on 2007-12-04
I had the same problem with my Linux-Mint distro.  My distro is Ubuntu based and is a Feisty 7.04 release.
I had no dictionaries showing up in my Evolution preferences.
I used apt to load the following packages and then restarted Evolution, and the English dictionaries showed up and the spell checker started working:

gnome-spell
aspell-en
myspell-en-us

Hope it works for you.

Regards,
pappo

---


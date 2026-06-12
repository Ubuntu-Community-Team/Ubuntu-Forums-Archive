---
title: "Envy 32-bit Compat Libs"
date: 2008-07-30
forum: x86 64-bit Users
---

### Post by Megatog615 on 2008-07-30
Are these installed with Envy? If not, how do I get them without having to use the official nvidia-installer?

---

### Post by flick on 2008-07-30
If you're talking about 32 bit stuff for things like watching Flash/YouTube, doing a :

sudo apt-get update && sudo apt-get install ubuntu-restricted-extras

should pull in the nonfree Flash plugin from Adobe, along with NSPluginwrapper and the 32 bit libraries needed to make it all work.

If you're talking about 32 bit libraries for some other purpose, please clarify, and I'll happily help search for the answer.

---

### Post by Megatog615 on 2008-07-30
NVIDIA supplies 32-bit OpenGL compatibility libraries with their installer(for running 32-bit games). I am trying to use Envy though. Envy does not supply these.

---

### Post by flick on 2008-07-30
Ah, ok. I did not know that, about the 32 bit OpenGL stuff. Thanks for telling me about it. Sorry I couldn't be of help.

---


---
title: "xmame"
date: 2005-06-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by FluffyElmo on 2005-06-27
Does any one have xmame running under Ubuntu 64bit? I've found references via google which imply that it works, but no specific instructions, and it's not working for me. And I could always install a chroot though I've avoided one so far and would prefer to stay purely 64bit. 

I'd appreciate any tips if anybody has it running, a brief list of what I've tried so far follows...

First, if I install from the repositories (Hoary or Breezy, they both have the same version) and try to run xmame.SDL or xmame.x11 I get the following error:
```
error: compiled byte ordering doesn't match machine byte ordering
are you sure you choose the right arch?
compiled for msb-first, are you sure you choose the right cpu in makefile.unix
```

So I've downloaded the source for v0.97 and have tried compiling it, but without luck so far. I've changed the cpu to amd64 in the makefile but still get a bunch of pointer cast size warnings and a number of errors relating to the XML parser.

Tomorrow I guess I will try compiling it using different versions of gcc and or try compiling it with a 32bit target. But I'm really hoping someone has been down this road already and can help me out:)

---


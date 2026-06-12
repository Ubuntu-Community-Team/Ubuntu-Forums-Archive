---
title: "How to get ndiswrapper?"
date: 2006-08-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by harisund on 2006-08-11
Helllo

On my laptop right now, I have wireless internet working on Dapper 32 bit using ndiswrapper and my Windows drivers 

Before making the switch to 64 bit, I wanted to ensure that I can continue to have it working by using ndiswrapper. Or is there no ndiswrapper for 64 bit? 

Also, what is the state of the RealPlayer? In the sticky by Hendrik, I read the line "if the movie uses RealPlayer, it is not worth checking at all" which upset me quite a bit.

---

### Post by tymek666 on 2006-08-11
The question is if your card has drivers for winxp 64. If yes, there's ndiswrapper for AMD64.

---

### Post by John Jason Jordan on 2006-08-11
> **harisund said:**
> On my laptop right now, I have wireless internet working on Dapper 32 bit using ndiswrapper and my Windows drivers 

Before making the switch to 64 bit, I wanted to ensure that I can continue to have it working by using ndiswrapper. Or is there no ndiswrapper for 64 bit? 
Can't answer the question without knowing what make/model wireless chip your laptop has. For example, Dapper now supports most Broadcom chips directly without needing ndiswrapper (although I have a Broadcom chip and found that the new Dapper driver for it didn't work very well, so I went back to ndiswrapper). And yes, there is a 64-bit ndiswrapper. You can just install it via Synaptic. 

> **harisund said:**
> Also, what is the state of the RealPlayer? In the sticky by Hendrik, I read the line "if the movie uses RealPlayer, it is not worth checking at all" which upset me quite a bit.
I have RealPlayer installed and working fine. You have to use -forcearchitecture to install it, but that's trivial. In fact, you can use Automatix to install it. Automatix is a script for installing obstinate stuff in 64-bit Dapper. You can find the specific instructions just by searching the forums.

---


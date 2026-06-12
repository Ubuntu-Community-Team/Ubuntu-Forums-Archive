---
title: "flash player install help"
date: 2008-04-28
forum: x86 64-bit Users
---

### Post by hitmanj on 2008-04-28
i downloaded flash player 9 and unpacked it and followed the instructions and get a error message. the error says: 
"ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer."

i don't know what else to do. can someone please help me?

---

### Post by crane on 2008-04-28
Looks like more info is needed. What version did you download? and what is your system?
 It sounds like you are trying to install 32bit version on a 64 bit system.
Not sure though, I am not too familiar with flash.

---

### Post by hitmanj on 2008-04-28
> **crane said:**
> Looks like more info is needed. What version did you download? and what is your system?
 It sounds like you are trying to install 32bit version on a 64 bit system.
Not sure though, I am not too familiar with flash.

i downloaded the x86 version because there was no x64 version. and i wouldnt be able to tell you my system because i dont know how to look it up in linux, sorry.

---

### Post by RyanJSull on 2008-04-28
Never used Ubuntu in amd64, but I currently run Gentoo in a 64 bit environment.  Flash is not released for linux in 64 bits.  There are a couple of workarounds: 
1. You can get a 32 bit binary of firefox, which will be compatable with a 32 bit plugin.  This worked in Gentoo because I had 32 bit librarys (I would guess this would be standard in Ubuntu, but you may have to search for it in synaptic).
2. Use a differant open-source alternative than flash. (can be problamatic sometimes because of comaptibility).
3. I forget what it it is called but i believe there is a 64 bit wrapper plugin for 32 bit plugins which you can run flash inside.  However, I hear the stability can be a problem with this solution.

On my gentoo install, i used the first option, and browse the web in 32 bits when i want to use flash.

---

### Post by vishalrao on 2008-04-28
To get Flash on Hardy amd64, I just visited a Flash-enabled page in Firefox where it asked to install the plugin and I clicked that (might have also clicked allow popup/install), I believe Ubuntu's FF plugin takes care of installing your choice of Adobe Flash or one of the other Free versions via the apt machinery... works fine for me.

---


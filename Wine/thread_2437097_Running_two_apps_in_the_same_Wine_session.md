---
title: "Running two apps in the same Wine session"
date: 2020-02-18
forum: Wine
---

### Post by rva1945 on 2020-02-18
Hi:

I want to run a RC planes simulator, Aerofly RC7. It can be controlled using a RC transmitter whose audio signal is fed into the mic input and there is an app, SmartPropoPlus that creates a virtual joystick (vJoy) with thoat audio signal. This works ok in a Windows 7 (not in a virtual box, I tried many times to no avail, it crashes, there is an issued with 3D acceleration).

So both SmartPropoPlus and Aerofly need to be running. How do I run them both as in the same session? I think that when running each one they will run in separate sessions, or maybe I'm wrong.

Anyway I know I will have to fix a problem: I tried to run Aerofly and it doesn't run as no OpenGL is installed.

Thanks.

---

### Post by mastablasta on 2020-02-18
interesting. well you owuld definitelly need ot install them in same prefix. wine is not an emulator so both will run in linux anyway (if they are supported).

you could maybe run them at the same time with a manually created .bat file?

---

### Post by rva1945 on 2020-02-18
What do you mean by the same prefix?
And
Will launching them in a .bat make them running in the same session?

---

### Post by CatKiller on 2020-02-18
> **rva1945 said:**
> So both SmartPropoPlus and Aerofly need to be running. How do I run them both as in the same session? I think that when running each one they will run in separate sessions, or maybe I'm wrong.

Wine works by creating pretend environments - pretend C:, pretend Windows - which are called prefixes. Each prefix is just a directory that holds the files and configuration. By default Wine uses just one prefix for everything. Other tools that use Wine - such as Lutris or Proton - default to using a different prefix for each application, so that they don't interfere with each other. In each case you can configure which prefix you want to use. 

Wine won't make every application work. Applications that directly interface with hardware are the least likely to work.

---


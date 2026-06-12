---
title: "Alt-Tab programs not showing up (Wine)"
date: 2008-05-02
forum: Wine
---

### Post by lcohen999 on 2008-05-02
I have two programs which I use quite extensively in Wine.

Anzio and Imgburn

Neither of them seem to show up when I do an alt-tab.

Any thoughts?

---

### Post by lcohen999 on 2008-05-06
:)

---

### Post by jbysmith on 2008-05-06
What build of Wine and Ubuntu?

Currently, I'm using 7.10 still as I figured I'd wait a bit on 8.04.. too many problem reports on the forums for my tastes yet, give it a bit to settle down.

Using the build that's in Ubuntu 7.10's repo.. ummmm 0.9.53? I forget.. that one worked properly with window behavior, but a few applications I need didn't work properly on it; needed a newer build for some bug fixes.

Using the 0.9.59 build out of the Wine repositories, and the stock Compiz Fusion out of the 7.10 repo, I was getting that exact behavior from a few Windows apps.  Not only did the task switcher seem to completely ignore the program, but if I minimized it, it was gone.  I had to do a wineserver -k to end the process.  

First thing I did as a test was to remove Compiz Fusion.  (Hey it *is* a beta and prone to problems)  Not just disabled it, but completely blasted it, just to narrow down the problem.  No help, still did the same thing.

Then, I compiled Wine from source following the instructions on the WineHQ site. (The last version in their 7.10 repo is 0.9.59, not updating anymore) Pretty easy really; downloaded the one script to get all the dependencies you need, then in the source tarball ran the build script to compile the thing.  After a half hour or so compiling, I had a working 0.9.60 build of Wine working.  (I haven't compiled 0.9.61 yet)

Helped a *lot*.  Programs don't get "lost" anymore. The task switcher was working better too.  Didn't always bring the task to the foreground, but it was listing them anyway.  I was happy as I didn't have to worry about forgetting not to minimize an app anymore.

Then, since I was happy I was able to compile Wine with no problems, I figured I'd compile Compiz Fusion from Git following some how-tos on the Ubuntu and Compiz forums. I actually had an easy time with that too, considering I'm a relative *Nix idiot still.  

Once I had that done, not only was Wine not losing windows, but the switchers were properly rendering previews, bringing windows to the foreground when switched to, the works.  (And the cylinder effect is just insanely neat.. cubes are sooooo 2007.)

Don't know if that'll help any, or I'm just flapping my gums, but it helped for my setup anyway.  For me, part of the issue was Compiz, mostly it was what version of Wine I was using.

---

### Post by lcohen999 on 2008-05-06
That is exactly what I ended up doing (before I read this email)

I am running .60 (.61 is buggy) and everything is back as it should.

I don't get a preview in Compiz Alt-Tab, but it does work, and that is what counts.

Thank you!

---


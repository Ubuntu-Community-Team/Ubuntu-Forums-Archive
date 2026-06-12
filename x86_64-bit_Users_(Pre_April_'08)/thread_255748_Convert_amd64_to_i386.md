---
title: "Convert amd64 to i386"
date: 2006-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by dmfrey on 2006-09-11
Good Evening All:

I am contemplating moving my ubuntu Dapper amd64 back to i386.  This is mainly for compatibility reasons and providing a better experience for others in my household.  I am looking for any instructions and pointers on the safest way to perform this.  Also, are there any risks that I should be aware of.

Thanks for your help.
Dan

---

### Post by kuja on 2006-09-12
The only way to do it is to do start over really. Get your hands on the i386 cd and well, you get the idea. In other words, converting doesn't happen, you just have to reinstall using the other cd.

---

### Post by Kilz on 2006-09-12
> **dmfrey said:**
> Good Evening All:

I am contemplating moving my ubuntu Dapper amd64 back to i386.  This is mainly for compatibility reasons and providing a better experience for others in my household.  I am looking for any instructions and pointers on the safest way to perform this.  Also, are there any risks that I should be aware of.

Thanks for your help.
Dan

Before you do that , could you please tell us what you think isnt compatible?

---

### Post by dmfrey on 2006-09-12
It is mostly to appease my wife using the ubuntu box.  Your basis flash compatibility and printer issues.  Also, firefox seems to close on her pretty frequently and I haven't determined a root cause yet for her.  I did notice your how-to for flash and firefox, so I am going to give that a try first.  I am going to hold off until I try that before I do any converting back to the i386.

Thanks for your help.

---

### Post by Kilz on 2006-09-12
> **dmfrey said:**
> It is mostly to appease my wife using the ubuntu box.  Your basis flash compatibility and printer issues.  Also, firefox seems to close on her pretty frequently and I haven't determined a root cause yet for her.  I did notice your how-to for flash and firefox, so I am going to give that a try first.  I am going to hold off until I try that before I do any converting back to the i386.

Thanks for your help.

I fully understand the wife issue. Mine has her own computer, the only one running Windows on my home network. I recommend the automatic install scripts on my howto if you are going to install 32bit firefox.

---

### Post by dmfrey on 2006-09-13
I used your scripts and they worked nicely.  They got me almost the whole way there.

2 Things to mention...
Java didn't seem to install correctly.  After the script ran, I immediately got a notification like there were newer packages to install.  The notification actually told me to go run sudo apt-get install -f to fix the broken package.  It ended up being the JRE.

Second, and I am not sure if this is related to the above (didn't finish and what not).  Flash did not get installed.  I still had to go into Firefox's plugin finder to install flash.  I did, however, see your script download and , what appeared to be, install flash.

Does your script produce any logs that I could send you, or anything I could try?

After those 2 issues, 32-bit firefox is working nicely on my amd64.

---

### Post by Kilz on 2006-09-13
> **dmfrey said:**
> I used your scripts and they worked nicely.  They got me almost the whole way there.

2 Things to mention...
Java didn't seem to install correctly.  After the script ran, I immediately got a notification like there were newer packages to install.  The notification actually told me to go run sudo apt-get install -f to fix the broken package.  It ended up being the JRE.

Second, and I am not sure if this is related to the above (didn't finish and what not).  Flash did not get installed.  I still had to go into Firefox's plugin finder to install flash.  I did, however, see your script download and , what appeared to be, install flash.

Does your script produce any logs that I could send you, or anything I could try?

After those 2 issues, 32-bit firefox is working nicely on my amd64.

So now there is a Firefox 32 in the menu right? You did make sure the Universe and Multiverse repositories were enabled before running the script right? If the repositories are not enabled plugins dont get installed sometimes.
Make sure that all browsers are closed, then open the 32bit firefox from the menu. Click Help then About Mozilla Firefox and make sure it says ```
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.6) Gecko/20060728 Firefox/1.5.0.6
``` at the botton. Type ```
about:plugins
``` into the address bar, and see what plugins are installed.
Im going to look into the java plugin error and post back here what I find.

---

### Post by mwshook on 2006-09-13
Being an "Absolute Beginner," I installed the AMD64 distribution in the mistaken belief that it was my only choice with an AMD64 processor.

I've gotten tired of futzing around with HOWTOs and tips and tricks. I got Flash working, but not Java or FreeNX. I'm tired of configure/make/install (it makes me feel dirty).

I do thank everyone in this forum for all the help, but I seem to be a newbie with Linux flavor intended for the cutting-edge types. I'll probably just stick to apps available in the Add/Remove Programs list for now, and maybe re-install with i386 when I get a free weekend.

It does make me sad to feel that I'm not getting the most out of my computer :-(

---

### Post by Kilz on 2006-09-14
> **mwshook said:**
> Being an "Absolute Beginner," I installed the AMD64 distribution in the mistaken belief that it was my only choice with an AMD64 processor.

I've gotten tired of futzing around with HOWTOs and tips and tricks. I got Flash working, but not Java or FreeNX. I'm tired of configure/make/install (it makes me feel dirty).

I do thank everyone in this forum for all the help, but I seem to be a newbie with Linux flavor intended for the cutting-edge types. I'll probably just stick to apps available in the Add/Remove Programs list for now, and maybe re-install with i386 when I get a free weekend.

It does make me sad to feel that I'm not getting the most out of my computer :-(
Part of having an AMD or modern Intell 64bit processor is being able to run an environment of mixed32 and 64bit. Its designed into it. Howto's that show you how to do this manually are a good thing. My automatic scripts use i386 .deb files. The same ones you will use if you install the 32bit version.
You shouldnt have to configure/make/install to get java running. You may have to for some program, but that's a part of Linux. Being able to compile a application. Its a benefit, not something "dirty". You will even have to do it on the i386 version to get some applications. Nothing on Linux is 100% automatic, never have to mess with the command line, just click and its done. No matter what distro or version.

---

### Post by dmfrey on 2006-09-14
Yeah, the firefox32 was in the menu.  I was able to open it, but the flash plugin didn't seem to install.  That is why i hasd to do it from within firefox.

---

### Post by Pinoy915 on 2006-09-14
I have a weird problem. I had everything working but now it's not. My Firefox 32 will not load up. It's always loading the AMD64 Firefox. Plugins work with Opera though. I tried running the firefox32 command and the shortcut in my menu but both are loading the default one instead. Anyway to get Firefox 32 back?

---

### Post by Kilz on 2006-09-14
> **Pinoy915 said:**
> I have a weird problem. I had everything working but now it's not. My Firefox 32 will not load up. It's always loading the AMD64 Firefox. Plugins work with Opera though. I tried running the firefox32 command and the shortcut in my menu but both are loading the default one instead. Anyway to get Firefox 32 back?

When you tried the 32bit version, did you have the 64bit version open? For some reason once you have one open no matter what link you use it starts that version. Try it again making sure all browser windows are closed.

---

### Post by justaguynpc on 2006-09-14
Quick question..........Before I ran across Kilz' Firefox 32 thread, I installed the native (?) 64 bit Firefox browser from synaptic.  (Why synaptic?  I am more accustomed to it after having spend alot of time using Ubuntu).  I then proceeded to install the Firefox 32 package.

After successfully installing Java and Flash, and unsuccessfully installing the MPlayer for Firefox32, I noticed that both the Flash and Java plugins are also alive and well (and WORKING) in the Firefox64 version.

Finally, the question arises, do I need both?  Can I uninstall one?  If so, which do I uninstall, which could potentially cause the least amout of "collateral damage"?

Kilz, are you there?  

Cheers .............

---

### Post by Pinoy915 on 2006-09-14
It works again now but that's weird that it does that.

---

### Post by Kilz on 2006-09-14
> **justaguynpc said:**
> Quick question..........Before I ran across Kilz' Firefox 32 thread, I installed the native (?) 64 bit Firefox browser from synaptic.  (Why synaptic?  I am more accustomed to it after having spend alot of time using Ubuntu).  I then proceeded to install the Firefox 32 package.

After successfully installing Java and Flash, and unsuccessfully installing the MPlayer for Firefox32, I noticed that both the Flash and Java plugins are also alive and well (and WORKING) in the Firefox64 version.

Finally, the question arises, do I need both?  Can I uninstall one?  If so, which do I uninstall, which could potentially cause the least amout of "collateral damage"?

Kilz, are you there?  

Cheers .............

Macromedia Flash plugin will not work in the 64bit browser. 32bit plugins wont work at all in a 64bit browser. Since you have both installed it may be confusing you what browser is actualy rrunning. Because as I explained in the above post. If I have the 32bit version of firefox open, and I click on any other firefox link, no matter where. The browser that will open in the second instance will be the 32bit one.
If I were to remove one version it would be the 64bit version. I would just delete the 46bit version
```
rm -rfd /usr/lib/firefox 
```
and replace it with a symbolic link to the 32bit install. 
```
ln -s /usr/local/firefox32 /usr/lib/firefox
```
That way any programs that use it will open up the 32version without a lot of setup.
I have done a lot of work in the last week or so on the firefox- flash-mplayer script. You may want to give it a try. Just reinstall it. There have even been some nice improvements to firefox.

---

### Post by Kilz on 2006-09-14
> **Pinoy915 said:**
> It works again now but that's weird that it does that.

I agree :D  but its a minor flaw that most people can live with as long as they know about it.

---


---
title: "Whn i try to start wine it restarts my session"
date: 2008-05-31
forum: Wine
---

### Post by Snappo on 2008-05-31
title says it all etc

ubuntu hardy

---

### Post by cogadh on 2008-05-31
What are you trying to run with Wine? How are you launching it?

---

### Post by Snappo on 2008-05-31
> **cogadh said:**
> What are you trying to run with Wine? How are you launching it?

i'm click the "configure wine" dropdown under wine on the applications menu.

---

### Post by cogadh on 2008-05-31
Open a terminal and run "winecfg" to see if it does the same thing.

---

### Post by Snappo on 2008-05-31
> **cogadh said:**
> Open a terminal and run "winecfg" to see if it does the same thing.

It does

---

### Post by cogadh on 2008-05-31
That's really odd...

Have you tried completely removing and reinstalling Wine?
```
sudo apt-get remove --purge wine
rm -r ~/.wine
sudo apt-get install wine
winecfg
```

---

### Post by Snappo on 2008-05-31
> **cogadh said:**
> That's really odd...

Have you tried completely removing and reinstalling Wine?
```
sudo apt-get remove --purge wine
rm -r ~/.wine
sudo apt-get install wine
winecfg
```

yes same result

wait i get errors and if i sudo i get in trouble for not being the owner of that account

---

### Post by Overquoted on 2008-06-01
I'm having the same issue on a new install of Hardy on a new system. AMD Athlon 64 X2 4800+, Asus M2V-MX SE AM2 VIA K8M890 + 8237S (onboard video), 1GB DDR2 800 (PC 6400) RAM. I've made sure I have Wine HQ's repository and it's currently installing wine_0.9.59-0ubuntu5_amd64.deb. After completely removing and reinstalling Wine, I am still having the issue. It seems similar to (or is) bug #12561, but the work-around for it doesn't help.

Partial read-out from terminal when I start Wine (partial because I have to hit ctr+C to stop from being booted to the login screen and losing the terminal read-out):

```
preloader: Warning: failed to reserve range 00000000-60000000
wine: creating configuration directory '/home/revelry/.wine'...
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

name@Desktop:~$ err:module:attach_process_dlls "gdi32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\rundll32.exe" failed, status c000013a
```

After attempting the [work-around]("http://wiki.winehq.org/PreloaderPageZeroProblem") and entering winecfg in the terminal (cut short by ctr+C):

```
wine: creating configuration directory '/home/revelry/.wine'...
err:module:attach_process_dlls "gdi32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\rundll32.exe" failed, status c000013a
```

If I don't hit ctr+c (or don't hit it soon enough), I get a weird error and then it slams me back to the login window:

```
wine: creating configuration directory '/home/revelry/.wine'...
Could not load Mozilla. HTML rendering will be disabled.
```

Also, the first post-work-around error only occurs initially. If I hit ctr+c after trying winecfg again, I just get the Mozilla error (which also occurs without ctr+c).

Once I've logged back in, I can pull up System Monitor and there are multiple instances of dbus-daemon, gnome-vfs-daemon (only two, whereas the others are for each boot back), gvsfd, gvfsd-burn, gvfsd-trash, trackered. Then there's the Wine services up and running (which does not occur before the work-around): explorer.exe, rundll32.exe, services.exe (x2), wineprefixcreat, wineserver (x2).


I may just try to go down (or up) a Wine version tonight, but I figured I'd throw in this info in case the bug doesn't go away (ie, if it's relevant more to Hardy than Wine).

(My old setup - upgraded to Hardy - had no Wine issues.)

---

### Post by Overquoted on 2008-06-01
So I tried completely removing 0.9.59 and installing 0.9.60. I didn't receive the 'reserve range' errors. However, I haven't rebooted so it may be that the previous work-around is still in effect. It did, however, repeat the HTML rendering error and I went back to the login screen.

So I removed that one and installed 1.0-rc1. Opening winecfg went fine, though it displayed the HTML rendering error (how this will effect apps later installed, I'm not sure). But since I can access Wine now without being sent to the login screen, I'm not upset over it. I mostly wanted to use Wine for uTorrent anyway.

Installing uTorrent did as asked once I right-clicked, but installing from terminal resulted in this error:

```
wine: could not load L"C:\\windows\\system32\\install.exe": Module not found
```

Feh. Is 1.0-rc1 stable?

Snappo, are you on an Intel or AMD system?

---

### Post by cogadh on 2008-06-01
> **Snappo said:**
> yes same result

wait i get errors and if i sudo i get in trouble for not being the owner of that account
What do you mean you get errors when you "sudo"? Are you using sudo to run Wine? If so, don't do that, it screws up Wine's permissions and makes Wine into a potential security risk. If you have used sudo to run Wine in the past, then you need to remove the .wine directory and start all over again:
```
sudo rm -r ~/.wine
```

@Overquoted
You are getting those HTML rendering messages because you haven't installed the Wine Gecko HTML rendering engine yet:
```
wine iexplore http://www.winehq.org
```
Follow the prompts and the engine will install itself. You'll know the install was successful when the WineHQ web page is displayed.

The "could not load" error happens when you try running something without being in the correct directory or without specifying the correct directory path. For example, if the Windows executable you are trying to run is on the Desktop, then you need to either specify that, or change directories to the Desktop, then run it:
```
wine ~/Desktop/windows_executable.exe
```
OR
```
cd ~/Desktop
wine windows_executable.exe
```
Wine 1.0-rc1 is a "Release Candidate", by definition, that is not necessarily stable. Wine itself has never been considered stable, since it has been in beta for most of the last 15 years. The first true stable release of Wine will be the official 1.0 release, supposedly due sometime this June.

---

### Post by Overquoted on 2008-06-02
> You are getting those HTML rendering messages because you haven't installed the Wine Gecko HTML rendering engine yet:
wine iexplore [http://www.winehq.org](http://www.winehq.org)

Why would it pop up at all? It didn't on my previous build (even after the upgrade to Hardy) and I never installed iexplore. It was also the last error before a brief freeze and then going back to the login screen.

> The "could not load" error happens when you try running something without being in the correct directory or without specifying the correct directory path. For example, if the Windows executable you are trying to run is on the Desktop, then you need to either specify that, or change directories to the Desktop, then run it

Actually, you're wrong, at least in this case. I had the right directory (it was on Desktop, in fact). To make sure I wasn't entering it incorrectly in the terminal after the first error, I copied it directly from the Location Bar.

But it's not a big deal (I can just right-click an app for install), and it's completely unrelated to the original issue.

> Wine 1.0-rc1 is a "Release Candidate", by definition, that is not necessarily stable. Wine itself has never been considered stable, since it has been in beta for most of the last 15 years. The first true stable release of Wine will be the official 1.0 release, supposedly due sometime this June.

Stable-ish then. :P

---

### Post by cogadh on 2008-06-02
> **Overquoted said:**
> Why would it pop up at all? It didn't on my previous build (even after the upgrade to Hardy) and I never installed iexplore. It was also the last error before a brief freeze and then going back to the login screen.
It didn't happen before because that check was not in place in previous Wine versions. You don't have to install iexplore, it comes with Wine. Its not actually Internet Explorer, just a functional shell that the Gecko engine runs in.
> Actually, you're wrong, at least in this case. I had the right directory (it was on Desktop, in fact). To make sure I wasn't entering it incorrectly in the terminal after the first error, I copied it directly from the Location Bar.

But it's not a big deal (I can just right-click an app for install), and it's completely unrelated to the original issue.
Sorry, but in order to get that error, you must have the wrong directory specified in the path, or you didn't specify the path and were trying to run it from the wrong directory. When you run an application, Wine first checks the current or specified directory, then if it can't find the executable you are trying to run there, it assumes you are trying to run a Windows system executable and looks in the System32 directory for it. When it can't find it there, it produces the "could not load" error message you saw. There is no other way (that I am aware of) to produce that particular error message.
> Stable-ish then. :P
Yeah, "stable-ish" is fair. Just remember, stable doesn't necessarily mean functional, it just means it isn't so buggy that it will crash constantly. Even though Wine 1.0 will be out soon, it is still not a complete implementation of the Windows API, so you will likely still run into a lot of applications that won't work properly.

---

### Post by Snappo on 2008-06-02
I'm getting the same shyt as this other guy and i'm on an 32 bit system.

---


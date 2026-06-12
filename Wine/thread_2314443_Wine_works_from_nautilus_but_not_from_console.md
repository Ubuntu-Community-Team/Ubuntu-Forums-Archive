---
title: "Wine works from nautilus but not from console"
date: 2016-02-21
forum: Wine
---

### Post by Zorgoth on 2016-02-21
I was trying to play an old game (the 2000 version of Reach For The Stars, which does not have a WineHQ page), and I found that I can open it by launching it from nautilus using "Open With Wine Windows Program Loader", but not by using the wine command from the terminal.

What can cause those two methods to behave differently, and how can I use the command line to get the same behavior I would get from nautilus?

The only error message when opening from console is:

fixme:service:scmdatabase_autostart_services Auto-start service L"dxregsvc" failed to start: 2

Then I get a dialog box entitled Microsoft Visual C++ Runtime Library that says:

Runtime Error!
....path to executable
abnormal program termination

---

### Post by kc1di on 2016-02-21
What is the actual command you used?
Wine is a hidden folder on your home partition and must be addressed as such.  you may find it easier to install playonlinux it's in the repository and install the game from there.
it will also allow you to use newer or older versions of wine which may be of help with older games. good luck :)

---

### Post by Zorgoth on 2016-02-21
I ran 

wine C:\ Program\ Files\ \(x86\)\\SSI\\Reach\ For\ The\ Stars\\reach\ for\ the\ stars.exe

Running

wine ~/.wine/Program\ Files\ \(x86\)\\SSI\\Reach\ For\ The\ Stars\\reach\ for\ the\ stars.exe

does the same thing.

I've used wine a lot and I've never had a program work from nautilus and not work from the terminal before. That is what is confusing me here. It is obnoxious because there are a few errors ingame and I have no opportunity to debug.

I also tried running wine in a 32-bit wine prefix, but this did not change anything.

---


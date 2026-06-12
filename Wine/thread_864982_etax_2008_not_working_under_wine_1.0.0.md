---
title: "etax 2008 not working under wine 1.0.0"
date: 2008-07-20
forum: Wine
---

### Post by map7 on 2008-07-20
I've installed wine 1.0.0 under Ubuntu 804 then installed etax 2008.  etax worked all the way up to the Validation stage put it cannot connect to the internet, it's like a DLL is missing or some library function to connect to the internet.

I used these commands to install etax:
# apt-get install wine
# wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks) && sh winetricks msxml4

Here is the error I get at the Validation stage.
err:ole:CoGetClassObject class {76a64158-cb41-11d1-8b02-00600806d9b6} not registered
err:ole:create_server class {76a64158-cb41-11d1-8b02-00600806d9b6} not registered
err:ole:CoGetClassObject no class object {76a64158-cb41-11d1-8b02-00600806d9b6} could be created for context 0x5

---


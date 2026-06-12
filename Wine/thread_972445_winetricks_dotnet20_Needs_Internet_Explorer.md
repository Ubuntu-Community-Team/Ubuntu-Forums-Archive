---
title: "winetricks dotnet20: Needs Internet Explorer?"
date: 2008-11-05
forum: Wine
---

### Post by Tarvok on 2008-11-05
winetricks dotnet20

It opens up a nifty installer, but the installer complains that I don't have Internet Explorer 5.1 installed. So I use a well known script (can't remember what it's called) to install Internet Explorer. I figured 6.0 would be fine, but it didn't help. The installer still complains I don't have IE 5.1.

Does anybody have any suggestions?

---

### Post by Tarvok on 2008-11-06
Could somebody who is fairly knowledgeable about this at least post in this thread to say "I've never heard of this before." I can't find anything about it on the 'net (aside from one other post in this forum where the OP says "NM, figured it out" but does not elaborate as to how he fixed it).

I'm at the point where if I ever have sufficient disposable income to justify buying a copy of Windows, I will. Honestly, I'm tired of fighting with Linux.

---

### Post by Tarvok on 2008-11-09
I've looked a little deeper into this, and I've noticed the words "requires Windows license." I don't actually have one of those (my computer was totally clean, built for Linux only). Could that be the reason this isn't working?

---

### Post by binbash on 2008-11-09
i guess you mean winetricks script and fakeie6 part?

---

### Post by cogadh on 2008-11-09
See the Wine [Useful Registry Keys](http://wiki.winehq.org/UsefulRegistryKeys) page for info on how to fake an IE version in the Wine registry (scroll down to the "HKEY_LOCAL_MACHINE" section). That may allow the installation to continue.

Almost forgot, the "requires Windows license" thing is just a legal requirement, not an installation requirement. Technically by installing it anywhere without at least owning a Windows license is a violation of the MS license agreement.

---


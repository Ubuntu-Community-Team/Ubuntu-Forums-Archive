---
title: "Moon Base Alpha"
date: 2013-09-18
forum: Wine
---

### Post by innocent-devil85 on 2013-09-18
So I've successfully installed steam through wine and downloaded moon base alpha, but I am unable to play it. First error message consisted of missing .dll files which I dragged into the Win32 and Winow64 (probably spelt it wrong). The missing files were dwrite.dll, d3d10_1.dll, and d2d1.dll. Every time I click play it just stick on installing Microsoft Direct X. So I decided to check every box label microsoft direct x in the install windows component option. That still doesn't work, now I'm stuck forever installing this Microsoft Direct X.  Can someone please help me

---

### Post by fireflower on 2013-09-18
[** Before asking for help with Wine << PLEASE READ BEFORE POSTING **]("http://ubuntuforums.org/showthread.php?t=885111")

> 4. Do not try and install DirectX - Wine already has its own implementation of DirectX, and attempting to install the Windows version might break some things. Cancel or skip the install if an application prompts you.

---

### Post by innocent-devil85 on 2013-09-19
I understand that I may have worsen the problem, but are you able to help me fix it?

---

### Post by fireflower on 2013-09-19
[** Before asking for help with Wine << PLEASE READ BEFORE POSTING **](http://ubuntuforums.org/showthread.php?t=885111) > 5. Reinstalling Wine won't help - Reinstalling the same Wine package in Synaptic or Software Center won't do anything - your virtual Windows drive and applications will be just the same unless you manually remove them. What you probably wanted to do is erase your fake Windows install entirely; to do this, you must remove (or rename) the hidden .wine folder in your home directory (view->show hidden files). This will erase all Windows applications you've installed with Wine and let you start fresh. Note that you'll still have (nonworking) start menu entries for the removed apps in Applications->Wine unless you first removed them with Wine's uninstaller.

---


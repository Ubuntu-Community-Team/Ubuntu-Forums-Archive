---
title: "Installing Another App Using Wine?"
date: 2021-08-27
forum: Wine
---

### Post by wyattwhiteeagle on 2021-08-27
For apps that need Wine, every guide and tutorial I see never mentions anything about "If you already have Wine installed".

Those that do, tell to uninstall Wine and everything about it and update then reinstall what all you had.

I installed Wine-(staging) then installed a windows .exe app.

How can I install another app under Wine without uninstalling and reinstalling Wine?

---

### Post by deadflowr on 2021-08-28
Where does it tell you that it needs to be uninstalled?
You should be able to just install the app you want the same as you did the first app.

---

### Post by wyattwhiteeagle on 2021-08-28
> **deadflowr said:**
> Where does it tell you that it needs to be uninstalled?

At [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)

> [COLOR=#000000][FONT=&amp]Installing WineHQ packages[/FONT][/COLOR][COLOR=#000000][FONT=&amp]
...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]If you have previously installed a Wine package from another repository, please remove it and any packages that depend on it (e.g., wine-mono, wine-gecko, winetricks) before attempting to install the WineHQ packages, as they may cause dependency conflicts.[/FONT][/COLOR]

I was wondering if each individual app carries the same kind/type of issue's.

> **deadflowr said:**
> You should be able to just install the app you want the same as you did the first app.

Ok, when I can't find a satisfying equivalent, I will try it.
I'm gonna try KolourPaint before seeing how WinXP's mspaint.exe will work.

---

### Post by monkeybrain20122 on 2021-08-28
> **wyattwhiteeagle said:**
> At [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)



Maybe you misunderstood what the link says, or we misunderstood what you said. The link says if you have installed other versions of wine, they should be uninstalled before you use winehq's version, not that you have to uninstall and reinstall wine everytime you install an application that needs wine. A "wine package" in the link means a package in the wine suit, not a Windows application that needs wine.

Not withstanding what winehq wiki says, you can have multiple versions of wine installed through playonlinux (which is in the repo), this is very handy because it happens very often that an app may run in one version of wine but not another.

---

### Post by wyattwhiteeagle on 2021-08-28
> **monkeybrain20122 said:**
> Maybe you misunderstood what the link says, or we misunderstood what you said. The link says if you have installed other versions of wine, they should be uninstalled before you use winehq's version, not that you have to uninstall and reinstall wine everytime you install an application that needs wine. A "wine package" in the link means a package in the wine suit, not a Windows application that needs wine.

Thank you

I misunderstood what the link says. Happens to me a lot.

> **monkeybrain20122 said:**
> Not withstanding what winehq wiki says, you can have multiple versions of wine installed through playonlinux (which is in the repo), this is very handy because it happens very often that an app may run in one version of wine but not another.

I don't quite understand.

like say...Windows Experience Index...Do you mean Wine stable may not run it but Wine devel might?

or do you mean the current version of Wine, no matter the branch, may not run it but an older Wine will run it?

Please clarify.

---

### Post by monkeybrain20122 on 2021-08-28
> **wyattwhiteeagle said:**
> 


like say...Windows Experience Index...Do you mean Wine stable may not run it but Wine devel might?

or do you mean the current version of Wine, no matter the branch, may not run it but an older Wine will run it?

Please clarify.


Yes and yes.

---

